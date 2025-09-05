# LinkedIn_Job_Match_Automation
Automates daily job discovery from an RSS feed, extracts structured job details with an LLM, scores fit against a resume, and logs results to Google Sheets.

# N8N
n8n is a self-hosted workflow automation tool. It connects APIs, runs code, and orchestrates steps with retries and credentials. I used n8n because it lets me chain RSS → HTTP → LLM → Google Sheets with low code, full transparency, and easy on-prem control of secrets and costs.

# Purpose
My workflow automatically pulls LinkedIn job postings via RSS and organizes them into a Google Sheet. But what really makes this workflow powerful is the custom Score Generator node I added. For each job, the Score Generator analyzes my resume against the job description, then:
 • Assigns a score out of 5 based on how well my skills match the requirements
 • Highlights matched skills and identifies any skill gaps
 • Generates a rationale explaining the score, so I know exactly where I stand and what I can improve

This means I get instant, actionable insights for every opportunity—helping me target roles where I’m the strongest fit and quickly spot areas to upskill.

## Overview
- Schedule runs daily at 12:00.
- Read jobs from an RSS feed.
- For each job:
  - Fetch the job page HTML.
  - Extract normalized fields via an OpenAI node.
  - Score match vs a resume (`score`, `rationale`, `gaps`, `matched_skills`).
- Upsert a Google Sheet keyed by job link to avoid duplicates.

# Requirements

n8n (Docker or Desktop)

OpenAI API key

Google account and target Google Sheet
