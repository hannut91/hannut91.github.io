---
title: 로컬에서 GPT 실행하기 (llama.cpp)
subTitle:
category:
tags:
createdat: 2024-06-01 20:24:00
updatedat: 2024-06-09 14:06:37
---

## 서버 설치 && 서버 실행

```bash
brew install llama.cpp # llama.cpp 설치
llama-server --hf-repo microsoft/Phi-3-mini-4k-instruct-gguf --hf-file Phi-3-mini-4k-instruct-q4.gguf
```

서버를 설치하고 실행한 다음에 브라우저에서 `localhost:8080`으로 접속하면 다음과
같은 화면이 나옵니다.

![main page](/images/blogs/llama-server/page.png)

맨 아래에 프롬프트를 입력하고 엔터 혹은 `send`버튼을 클릭합니다.

![chat](/images/blogs/llama-server/chat.png)

그러면 응답이 오는 것을 확인할 수 있습니다. 채팅창에 입력을 하여 계속 사용할 수 있습니다.

### HTTP로 프롬프트 요청하기

HTTP 요청으로도 프롬프트를 입력할 수 있습니다.

```bash
$ curl -X POST http://localhost:8080/v1/chat/completions \
-H "Content-Type: application/json" \
-d '{
  "model": "phi3",
  "messages": [
    { "role": "user", "content": "Why is the sky blue?" }
  ]
}'

# 응답
{
  "choices": [
    {
      "finish_reason": "stop",
      "index": 0,
      "message": {
        "content": " The sky appears blue to the human eye because of a phenomenon called Rayleigh scattering. When sunlight reaches Earth's atmosphere, it is made up of different colors of light, which correspond to different 
# ... 생략
```

## 모델 다운 받고, 받은걸로 실행

### hugging-face cli 설치

```bash
pip install huggingface_hub
huggingface-cli login
```

### 모델 다운받고, 다운받은 모델로 llama-server 실행

```bash
huggingface-cli download microsoft/Phi-3-mini-4k-instruct-gguf --local-dir phi3
llama-server --model ./phi3/Phi-3-mini-4k-instruct-q4.gguf
```

## safetensors파일 quantize하기

```bash
# 모델 파일 다운로드
huggingface-cli JetBrains/CodeLlama-7B-Kexer --local-dir CodeLlama-7B-Kexer
# quantize
docker run --rm -v /path/to/model/CodeLlama-7B-Kexer:/repo ollama/quantize -q q4_0 /repo
# 라마 서버 실행
llama-server --model /path/to/model/CodeLlama-7B-Kexer/q4_0.bin
```

### 직접 빌드해서 하는 방법

```bash
git clone git@github.com:ggerganov/llama.cpp.git
cd llama.cpp
pip install -r requirements.txt
python convert-hf-to-gguf.py /path/to/model/CodeLlama-7B-Kexer
make -C llm/llama.cpp quantize
./quantize /path/to/model/CodeLlama-7B-Kexer/ggml-model-f16.gguf /path/to/model/CodeLlama-7B-Kexer/ggml-model-Q4_K_M.gguf Q4_K_M
```

## 참고

- [사용가능한 API 스펙 (OpenAPI 스펙) 문서](https://github.com/openai/openai-openapi/blob/master/openapi.yaml)
- <https://github.com/ggerganov/llama.cpp>
- [llama-server README](https://github.com/ggerganov/llama.cpp/blob/master/examples/server/README.md)
- <https://hub.docker.com/r/ollama/quantize>
