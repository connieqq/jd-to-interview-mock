# JD-to-InterviewMock

**A universal AI Skill that transforms Job Descriptions (JD) and Resumes into personalized interview preparation materials**

Works with Trae IDE, Cursor, Claude Code, GitHub Copilot, Codex, OpenCLA, and any AI IDE or Agent that supports custom skills

---

## Features

- **📝 Smart Generation** - Auto-generate 10-15 targeted interview questions from JD and resume
- **🎨 Visual Page** - Output beautiful interactive HTML interview preparation page
- **📄 Markdown Document** - Also output easy-to-read Markdown format document
- **💡 Answer Strategies** - Provide interview evaluation points, answer strategies, and sample answers for each question
- **✅ Preparation Tips** - Clear analysis of core strengths and areas to improve
- **🌐 Universal Design** - Works with all major AI IDEs and Agents

## Question Types Coverage

| Type | Count | Description |
|------|-------|-------------|
| Behavioral | 3-4 | Based on resume project experience, assess actual abilities |
| Product Design | 2-3 | Combined with company product direction, assess design thinking |
| Product Strategy | 2-3 | Assess market and business understanding |
| Estimation | 1-2 | Assess logical and data thinking |
| Scenario | 2-3 | Simulate real work challenges |

## Platform Compatibility

This skill works with the following platforms:

| Platform | Usage |
|----------|-------|
| **Trae IDE** | Place in `.trae/skills/` directory |
| **Cursor** | Place in `.cursor/rules/` directory |
| **Claude Code / Desktop** | Use as system prompt or custom instructions |
| **GitHub Copilot** | Use as custom instructions |
| **Codex / OpenCLA** | Use as prompt instructions |
| **Other Agents** | Copy as custom skill definition |

## Installation

### Basic Installation

1. Download or clone this repository
2. Place files in the appropriate directory for your platform (see table above)
3. Restart IDE or reload workspace

### Trae IDE

```
.your-project/
├── .trae/
│   └── skills/
│       └── jd-to-interview-mock/
│           ├── SKILL.md
│           └── TEMPLATES/
│               ├── HTML-template.md
│               └── MD-template.md
```

### Cursor

```
.your-project/
├── .cursor/
│   └── rules/
│       └── jd-to-interview-mock.md
```

### Claude Code / Desktop

Use the `SKILL.md` content as your system prompt:

```json
{
  "systemPrompt": "[paste SKILL.md content here]"
}
```

### Other Platforms

Simply copy the `SKILL.md` content into your platform's custom instructions configuration.

## Usage

### 1. Prepare Materials

Before starting, prepare:
- **Company Name** - e.g., "XX Tech"
- **Job Title** - e.g., "AI Product Manager"
- **Job Description (JD)** - Complete job posting including team intro, responsibilities, requirements
- **Resume** - Markdown format or file path

### 2. Invoke Skill

Invoke the `jd-to-interview-mock` skill in your AI IDE, then provide the above materials.

### 3. Get Output

The skill generates two files:

```
{candidate_name}_{company}_{job_title}_interview_prep.html
{candidate_name}_{company}_{job_title}_interview_prep.md
```

## Output Content

### HTML Page

- 🎨 Dark theme with orange/cyan colors
- 📂 Expandable/collapsible question cards
- 🔍 Filter navigation by question type
- ✨ Scroll animations
- 📱 Responsive design

### Markdown Document

- 📖 Structured chapter layout
- 📋 Clear tables and lists
- 💬 Conversational sample answers
- 🎯 Targeted preparation suggestions

## Project Structure

```
jd-to-interview-mock/
├── README.md             # This file
├── README_EN.md         # English version
├── SKILL.md             # Main skill file (universal)
├── TEMPLATES/
│   ├── HTML-template.md # HTML design specifications
│   └── MD-template.md   # Markdown format specifications
├── EXAMPLES/
│   └── sample-output.md # Sample output
└── LICENSE              # MIT License
```

## Customization

### Modify HTML Styles

Edit CSS variables in `TEMPLATES/HTML-template.md`:

```css
--bg-dark: #0a0a0f;        /* Background color */
--accent-orange: #ff6b35;   /* Orange accent */
--accent-cyan: #00d4aa;    /* Cyan accent */
```

### Modify Markdown Format

Edit document structure in `TEMPLATES/MD-template.md`.

## Tech Stack

- **HTML5** - Semantic tags
- **CSS3** - CSS Variables, animations, responsive
- **JavaScript** - Vanilla JS, no dependencies
- **Google Fonts** - Outfit, Noto Sans SC, Space Mono

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the Repository
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Changelog

### v1.1.0 (2026-04-11)
- Redefined as universal AI Skill supporting all major IDEs and Agents
- Removed platform-specific descriptions
- Added multi-platform usage instructions

### v1.0.0 (2026-04-10)
- Initial release
- Support generating HTML and Markdown formats
- Includes complete interview question bank and answer strategies

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file

## Show Your Support

Give a ⭐ if this project helped you!