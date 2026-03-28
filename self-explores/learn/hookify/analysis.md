# hookify

## Đánh giá (Score: 9/10)

**Lý do:** Giải quyết một pain point rất thực tế: users muốn tạo hooks nhưng không muốn edit JSON files. Markdown-based rule format + conversation analysis = accessible automation for non-technical users.

---

## Ưu & Nhược điểm

### Ưu điểm
- **No JSON editing:** Hooks lưu trong `.claude/hookify.{name}.local.md` — human-readable
- **Conversation analysis:** `/hookify` phân tích conversation để tự tạo rules — smart
- **4 commands:** `/hookify`, `/hookify:list`, `/hookify:configure`, `/hookify:help` — full lifecycle
- **Multiple event types:** bash, file, stop, prompt, all — comprehensive coverage
- **Conditional operators:** regex_match, contains, equals, not_contains, starts_with, ends_with — flexible
- **Enable/disable toggle:** Non-destructive — có thể disable mà không xóa rule
- **conversation-analyzer agent:** Specialized agent tìm problematic behaviors trong conversation history
- **4 example rules:** Documented patterns (rm -rf block, console.log warn, test requirement, sensitive files)

### Nhược điểm
- **Regex complexity:** Users có thể gặp khó khăn với regex patterns
- **No rule testing built-in:** Không có preview mode để test rule trước khi activate
- **Python scripts:** 4 hook scripts dùng Python — requires Python runtime
- **10-second timeout:** Hook scripts có hard timeout — long operations sẽ fail
- **Local-only:** Không sync rules qua projects

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với OMC/viec
- **High value:** Tạo hooks để enforce `/viec` conventions
- Example hooks cho viec workflow:
  - Block git push mà không có `/viec xong` trước
  - Warn khi không có worklog file
  - Auto-capture khi session stop

### Với project workflows
- Security: Block nguy hiểm operations (rm -rf, DROP TABLE, etc.)
- Quality: Enforce test writing trước khi commit
- Context: Auto-load project context khi mở session

### Integration steps
1. Install: copy `plugins/hookify/` vào `~/.claude/plugins/`
2. Tạo rule từ conversation: `/hookify`
3. View rules: `/hookify:list`
4. Toggle: `/hookify:configure`

---

## Ghi chú kỹ thuật (Technical Decisions)

### Rule File Format (Basic)
```markdown
# File: .claude/hookify.rule-name.local.md
---
name: rule-name
enabled: true
event: bash           # bash|file|stop|prompt|all
pattern: "rm -rf"     # regex hoặc string
action: block         # block|warn
---

# Rule Name
Explanation message shown when rule triggers.
```

### Rule File Format (Advanced — với conditions)
```markdown
---
name: sensitive-files
enabled: true
event: file
conditions:
  operator: or
  rules:
    - type: regex_match
      value: "\.env$"
    - type: regex_match
      value: "credentials"
    - type: contains
      value: "secrets"
action: warn
---

# Sensitive Files Warning
Attempting to modify a sensitive file. Make sure this is intentional!
```

### Condition Operators
```
regex_match   — Full regex support
contains      — Substring check
equals        — Exact match
not_contains  — Negative substring
starts_with   — Prefix check
ends_with     — Suffix check
```

### Python Hook Architecture
```
hooks/
├── hooks.json          # Event → script mappings
├── pre_tool_use.py     # Handles PreToolUse events
├── post_tool_use.py    # Handles PostToolUse events
├── stop.py             # Handles Stop events
└── user_prompt.py      # Handles UserPromptSubmit events
```

### 4 Example Rules (Templates để học)

**1. Block dangerous rm:**
```yaml
event: bash
pattern: "rm\\s+-rf\\s+[/~]"
action: block
```

**2. Warn console.log:**
```yaml
event: file
conditions:
  operator: and
  rules:
    - type: regex_match
      value: "\\.(js|ts|jsx|tsx)$"
    - type: contains
      value: "console.log"
action: warn
```

**3. Require tests before stop:**
```yaml
event: stop
conditions:
  - type: not_contains
    value: "npm test|jest|pytest"
action: block
message: "Please run tests before finishing!"
```

**4. Sensitive files:**
```yaml
event: file
conditions:
  operator: or
  rules:
    - {type: regex_match, value: "\\.env$"}
    - {type: contains, value: "credentials"}
action: warn
```

### Conversation Analyzer Agent
```
5-step analysis:
1. Search for repeated user corrections
2. Identify problematic Claude behaviors
3. Create regex patterns for each
4. Categorize by severity
5. Output structured findings for rule creation
```

### Teachable Patterns
1. **Markdown-based config** thay vì JSON — user-friendly
2. **Conversation analysis** → automated rule suggestions
3. **Enable/disable** non-destructive toggles
4. **Conditional rule expressions** với multiple operators
5. **Event-driven hook architecture**
