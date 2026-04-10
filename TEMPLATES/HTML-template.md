# HTML Template Specification

This document contains the complete HTML design specifications for the interview preparation webpage.

## Visual Style

### Color Palette
```css
--bg-dark: #0a0a0f;
--bg-card: #12121a;
--bg-card-hover: #1a1a25;
--accent-orange: #ff6b35;
--accent-orange-light: #ff8f66;
--accent-cyan: #00d4aa;
--accent-cyan-dim: #00d4aa40;
--accent-purple: #a855f7;
--accent-blue: #3b82f6;
--text-primary: #ffffff;
--text-secondary: #a1a1aa;
--text-muted: #71717a;
--border-color: #27272a;
--gradient-fire: linear-gradient(135deg, #ff6b35 0%, #ff8f66 50%, #ffb347 100%);
--gradient-cyan: linear-gradient(135deg, #00d4aa 0%, #00b894 100%);
```

### Typography
- Headings: **Outfit** (Google Font, weights 300-900)
- Body: **Noto Sans SC** (Chinese support)
- Code/Numbers: **Space Mono**

## Page Layout

### Hero Section
```
┌─────────────────────────────────────────────────┐
│  [Avatar]  Candidate Name                        │
│           Product Manager · X years experience   │
│                                                  │
│  [求职岗位]  Company · Job Title                │
│                                                  │
│  Summary line 1                                 │
│  Summary line 2                                 │
│                                                  │
│  [Tag: Education]  [Tag: Experience]  [Tag:Skills] │
└─────────────────────────────────────────────────┘
```

**HTML Structure:**
```html
<section class="hero">
    <div class="hero-content">
        <div class="candidate-header">
            <div class="candidate-avatar">[姓]</div>
            <div class="candidate-info">
                <h1 class="candidate-name">候选人名字</h1>
                <p class="candidate-title">产品经理 · 3年经验</p>
            </div>
        </div>
        <p class="job-position">
            <span class="position-label">求职岗位</span>
            公司 · 岗位名称
        </p>
        <p class="hero-subtitle">
            浙大CS硕士 · 音视频+AI产品专家 · PaaS平台经验<br>
            从快手到即构，深度理解企业级AI产品落地
        </p>
        <div class="hero-meta">
            <div class="meta-tag">教育背景</div>
            <div class="meta-tag">工作经历</div>
            <div class="meta-tag">核心技能</div>
        </div>
    </div>
</section>
```

### Question Card Layout
```
┌─────────────────────────────────────────────────┐
│  [01]  [Behavioral]                            │
│         Question title                          │
│         Brief question description              │
│                                         [▼]     │
├─────────────────────────────────────────────────┤
│  面试官考察点                                   │
│  Answer content...                              │
│                                                  │
│  回答策略                                       │
│  Answer content...                              │
│                                                  │
│  ┌─────────────────────────────────────────┐    │
│  │ Highlight quote (金句)                   │    │
│  └─────────────────────────────────────────┘    │
└─────────────────────────────────────────────────┘
```

**HTML Structure:**
```html
<div class="question-card" data-type="behavioral">
    <div class="question-header" onclick="toggleQuestion(this)">
        <span class="q-number">01</span>
        <div class="q-content">
            <span class="q-type">行为面试</span>
            <h3>问题标题</h3>
            <p>问题描述</p>
        </div>
        <div class="q-toggle">
            <svg><!-- arrow icon --></svg>
        </div>
    </div>
    <div class="question-body">
        <div class="q-answer">
            <div class="answer-section">
                <h4>面试官考察点</h4>
                <p>内容...</p>
            </div>
            <div class="answer-section">
                <h4>回答策略</h4>
                <p>内容...</p>
            </div>
            <div class="highlight-box">
                <p>金句...</p>
            </div>
        </div>
    </div>
</div>
```

## Navigation

### Filter Buttons
```
[全部] [行为面试] [产品设计] [产品策略] [估算分析] [情境题]
```

**JavaScript:**
```javascript
document.querySelectorAll('.q-nav-btn').forEach(btn => {
    btn.addEventListener('click', function() {
        const filter = this.dataset.filter;
        document.querySelectorAll('.question-card').forEach(card => {
            if (filter === 'all' || card.dataset.type === filter) {
                card.style.display = 'block';
            } else {
                card.style.display = 'none';
            }
        });
    });
});
```

## Interactions

### Expand/Collapse Question
```javascript
function toggleQuestion(element) {
    const card = element.closest('.question-card');
    card.classList.toggle('open');
}
```

### Scroll Animation
```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('visible');
        }
    });
}, { threshold: 0.1 });
```

## CSS Animations

### Keyframes
```css
@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
    0%, 100% { transform: scale(1); opacity: 0.15; }
    50% { transform: scale(1.1); opacity: 0.2; }
}

@keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
}
```

### Transition Effects
- Cards: `transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1)`
- Meta tags: `transition: all 0.3s ease`
- Question body: `max-height: 0` to `max-height: 2000px` (expandable)

## Responsive Design

```css
@media (max-width: 768px) {
    .hero h1 { font-size: 2.5rem; }
    section { padding: 4rem 1.5rem; }
    .question-header { flex-direction: column; }
    .stat-row { flex-direction: column; }
    .jd-summary { padding: 1.5rem; }
}
```

## Section Structure

1. **Hero** - Candidate introduction with job position
2. **Overview (Section 01)** - Company & Position Overview
3. **Questions (Section 02)** - 10-15 Interview Questions with expandable answers
4. **Tips (Section 03)** - Interview Preparation Tips

## File Naming

```
{候选人名字}_{公司名}_{岗位名}_面试准备.html
```

Example: `蔡情情_字节跳动_豆包AI大模型产品经理_面试准备.html`

## Complete Template

See the actual generated file at project root for complete implementation:
`/Users/connie/Documents/trae_projects/Resume-JD-skills/面试准备页面.html`
