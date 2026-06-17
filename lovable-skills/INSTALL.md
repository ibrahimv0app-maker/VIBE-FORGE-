# Installation Guide

## Method 1: Upload ZIP (Recommended)

### For Lovable.dev
1. Download this ZIP file
2. Open [Lovable.dev](https://lovable.dev) and log in
3. Navigate to **Settings → Skills**
4. Click **Add → Upload ZIP**
5. Drag the ZIP file in (or browse)
6. Wait for validation
7. Skills are now available across your workspace

### For Anthropic Claude (Claude Code / Claude Desktop)
1. Download this ZIP file
2. Extract it
3. For each skill you want to use:
   - Zip just that skill's folder (must contain SKILL.md at root)
   - Upload via Claude's skill upload interface
4. Or copy skill folders to `~/.claude/skills/`

### For other Agent Skills-compatible tools
Any tool that supports the [Agent Skills convention](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills)
can use these skills. Consult your tool's documentation.

## Method 2: Import from GitHub

1. Push this collection to a public GitHub repo
2. In Lovable.dev → Settings → Skills → Add → Import from GitHub
3. Paste the repo URL: `https://github.com/YOUR_USERNAME/lovable-skills`
4. Lovable will fetch and validate

For a single skill from a monorepo:
- Use the subdirectory URL format: `https://github.com/YOUR_USERNAME/lovable-skills/tree/main/skills/ai-image-generation/ultra-consistent-character-generator`

## Method 3: Install Selectively

If you don't want all 1000+ skills, extract the ZIP and:
1. Browse the `skills/` directory
2. Pick the categories and skills you want
3. Create a new ZIP with just those skills
4. Upload to Lovable.dev

## Verifying Installation

After installing:
1. In a Lovable.dev chat, type `/`
2. The slash menu should show your installed skills
3. Each skill has a description shown on hover

## Using Skills

### Automatic Use
Just describe your task. Lovable will load the matching skill automatically:
> "Generate a hero image for my landing page, I want it to match my brand colors"
(Lovable will likely load `reference-image-director` and `style-preset-library`)

### Direct Invocation
Type the skill name with a slash:
> `/ultra-consistent-character-generator Create a character named Aria, a 25-year-old cartographer with red hair, and put her in three scenes: a library, a mountain, and a ship`

### Combining Skills
You can invoke multiple skills:
> `/character-sheet-creator` then later `/ultra-consistent-character-generator`

## Managing Skills

### Enable / Disable Automatic Use
In Settings → Skills, toggle "Automatic use" per skill.
- Enabled (default): Lovable loads it when relevant
- Disabled: Only loads when you type `/skill-name` manually

### Edit a Skill
In Settings → Skills, click a skill to edit its description or instructions.

### Delete a Skill
In Settings → Skills, click a skill → Delete.

## Troubleshooting

### Skill doesn't load automatically
- Check the description is specific enough
- Disable similar skills that might conflict
- Try invoking manually with `/skill-name`

### Upload fails
- ZIP must be < 50MB
- Each bundled file must be < 1MB
- SKILL.md must exist at root or inside one wrapping folder
- Remove `__MACOSX/` and `.DS_Store` files

### Skill is too aggressive (loads when not wanted)
- Make the description more specific
- Add explicit boundaries ("Not for X")
- Disable automatic use; invoke manually

## Best Practices

1. **Install selectively**: 1000+ skills is a lot. Pick the categories relevant to your work.
2. **Customize**: Edit descriptions to match your team's vocabulary.
3. **Composability**: Build workflows that chain skills (e.g., character-sheet → character-generator).
4. **Review periodically**: As Lovable improves built-in skills, some custom ones may become redundant.
5. **Share with your team**: Workspace skills are shared — use this to enforce team conventions.
