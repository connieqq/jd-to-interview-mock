---
name: "jd-to-interview-mock"
description: "Generates personalized interview preparation materials (HTML & MD) from JD and resume. Invoke when user wants to prepare for a specific job interview or asks to generate interview questions."
---

# JD-to-InterviewMock

Generate personalized interview preparation materials from job description (JD) and candidate's resume.

## When to Invoke

Use this skill when:
- User wants to prepare for a specific job interview
- User asks to generate interview questions based on JD and resume
- User wants to create interview preparation materials
- User provides a job description and resume and wants practice questions

## Required User Inputs

Before starting, collect the following information from the user:

1. **Company Name** - e.g., "字节跳动", "阿里巴巴", "腾讯"
2. **Job Title** - e.g., "高级产品经理", "AI产品经理"
3. **Job Description (JD)** - Full text of the job posting including:
   - Team/Product introduction
   - Job responsibilities
   - Job requirements
4. **Resume** - Candidate's resume in markdown format or file path (e.g., `/path/to/resume.md`)

If user hasn't provided all inputs, ask for them before proceeding.

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
2. Analyze JD requirements and resume alignment
       ↓
3. Search for company/product information (WebSearch)
       ↓
4. Generate 10-15 interview questions
       ↓
5. Generate answer strategies for each question
       ↓
6. Create HTML file (follow HTML-template.md)
       ↓
7. Create MD file (follow MD-template.md)
       ↓
8. Start local HTTP server for HTML preview
```

## Example Usage

```
User: 我要面试字节跳动的豆包AI大模型产品经理岗位，这是我的简历 /Users/connie/resume.md

Assistant:
1. Please provide:
   - Company: 字节跳动 ✓
   - Job Title: 豆包AI大模型产品经理 ✓
   - Job Description (JD): ?
   - Resume: /Users/connie/resume.md ✓

2. [User pastes JD]

3. [AI generates content following templates]

4. Output:
   - 蔡情情_字节跳动_豆包AI大模型产品经理_面试准备.html
   - 蔡情情_字节跳动_豆包AI大模型产品经理_面试准备.md
```

## Technical Notes

- Use WebSearch to gather company and product information
- Use WebFetch to get detailed company/product pages from JD links
- Read resume file if provided as file path
- Create files in current working directory
- Use candidate's actual name from resume for file naming
