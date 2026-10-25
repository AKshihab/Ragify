# RAG practice

Write the code yourself in `notebooks/rag_practice.ipynb` or `practice.py`.
Both contain exercises only. No RAG pipeline has been implemented.

## Files

```text
rag_practice/
  data/                          Index only this folder
    txt/academy_overview.txt
    pdf/course_guide.pdf          Selectable text, not a scan
    word/student_handbook.docx    A real Word document
    json/course_catalog.json     Object with a courses array
    images/library_notice.png    Text image for OCR practice
  notebooks/rag_practice.ipynb    Empty code cells with exercise prompts
  practice.py                    Python alternative to the notebook
  evaluation/questions.json      Questions, expected answers, source files
  outputs/                       Your extracted text and vector index
  .env.example                   Optional environment variable placeholders
```

All source material describes the fictional Riverlight Learning Academy.
Names, prices, schedules, and policies are invented practice data.

## Practice order

1. Open the notebook and select your Python environment.
2. Load the TXT file and inspect its text and source metadata.
3. Load PDF, Word, and JSON separately. Inspect each result before combining.
4. Extract the image text with OCR; check the extracted text against the image.
5. Split the documents into chunks and keep source metadata on every chunk.
6. Choose your embeddings provider and create a vector index, such as FAISS.
7. Retrieve chunks for a question and inspect them before adding an LLM.
8. Generate answers with source filenames. Use "I don't know based on these documents" when evidence is missing.
9. Compare your results with `evaluation/questions.json`.

Keep the evaluation file, notebook, README, and starter code out of the index.
Start with the text documents; add the image after the basic pipeline works.
An image needs OCR or a model that can read images before ordinary text embeddings can use it.
For JSON, preserve each course's ID, title, fee, duration, and other fields together.

## Environment

Use an environment of your choice. The screenshots use LangChain, an embeddings
provider, and FAISS. Install the packages needed for your chosen loaders,
embedding provider, notebook kernel, and OCR tool as you implement each exercise.
OCR tools may also require a separately installed OCR engine.

If your provider needs an API key, copy `.env.example` to `.env` in this folder
and enter your own key locally. Loading an environment file is part of your exercise.
No credentials are included in this practice kit.

The notebook may start with its working directory inside `notebooks/`.
Check your working directory and resolve the data path before loading files.

## Challenges

- Compare chunk sizes and overlap values.
- Compare the top 1, 3, and 5 retrieved chunks.
- Answer a question that needs both the JSON catalog and the PDF guide.
- Cite the Word policy separately from course enrollment facts.
- Retrieve library hours from OCR text.
- Refuse the deliberately unanswerable questions in the evaluation set.
- Save your index under `outputs/` and reload it in a later session.
