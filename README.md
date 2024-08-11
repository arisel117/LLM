# NLP


NLP와 관련된 연구 노트

(이후 천천히 추가 할 예정!!)


기타 흥미로운 세부 주제! 하나씩 내용을 찾아서 정리하자~

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
- 

## LangChain
- 

## LLMops
- 

## figma
- 

## streamlit
- 

## gradio
- 
