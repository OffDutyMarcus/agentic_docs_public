##System Overview
```mermaid
flowchart LR
 subgraph AGENTIC["🤖Agentic Process"]
        ORC["🤖Agentic <br>Orchestration"]
        APIs["💬WebAPIs <br>Stream"]
        P["**👩‍✈️Planner** <br>openai/gpt-mini"]
        C["**⚠️Critic / Validate**  <br>qwen/qwen3-14B"]
        CO["**👨‍💻Composer** <br>openai/gpt-mini"]
        DBA["**🤖DatabaseAnalysis** <br>Agent"]
        EA["**🤖Email Agent**"]
  end
 subgraph MCP["MCP SERVER"]
        SQLT[["🔨SQL Tools"]]
        EMT[["🔨Email Tools"]]
  end
    UQ["🤦‍♂️ User Question"] --> APIs
    APIs <--> UQ & ORC
    ORC --> P & C & CO & DBA & EA
    DBA --> SQLT
    EA --> EMT
    SQLT --> MSSQL[("MSSQL Connector")]
    EMT --> SMTP["📧 SMTP Email"]
