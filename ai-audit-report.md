# AI Audit Report – HW02 Domain Testing

## Declaration

I use AI tools for the following tasks in this assignment.

---

## AI Interaction Log

### Interaction 1

| Field | Value |
|-------|-------|
| AI Tool | Gemini (Antigravity IDE) |
| Date & Time | 2026-06-27 23:18 |
| Skill Step Used | SKILL-01 – Variable Analysis |
| Feature | FR-02: Login & Account Lockout |
| My Prompt | `SKILL-01 FR-02: Login & Account Lockout [accompanied by observations on UI and lockout behavior]` |
| AI Output Summary | Identified 4 variables (email, password, login_attempts, locked_until) with data types, domains, constraints, and inter-variable dependencies. |
| Corrections Made | None yet |

---

### Interaction 2

| Field | Value |
|-------|-------|
| AI Tool | Gemini (Antigravity IDE) |
| Date & Time | 2026-06-27 23:23 |
| Skill Step Used | SKILL-02 – Equivalence Partitioning |
| Feature | FR-02: Login & Account Lockout |
| My Prompt | `SKILL-02` |
| AI Output Summary | Formulated 13 equivalence classes (valid/invalid) for the identified variables and defined 5 combination scenarios. |
| Corrections Made | None yet |

---

### Interaction 3

| Field | Value |
|-------|-------|
| AI Tool | Gemini (Antigravity IDE) |
| Date & Time | 2026-06-27 23:26 |
| Skill Step Used | SKILL-03 – Boundary Value Analysis |
| Feature | FR-02: Login & Account Lockout |
| My Prompt | `SKILL-03` |
| AI Output Summary | Analyzed boundary points for password length (7, 8, 9, 12, 254, 255, 256 chars) and login attempts (0, 1, 2, 3), identifying 2 skipped variables and 2 unknowns. |
| Corrections Made | None yet |

---

### Interaction 4

| Field | Value |
|-------|-------|
| AI Tool | Gemini (Antigravity IDE) |
| Date & Time | 2026-06-27 23:30 |
| Skill Step Used | SKILL-04 – Test Case Writer |
| Feature | FR-02: Login & Account Lockout |
| My Prompt | `SKILL-04` |
| AI Output Summary | Generated 21 test case files (10 EP-based, 11 BVA-based) in Markdown format matching the required template. |
| Corrections Made | Updated placeholder email and password to use the SUT default credentials (`test@eshop.com` / `Test1234!`) to make them executable on EShop. |

---

### Interaction 5

| Field | Value |
|-------|-------|
| AI Tool | Gemini (Antigravity IDE) |
| Date & Time | 2026-06-28 00:42 |
| Skill Step Used | SKILL-05 – Gap Analysis |
| Feature | FR-02: Login & Account Lockout |
| My Prompt | `SKILL-05` |
| AI Output Summary | Identified 4 critical testing gaps (XSS, JWT, lockout recovery, and state transitions) and wrote a critical reflection. |
| Corrections Made | None yet |

---

## AI Critique (200–300 words)

Trong quá trình thiết kế test case cho tính năng Đăng nhập và Khóa tài khoản (FR-02), tôi nhận thấy AI đã bỏ sót một số kịch bản kiểm thử tích hợp quan trọng:
1. **Thiếu kịch bản reset bộ đếm khi đăng nhập thành công:** AI tập trung vào việc đếm lỗi để khóa tài khoản nhưng quên kiểm tra xem đăng nhập đúng có khôi phục `login_attempts` về 0 hay không.
2. **Thiếu kịch bản vô hiệu hóa JWT token khi tài khoản bị khóa:** AI bỏ qua mối liên hệ giữa trạng thái tài khoản bị khóa trên database với các phiên hoạt động hiện hành được xác thực tĩnh qua JWT token.

Nguyên nhân là do AI có xu hướng phân tích độc lập từng biến số đầu vào qua kỹ thuật phân hoạch tương đương và phân tích giá trị biên truyền thống, thay vì mô hình hóa hệ thống dựa trên sơ đồ chuyển trạng thái hoặc kiến trúc bảo mật của ứng dụng.

Bài học thực tế là AI rất tốt trong việc sinh nhanh các bộ test case theo biên số lượng và các trường dữ liệu tĩnh, nhưng kiểm thử viên con người bắt buộc phải trực tiếp rà soát và bổ sung các kịch bản liên quan đến bảo mật phiên, phân quyền vai trò và luồng logic chuyển đổi trạng thái của toàn hệ thống.

---

## Tools Used

- Gemini (Antigravity IDE)
