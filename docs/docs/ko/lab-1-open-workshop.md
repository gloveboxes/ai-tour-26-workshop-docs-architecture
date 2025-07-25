## 실험실 1: 워크숍 시작하기

이것은 콘텐츠 작성자가 MkDocs 고정 탭을 사용하여 다국어 워크숍 콘텐츠를 생성하는 방법을 보여주는 예제 실험실입니다.

## 학습 내용

이 실험실에서 다음을 학습합니다:

- 워크숍을 위한 개발 환경 설정
- 샘플 데이터베이스에 연결하고 데이터 액세스 확인
- 첫 번째 AI 기반 애플리케이션 생성
- Model Context Protocol (MCP)의 기본 아키텍처 이해
- 간단한 쿼리 및 응답으로 설정 테스트

## 소개

Model Context Protocol (MCP)은 대형 언어 모델 (LLMs)을 데이터베이스 및 API와 같은 외부 도구 및 데이터 소스에 연결하여 더 스마트하고 확장 가능한 AI 애플리케이션을 가능하게 하는 표준화된 인터페이스입니다.

이 소개 실험실에서 다음을 수행합니다:

- Python 또는 C# 개발을 위한 개발 환경 구성
- MCP를 사용하여 Zava DIY 소매 데이터베이스에 연결
- 판매 데이터를 쿼리할 수 있는 기본 에이전트 생성
- 고급 주제로 이동하기 전에 설정이 올바르게 작동하는지 확인

## 실험실 연습

이 실험실에서는 첫 번째 MCP 지원 애플리케이션을 설정하고 샘플 데이터베이스에 연결합니다.

=== "Python"

    ### 1단계: Python 환경 구성

    1. 워크스페이스에서 `src/python/workshop` 폴더를 엽니다.

    2. `my_first_agent.py`라는 새 파일을 만듭니다:

        ```python
        import asyncio
        from mcp_client import MCPClient
        
        async def main():
            """첫 번째 MCP 지원 에이전트를 생성합니다."""
            client = MCPClient()
            
            # MCP 서버에 연결
            await client.connect("localhost:8000")
            
            # 기본 연결 테스트
            response = await client.query("SELECT COUNT(*) FROM products")
        ```

---

이 파일은 GitHub Copilot 및 GPT-4o를 사용하여 번역되었습니다.
