# copywriting

**Nguồn:** 18_marketingskills (Corey Haines — Conversion Factory)
**File:** `/home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/copywriting/SKILL.md`

## Đánh giá (Score: 8/10)

**Lý do:** Practical, actionable copywriting framework với page-specific guidance. CTA formula và page structure template là các patterns có thể áp dụng ngay.

---

## Ưu & Nhược điểm

### Ưu điểm
- **CTA formula:** `[Action Verb] + [What They Get] + [Qualifier]` — simple và effective
- **Page structure framework:** Above-the-fold + 8 core sections — complete landing page blueprint
- **Page-specific guidance:** Homepage, landing page, pricing page, feature page, about page — không generic
- **Quality check items:** Jargon, sentence complexity, passive voice, buzzwords — actionable checklist
- **Weak vs strong CTA examples:** Concrete comparison giúp hiểu ngay
- **5 copywriting principles:** Clarity over cleverness, benefits over features, specificity, customer language, one idea per section
- **Output format có annotations:** Giải thích tại sao chọn từng phrase — educational value
- **Related skills ecosystem:** copy-editing, page-cro, email-sequence, popup-cro, ab-test-setup

### Nhược điểm
- **Thiếu tone voice guidance chi tiết:** "Establish formality level" còn generic
- **Không có industry-specific examples:** Một framework fit-all, thiếu SaaS vs e-commerce nuance
- **Không đề cập A/B testing trong copy:** Không kết nối rõ với ab-test-setup skill
- **Missing psychological triggers:** Không có section về FOMO, social proof specifics, anchoring

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với OMC/viec
- Task type mới: "Viết copy cho trang X" → trigger copywriting skill
- Output annotations → có thể lưu vào self-explores/decisions/ (why we chose this wording)

### Với marketing workflows
- Input: content-strategy (biết what to write about)
- Output feeds: ab-test-setup (test variations), email-sequence (repurpose copy)

### Installation
```bash
cp -r /home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/copywriting/ ~/.claude/skills/
```

---

## Ghi chú kỹ thuật (Technical Decisions)

### 5 Core Copywriting Principles
```
1. Clarity over cleverness     → Reader understands first time
2. Benefits over features      → "What's in it for me?"
3. Specificity                 → Numbers and examples > generalities
4. Customer language           → Their words, not your jargon
5. One idea per section        → No cognitive overload
```

### Page Structure Framework
```
ABOVE THE FOLD:
├── Headline (biggest promise / transformation)
├── Subheadline (clarify + expand)
└── Primary CTA

CORE SECTIONS:
├── Social proof (trust)
├── Problem (pain point)
├── Solution (how you solve it)
├── How it works (mechanics)
├── Objection handling (preempt doubts)
└── Final CTA
```

### CTA Formula
```
[Action Verb] + [What They Get] + [Qualifier if needed]

Weak:  "Submit", "Click here", "Learn more"
Strong:
  "Start your free trial" (action + what + qualifier)
  "Get the template" (action + specific thing)
  "See how it works" (action + curiosity hook)
```

### Writing Style Rules
```
Simple     → Short sentences, common words
Specific   → "$X saved" not "save money"
Active     → "We do X" not "X is done by us"
Confident  → No "might", "could", "perhaps"
Results    → Show outcomes, not just process
Honest     → No exaggeration, no empty promises
```

### Quality Check (Pre-publish)
```
□ Any jargon the audience wouldn't use?
□ Any sentence over 20 words?
□ Any passive voice?
□ Any buzzwords (innovative, revolutionary, synergy)?
□ Does each section have one clear idea?
□ Is the CTA specific about what happens next?
```

### Page-Specific Notes
```
Homepage:   30-sec clarity test — can visitor understand offer?
Landing:    Match headline to ad copy exactly
Pricing:    Feature copy = what it does, benefit copy = why you want it
Feature:    Lead with problem solved, not feature name
About:      Company story → customer benefit angle
```

### Teachable Patterns
1. **CTA formula** — Action + What + Qualifier
2. **Above-the-fold priority** — 3 elements only
3. **One idea per section** principle
4. **Benefits-first** structure
5. **Annotation output** — explain reasoning
