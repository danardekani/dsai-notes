### Hallucinations 
This is when models give you incorrect answers, but are very confident in their response. They can make up data and sources to support their response.

### Bias
If there is bias in the training data thta trains the model(s), then the LLMs output will also be biased.
- Models reflect human bias.
- Can reproduce stereotypes.

### Context Window Limits
Models can only see so much at once.
- limited number of tokens "in memory"
- long documents may get cut off or ignored.
- Summraies may miss key details
- requires chunking or multi-step prompting.
- Unless connected to a real-time API or external source, LLLM do not know the present moment.
    - Knowledge stops at the training cutoff

### Overconfidence
- AI can sound more certain than it actually is. Modells can use authoritative tones, hide uncertainty in language, leads users to trust incorrect outputs.

### Misinterpreted Instructions
- Vauge prompts will generally render unpredictable results.

### Training Data Quality
Models are only as good as their training data.
- training data can include noise.
- inaccurate pattersns = inaccurate output. 
