[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/vgbm4cZ0)


# 📄 ADGM Compliance Document Checker

An AI-powered compliance agent that reviews uploaded `.docx` documents against **ADGM-specific templates** and detects issues like:

- **Incorrect jurisdiction** (e.g., referencing UAE Federal Courts instead of ADGM)
- **Non-compliance with ADGM-specific clauses**
- **Unfilled placeholders**
- **Missing mandatory clauses**
- **Process checklist validation** (detects which process you’re trying to complete and checks for missing required documents)
- **Document similarity matching** against stored templates using vector embeddings
- **Annotated `.docx` output** with highlights and inline comments
- **Downloadable JSON report** summarizing findings

---

## 🚀 Features
- **Multiple File Upload** — Upload several `.docx` files at once.
- **Template Matching** — Uses FAISS vector embeddings to identify the document type from a stored templates folder.
- **Placeholder Check** — Detects unfilled placeholders like `[insert name here]`.
- **Clause Verification** — Ensures mandatory clauses are present.
- **LLM-Powered Jurisdiction Check** — Uses GPT to detect incorrect jurisdiction references.
- **Process Checklist Validation** — Detects which legal process is being attempted and ensures all required documents are present.
- **Annotated Review File** — Returns `.docx` with inline comments for flagged content.
- **JSON Summary Output** — Issues list, missing documents, and compliance results.
- **Downloadable Reports** — Download both reviewed `.docx` and JSON report.

---

## 🛠️ Tech Stack
- **Python 3.10+**
- **Streamlit** (UI)
- **LangChain** (Vector search)
- **OpenAI GPT-5** (LLM for legal checks)
- **python-docx** (Docx parsing & annotation)
- **FAISS** (Vector store for template similarity)
- **RAG (Retrieval-Augmented Generation)**

---

## 📂 Project Structure
├── app.py # Main Streamlit app
├── red_flag_detector.py # Rule-based checks and LLM functions
├── process_checklists.py # Required document lists per process
├── templates/ # Stored template DOCX files
├── reviewed_docs/ # Output folder for annotated DOCX files
├── requirements.txt # Dependencies
├── .gitignore # Git ignore file
└── README.md # Project documentation


## ⚡ Installation
1. **Clone the repository**
```bash
git clone https://github.com/2CentsCapitalHR/ai-engineer-task-Lovi07.git
cd ai-engineer-task-Lovi07

**Create a virtual environment**

python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows


**Install dependencies**

pip install -r requirements.txt

**add OpenAI api key**

streamlit run app.py


Upload one or multiple .docx files.

The app will:

Identify document type from stored templates

Perform placeholder and clause checks

Run LLM-based jurisdiction validation

Detect process type & missing documents

Download the reviewed .docx and JSON report.

📊 Example JSON Output

{
  "process": "Company Incorporation",
  "documents_uploaded": 4,
  "required_documents": 5,
  "missing_document": ["Register of Members and Directors"],
  "issues_found": [
    {
      "document": "Articles of Association.docx",
      "issue": "Jurisdiction clause does not specify ADGM",
      "severity": "High",
      "suggestion": "Update jurisdiction to ADGM Courts."
    },
    {
      "document": "Resolution.docx",
      "issue": "Unfilled placeholder: [insert company name]",
      "severity": "High"
    }
  ]
}


