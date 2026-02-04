---
name: happycapy-skill-creator
description: Novice-friendly skill creation for HappyCapy. Automatically searches anthropics/skills for similar skills, clones and adapts them, integrates new features with LLM fine-tuning, and auto-fixes compatibility issues. Adaptation-first approach that leverages existing high-quality skills rather than building from scratch.
---

# HappyCapy Skill Creator

**For Beginners** - Automated skill creation through adaptation

## What This Does

Instead of building skills from scratch, this tool:

1. **Searches** for similar existing skills in anthropics/skills
2. **Clones** the most relevant skill
3. **Adds** your requested features using LLM
4. **Fixes** any HappyCapy compatibility issues automatically
5. **Packages** a ready-to-use skill

## Quick Start

```bash
python scripts/create_skill.py "I need to compress PDF files"
```

The system will:
- Find the `pdf` skill (closest match)
- Clone it
- Add compress functionality
- Fix any compatibility issues
- Package as `compress-pdf.skill`

## How It Works

```
Your Request → Find Similar Skill → Clone → Add Features → Auto-Fix → Package
```

### Step-by-Step

1. **Semantic Search**
   - Uses LLM to understand your need
   - Finds most relevant skill from anthropics/skills
   - Example: "compress PDF" → finds "pdf-skill"

2. **Clone Base Skill**
   - Downloads the skill from GitHub
   - Preserves all existing functionality

3. **Feature Integration**
   - Searches for implementation of your feature
   - LLM adapts it to match skill's style
   - Keeps all original features

4. **Compatibility Check**
   - Scans for Docker usage (not available)
   - Checks for unavailable dependencies
   - Verifies memory patterns

5. **Auto-Fix**
   - LLM rewrites incompatible code
   - Removes Docker dependencies
   - Optimizes memory usage
   - Ensures Python 3.11 / Node.js 24 compatibility

6. **Test & Package**
   - Basic validation
   - Creates .skill file
   - Ready to install

## Environment Awareness

Skills must work within HappyCapy constraints:

### ✅ Available
- Python 3.11, Node.js 24
- pandoc, ImageMagick, jq
- 4GB RAM, 2 CPU cores

### ❌ NOT Available
- Docker, Java, Ruby, Go

The tool **automatically handles** these constraints.

## Examples

### Example 1: Compress PDF

```bash
python scripts/create_skill.py "I need to compress PDF files"
```

**Process:**
1. Finds `pdf` skill (best match)
2. Clones it
3. Adds `compress` function
4. No compatibility issues
5. Creates `compress-pdf.skill`

**Time:** ~2 minutes

### Example 2: Extract Video Frames

```bash
python scripts/create_skill.py "Extract frames from videos every second"
```

**Process:**
1. Finds `video-frames` skill
2. Clones it
3. Adds "every second" parameter
4. Verifies ffmpeg available (✅ yes)
5. Creates `video-frames-extract.skill`

### Example 3: Image Enhancement

```bash
python scripts/create_skill.py "Enhance image quality for screenshots"
```

**Process:**
1. Finds `image-enhancer` skill (perfect match!)
2. Already exists, recommends direct installation
3. No need to create new skill

## Tools

### scripts/create_skill.py
Main entry point - orchestrates entire workflow

### scripts/semantic_search.py
LLM-powered search for similar skills

### scripts/find_skills_integration.py
Checks if perfect match already installed

### scripts/clone_skill.py
Clones skill from anthropics/skills repo

### scripts/integrate_feature.py
Adds new features with LLM fine-tuning

### scripts/check_compatibility.py
Scans for HappyCapy compatibility issues

### scripts/auto_fix.py
Automatically fixes compatibility problems

### scripts/test_skill.py
Basic validation

### scripts/package_skill.py
Creates distributable .skill file

## Requirements

- Python 3.11+
- Environment variable: `ANTHROPIC_API_KEY` or `AI_GATEWAY_API_KEY`
- Internet connection (to clone from GitHub)

## Advanced Usage

### Skip Find-Skills Check

If you know no existing skill matches:

```bash
# (Edit create_skill.py to skip Step 1)
```

### Custom Workspace

Skills are created in `./workspace/` by default.

### Manual Review

Before packaging, review:
- `workspace/<skill-name>/SKILL.md` - Documentation
- `workspace/<skill-name>/scripts/` - Code

## Troubleshooting

### "No similar skills found"

→ Try different wording or create from scratch manually

### "API key not found"

→ Set `ANTHROPIC_API_KEY` or `AI_GATEWAY_API_KEY`

### "Clone failed"

→ Check internet connection
→ Fallback: template skill created

### "Tests failed"

→ Review workspace files
→ Check for syntax errors

## Limitations

1. **Requires similar base skill**
   - Works best when similar skill exists
   - Novel requirements may need manual creation

2. **LLM-dependent**
   - Needs API key for best results
   - Fallback to templates without API

3. **Basic testing only**
   - Validates structure and syntax
   - Manual testing recommended

## Best Practices

1. **Be specific** in requirements
   - ✅ "Compress PDF files to reduce size"
   - ❌ "Do something with PDFs"

2. **Check existing skills first**
   - Use /find-skills before creating
   - May already exist!

3. **Review before use**
   - Check generated code
   - Test with your data

4. **Iterate if needed**
   - First version may need tweaks
   - Re-run with refined requirement

## Philosophy

**Adaptation > Creation**

- Leverage anthropics/skills (community-validated)
- Preserve proven functionality
- Add only what's needed
- Auto-fix environment issues

**Result:** High-quality skills in minutes, not hours.

## See Also

- `references/happycapy-environment.md` - Environment details
- `examples/` - Example workflows
