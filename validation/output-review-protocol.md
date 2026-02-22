# AI Output Review Protocol

## 1. Decision Tree: When to Accept, Refine, or Reject
All Copilot suggestions must pass through this decision logic before merging. 
Copy this logic into your mental checklist during code review.

START: Copilot Suggestion Generated
  
  +--- [STEP 1: SECURITY CHECK]
       |
        +--- Contains Secrets/PII? ---> [REJECT IMMEDIATELY] 🔴
       |
        +--- Clean? ---> Go to Step 2
  
  +--- [STEP 2: LOGIC VERIFICATION]
       |
        +--- Hallucinated API/Logic? ---> [REJECT & REPORT] 🔴
        |
        +--- Valid Logic? ---> Go to Step 3
  
  +--- [STEP 3: PERFORMANCE & BEST PRACTICE]
       |
        +--- Suboptimal Pattern? ---> [REFINE & OPTIMIZE] 🟡
        |     (e.g., uses 'any', inefficient loops)
       |
        +--- Aligned with Standards? ---> Go to Step 4
  
  +--- [STEP 4: TEST COVERAGE]
        |
        +--- No Tests Generated? ---> [REFINE: ADD TESTS] 🟡
        |
        +--- Tests Verified? ---> [ACCEPT] 🟢
  
END: Code Ready for Merge

| Action | Condition | Example |
|---|---|---|
| ACCEPT | "Boilerplate, standard patterns, verified logic." | Getter/Setter methods, standard DTO mappings. |
| REFINE | Logic is correct but pattern is outdated or insecure. | Copilot uses any instead of Interface; uses eval(). |
| REJECT | "Hallucinated methods, security risks, IP violations." | Copilot invents a library function; exposes API key. |

