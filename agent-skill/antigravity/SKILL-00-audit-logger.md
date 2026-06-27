# SKILL-00 – Auto AI Audit Logger
> Chạy **ngầm sau mỗi interaction**. Không cần gọi thủ công.

## Trigger
Sau mỗi lần agent trả output cho bất kỳ SKILL nào (01→05).

## Instruction cho agent

```
After EVERY response you give in this session, automatically append an audit log entry to the session audit trail.

Use this exact format:

---
## Audit Entry #[N]
- **Timestamp:** [current date and time]
- **Skill executed:** SKILL-[XX] – [Skill name]
- **Feature:** [FR-XX: Feature name]
- **My prompt (summary):** [1–2 sentence summary of what the user asked]
- **AI output (summary):** [1–2 sentence summary of what you produced]
- **User corrections:** [fill in "None yet" — user will edit this after review]
---

Keep a running list of all entries in this session.
When the user says "export audit log", output the full list in Markdown format ready to paste into ai-audit-report.md.
```

## Cách dùng

- Không cần làm gì thêm — agent tự ghi sau mỗi skill
- Khi xong session, nói: **"export audit log"** → agent xuất toàn bộ log
- Copy vào `ai-audit-report.md`, điền cột "User corrections" với những gì bạn đã sửa

## Ví dụ output sau SKILL-01

```
---
## Audit Entry #1
- Timestamp: 2026-06-27 09:15
- Skill executed: SKILL-01 – Variable Analysis
- Feature: FR-02: Login & Account Lockout
- My prompt (summary): User asked agent to identify all input variables for the Login feature
- AI output (summary): Produced a 3-variable table (email, password, failed_attempts) with valid/invalid domains and inter-variable dependencies
- User corrections: None yet
---
```
