# JD-to-InterviewMock

**一个将职位描述(JD)和简历转化为个性化面试准备材料的 Trae IDE Skill**

[English](README_EN.md) | 中文

---

## 功能特点

- **📝 智能生成** - 基于JD和简历，自动生成10-15道针对性面试题
- **🎨 可视化页面** - 输出精美的HTML交互式面试准备页面
- **📄 Markdown文档** - 同时输出易读的Markdown格式文档
- **💡 回答策略** - 每道题提供面试官考察点、回答策略和示范回答
- **✅ 准备建议** - 清晰的核心优势和待提升点分析

## 面试题类型覆盖

| 类型 | 数量 | 说明 |
|------|------|------|
| 行为面试 | 3-4道 | 基于简历项目经历，考察实际能力 |
| 产品设计 | 2-3道 | 结合公司产品方向，考察设计思维 |
| 产品策略 | 2-3道 | 考察市场和业务理解 |
| 估算分析 | 1-2道 | 考察逻辑和数据思维 |
| 情境题 | 2-3道 | 模拟真实工作挑战 |

## 安装

### 方法一：复制 Skill 文件

1. 下载或克隆本仓库
2. 将 `SKILL.md` 复制到你的 Trae IDE 项目中：
   ```
   .trae/skills/jd-to-interview-mock/SKILL.md
   ```
3. 将 `TEMPLATES/` 目录也复制到对应位置：
   ```
   .trae/skills/jd-to-interview-mock/TEMPLATES/
   ```

### 方法二：创建目录结构

```
.trae/skills/jd-to-interview-mock/
├── SKILL.md              # 主技能文件
└── TEMPLATES/
    ├── HTML-template.md  # HTML设计规范
    └── MD-template.md   # Markdown格式规范
```

## 使用方式

### 1. 准备材料

在开始前，请准备：
- **公司名称** - 如 "字节跳动"
- **岗位名称** - 如 "AI产品经理"
- **岗位JD** - 完整的职位描述（包含团队介绍、职责、要求）
- **个人简历** - Markdown格式或文件路径

### 2. 调用 Skill

在 Trae IDE 中调用 `jd-to-interview-mock` skill，然后提供以上材料。

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
公司：字节跳动
岗位：豆包AI大模型产品经理
JD：火山方舟MaaS平台产品经理...
简历：蔡情情 - 浙大CS硕士，3年产品经理经验...
```

### 输出结构

```markdown
# 蔡情情 - 字节跳动 豆包AI大模型产品经理 面试准备

## 一、公司 & 岗位概况
### 1.1 字节跳动
- 公司基本信息、核心业务、财务表现

### 1.2 豆包AI大模型产品经理
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
├── SKILL.md             # 主技能文件
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

## 技术栈

- **HTML5** - 语义化标签
- **CSS3** - CSS变量、动画、响应式
- **JavaScript** - 原生JS，无依赖
- **Google Fonts** - Outfit, Noto Sans SC, Space Mono

## 贡献

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建你的 Feature Branch (`git checkout -b feature/AmazingFeature`)
3. 提交你的 Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push 到 Branch (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 更新日志

### v1.0.0 (2026-04-10)
- 初始版本发布
- 支持生成HTML和Markdown两种格式
- 包含完整的面试题库和回答策略

## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

## 致谢

- [Trae IDE](https://www.trae.ai/) - AI驱动的开发环境
- [Google Fonts](https://fonts.google.com/) - 开源字体

---

如果你觉得这个项目有帮助，请 ⭐ star 支持一下！
