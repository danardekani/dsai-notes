## Self-Consistency Prompts
Asking the model to generate multiple reasoning paths and compare them. This helps reduce single path hallucinations and helps with increasing accuracy in multi-step reasoning tasks. Furthermore, prompting the AI model to create multiple reasoning paths also enables deeper thought and analysis from the user. These paths can provide new perspectives and insights to continue to build off from.
- different reasoning paths expose weak logic
- incorrect paths get filtered out
- overlpas acorss answers reveal the "signal".

We can also use an iterative approach to add constraints, which in return improves relaiability and accuracy.
Examples:
    - "use only information from the provided text."
    - "limit each reasoning path to 4 steps."
    - "Avoid unsupported assumptions."

### Combining Self-Consistency with CoT prompting 
- Use CoT inside each path
- Generate multiple paths
- Compare their logic
- Select the most robust answer