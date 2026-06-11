# 🤖 AI Resume Screening Agent

An AI-powered Resume Screening Agent built using Python, PDF Processing, and Machine Learning techniques. The agent automatically compares candidate resumes against a Job Description (JD), calculates match scores, ranks candidates, and classifies them as **Selected** or **Rejected**.

This project simulates the first round of recruitment screening performed by HR teams and Applicant Tracking Systems (ATS).

---

# 📌 Project Overview

Recruiters often receive hundreds of resumes for a single job opening.

Manually reviewing every resume is time-consuming and inefficient.

This AI Resume Screening Agent automates the process by:

* Reading a Job Description (JD)
* Reading candidate resumes
* Comparing resumes with the JD
* Calculating similarity scores
* Selecting strong candidates
* Rejecting low-matching candidates
* Generating a downloadable CSV report

---

# 🚀 Features

✅ Upload Job Description PDF

✅ Upload Multiple Resume PDFs

✅ Extract Resume Content

✅ ATS-Style Resume Matching

✅ Similarity Score Calculation

✅ Candidate Ranking

✅ Automatic Selection/Rejection

✅ CSV Report Generation

✅ Google Colab Compatible

---

# 🛠️ Technologies Used

| Technology        | Purpose                 |
| ----------------- | ----------------------- |
| Python            | Programming Language    |
| PyPDF             | PDF Text Extraction     |
| Pandas            | Data Processing         |
| Scikit-Learn      | Similarity Calculation  |
| TF-IDF            | Text Vectorization      |
| Cosine Similarity | Resume Matching         |
| Google Colab      | Development Environment |

---

# 📂 Project Structure

```text
ai-resume-screening-agent/
│
├── jd.pdf
├── resume1.pdf
├── resume2.pdf
├── resume3.pdf
│
├── candidate_screening_report.csv
├── app.ipynb
├── requirements.txt
└── README.md
```

---

# ⚙️ Installation

Install required libraries:

```bash
pip install pypdf
pip install pandas
pip install scikit-learn
```

---

# 📄 Input Files

### Job Description

```text
jd.pdf
```

Contains:

* Required Skills
* Experience Requirements
* Education Requirements
* Responsibilities

---

### Candidate Resumes

```text
resume1.pdf
resume2.pdf
resume3.pdf
...
```

Each resume is automatically analyzed and compared against the Job Description.

---

# ▶️ How To Run

## Step 1: Upload Files

```python
from google.colab import files

uploaded = files.upload()
```

Upload:

```text
jd.pdf
resume1.pdf
resume2.pdf
resume3.pdf
```

---

## Step 2: Extract PDF Text

```python
from pypdf import PdfReader

def extract_pdf_text(pdf_file):

    reader = PdfReader(pdf_file)

    text = ""

    for page in reader.pages:

        page_text = page.extract_text()

        if page_text:

            text += page_text

    return text
```

---

## Step 3: Read Job Description

```python
jd_text = extract_pdf_text("jd.pdf")
```

---

## Step 4: Resume Matching

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
```

The system converts text into vectors and calculates similarity.

---

## Step 5: Calculate Match Score

```python
def calculate_match(jd, resume):

    vectorizer = TfidfVectorizer()

    vectors = vectorizer.fit_transform(
        [jd, resume]
    )

    similarity = cosine_similarity(
        vectors[0:1],
        vectors[1:2]
    )

    return round(
        similarity[0][0] * 100,
        2
    )
```

---

## Step 6: Candidate Classification

```python
if score >= 40:

    status = "SELECTED"

else:

    status = "REJECTED"
```

### Rule

| Score    | Result   |
| -------- | -------- |
| 40+      | Selected |
| Below 40 | Rejected |

---

## Step 7: Generate CSV Report

```python
df.to_csv(
    "candidate_screening_report.csv",
    index=False
)
```

---

# 🔄 Agent Workflow

```text
Job Description PDF
          │
          ▼
Text Extraction
          │
          ▼
Resume PDFs
          │
          ▼
Text Extraction
          │
          ▼
TF-IDF Vectorization
          │
          ▼
Cosine Similarity
          │
          ▼
Match Score
          │
          ▼
Selected / Rejected
          │
          ▼
CSV Report Generation
```

---

# 📊 Example

### Job Description

```text
Required Skills:
Python
Machine Learning
SQL
Data Analysis
```

---

### Resume 1

```text
Skills:
Python
SQL
Machine Learning
Pandas
Scikit-Learn
```

### Match Score

```text
82%
```

### Result

```text
SELECTED
```

---

### Resume 2

```text
Skills:
HTML
CSS
JavaScript
Bootstrap
```

### Match Score

```text
15%
```

### Result

```text
REJECTED
```

---

# 📈 Output Report

```csv
Resume,Match Score,Status
resume1.pdf,82,SELECTED
resume2.pdf,15,REJECTED
resume3.pdf,61,SELECTED
```

---

# 🎯 Applications

* HR Automation
* Resume Screening
* Applicant Tracking Systems (ATS)
* Recruitment Analytics
* Candidate Ranking
* Talent Acquisition

---

# Advantages

* Saves Recruiter Time
* Fast Candidate Screening
* Consistent Evaluation
* Handles Multiple Resumes
* Automated Reporting
* Easy To Scale

---

# Limitations

* Depends on Resume Quality
* Keyword-Based Matching
* Cannot Fully Judge Soft Skills
* Limited Context Understanding

---

# Future Improvements

* Skill Extraction Agent
* Experience Matching Agent
* Education Verification Agent
* ATS Score Generator
* Candidate Ranking Dashboard
* Streamlit Web Application
* Hugging Face Embeddings
* LLM-Based Resume Analysis
* Interview Recommendation Agent

---

# Learning Outcomes

After completing this project, you will understand:

* PDF Processing
* Information Extraction
* Text Similarity
* TF-IDF Vectorization
* Cosine Similarity
* AI-Based Recruitment Systems
* Automated Decision Making
* Report Generation

---

# Resume Description

Developed an AI Resume Screening Agent using Python, PDF Processing, and Machine Learning. The system automatically compares candidate resumes with job descriptions, calculates ATS-style match scores, classifies candidates as selected or rejected, and generates downloadable recruitment reports.

---

# 👨‍💻 Author

## Ajay Sagar

* Python Developer
* AI & Machine Learning Enthusiast
* B.Tech CSE Student

### Connect With Me

🔗 LinkedIn: https://www.linkedin.com/in/engineerajay

🚀 Building AI Projects and Learning New Technologies Every Day.

**Code the Future with Us..!**
