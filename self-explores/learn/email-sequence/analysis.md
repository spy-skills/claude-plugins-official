# email-sequence

**Nguồn:** 18_marketingskills (Corey Haines — Conversion Factory)
**File:** `/home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/email-sequence/SKILL.md`

## Đánh giá (Score: 8/10)

**Lý do:** Practical framework với timing guidelines, length guides, và tool integrations cụ thể. Đặc biệt strong ở sequence types và per-email template.

---

## Ưu & Nhược điểm

### Ưu điểm
- **Sequence length guidelines:** 3-10 emails tùy type — cụ thể, không generic
- **Timing/delay specs:** Không chỉ "send after X days" mà có rationale
- **4 sequence types:** Welcome, lead nurture, re-engagement, onboarding — cover main use cases
- **Per-email template:** timing, subject, preview, body, CTA, conditions — deliverable-ready
- **Subject line patterns:** Specific formulas, not just tips
- **Tool integrations:** Customer.io, Mailchimp, Resend, SendGrid, Kit — với links
- **Email types by category:** Onboarding, retention, billing, usage, win-back, campaign — comprehensive
- **4 core principles:** One job per email, value before ask, relevance over volume, clear path forward

### Nhược điểm
- **Không có A/B test guidance trong emails:** Phụ thuộc ab-test-setup skill
- **Preview text khá brief:** Section này có thể expand hơn
- **Tool integrations generic:** Chỉ link, không có integration tips
- **Không cover transactional emails:** Focus on marketing sequences

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với viec/OMC
- Task: "Thiết kế email sequence cho [use case]" → trigger email-sequence
- Output template → lưu vào project context
- Tạo sub-tasks cho từng email trong sequence

### Với marketing workflows
- Input: content-strategy + copywriting (content plan + copy guidelines)
- Output feeds: ab-test-setup (test subject lines)

### Installation
```bash
cp -r /home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/email-sequence/ ~/.claude/skills/
```

---

## Ghi chú kỹ thuật (Technical Decisions)

### 4 Core Principles
```
1. One email one job   → Don't mix messages/CTAs
2. Value before ask    → Give first, then ask
3. Relevance over volume → Better to send fewer, more relevant
4. Clear path forward  → Always next step is obvious
```

### Sequence Types & Structure
```
Welcome Sequence:        3-5 emails, immediate → day 7
Lead Nurture:            5-10 emails, week 1 → week 8
Re-engagement:           3-5 emails, 60/90/180 day inactive
Onboarding:              5-7 emails, day 0 → day 30
```

### Subject Line Patterns
```
Question:    "Are you making this mistake?"
Number:      "5 ways to improve your X"
Curiosity:   "The thing nobody tells you about..."
Urgency:     "Last chance: [specific benefit]"
Personal:    "Hey [first name], quick question"
Direct:      "[Specific value/benefit]"
```

### Per-Email Template
```markdown
## Email [N]: [Purpose]
- **Timing:** Day X after trigger
- **Subject:** Primary subject line
- **Preview text:** 40-90 chars preview
- **Body:**
  Hook (1-2 sentences)
  Context (why relevant now)
  Value (main content/insight)
  CTA (single, specific action)
  Sign-off (personal, human)
- **Primary CTA:** [Action] → [URL/destination]
- **Conditions:** [When to send / When to skip]
```

### Email Length Guidelines
```
Transactional/Trigger:  100-200 words
Welcome:                200-400 words
Nurture:                300-500 words
Newsletter:             400-800 words
Long-form educational:  800+ words (rare, must earn it)
```

### CTA Best Practices
```
□ One CTA per email (occasionally two if hierarchy is clear)
□ Button text = specific action, not generic "click here"
□ Link placement: early + button at end
□ Mobile-friendly button size (min 44x44px)
```

### Email Types by Category
```
Onboarding:  welcome, setup nudge, first win, check-in, power user
Retention:   feature adoption, milestone celebration, usage summary
Billing:     trial ending, upgrade nudge, payment failure, renewal
Usage:       inactive, re-engagement, win-back
Campaign:    announcement, launch, promotion, event
```

### Teachable Patterns
1. **One job per email** principle
2. **Value-before-ask** sequencing
3. **Sequence type specifications** (length + timing)
4. **Per-email template** format
5. **Subject line pattern library**
