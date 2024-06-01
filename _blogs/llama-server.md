---
title: 로컬에서 llama.cpp로 LLM 실행하기
subTitle:
category:
tags:
createdat: 2024-06-01 20:24:00
updatedat: 2024-06-01 20:29:36
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

## 지원 모델들

LLaMA
LLaMA 2
LLaMA 3
Mistral 7B
Mixtral MoE
DBRX
Falcon
Chinese LLaMA / Alpaca and Chinese LLaMA-2 / Alpaca-2
Vigogne (French)
Koala
Baichuan 1 & 2 + derivations
Aquila 1 & 2
Starcoder models
Refact
MPT
Bloom
Yi models
StableLM models
Deepseek models
Qwen models
PLaMo-13B
Phi models
GPT-2
Orion 14B
InternLM2
CodeShell
Gemma
Mamba
Grok-1
Xverse
Command-R models
SEA-LION
GritLM-7B + GritLM-8x7B
OLMo
GPT-NeoX + Pythia

## 참고

사용가능한 API 스펙 (OpenAPI 스펙) 문서: <https://github.com/openai/openai-openapi/blob/master/openapi.yaml>
모델 목록: <https://huggingface.co/models>
llama.cpp README: <https://github.com/ggerganov/llama.cpp>
llama-server README: <https://github.com/ggerganov/llama.cpp/blob/master/examples/server/README.md>
