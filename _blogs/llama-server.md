---
title: 로컬에서 llama.cpp로 LLM 실행하기
subTitle:
category:
tags:
createdat: 2024-06-01 20:24:00
updatedat: 2024-06-02 19:41:05
---

## 서버 설치 && 서버 실행

```bash
brew install llama.cpp # llama.cpp 설치
llama-server --hf-repo microsoft/Phi-3-mini-4k-instruct-gguf --hf-file Phi-3-mini-4k-instruct-q4.gguf
```

## 명령 실행

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
- [](https://hub.docker.com/r/ollama/quantize)
