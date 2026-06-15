## Teach AI to Self Check (Reflective Prompting)

How to guide the model to critique, diagnose, and improve its own answers. 

### Self Checking Prompt Examples

Thse examples are not fixed or specific. They can be used in a multitude of scenarios and uses cases.

- Error Detection:
  - "review your previous answer for errors or gaps."
- Assumption Validation:
  - "List assumptions you made and evaluate whether they're valid."

Quality Improvement Loop:
    1 - "identify 3 ways your response could be improved."
    2 - "Explain how each weakness affects the conclusion."
    3 - "Rewrite your answer to address these weaknesses."

### Check for Bias Using Reflective Prompts
1 - "Does your response contain biased language?"
2 - "Did you make cultural or demographic assumptions?"
3 - "Rewrite to ensure inclusivity and neutrality."

### Checking Data Integrity using Reflective Prompts
- "did you inest any information?"
- "Did you assume data not provided?
- "Rewrite the asnwer using only the supplied text."
Furthermore, ask for sources if its referencing data from an external source, and do not assume that because a source is provided that it's true. Review the source and the contexts provided.