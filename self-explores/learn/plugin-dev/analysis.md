# plugin-dev

## Đánh giá (Score: 10/10)

**Lý do:** Meta-skill quan trọng nhất trong repo — dạy cách xây dựng tất cả skill types khác. 7 skills + 8-phase workflow + 3 specialized agents = comprehensive plugin development system.

---

## Ưu & Nhược điểm

### Ưu điểm
- **7 skills bao quát toàn bộ:** hook-development, mcp-integration, plugin-structure, plugin-settings, command-development, agent-development, skill-development
- **8-phase guided workflow** (`/plugin-dev:create-plugin`): Discovery → Planning → Design → Structure → Implementation → Validation → Testing → Documentation
- **3 specialized agents:** agent-creator, plugin-validator, skill-reviewer
- **Progressive disclosure pattern:** README → SKILL.md → References → Examples → Scripts
- **${CLAUDE_PLUGIN_ROOT} portability:** Environment variable cho tất cả paths, không hardcode
- **Configuration pattern:** `.claude/plugin-name.local.md` với YAML frontmatter — user-friendly
- **10 proven hook patterns:** Documented in patterns.md reference
- **Security-first:** Input validation, path safety, sensitive data protection

### Nhược điểm
- **Rất verbose:** ~100,000+ words across 40+ files — steep learning curve
- **Meta-complexity:** Phải hiểu toàn bộ ecosystem trước khi dùng hiệu quả
- **Skills tự-reference nhau:** hook-development references patterns.md → không standalone
- **Create-plugin command khá cứng nhắc:** 8 phases sequential, không flex

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với OMC
- **Trực tiếp:** Dùng `plugin-dev:create-plugin` để tạo OMC skills/commands mới
- skill-reviewer agent → quality gate cho skills tạo bởi `/viec`
- agent-creator → template cho OMC executor agents

### Với /viec skills
- `skill-creator` trong repo dùng logic tương tự nhưng lighter
- **`plugin-dev` là academic version, `skill-creator` là practical version**
- Học plugin-dev → hiểu depth, dùng skill-creator → daily use

### Integration steps
1. Install: copy `plugins/plugin-dev/` vào `~/.claude/plugins/`
2. Bắt đầu: `/plugin-dev:create-plugin`
3. Follow 8-phase guided workflow

---

## Ghi chú kỹ thuật (Technical Decisions)

### SKILL.md Structure (from skill-development skill)
```markdown
---
name: skill-name
description: Trigger conditions + what it does (third-person)
version: 1.0.0
---

# Skill Name
[Core content]
[Progressive disclosure: bundled references in ]]
```

### Progressive Disclosure Pattern
```
Level 1 (SKILL.md):    Core instructions + trigger conditions
Level 2 (README.md):   User documentation + examples
Level 3 (references/): Deep dives for specific topics
Level 4 (scripts/):    Automation and tooling
```

### ${CLAUDE_PLUGIN_ROOT} Pattern
```bash
# ALWAYS use this, never hardcode paths
${CLAUDE_PLUGIN_ROOT}/skills/my-skill/SKILL.md
${CLAUDE_PLUGIN_ROOT}/references/my-reference.md
```

### Hook Types: Prompt vs Command
```
Prompt-based:  RECOMMENDED — LLM reasoning, flexible
  Trigger: "When user does X, do Y via prompt"

Command-based: Deterministic — bash script execution
  Use for: file operations, git commands, system checks
```

### 9 Hook Events
```
PreToolUse     — Before any tool execution
PostToolUse    — After any tool execution
PreBash        — Before bash commands
PostBash       — After bash commands
PreFileEdit    — Before file modifications
PostFileEdit   — After file modifications
Stop           — When Claude completes response
UserPromptSubmit — When user submits prompt
SessionStart   — When session begins
```

### Plugin Settings Pattern
```markdown
# File: .claude/plugin-name.local.md
---
enabled: true
threshold: 80
custom_option: value
---

# Plugin Name Settings

Additional markdown content with user preferences...
```

### 10 Proven Hook Patterns
1. Security validation (blocks dangerous operations)
2. Test enforcement (requires tests before stop)
3. Context loading (auto-loads relevant context)
4. Notification logging (tracks events)
5. MCP monitoring (monitors external services)
6. Build verification (checks build passes)
7. Permission confirmation (confirms destructive ops)
8. Code quality (enforces style guidelines)
9. Temporarily active hooks (session-scoped rules)
10. Configuration-driven (reads from .local.md)

### Agent Creator 6-Step Process
```
1. Intent       — Understand what the agent should accomplish
2. Persona      — Define agent's role and expertise
3. Instructions — Write precise, unambiguous steps
4. Optimize     — Remove redundancy, sharpen clarity
5. Identifier   — Create trigger phrases
6. Examples     — Provide concrete usage examples
```

### Teachable Patterns
1. **Progressive disclosure** trong skill design
2. **${CLAUDE_PLUGIN_ROOT}** portability pattern
3. **Prompt vs command hooks** decision framework
4. **Configuration via .local.md** pattern
5. **plugin-validator** for quality gates
6. **8-phase plugin creation** workflow
