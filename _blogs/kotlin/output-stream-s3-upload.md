---
title: OuputStream을 S3에 업로드하려면 어떻게 해야 하나요?
createdat: 2024-09-18 01:57:00
updatedat: 2024-09-18 13:19:36
---

## 문제

OutputStream으로 만들어진 데이터를 바로 AWS S3로 전송하고 싶다. 하지만 AWS의
SDK의 `RequestBody`는 InputStream만 입력으로 받고 있어서 OutputStream을
InputStream으로 바꿔야 한다.

## 해결

1. OutputStream을 ByteArray로 만든 후 InputStream을 만들 수 있다.
2. PipedInputStream과 PipedOutputStream을 사용해서 추가적인 ByteArray를 만들지 않고 바로 InputStream으로 변환할 수 있다.
3. `AsyncRequestBody.forBlockingOutputStream`을 이용해서 OutputStream을 바로 업로드할 수 있다.

## 설명

### 1.OutputStream을 ByteArray로 변환

```kotlin
fun main() {
    val outputStream = ByteArrayOutputStream()
    outputStream.write("Hello, World!".toByteArray())

    val inputStream = ByteArrayInputStream(outputStream.toByteArray())
    outputStream.close()

    val s3Client = S3Client.builder()
        .credentialsProvider(
            StaticCredentialsProvider.create(
                AwsBasicCredentials.create("KEY", "SECRET_KEY")
            )
        )
        .region(Region.AP_NORTHEAST_2)
        .build()

    // OutputStream을 InputStream으로 변환


    val body = RequestBody.fromInputStream(
      inputStream,
      inputStream.available().toLong()
    )
    inputStream.close()

    s3Client.putObject({
        it.bucket("bucket-upload-sample").key("filename.txt").build()
    }, body)
}
```

이 방법은 가장 간단하지만, ByteArray를 다시 만들어야 하므로 데이터 크기 만큼의 메모리를 사용할 수 있으므로 주의해야 합니다.

### 2. PipedStream을 사용

```kotlin
suspend fun main() {
  coroutineScope {
    val inputStream = PipedInputStream()
    val outputStream = PipedOutputStream(inputStream)

    val job1 = launch(Dispatchers.IO) {
      outputStream.write("Hello, World!".toByteArray())
      outputStream.close()
    }

    val job2 = launch(Dispatchers.IO) {
      // S3Client 대신에 S3AsyncClient 사용
      val s3Client = S3AsyncClient.builder()
          .credentialsProvider(
              StaticCredentialsProvider.create(
                  AwsBasicCredentials.create("KEY", "SECRET")
              )
          )
          .multipartEnabled(true) // 멀티파트로 업로드 활성화
          .region(Region.AP_NORTHEAST_2)
          .build()

      // null을 넘긴다는 것은 스트림의 길이를 알 수 없다는 것을 의미
      val body = AsyncRequestBody.forBlockingInputStream(null)

      val future = s3Client.putObject({
          it.bucket("bucket-upload-sample").key("filename.txt").build()
      }, body)

      body.writeInputStream(inputStream)
      inputStream.close()

      future.join()
    }

    job1.join()
    job2.join()
  }
}
```

PipedStream을 사용하면 데이터를 OutputStream에 쓰는 만큼 동시에 InputStream으로 데이터를 읽어서 추가적인 ByteArray를 만들지 않고 InputStream으로 변경할 수 있습니다.

### 3. forBlockingOutputStream 사용

```kotlin
fun main() {
    // S3Client 대신에 S3AsyncClient 사용
      val s3Client = S3AsyncClient.builder()
          .credentialsProvider(
              StaticCredentialsProvider.create(
                  AwsBasicCredentials.create("KEY", "SECRET")
              )
          )
          .multipartEnabled(true) // 멀티파트로 업로드 활성화
          .region(Region.AP_NORTHEAST_2)
          .build()

    // null을 넘긴다는 것은 스트림의 길이를 알 수 없다는 것을 의미
    val body = AsyncRequestBody.forBlockingOutputStream(null)
    val future = s3Client.putObject({
        it.bucket("bucket-upload-sample").key("filename.txt").build()
    }, body)

    body.outputStream().use {
        it.write("Hello, World!".toByteArray())
    }

    future.join()
}
```

`forBlockingOutputStream`을 이용하면 OutputStream으로 만든 데이터를 바로 S3로 업로드할 수 있습니다.

## 문제 해결

```bash
java.util.concurrent.CancellationException: subscription has been cancelled.
```

만약 위와 같은 에러가 발생한다면 Multipart로 업로드하는 설정이 활성화되지
않았는지 확인해 봐야 합니다. 다음과 같이 `multipartEnabled(true)`로 멀티파트로 업로드 설정을 해야 합니다.

```kotlin
S3AsyncClient.builder()
    .credentialsProvider(
        StaticCredentialsProvider.create(
            AwsBasicCredentials.create("KEY", "SECRET")
        )
    )
    .multipartEnabled(true) // 멀티파트로 업로드 활성화
    .region(Region.AP_NORTHEAST_2)
    .build()
```
