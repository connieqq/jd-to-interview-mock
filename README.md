# JD-to-InterviewMock

**一个基于职位描述(JD)和简历，转化生成个性化面试准备材料的通用 AI Skill（目前主要for 产品经理岗位）**

适用于 Trae 、Cursor、Claude Code、Codex、Openclaw 等所有支持自定义技能的 AI Agent 和 IDE

[English](README_EN.md) | 中文

***

## 功能特点

- **📝 智能生成** - 基于JD和简历，自动生成10-15道针对性面试题
- **🎨 可视化页面** - 输出精美的HTML交互式面试准备页面
- **📄 Markdown文档** - 同时输出易读的Markdown格式文档
- **💡 回答策略** - 每道题提供面试官考察点、回答策略和示范回答
- **✅ 准备建议** - 清晰的核心优势和待提升点分析
- **🌐 通用设计** - 适配所有主流 AI IDE 和 Agent

## 面试题类型覆盖

| 类型   | 数量   | 说明              |
| ---- | ---- | --------------- |
| 行为面试 | 3-4道 | 基于简历项目经历，考察实际能力 |
| 产品设计 | 2-3道 | 结合公司产品方向，考察设计思维 |
| 产品策略 | 2-3道 | 考察市场和业务理解       |
| 估算分析 | 1-2道 | 考察逻辑和数据思维       |
| 情境题  | 2-3道 | 模拟真实工作挑战        |

## 安装

### 基本安装

1. 下载或克隆本仓库
2. 根据您使用的平台，将文件放置到对应目录（见上表）
3. 重启 IDE 或重新加载工作区


### Claude Code /Codex/ Desktop （以及其他平台）

手动安装该技能：

```Markdown
git clone https://github.com/connieqq/jd-to-interview-mock  

##或者直接用自然语言描述
帮我安装这个技能：https://github.com/connieqq/jd-to-interview-mock
```

<br />

## 使用方式

### 1. 准备材料

在开始前，请准备：

- **公司名称** - 如 "XX 跳动"
- **岗位名称** - 如 "AI产品经理"
- **岗位JD** - 完整的职位描述（包含团队介绍、职责、要求）
- **个人简历** - Markdown格式或文件路径

### 2. 调用 Skill

在对应的 AI Agent 工具中调用 `jd-to-interview-mock` skill，然后提供以上材料。
生成面试模拟的prompt 描述参考如下：

```
我要面试XX公司的 XX 产品经理岗位，请用 jd-to-interview-mock 帮我生成面试准备材料。
# 这是我的简历：/Users/resume.md
# 这是岗位 JD：……

```

### 3. 获取输出

Skill 会生成两个文件：

```
{候选人名字}_{公司名}_{岗位名}_面试准备.html
{候选人名字}_{公司名}_{岗位名}_面试准备.md
```

## 输出内容

### HTML 页面

- 🎨 深色主题，橙青色配色
- 📂 可展开/收起的面试题卡片
- 🔍 按题目类型筛选导航
- ✨ 滚动动画效果
- 📱 响应式设计

### Markdown 文档

- 📖 结构化章节布局
- 📋 清晰的表格和列表
- 💬 对话式示范回答
- 🎯 针对性准备建议

## 示例输出

### 输入

```
公司：XX跳动
岗位：XX产品经理
JD：XX平台产品经理...
简历：张三 - XX硕士，3年产品经理经验...
```

### 输出结构

```markdown
# 张三 - XX跳动 XX产品经理 面试准备

## 一、公司 & 岗位概况
### 1.1 XX跳动
- 公司基本信息、核心业务、财务表现

### 1.2 XX产品经理
- 团队介绍、核心职责、职位要求

## 二、面试题 (共15道)
### Q1. 产品定义与落地能力...
### Q2. 技术深度与跨团队协作...
...

## 三、面试准备建议
### 3.1 你的核心优势
### 3.2 需要加强的点
### 3.3 面试当天建议
```

## 项目结构

```
jd-to-interview-mock/
├── README.md             # 本文件
├── README_EN.md         # English version
├── SKILL.md             # 主技能文件（通用）
├── TEMPLATES/
│   ├── HTML-template.md # HTML设计规范
│   └── MD-template.md   # Markdown格式规范
├── EXAMPLES/
│   └── sample-output.md # 示例输出
└── LICENSE              # MIT许可证
```

## 自定义

### 修改 HTML 样式

编辑 `TEMPLATES/HTML-template.md` 中的 CSS 变量：

```css
--bg-dark: #0a0a0f;        /* 背景色 */
--accent-orange: #ff6b35;   /* 橙色强调 */
--accent-cyan: #00d4aa;    /* 青色强调 */
```

### 修改 Markdown 格式

编辑 `TEMPLATES/MD-template.md` 中的文档结构。


## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

## 致谢

- [Google Fonts](https://fonts.google.com/) - 开源字体

***

如果你觉得这个项目有帮助，请 ⭐ star 支持一下！
