# AI Resume Screener & Job Matcher

An NLP system that ranks resumes against a job description and shows which skills match and which are missing. Built as a baseline that can grow into a full applicant-screening tool.

## Problem

Recruiters receive hundreds of resumes per opening and screen them manually. This project automates the first-pass shortlist by scoring each resume against the job description.

## Current Scope (v0.1)

- Parse resumes from PDF/TXT
- Clean and preprocess text (tokenization, stopword removal, lemmatization)
- Extract skills using a keyword/skill dictionary
- Rank resumes with TF-IDF + cosine similarity
- Output a ranked list with match score and missing skills

## Tech Stack

Python, pandas, scikit-learn, NLTK / spaCy, PyPDF2

## Dataset

- Kaggle: *Resume Dataset* (resumes labelled by category)
- Job descriptions: any scraped or hand-written postings (3-5 for testing)

## Project Structure

```
resume-screener/
├── data/
│   ├── resumes/
│   └── job_descriptions/
├── notebooks/
│   └── 01_baseline.ipynb
├── src/
│   ├── preprocess.py
│   ├── skills.py
│   └── matcher.py
├── requirements.txt
└── README.md
```

## Setup

```bash
git clone https://github.com/<your-username>/resume-screener.git
cd resume-screener
pip install -r requirements.txt
python src/matcher.py --jd data/job_descriptions/jd1.txt --resumes data/resumes/
```

## Example Output

| Rank | Resume | Match Score | Missing Skills |
|------|--------|-------------|----------------|
| 1 | resume_12.pdf | 0.81 | docker |
| 2 | resume_07.pdf | 0.74 | aws, docker |

## Results

| Method | Top-5 Accuracy |
|--------|----------------|
| TF-IDF + Cosine | _to be filled_ |

## Roadmap (Future Scope)

- [ ] Replace TF-IDF with BERT / Sentence-Transformer embeddings
- [ ] Named Entity Recognition for skills, education, experience years
- [ ] Learning-to-rank model trained on recruiter feedback
- [ ] Bias and fairness audit (remove name, gender, age signals)
- [ ] FastAPI backend + Streamlit UI
- [ ] Dockerize and deploy
- [ ] Multi-language resume support

## License

MIT
