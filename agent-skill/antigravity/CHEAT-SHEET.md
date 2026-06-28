# Cheat Sheet – Dùng Agent Skills trên Antigravity

## Setup (làm 1 lần)

1. Tạo Agent mới trên Antigravity
2. Load tất cả skill files vào Knowledge Base của agent:
   - `SKILL-00-audit-logger.md` → **System Prompt** (luôn active)
   - `SKILL-01` đến `SKILL-05` → Knowledge / Skills

3. System prompt gợi ý cho agent:

```
You are a software testing expert helping a student complete HW02 – Domain Testing on EShop.

You have 5 skills (SKILL-01 to SKILL-05) that form a pipeline.
You also run SKILL-00 (audit logging) automatically after every response.

When the user says "SKILL-0X [optional info]", execute that skill.
Always use outputs from previous skills in this conversation — never ask the user to paste them again.
After each skill, always show the review checklist and the next step prompt.
```

---

## Lệnh nhanh – chạy theo thứ tự này

```
# ── FEATURE FR-02 ──────────────────────────────

SKILL-01 FR-02: Login & Account Lockout

# [review output, sửa nếu cần]

SKILL-02

# [review EP classes]

SKILL-03

# [verify ⚠️ unknowns trên app thực tế trước bước này]

SKILL-04

# [review TCs, tạo file .md, commit lên GitHub]

SKILL-05

# [review gaps, tạo TC bổ sung, commit]

export audit log

# [copy vào ai-audit-report.md, điền User corrections]


# ── FEATURE FR-09 ──────────────────────────────
# Bắt đầu session mới hoặc nói "new feature" để reset context

SKILL-01 FR-09: Discount Coupons
...


# ── FEATURE FR-14 ──────────────────────────────

SKILL-01 FR-14: Category Management CRUD
...


# ── FEATURE FR-06 MOBILE ───────────────────────

SKILL-01 FR-06 Mobile: Product Detail View
...
```

---

## Việc phải tự làm

| Bước             | Việc                                                         | Lúc nào       |
| ---------------- | ------------------------------------------------------------ | ------------- |
| Verify unknowns  | Mở app, test thực tế để tìm MAX length, lockout threshold... | Sau SKILL-03  |
| Review TC        | Đọc từng TC, sửa expected result sai                         | Sau SKILL-04  |
| Tạo file .md     | Copy output → tạo file trong repo                            | Sau SKILL-04  |
| Git commit       | `git add` + `git commit` + `git push`                        | Sau mỗi skill |
| Execute TC       | Chạy tay từng TC trên app EShop                              | Sau SKILL-04  |
| Chụp screenshot  | Screenshot bug, đính vào GitHub Issue                        | Khi TC fail   |
| Tạo GitHub Issue | Điền bug report, gắn label                                   | Khi TC fail   |
| Điền audit log   | Thêm "User corrections" vào mỗi entry                        | Sau mỗi skill |
| Viết AI Critique | Dùng SKILL-05 output làm nháp, viết lại bằng lời mình        | Cuối bài      |

---

## Git commit message chuẩn

```bash
# Sau SKILL-01+02+03
git commit -m "analysis(fr02): variable analysis, EP and BVA planning"

# Sau SKILL-04
git commit -m "feat(fr02): add 23 test cases – domain testing and BVA"

# Sau execute TCs
git commit -m "test(fr02): sprint 1 execution – 18 pass, 3 fail, 2 blocked"

# Sau bug reports
git commit -m "bug(fr02): update test run with bug issue references"

# Sau SKILL-05
git commit -m "feat(fr02): add 4 gap analysis test cases (security + context)"
```

---

## Lệnh đặc biệt

| Lệnh               | Tác dụng                                       |
| ------------------ | ---------------------------------------------- |
| `export audit log` | Agent xuất toàn bộ audit entries của session   |
| `new feature`      | Reset context sang feature mới (giữ audit log) |
| `summary so far`   | Agent tóm tắt TCs đã tạo + trạng thái          |
| `what's missing`   | Agent kiểm tra checklist còn thiếu gì          |
