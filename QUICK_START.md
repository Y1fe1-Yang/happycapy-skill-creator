# Quick Start Guide

## 1-Minute Setup

```bash
# Install dependencies
pip install -r requirements.txt

# Set API key (HappyCapy environment has this pre-configured)
export AI_GATEWAY_API_KEY=your-key-here

# You're ready!
```

## 1-Command Usage

```bash
# Interactive mode
python scripts/create_skill.py "your requirement"

# Non-interactive mode (for CI/CD)
python scripts/create_skill.py "your requirement" --name skill-name
```

## Examples

### Example 1: PDF Compression
```bash
python scripts/create_skill.py "I need to compress PDF files"
```

**Output**: `compress-pdf.skill` in 3 minutes

### Example 2: Image Enhancement
```bash
python scripts/create_skill.py "Enhance image quality"
```

**Output**: May suggest existing `image-enhancer` skill

### Example 3: Video Frames
```bash
python scripts/create_skill.py "Extract video frames every second"
```

**Output**: `video-frames-extract.skill`

## What Happens?

```
Your Input
    ↓
[1] Search similar skills (5 sec)
    ↓
[2] Clone best match (10 sec)
    ↓
[3] Add your features (15 sec)
    ↓
[4] Fix compatibility (2 sec)
    ↓
[5] Test (1 sec)
    ↓
[6] Package (2 sec)
    ↓
Done! Install with /install output.skill
```

## Tips

### Be Specific
- ✅ "Compress PDF files to reduce size"
- ❌ "Do something with files"

### Check First
Before creating, try:
```bash
/find-skills "your need"
```

May already exist!

### Review Generated Code
```bash
cd workspace/<skill-name>
cat SKILL.md
ls scripts/
```

## Troubleshooting

### "No API key"
```bash
export AI_GATEWAY_API_KEY=your-key
```
Note: HappyCapy environment has this pre-configured

### "No similar skill"
Try different wording or broader description

### "Clone failed"
- Check internet
- Tool will create template fallback

## Next Steps

1. Install skill: `/install outputs/<skill-name>.skill`
2. Try it: Ask Claude to use the skill
3. Iterate if needed: Run again with refined requirement

## Full Documentation

- `README.md` - Complete guide
- `SKILL.md` - Full methodology  
- `examples/example-workflow.md` - Detailed walkthrough
