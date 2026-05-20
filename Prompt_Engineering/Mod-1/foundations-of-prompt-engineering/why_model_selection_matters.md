## Why Model Selection Matters
Understanding that not all LLMs are created is an essential first step when deciding which model you want to use for a project. Whether the project or task personal or professional, which model you choose matters.
### Strategic Considerations
- Costs
- Data privacy
- Output quality
- Workflow objectives
- What do you want the LLM to help you with? (innovation, productivity, research, programming, etc.)

### Key Factors
- Accuracy and Reliability 
    - Accuracy varies depending on use case (maths, logic, planning, reasoning, research, etc.)
- Context Window Size
    - Larger context windows = better for long documents. 
    - Not all models can handle large, detailed user inputs (i.e. legal documents, financial records, etc.) Because of this, models that do not have large context windows can begin to drift in their responses. Technically known as, "Lost in the Middle".
        - This happens becuase LLMs attention mechanisms in transformers distributes computational focus unevenly across long user inputs; Most attention being directed at the beginning and end of the input. Therefore, user prompts where the bulk of the relevant information is in the middle causes some LLM responses to degrade. 
        - Some of the most well known models have experiencd this "Lost in the middle" problem such as OpenAI's GPT-3.5 Turbo, and GPT-4.1, Anthropic Claude Opus 4, and Gemini 2.5 