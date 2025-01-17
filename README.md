

## 튜토리얼을 ChatGPT로 하는 이유 

저희의 목표는 Local에서 작동되는 Ollama를 이용하는것이지만, 
이 Ollama를 fine-tunning 하기 위해서는 정답에 가까운 아주 좋은 성능의 
LLM의 답변으로 이루어진 질문-답변 데이터셋이 필요합니다.

따라서 먼저 ChatGPT로 튜토리얼을 진행하여, 잘 대답하는 것을 확인하고 

RAG를 구축하여 ROS2 명령어 생성을 잘하고, 로봇을 잘 컨트롤 하는지 확인하여 ROS AI Agent를 구축합니다.

이후, 구축한 ChatGPT ROS AI Agent를 이용해 질문-답변 데이터셋을 구축합니다.

그리고 이렇게 구축한 데이터셋으로 Llama 3.2에 LLM Fine-tunning을 진행합니다. 

### 요약 

1. ChatGPT로 튜토리얼 진행 

2. ChatGPT로 ROS AI Agent 구축 및 결과 확인과 평가 

3. ChatGPT ROS AI Agent 질문-답변 데이터셋 구축 

4. Llama3.2 LLM Fine-Tunning 진행 


그러나 해당 레파지토리에서는 ollama도 간단하게 다루겠습니다.

해당 레파지토리는 단순히 튜토리얼 예제입니다.

핑크랩에서 LLM 및 ROS 학습이 필요하시고 즉각적인 문서화를 강조하셔서 먼저 튜토리얼을 다루고 

이후, 본격적으로 ROS-agent 구축 들어가겠습니다. 


## 1. 환경 세팅 

1. 가상환경 생성 

```
conda create -n rag python=3.10 -y 

conda activate rag 

```

2. 라이브러리 설치 

```
pip install -r requirements.txt
```

GPU가 있는 경우 

```
pip install faiss-cpu
```

GPU가 없는 경우 

```
pip install faiss-gpu
```


## 2. API Key 발급 

먼저 .env.example 파일을 .env로 이름을 바꿔주세요. 


[openai api key 발급](https://platform.openai.com/settings/organization/api-keys)

해당 페이지에서 <code>+ Chreate new secret key</code> 버튼을 클릭합니다

이름은 아무거나 정해주고

defalut project를 선택해줍니다.

api key를 copy 해줍니다.

.env 파일에 붙여넣기를 합니다.

OPENAI_API_KEY = sk-xxxxxx


## 3. 01부터 04까지 튜토리얼 진행 

01부터 04까지 ipynb 파일로 LLM과 RAG를 파이썬으로 간단하게 다루어 보겠습니다. 


