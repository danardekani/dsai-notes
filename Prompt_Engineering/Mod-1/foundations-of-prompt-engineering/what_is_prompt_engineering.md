## What is Prompt Engineering?
Prompting is the process of designing high-quality prompts that guide LLMs to produce accurate outputs. In this process the end user tinkers the output length, wirting style, format, and overall inputs to try produce the best output relative to the task. In short, a prompt is a user input provided to the model to generate an output (response/prediction).

### Output Length
The output length is a configuration users should spend time on because the length dictates the type of energy consumption, cost, efficiency, and output style. 

### Sampling Controls
LLMs don't formally predict tokens, they predict probabilities of what the next token may be. Each token in the LLMs vocabulary getting a probabilitiy. Each token probability is sampled to determine which token will be produced next.

#### Control Configurations
Temperature, top-k, top-p are common configuration settings to determine how token probabilities are predicted.
- Temperature: controls the degree o readomness in token selection. Lower temperatures are good for prompts that require deterministic response, while higher temperatures can lead to more diverse, creative, or unexpected responses. 
- Top-K and Top-P: (nucleus sampling) are sampling settings used in LLMs to restrict the predicted next token to come from tokens with the top predicted probabilities. These settings also control randomness and diversity of generated text.
    - Top-K: The higher top-K, the more creative and varied the model's outut; the lower it is the more factual the model's output. Top-K of 1 is equivalent to greedy decoding. 
    - Top-P:sampling selects the top tokens whose cumulative probability does not exceed a certain value (P). Values for P range from 0 (greedy) to 1 (all tokens in the LLM's vocabulary).