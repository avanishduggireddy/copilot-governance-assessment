graph TD
    A[Copilot Suggestion Generated] --> B{Security Check?}
    B -->|s11| C[REJECT Immediately]
    B -->|s12| D{Logic Verification}
    D -->|s13| E[REJECT & Report]
    D -->|s14| F{Performance/Best Practice}
    F -->|s15| G[REFINE & Optimize]
    F -->|s16| H{Test Coverage}
    H -->|s17| I[REFINE: Add Tests]
    H -->|s18| J[ACCEPT]
    
    style C fill:#ff9999,stroke:#333,stroke-width:2px
    style E fill:#ff9999,stroke:#333,stroke-width:2px
    style J fill:#99ff99,stroke:#333,stroke-width:2px
    style G fill:#ffff99,stroke:#333,stroke-width:2px
    style I fill:#ffff99,stroke:#333,stroke-width:2px