
## The belows are the set of the forked repo for my personal interests

# 1 financial and stock
 - https://github.com/IntuitionSeeker/bullga-mcp
 - https://github.com/IntuitionSeeker/financial-services
 - https://github.com/IntuitionSeeker/AI-Trader
 - https://github.com/IntuitionSeeker/TradingAgents_hedge
 - https://github.com/IntuitionSeeker/bloomAI-public
 - 


# 2 chat, SNS wiki
 - https://github.com/IntuitionSeeker/openclaw-kakao-plugin


## 📊 AI-Trader 시스템 아키텍처 분석 (Understand-Anything 시뮬레이션)
에이전트가 트레이딩 플랫폼과 어떻게 통신하고 백엔드에서 어떻게 처리되는지 구조화한 다이어그램입니다.

```mermaid
graph TD
    %% 노드 정의 (ID[라벨])
    BackendMain[server/main.py<br/>FastAPI 메인]
    BackendLogic[service/trading_logic.py<br/>백그라운드 체결 로직]
    FrontendApp[frontend/App.tsx<br/>React 프론트엔드]
    AgentCore[skills/ai4trade/SKILL.md<br/>에이전트 코어 스킬]
    AgentCopy[skills/copytrade/SKILL.md<br/>카피 트레이딩 스킬]
    APIDocs[docs/api/openapi.yaml<br/>API 명세]

    %% 의존성 및 흐름 연결
    FrontendApp -->|API 호출| APIDocs
    BackendMain -->|스펙 정의| APIDocs
    BackendMain -->|비동기 실행| BackendLogic
    AgentCore -->|플랫폼 접속/통신| BackendMain
    AgentCopy -->|매매 신호 전송| BackendLogic

    %% 시각적 스타일링 (그룹별 색상 지정)
    classDef backend fill:#f9f0ff,stroke:#d4b3ff,stroke-width:2px;
    classDef frontend fill:#e6f7ff,stroke:#91d5ff,stroke-width:2px;
    classDef agent fill:#f6ffed,stroke:#b7eb8f,stroke-width:2px;
    classDef docs fill:#fffbe6,stroke:#ffe58f,stroke-width:2px;

    %% 노드에 클래스 적용
    class BackendMain,BackendLogic backend;
    class FrontendApp frontend;
    class AgentCore,AgentCopy agent;
    class APIDocs docs;
```



