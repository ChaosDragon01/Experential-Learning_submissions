# Week 7: RAG Security Knowledge Assistant

## 1. Setup Summary

**LLM:** 
llama-3.3-70b-versatile via Groq

**Embeddings:** sentence-transformers/all-MiniLM-L6-v2 via HuggingFace

**Vector Store:** In-Memory Vector Store

**Documents loaded:** 3 text files covering MITRE ATT&CK techniques (Initial Access, Credential Access, and Lateral Movement). Each document was approximately 1 to 2 pages in length.

## 2. Test Results

| # | Question | Used Documents? | Quality | Notes |
|:---|:---|:---|:---|:---|
| 1 | What are common techniques for credential access? | Yes | Good | The bot correctly cited T1110 and mentioned specific groups like Turla and OilRig. |
| 2 | How does phishing relate to initial access? | Yes | Good | It identified phishing as a tactic and correctly broke down spearphishing sub-techniques. |
| 3 | What is lateral movement and what techniques do attackers use? | Yes | Good | Successfully listed Net use commands and the Adversary-in-the-middle technique. |
| 4 | What does the NIST framework recommend for the Detect function? | No | Good | The bot admitted it was unsure because NIST information was not in the provided documents. |
| 5 | What is the difference between spearphishing attachment and link? | Yes | Good | Provided a clear distinction between file-based delivery and URL-based redirection. |

## 3. Edge Case Observations

**Unrelated question:** When asked about the weather, the chatbot correctly stated it did not have access to that information, proving the RAG system was properly constraining the response.

**Topic not in documents:** For the NIST framework question, the bot avoided hallucination by explicitly stating it was unsure based on the provided context.


## 4. Reflection

What surprised me most about RAG was how effectively it acts as a factual anchor for the LLM. Even with a powerful model like Llama 3.3, the ability to restrict its knowledge to a specific set of documents makes it much more reliable for specialized technical tasks.

To improve this for real-world use, I would implement a persistent vector store like Pinecone or Chroma. This would allow the knowledge base to scale without needing to re-process every document whenever the system restarts.

In my capstone project, I plan to use RAG to allow my security automation tools to reference specific internal policy documents or historical incident logs. This will enable the AI to provide context-aware recommendations during an investigation rather than just general security advice.
