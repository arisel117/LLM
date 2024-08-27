# NLP


NLP와 관련된 연구 노트

(이후 천천히 추가 할 예정!!)
라마3 설치랑 테스트 해보기!
  - https://huggingface.co/meta-llama/Meta-Llama-3.1-70B-Instruct


기타 흥미로운 세부 주제! 하나씩 내용을 찾아서 정리하자~

## LLAMA 3.1 8b
- 사용 후기
  - 장점
    - 무료 LLM이고 한국어로도 대답을 곧 잘 함!
    - vscode에서 실행해서 사용하면 인터넷에서 자료 검색해서 대답도 잘 해주는 것 같은데..?!
  - 단점
    - 한국어로 대답을 하라고 해야 한국어로 대답하고, 조금만 지나면 다시 영어로 대답하는데다 딱 물어본 거에만 대답을 하거나 물어본거의 일부를 그냥 대답으로 해버리는 문제들이 있음..
    - 약간 프롬프트 엔지니어링이 GPT에 비해서 부족한 것인지, 솔직히 사용하기가 너무 답답함.. 3.1 8b 보다 무거운 모델을 사용하면 괜찮을지 궁금함!
- 다운로드 방법
  - Mac OS
    - [https://ollama.com/download/mac](https://ollama.com/download/mac) 에 들어가서 파일 다운로드
  - Linux
    ```shell
    curl -fsSL https://ollama.com/install.sh | sh
    ```
  - Windows
    - [https://ollama.com/download/windows](https://ollama.com/download/windows) 에 들어가서 OllamaSetup.exe 파일 다운로드
    - OllamaSetup.exe 파일을 실행하여 [Install] 진행
    - Terminal(Git bash, Anaconda Prompt, cmd 등) 실행 후, 설치 확인을 위해 다음 코드 입력 (Available Commands 어쩌구 나오면 성공적으로 설치 완료!)
      ```shell
      ollama -h
      ```
    - 모델 다운로드 진행 (여기선 4.7gb인 llama 3.1 8b 모델을 다운로드함)
      ```shell
      ollama run llama3.1:8b
      ```
      * 이 밖에도 다양한 모델을 사용 가능함!!
    - 이후 대화 가능
- vscode에서 실행 방법
  - extension에서 [codegpt] 다운로드
  - 설정에서 [ollama] - [llama3.1:8b] 선택 후 실행
  - 하단 대화창에서 대화 가능
  - 실행을 위해서는 앞서서 ollama로 llama3.1:8b 설치 및 실행 필요



## LLM (Large Language Model)
- 방대한 양의 텍스트 데이터를 학습하여 다양한 종류의 텍스트를 생성할 수 있는 능력을 갖춘 모델

## SLM (Small Language Model)
- 모델의 파라미터 수가 적은 모델로 빠른 학습 및 추론 속도를 기반으로 Edge Device에서의 작동을 목표로 한 모델

## LMM (Large Multimodal Model)
- 텍스트 데이터 외에도 이미지, 오디오 등 여러 가지 유형의 데이터를 통합하여 처리할 수 있는 능력을 갖춘 모델

## RAG
- **정의**
  - 대규모 언어 모델의 출력을 최적화하여 응답을 생성하기 전에 학습 데이터 소스 외부의 신뢰할 수 있는 지식 베이스를 참조하도록 하는 프로세스
- **주요 특징**
  - LLM의 경우, 최신 정보나 특정 도메인의 지식은 학습하지 못하였기 때문에, 이러한 질문이 들어오면 허위 정보를 생성(Hallucination)하거나 응답이 정확하지 않게 되는 문제가 있음
  - 이 때문에 특정 도메인의 지식을 보다 자세히 이해하기 위해서는 Transfer Learning이 요구되는데 Pre-Trained된 모델이라도 학습에 막대한 Cost가 필요하다는 단점이 있음
  - RAG를 사용하면 비용 효율적으로 Transfer Learning을 하지 않더라도 문제를 다소 해결 할 수 있음
  - 특히, 학습에 직접적으로 사용되지 않은 **외부 정보를 증거 기반으로 맥락에 따라 답변**을 하도록 함으로써 LLM의 단점을 보완하고자 함
- **작동 방식**
  - 사용자의 질문이 주어지면, Query Encoder가 이를 변환함
  - Knowledge Retriever가 질의 내용에 따라 외부 Knowledge Base에서 관련 정보를 검색함
  - 검색된 정보를 Knowledge-Augmented Generator의 입력으로 전달함
  - Knowledge-Augmented Generator는 검색된 정보를 활용하여 질의 사항에 대한 답변을 생성함
- **적용 사례**
  - Microsoft Bing, OpenAI WebGPT, Perplexity AI 등

## 시맨틱 검색 기술
- 단어와 구문의 의미를 해석하여 사용자의 검색 의도를 파악하여 검색하는 기술
- 쿼리의 단어와 문자 그대로 일치하는 콘텐츠가 아니라 **쿼리의 의미와 일치하는 콘텐츠**를 반환
- ML과 AI의 도움을 받아 벡터 검색을 통해 제공
- 사용자의 지리적 맥락, 사용자의 과거 검색 기록, 사용자 의도를 기반으로 결과를 제공

## LangChain
- LLM과 애플리케이션의 통합을 간소화하도록 설계된 SDK를 의미함
- 코드를 크게 변경하지 않고 모델을 쉽게 교체하거나 대체하도록 지원
- 애플리케이션이 LLM에 대한 컨텍스트를 구축하기 위해 외부 소스(PDF, 웹 페이지, CSV, 관계형 데이터베이스)에서 검색해야 하는 경우, 서로 다른 소스에서 데이터에 액세스하고 검색할 수 있는 모듈과 원활하게 통합하도록 지원
- 외부 소스를 선택한 LLM을 기반으로 최적의 임베딩 모델을 선택하도록 지원
- 생성된 임베딩은 유사성 검색을 위해 벡터 데이터베이스에 저장되는데, 메모리 내 배열부터 파인콘(Pinecone)과 같은 호스팅 벡터 데이터베이스에 이르기까지 다양한 소스에서 벡터를 쉽게 저장하고 검색할 수 있도록 지원
- OpenAI, 코히어(Cohere), AI21에서 제공하는 주류 LLM과 허깅페이스(Hugging Face)에서 제공되는 오픈소스 LLM을 지원

## 프롬프트 엔지니어링(Prompt Engineering)
- NLP를 효과적으로 사용하기 위해 입력 프롬프트를 설계하고 최적화하는 과정
- 원하는 결과를 얻기 위해 프롬프트를 어떻게 구성할지 고민하는 작업
- 단순 프롬프트는 일반적인 답변을 제공할 수 있지만, 개선된 프롬프트는 구체적인 영역을 지정하여 더 정확하고 유용한 정보를 얻을 수 있도록 도와줌
- 예를 들면 다음과 같이 단순 입력 프롬프트를 가공하여 보다 만족스러운 결과를 얻도록 만듦
  - 단순 프롬프트: 사과가 건강에 좋나요?
  - 개선된 프롬프트: 사과를 매일 섭취하면 건강에 어떤 이점이 있나요? 예를 들어, 비타민, 섬유질, 심혈관 건강 등에 대해 설명해주세요.

## MLops
- 모델의 배포, 유지관리 프로세스의 간소화를 목표로 하는 일련의 워크플로우를 의미함
- 다음과 같은 구성 요소를 내포함
  - EDA(Exploratory Data Analysis, 탐색적 데이터 분석)
  - 데이터 준비 및 프롬프트 엔지니어링
  - 모델 조정
  - 모델 검토와 거버넌스
  - 모델 유추와 서빙
  - 인간 피드백을 통한 모델 모니터링

## LLMops
- 기본적으로 MLops + LLM과 같은 의미로 사용됨
- MLops와 다르게 추가적으로 RAG와 RLHF도 포함됨

## UI/UX 서비스 관련
- figma (UI/UX 관리)
- streamlit (Web)
- gradio (App)
