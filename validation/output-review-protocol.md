# Structured Copilot validation

# AI Output Review Protocol

## 1. Decision Tree: Accept, Refine, or Reject
All Copilot suggestions must pass through this decision logic before merging.

graph TD
    A[Copilot Suggestion Generated] --> B{Security Check?};
    B -- Secrets/PII Detected --> C[REJECT Immediately];
    B -- Clean --> D{Logic Verification};
    D -- Hallucinated API/Logic --> E[REJECT & Report];
    D -- Valid Logic --> F{Performance/Best Practice};
    F -- Suboptimal Pattern --> G[REFINE & Optimize];
    F -- Aligned with Standards --> H{Test Coverage};
    H -- No Tests Generated --> I[REFINE: Add Tests];
    H -- Tests Verified --> J[ACCEPT];
    
    style C fill:#ff9999,stroke:#333,stroke-width:2px
    style E fill:#ff9999,stroke:#333,stroke-width:2px
    style J fill:#99ff99,stroke:#333,stroke-width:2px
    style G fill:#ffff99,stroke:#333,stroke-width:2px
    style I fill:#ffff99,stroke:#333,stroke-width:2px
```

## Validation Criteria

| Action | Condition | Example |
|--------|-----------|---------|
| ACCEPT | Boilerplate, standard patterns, verified logic. | Getter/Setter methods, standard DTO mappings. |
| REFINE | Logic is correct but pattern is outdated or insecure. | Copilot uses any instead of Interface; uses eval(). |
| REJECT | Hallucinated methods, security risks, IP violations. | Copilot invents a library function; exposes API key. |

