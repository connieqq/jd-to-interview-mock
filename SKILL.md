---
name: "jd-to-interview-mock"
description: "Generates personalized interview preparation materials (HTML & MD) from JD and resume. Invoke when user wants to prepare for a specific job interview or asks to generate interview questions."
---

# JD-to-InterviewMock

Generate personalized interview preparation materials from job description (JD) and candidate's resume.

## Overview

This is a **universal AI skill** compatible with any AI-powered IDE or Agent that supports custom skills/instructions, including:

- **Trae IDE** - Use as a skill in `.trae/skills/` directory
- **Cursor** - Use as a rule in `.cursor/rules/`
- **Claude Code / Claude Desktop** - Use as system prompt or custom instructions
- **GitHub Copilot** - Use as custom instructions
- **Codex / OpenCLA** - Use as prompt instructions
- **Any Agent** - Copy-paste as custom skill definition

## When to Invoke

Use this skill when:
- User wants to prepare for a specific job interview
- User asks to generate interview questions based on JD and resume
- User wants to create interview preparation materials
- User provides a job description and resume and wants practice questions

## Required User Inputs

Before starting, collect the following information from the user:

1. **Company Name** - e.g., "XX跳动", "XX里", "XX讯"
2. **Job Title** - e.g., "高级产品经理", "AI产品经理"
3. **Job Description (JD)** - Full text of the job posting including:
   - Team/Product introduction
   - Job responsibilities
   - Job requirements
4. **Resume** - Candidate's resume content or file path. Supported formats:
   - Markdown: `.md`, `.markdown`
   - PDF: `.pdf`
   - Word: `.docx`, `.doc` where local tooling supports conversion

If user hasn't provided all inputs, ask for them before proceeding.

## Resume Normalization Requirement

Use Markdown as the single resume input format for all downstream analysis.

- If the user provides Markdown text or a Markdown file, use it directly as the normalized resume source.
- If the user provides a PDF or Word resume, first convert it into a Markdown file in the current working directory.
- Name the converted file with the original resume basename and `.md`, for example `resume.pdf` → `resume.md`.
- Treat PDF/Word-to-Markdown conversion as faithful content migration, not summarization or rewriting.
- Preserve the original resume content and key resume sections as completely as possible: candidate name, contact details, education, work experience, project experience, skills, dates, company names, role titles, metrics, achievements, tools/technologies, and section hierarchy.
- Keep the original section order, heading structure, bullet hierarchy, paragraph boundaries, and important keywords. Do not drop short bullets, quantified results, project context, or responsibility details just because they look repetitive.
- After conversion, read the generated Markdown file and use only that normalized Markdown content for JD/resume alignment and interview material generation.
- If PDF or Word conversion fails or produces obviously incomplete content, stop and ask the user for a cleaner PDF, Word, or Markdown version before generating interview materials.

## Output Files

The skill generates TWO files in the current working directory:

1. **HTML File**: `{候选人名字}_{公司名}_{岗位名}_面试准备.html`
   - Visual, interactive webpage
   - Dark theme with orange/cyan accent colors
   - Expandable/collapsible Q&A sections
   - Navigation filter by question type

2. **Markdown File**: `{候选人名字}_{公司名}_{岗位名}_面试准备.md`
   - Plain text format for easy reading/sharing
   - Complete content in structured sections

## Content Parity Requirement

The HTML and Markdown files must be generated from the same complete content source. Do not write separate shortened copy for HTML.

Before rendering either file, create a single internal content master that includes:
- Candidate, company, role, and generation date
- Company and position overview
- Full ordered question list with stable question IDs (`Q1`, `Q2`, ...)
- For every question: type, title, complete question text, interviewer evaluation criteria, answer strategy, sample answer, and key insight
- Candidate strengths, areas to improve, interview-day checklist, communication tips, and suggested reverse questions

Use the content master as the source of truth for both outputs:
- Markdown renders the content master as structured text.
- HTML renders the same content master with visual styling, cards, filters, and interactions.
- HTML may add layout labels, icons, badges, or navigation, but must not omit, summarize, or shorten any substantive text present in Markdown.
- Markdown may omit purely visual UI elements, but must include every substantive text item shown in HTML.

After generating both files, perform a parity check before finishing:
- The question count and question IDs must match exactly.
- Each question must have the same title, type, full question text, evaluation criteria, answer strategy, sample answer, and key insight in both files.
- The overview, strengths, improvement areas, interview-day tips, communication tips, and reverse questions must contain the same substantive content.
- If any mismatch is found, fix the shorter or missing side before reporting completion.

## Output Content Structure

Both files contain these four sections:

### Section 1: Company & Position Overview
- Company basic info (founded, valuation, products, financial performance)
- Team/Product introduction from JD
- Position responsibilities summary
- Position requirements summary

### Section 2: 10-15 Interview Questions
Generate diverse question types:

| Type | Count | Focus Areas |
|------|-------|-------------|
| Behavioral | 3-4 | Resume experiences matching JD, product definition, cross-team collaboration |
| Product Design | 2-3 | Company product direction, developer tools, UX optimization |
| Product Strategy | 2-3 | Market analysis, business model, customer pain points |
| Estimation | 1-2 | Market size, cost analysis, data-driven thinking |
| Scenario | 2-3 | Technical change, customer complaint, priority decisions |

### Section 3: Answer Strategies & Sample Answers

For EACH question, provide:
- **What interviewer wants to know**: The underlying evaluation criteria
- **Answer strategy**: Structured thinking process with methodology
- **Sample answer**: First-person narrative with specific examples from candidate's resume
- **Key insight box**: A memorable quote or highlight

### Section 4: Interview Preparation Tips

1. **Candidate's Strengths** (5-6 items based on resume vs JD match)
2. **Areas to Improve** (3-4 skill gaps with suggestions)
3. **Interview Day Tips** (checklist, communication, questions to ask)

## Question Generation Guidelines

### Alignment with JD
- Each question must relate to specific JD responsibilities or requirements
- Pay special attention to:
  - JD requirements NOT directly covered in resume → design targeted questions
  - Resume experiences matching JD requirements → emphasize deeply
- Design 1-2 questions to test JD requirements that resume doesn't fully demonstrate

### STAR Method for Behavioral Questions
- Situation: Set the context
- Task: Define your responsibility
- Action: Describe what you did
- Result: Share the outcome (with metrics if possible)

## Template Files

Detailed output specifications are in separate template files:

- **HTML Template**: `TEMPLATES/HTML-template.md`
  - Complete CSS variables and color palette
  - Hero section layout
  - Question card structure
  - JavaScript interactions
  - Navigation filter logic

- **Markdown Template**: `TEMPLATES/MD-template.md`
  - Document structure outline
  - Section headers format
  - Question formatting
  - Tips section template

## Generation Workflow

```
1. Collect user inputs (company, job, JD, resume)
       ↓
2. Normalize resume to Markdown if needed
       ↓
3. Analyze JD requirements and normalized resume alignment
       ↓
4. Search for company/product information (WebSearch)
       ↓
5. Build one complete content master for the whole deliverable
       ↓
6. Generate 10-15 interview questions and all answer content in that content master
       ↓
7. Create Markdown file from the content master (follow MD-template.md)
       ↓
8. Create HTML file from the same content master (follow HTML-template.md)
       ↓
9. Compare HTML and Markdown for substantive content parity
       ↓
10. Start local HTTP server for HTML preview (if supported)
```

## Example Usage

```
User: 我要面试XX跳动的AI产品经理岗位，这是我的简历 /path/to/resume.md

Assistant:
1. Please provide:
   - Company: XX跳动 ✓
   - Job Title: AI产品经理 ✓
   - Job Description (JD): ?
   - Resume: /path/to/resume.md ✓

2. [User pastes JD]

3. [AI generates content following templates]

4. Output:
   - 张三_XX跳动_AI产品经理_面试准备.html
   - 张三_XX跳动_AI产品经理_面试准备.md
```

## Technical Notes

- Use WebSearch to gather company and product information (if available)
- Use WebFetch to get detailed company/product pages from JD links (if available)
- Read resume file if provided as file path
- Convert PDF or Word resumes to a Markdown file before analysis, then use that generated Markdown file as the resume source
- Create files in current working directory
- Use candidate's actual name from resume for file naming
- If HTTP server is not available, output file path and suggest user open in browser
