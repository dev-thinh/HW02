# HW02 – Domain Testing on EShop

## Self-Assessment Table

| No. | Criteria                                                        | Grade   | Self-Assessed Grade |
| --- | --------------------------------------------------------------- | ------- | ------------------- |
| 1   | Feature A – FR-02: Login & Account Lockout (Domain + Boundary)  | 25      | 25                  |
| 2   | Feature B – FR-09: Discount Coupons (Domain + Boundary)         | 25      | 25                  |
| 3   | Feature C – FR-14: Category Management CRUD (Domain + Boundary) | 25      | 25                  |
| 4   | Feature D – Mobile: Product Detail View (Domain + Boundary)     | 15      | 15                  |
| 5   | Agent Skills                                                    | 10      | 10                  |
|     | **Total**                                                       | **100** | **100**             |

---

## Test Summary Report

| Metric                      | Count |
| --------------------------- | ----- |
| Features tested             | 4     |
| Test cases designed         | 82    |
| Test cases executed         | 82    |
| Test cases passed           | 61    |
| Test cases failed           | 21    |
| Test cases not yet executed | 0     |
| Bugs discovered             | 14    |

### Demo Videos & Walkthroughs

- Agent Skill Demo: _(Không yêu cầu trong bài nộp)_
- Feature FR-02 walkthrough: [Xem chi tiết tại main-report-template.md](main-report-template.md#feature-a)
- Feature FR-09 walkthrough: [Xem chi tiết tại main-report-template.md](main-report-template.md#feature-b)
- Feature FR-14 walkthrough: [Xem chi tiết tại main-report-template.md](main-report-template.md#feature-c)
- Feature Mobile walkthrough: [Xem chi tiết tại main-report-template.md](main-report-template.md#feature-d)

---

## Repository Structure

```
hw02-eshop/
├── README.md
├── main-report-template.md
├── agent-skill/
│   └── antigravity/
│       ├── CHEAT-SHEET.md
│       ├── SKILL-00-audit-logger.md
│       ├── SKILL-01-variable-analysis.md
│       ├── SKILL-02-domain-ep.md
│       ├── SKILL-03-bva.md
│       ├── SKILL-04-testcase-writer.md
│       └── SKILL-05-gap-analysis.md
└── tests/
    ├── test-cases/
    │   ├── fr02-login/
    │   │   ├── TC-LOGIN-001.md
    │   │   └── TC-LOGIN-BVA-001.md
    │   ├── fr09-coupons/
    │   │   ├── TC-COUPON-001.md
    │   │   └── TC-COUPON-BVA-001.md
    │   ├── fr14-category/
    │   │   ├── TC-CAT-001.md
    │   │   ├── TC-CAT-BVA-001.md
    │   │   └── TC-CAT-SEC-001.md
    │   └── fr-mobile-product/
    │       ├── TC-MPROD-001.md
    │       └── TC-MPROD-BVA-001.md
    ├── test-runs/
    │   └── sprint-1-test-run.md
    └── test-summary/
        └── traceability-matrix.md
```

---

## AI Declaration

Tôi sử dụng trợ lý AI Gemini (Antigravity Agent) để thực hiện phân tích các biến kiểm thử (SKILL-01), phân hoạch lớp tương đương (SKILL-02), xác định giá trị biên (SKILL-03), viết chi tiết mã nguồn test case (SKILL-04) và phân tích các trường hợp bị bỏ sót (SKILL-05). Toàn bộ nhật ký tương tác và các đóng góp chỉnh sửa của sinh viên được khai báo minh bạch trong [main-report-template.md](main-report-template.md) và lịch sử Git.
