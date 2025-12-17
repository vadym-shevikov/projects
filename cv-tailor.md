---
title: "CV Tailor (CV Optimization Assistant) @pre-alpha"
summary: "Multi-agent, local-first AI assistant that takes your CV (PDF) and a job description (text), then analyzes fit + ATS readiness, rewrites key sections, and explains why each change helps for this specific role."
techStack: ["Python", "LangChain", "LangGraph"]
githubUrl: "https://github.com/vadym-shevikov/cv-tailor"
featured: true
---

# CV Tailor — CV Optimization Assistant

**CV Tailor** is a local, multi-agent AI assistant that helps you tailor your resume to a specific job. You upload a **CV as a PDF** and paste a **job description** (as text), and the system returns a clear **Markdown report**: fit analysis, missing keywords, ATS-friendly improvements, and suggested rewrites for key sections.

<video controls width="100%" style="aspect-ratio: 16/9; border-radius: 8px; margin: 1.5rem 0;">
  <source src="/video/projects/cv-tailor/demo.mp4" type="video/mp4" />
  Your browser does not support the video tag.
</video>


## What it does

- Analyzes CV ↔ job description alignment (requirements, responsibilities, keywords)
- Performs basic **ATS readiness** checks (structure, keyword coverage, bullet style)
- Rewrites key sections:
  - Summary / Profile
  - Skills / Tech stack
  - Selected, most relevant experience bullets
- Explains **why** each change improves your CV for the specific role

## How it works (short)

The project is built as an orchestration of **three agents** in **LangGraph**:

1. **Parsing & Structuring**
   - extracts text from the PDF
   - structures the CV (summary/skills/experience)
   - parses the job description (requirements/skills/key phrases)
2. **Analysis & ATS Checker**
   - compares CV ↔ job description
   - finds gaps, missing keywords, and ATS readability issues
   - uses a local best-practices knowledge base
3. **Rewriting & Explanations**
   - produces “before/after” rewrites for each section
   - adds explanations grounded in the job description and ATS guidelines

The final output is assembled as **Markdown** and rendered in a minimal web UI.

## Tech stack

- **Python 3.11+**
- **FastAPI** (minimal web server + form UI)
- **LangChain** (LLM integration)
- **LangGraph** (multi-agent orchestration)
- **MCP** (filesystem MCP server as a knowledge layer)
