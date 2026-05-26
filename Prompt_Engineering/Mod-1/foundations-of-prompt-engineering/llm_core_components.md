## Core Components
1. Tokens = pieces of language (howm models read text)
- models dont read full words but rather break text into chunks(tokens).
    - exdample: "artificial intelligence" would be broken down by an LLM roughly as "art" "ificial" "intelli" "gence".
- Tokens are then used by the vendor to calculate context limits.
- Each model tokenizes characters differently. i.e the way Anthropic tokenizes characters can be and generally is done differently than how OpenAI, Google, or Mistral may do it.

2. Embeddings = maps of meaning (how models represent meaning)
- words are converted into numerical vectors
- related ideas sit close together and unrelated ideas sit far apart 
    - meanings and semantics are weighted to figure out the vector correlations. 

3. Training data = how LLMs learn patterns (the patterns models learn)
- trainined on massive text datasets (books, articles, websites, code, etc.)
- learns language patterns, structure style
- does not store or retrieve documents
- generates statistically likely outputs.
- training data enables LLMs to act like a well-read student.
    - imitate style and structure
***AI knowledge stops at a cutoff date*** It's very important to verify time sensitive AI responses.

4. Predicition = how Ai "thinks" (how outputs are generated)
- predits the next token based on previous tokens
- repeats until answer is complete
- works like powerful autocomplete

### Key Limitations of LLMs
1. Not factual databases — always check outputs.
2. Can hallucinate details - hallucinations occur when an LLM confidently generates factually incorrect, illogical, or completely fabricated information while presenting it as the truth.
3. limited by context windows.
4. biased based on training data.
5. No built-in understanding of truth.