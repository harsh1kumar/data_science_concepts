# Large Language Models

## NLP Terminology

- **Zero-shot classification:** Give labels and classify without retraining
- **Few-shot classification:** Give few examples of labelling and classify without retraining
- **Summarisation**
    - Extractive: Select representative pieces of text
    - Abstractive: Generate new text
- Sentiment Analysis
- Translation
- Question-Answers
- **Foundation models**: Trained on text generation tasks such as predicting the next token in a sequence
- **Instruction-following models**: Tuned to follow (almost) arbitrary instructions or prompts
- **Prompt Hacking**
    - Prompt injection: Adding malicious content
    - Prompt leaking: Extract sensitive information
    - Jailbreaking: Bypass moderation rule
- **Searching and Sampling**
    - **Search**: Given the tokens generated so far, pick the next most likely token in a "search."
        - Greedy search (default): Pick the single next most likely token in a greedy search.
        - Beam search: Greedy search can be extended via beam search, which searches down several sequence paths, via the parameter `num_beams`.
    - **Sampling**: Given the tokens generated so far, pick the next token by sampling from the predicted distribution of tokens.
        - Top-K sampling: The parameter `top_k` modifies sampling by limiting it to the `k` most likely tokens.
        - Top-p sampling: The parameter `top_p` modifies sampling by limiting it to the most likely tokens up to probability mass `p`.
    - For more background on search and sampling, [see this Hugging Face blog post](https://huggingface.co/blog/how-to-generate).

## Vector Databases and Libraries

1. **FAISS** ([video](https://www.youtube.com/watch?v=GKqtMBkFotA)): Vector Library for generating embeddings and searching
2. **Chroma db** ([video](https://www.youtube.com/watch?v=Kilc1mEHInY)): Vector database, for generating embedding and searching. It can be combined with LLM to build a RAG
3. **Pinecone** ([video](https://www.youtube.com/watch?v=kNI6ebY2Gyw)): Cloud based vector database
4. **Weaviate** ([video](https://www.youtube.com/watch?v=YHUaSmU9Qr4)): Vector database

## Multi-stage reasoning:

1. LangChain
2. HF Transformer agents
3. ChatGPT Plugins
4. Dust.tt
5. HuggingGPT/Jarvis
6. BabyAGI
7. AutoGPT

## LLM Evaluation Metrics

1. Perplexity
2. BLEU score: BiLingual Evaluation Understudy (for translation)
3. ROUGE (for summarisation)

SQuAD: Standform Question Answering Dataset

## Resources

- Databricks Course on LLM
    - [Videos](https://www.youtube.com/watch?v=MLLLDaR6P08&list=PLTPXxbhUt-YWSR8wtILixhZLF9qB_1yZm&index=1)
    - [Presentation](https://github.com/databricks-academy/large-language-models/releases/download/v1.0.3/LLM_Application_through_Production.pdf)
    - [My version of notebook on Google Collab](https://colab.research.google.com/drive/1DIKesu-0LS-yJWVN6ycii-toBFPXJv0J?usp=sharing)
    - [Notebooks](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbWtKTXQ5cnotUUFzQk1oOUswOUFZeWUwd29RUXxBQ3Jtc0tuem5KU3NMTV9uZ0p3Tk5rQVdyLWIyWG81bm4zc2VIeDhmZE1mLWp4SEM2cV9hN2hSMC1rZGN6anA2VjJCeFE5elVfLTF2bmMyVHV3ZHF1dEdCclFocjVSanIyOWhqX3QzVjc0TDBpOFFoS1d4Z1lCVQ&q=https%3A%2F%2Fgithub.com%2Fdatabricks-academy%2Flarge-language-models&v=zra2zr8r_n4)