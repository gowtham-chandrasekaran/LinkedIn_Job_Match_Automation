# LinkedIn_Job_Match_Automation | Resume-Based Job Scorer

This system runs end-to-end job discovery and triage using **n8n**, **OpenAI**, and **Google Sheets**. It ingests LinkedIn-style RSS items, pulls each posting’s page, extracts clean fields, scores fit against your resume, and writes only relevant roles to a sheet.

## About n8n and why it’s used
**n8n** is a self-hosted automation platform. I used it to chain **RSS → HTTP → LLM → Sheets** with low code, reproducible runs, and full control of keys and cost.


## Job Filtering Workflow

## Visual Workflow
![n8n workflow](workflow.png)

### Objective
- Collect job descriptions from public RSS feeds.  
- Evaluate resume fit with an LLM.  
- Skip low-match roles using a threshold.  
- Persist qualified roles to Google Sheets for review.

## How to Use

You can import the ready workflow JSON.

Import the provided workflow:

1. Clone/download this repo.  
2. Open your n8n instance.  
3. **Import** `Linkedin_Job_Match_Automation.json`.  
4. Create credentials:
   - **OpenAI** API key
   - **Google Sheets** OAuth2
5. In the scoring node, paste your latest **resume text** into the prompt.  
6. In the Sheets node, select your Spreadsheet and Sheet.  
7. Run once manually or enable the **Schedule**.

### Technologies

- n8n for orchestration
- OpenAI for parsing and scoring
- Google Sheets API for storage
- RSS as the job source

### Prerequisites

- OpenAI API access
- Google account with Sheets access
- n8n instance (local, Docker, or hosted)
- Resume text ready to embed in the scoring prompt

### Recommended Sheet Columns

Link (unique), Title, Date, Job Description, Exp Years Required, Type Of Job, Skills, Education Required, Salary Range, Work Arrangement, Location, Company Name, Benefits, Visa Sponsorship, Score, Gaps, Matched Skills, Rationale.

### Author

- Gowtham Chandrasekaran
- Portfolio: www.gowthamchandrasekaran.com
