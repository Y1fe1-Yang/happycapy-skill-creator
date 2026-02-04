# HappyCapy Skill Creator

<div align="center">

[![English](https://img.shields.io/badge/Language-English-blue)](#english) | [![中文](https://img.shields.io/badge/语言-中文-red)](#中文)

**Automated skill creation for HappyCapy - Adapt existing skills in minutes!**

[Quick Start](#quick-start) • [Features](#features) • [Documentation](#documentation) • [Examples](#examples)

</div>

---

<a name="english"></a>
## 🌏 English

### 🚀 What is This?

A tool that creates HappyCapy skills by **adapting existing skills** instead of building from scratch:

1. 🔍 **Searches** for similar skills in anthropics/skills
2. 📥 **Clones** the most relevant skill
3. ✨ **Adds** your requested features using AI
4. 🔧 **Fixes** HappyCapy compatibility issues automatically
5. 📦 **Packages** a ready-to-use skill

**No coding required!** Just describe what you need.

### ⚡ Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Set API key (HappyCapy environment has this pre-configured)
export AI_GATEWAY_API_KEY=your-key

# 3. Create a skill
python scripts/create_skill.py "I need to compress PDF files"

# Or with non-interactive mode:
python scripts/create_skill.py "I need to compress PDF files" --name pdf-compressor

# 4. Done in ~3 minutes! 🎉
```

### ✨ Features

| Feature | Description |
|---------|-------------|
| 🤖 **AI-Powered** | Uses LLM for semantic search and code integration |
| 🔄 **Adaptation-First** | Reuses proven code from anthropics/skills |
| 🛠️ **Auto-Fix** | Automatically handles compatibility issues |
| 👶 **Beginner-Friendly** | One command, clear messages |
| ⚡ **Fast** | 3 minutes vs 4.5 hours manual creation |
| 🎯 **Environment-Aware** | Respects HappyCapy constraints automatically |

### 📊 Comparison

| Method | Time | Difficulty |
|--------|------|-----------|
| Manual Creation | 4.5 hours | High |
| **This Tool** | **3 minutes** | **Very Low** |

**90x faster!**

### 🎯 How It Works

```
Your Request → AI Search → Clone Skill → Add Features → Auto-Fix → Package
     ↓              ↓            ↓             ↓            ↓          ↓
  "compress     Find pdf     Clone to     LLM adds    Remove      Ready
   PDFs"          skill      workspace    compress    Docker      .skill
```

### 📚 Documentation

- **[SKILL.md](SKILL.md)** - Complete methodology
- **[QUICK_START.md](QUICK_START.md)** - 1-minute setup
- **[PROJECT_SUMMARY.md](PROJECT_SUMMARY.md)** - Architecture & achievements
- **[examples/](examples/)** - Real-world examples

### 🎓 Examples

#### Example 1: Compress PDFs
```bash
python scripts/create_skill.py "I need to compress PDF files"
```
→ Finds `pdf` skill, adds compress function, creates `compress-pdf.skill`

#### Example 2: Extract Video Frames
```bash
python scripts/create_skill.py "Extract frames from videos every second"
```
→ Finds `video-frames` skill, adapts it, ready to use

#### Example 3: Already Exists
```bash
python scripts/create_skill.py "Enhance image quality"
```
→ Finds existing `image-enhancer`, suggests direct installation

### 🔧 Requirements

- Python 3.11+
- `AI_GATEWAY_API_KEY` (HappyCapy environment has this pre-configured)
- Internet connection (to clone from GitHub)
- Dependencies: `pip install -r requirements.txt`

### 📂 Project Structure

```
happycapy-skill-creator/
├── scripts/                      # Core system (10 modules)
│   ├── create_skill.py          # Main entry point
│   ├── semantic_search.py       # AI-powered search
│   ├── integrate_feature.py     # LLM code integration
│   ├── auto_fix.py              # Auto-fix compatibility
│   └── ...
├── references/
│   └── happycapy-environment.md # Environment constraints
├── examples/
│   └── example-workflow.md      # Complete walkthrough
└── README.md                     # This file
```

### 🤝 Contributing

Issues and PRs welcome! Please check existing issues first.

### 📄 License

[Specify License]

### 🙏 Acknowledgments

Built on top of [Anthropic's skill-creator](https://github.com/anthropics/skills).

---

<a name="中文"></a>
## 🌏 中文

### 🚀 这是什么？

一个通过**适配现有技能**而非从零开始来创建 HappyCapy 技能的工具：

1. 🔍 **搜索** anthropics/skills 中的相似技能
2. 📥 **克隆** 最相关的技能
3. ✨ **添加** 你需要的功能（使用 AI）
4. 🔧 **自动修复** HappyCapy 兼容性问题
5. 📦 **打包** 可直接使用的技能

**无需编程！** 只需描述你的需求。

### ⚡ 快速开始

```bash
# 1. 安装依赖
pip install -r requirements.txt

# 2. 设置 API key (HappyCapy 环境已预配置)
export AI_GATEWAY_API_KEY=你的密钥

# 3. 创建技能
python scripts/create_skill.py "我需要压缩 PDF 文件"

# 或使用非交互模式:
python scripts/create_skill.py "我需要压缩 PDF 文件" --name pdf-compressor

# 4. 约 3 分钟完成！🎉
```

### ✨ 核心特性

| 特性 | 说明 |
|------|------|
| 🤖 **AI 驱动** | 使用大语言模型进行语义搜索和代码集成 |
| 🔄 **适配优先** | 复用 anthropics/skills 中经过验证的代码 |
| 🛠️ **自动修复** | 自动处理兼容性问题 |
| 👶 **新手友好** | 一条命令，清晰提示 |
| ⚡ **快速** | 3 分钟 vs 手动创建 4.5 小时 |
| 🎯 **环境感知** | 自动遵守 HappyCapy 约束 |

### 📊 对比

| 方法 | 时间 | 难度 |
|------|------|------|
| 手动创建 | 4.5 小时 | 高 |
| **本工具** | **3 分钟** | **极低** |

**快 90 倍！**

### 🎯 工作原理

```
你的需求 → AI搜索 → 克隆技能 → 添加功能 → 自动修复 → 打包
    ↓         ↓          ↓          ↓          ↓         ↓
  "压缩     找到 pdf   克隆到     LLM添加    移除      生成
   PDF"      技能     工作区     压缩功能   Docker    .skill
```

### 📚 文档

- **[SKILL.md](SKILL.md)** - 完整方法论（英文）
- **[QUICK_START.md](QUICK_START.md)** - 1分钟设置指南（英文）
- **[PROJECT_SUMMARY.md](PROJECT_SUMMARY.md)** - 架构与成就（英文）
- **[examples/](examples/)** - 实际案例

### 🎓 示例

#### 示例 1: 压缩 PDF
```bash
python scripts/create_skill.py "我需要压缩 PDF 文件"
```
→ 找到 `pdf` 技能，添加压缩功能，生成 `compress-pdf.skill`

#### 示例 2: 提取视频帧
```bash
python scripts/create_skill.py "每秒从视频中提取帧"
```
→ 找到 `video-frames` 技能，适配后即可使用

#### 示例 3: 已存在
```bash
python scripts/create_skill.py "提升图片质量"
```
→ 发现已有 `image-enhancer`，建议直接安装

### 🔧 需求

- Python 3.11+
- `AI_GATEWAY_API_KEY` (HappyCapy 环境已预配置)
- 互联网连接（用于从 GitHub 克隆）
- 依赖: `pip install -r requirements.txt`

### 📂 项目结构

```
happycapy-skill-creator/
├── scripts/                      # 核心系统（10个模块）
│   ├── create_skill.py          # 主入口
│   ├── semantic_search.py       # AI语义搜索
│   ├── integrate_feature.py     # LLM代码集成
│   ├── auto_fix.py              # 自动修复兼容性
│   └── ...
├── references/
│   └── happycapy-environment.md # 环境约束
├── examples/
│   └── example-workflow.md      # 完整演示
└── README.md                     # 本文件
```

### 🎓 核心创新

#### 1. 适配优先（vs 从零创建）
- 搜索现有的高质量技能
- 保留所有原功能
- 只添加用户需要的新功能

#### 2. LLM 驱动
- **语义搜索**：理解意图，而非只匹配关键词
- **代码集成**：自动匹配现有代码风格
- **智能修复**：重写不兼容的代码

#### 3. 环境感知
自动处理 HappyCapy 约束：
- ❌ 移除 Docker（不可用）
- ✅ 优化内存使用（4GB 限制）
- ✅ 确保 Python 3.11 / Node.js 24 兼容

#### 4. 新手友好
- 一条命令完成
- 清晰的进度提示
- 详细的错误处理

### 🔍 工作流程详解

```
步骤 1: 检查已安装的技能
  └─ 整合 find-skills 功能

步骤 2: 语义搜索相似技能
  └─ 使用 Claude 理解需求
  └─ 从 anthropics/skills 找最佳匹配

步骤 3: 克隆基础技能
  └─ 从 GitHub 下载
  └─ 保留所有现有功能

步骤 4: 识别新功能
  └─ 提取需求中的新功能

步骤 5: 搜索实现
  └─ 查找功能的现成实现

步骤 6: 集成功能
  └─ LLM 适配代码风格
  └─ 添加到技能中

步骤 7: 兼容性检查
  └─ 扫描 Docker、内存、依赖

步骤 8: 自动修复
  └─ LLM 重写不兼容代码
  └─ 循环直到通过检查

步骤 9: 测试
  └─ 验证结构和语法

步骤 10: 用户命名
  └─ 输入技能名称 (或使用 --name 参数)

步骤 11: 打包
  └─ 生成 .skill 文件
```

### 🛠️ 故障排除

#### "未找到 API key"
```bash
export ANTHROPIC_API_KEY=sk-ant-...
```

#### "未找到相似技能"
尝试不同的描述或更具体的需求

#### "克隆失败"
检查网络连接，工具会自动创建模板作为后备

#### "测试失败"
查看 `workspace/<技能名>/` 中的文件

### 💡 最佳实践

#### 1. 描述要具体
- ✅ "压缩 PDF 文件以减小文件大小"
- ❌ "处理文件"

#### 2. 先检查是否已存在
```bash
/find-skills "你的需求"
```

#### 3. 查看生成的代码
```bash
cd workspace/<技能名>
cat SKILL.md
ls scripts/
```

### 🤝 参与贡献

欢迎 Issues 和 PRs！请先查看现有 issues。

### 📄 许可证

[指定许可证]

### 🙏 致谢

基于 [Anthropic skill-creator](https://github.com/anthropics/skills) 构建。

---

<div align="center">

**Get Started:** `python scripts/create_skill.py "your requirement"`

**立即开始：** `python scripts/create_skill.py "你的需求"`

Made with ❤️ for HappyCapy

</div>
