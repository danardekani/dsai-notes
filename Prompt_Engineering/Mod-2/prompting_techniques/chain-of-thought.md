##  Chain of Thought Prompting
Prompting techinque to improve the reasoning capabilities of LLMs by generating intermediate reasoning steps. This technique can be combined with few-shot prompting for when you are working on a complex task that requires reasoning before responding.
### Advantages
    - This method is low effort and works well with off the shelf LLMs (Claude, Gemini, etc.)
    - Interpretable — users can learn from LLM responses and see the reasoning steps that were followed. 
    - Chain of thought prompts also appear to transfer well between different LLMs; less drift.
### Disadvantages
    - chat of thought reasoning uses more output tokens, which means predictions cost more and take logner.