MIMIC-IV-Ext Direct Dataset | Retrieval-Augmented Generation | Gradio Interface
A Retrieval-Augmented Generation (RAG) system that answers clinical queries and generates diagnostic summaries by retrieving relevant discharge summaries & diagnostic flowcharts from the MIMIC-IV-Ext Direct dataset and augmenting an open-source LLM.
Built as the final project for an NLP course.
Features

Dense retrieval using Sentence-Transformers + FAISS
Open-source LLM generation (Mistral-7B / Llama-3-8B via Hugging Face)
Clean preprocessing & embedding pipeline
Interactive Gradio web interface (replaces Streamlit)
Shows retrieved documents + final answer
Ethical handling of de-identified clinical data

Quick Start
Bash# 1. Clone repo
git clone https://github.com/yourusername/direct-rag-project.git
cd direct-rag-project

# 2. Create environment (recommended)
python -m venv venv
source venv/bin/activate    # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Put the extracted MIMIC-IV-Ext Direct folder in the root (or update path in config.yaml)
#    Folder structure should be: ./mimic-iv-ext-direct-1.0.0/...

# 5. Run preprocessing & indexing (first time only)
python preprocess_and_index.py

# 6. Launch the app
python app.py
The Gradio interface will open automatically (usually http://127.0.0.1:7860).
Example Queries

"Diagnostic approach for Acute Coronary Syndrome"
"Summarize patient history for Heart Failure"
"What are common symptoms of Adrenal Insufficiency?"

Project Structure
text├── app.py                # Gradio interface
├── preprocess_and_index.py
├── rag_pipeline.py       # Retrieval + Generation
├── config.yaml           # Paths, model names, top-k
├── index/                # FAISS index + metadata (generated)
├── notebooks/            # Exploratory notebook
└── requirements.txt
Evaluation

Retrieval: Precision@5, Recall@10
Generation: Relevance, coherence (manual), ROUGE scores on held-out cases
Detailed results & error analysis in the Medium article

