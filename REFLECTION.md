<<<<<<< HEAD
# Reflection — Invoice Analysis Agent

## What worked well

- Separating the pipeline into **OCR (Azure Document Intelligence)**, **reasoning (Azure OpenAI)**, and **tools** meant that the system was easy to understand and score because the LLM had to provide reasoning by way of tool invocations rather than making random guesses.
- Utilizing **LangGraph’s `create_react_agent`** provided an elegant **ReAct** cycle without needing too much orchestration.
- Including a **tiny markdown-based knowledge base** and **BM25 retrieval** maintained RAG as a lightweight process (no GPU embeddings), but illustrated retrieval-augmented grounding nonetheless.

## What did not work (initially) and how it was handled

- **Versioning issues** arose whenever highly restrictive pins caused dependency problems between `langchain-*` and `langgraph-*`. It was remedied by aligning versions through the use of resolver-friendly pins and storing the resolved pins in `requirements.txt`.
- **PDF files for invoices** could not be easily shipped within the repo because of their large size and licensing concerns; instead, the repo explains how to create sample invoices stored within `data/sample_invoices/`.

## Biggest technical challenge

The main difficulty was making the **Document Intelligence JSON** compatible with both the LLM and a **validation deterministic function** without requiring inflexible parsing for any type of invoice format. To achieve this, we serialized the values of model fields to standard JSON-compatible values while maintaining validation criteria as simple as possible (only PASS/FAIL results).

## Single vs multi-agent

The project remained on **Option A (single agent)**. The process flow is largely sequential (OCR -> validation -> summarization), and dividing it into multiple agents does not seem to offer any advantages.

## What I would build next (another semester)

- A mini **Streamlit/Gradio interface** for uploads, dual PDF display, and manual editing of extracted data.    
- **Durable memory** (SQLite checkpointing) along with optional **duplicates filtering** using the processed invoice database.  
- Enhanced validation: tax jurisdiction logic, purchase order correlation, and intelligent forwarding to manual verification teams based on confidence.
=======
>>>>>>> 9c0675f (Update project)
