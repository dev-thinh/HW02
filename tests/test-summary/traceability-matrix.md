# Traceability Matrix – HW02 Domain Testing

| Requirement | Test Case | Technique | Result | Bug Issue | Status |
|-------------|-----------|-----------|--------|-----------|--------|
| FR-02 | TC-LOGIN-001 | EP (Valid) | | | |
| FR-02 | TC-LOGIN-002 | EP (Invalid: Email) | | | |
| FR-02 | TC-LOGIN-003 | EP (Invalid: Password) | | | |
| FR-02 | TC-LOGIN-BVA-001 | BVA (MAX: lockout) | | | |
| FR-09 | TC-COUPON-001 | EP (Valid) | | | |
| FR-09 | TC-COUPON-002 | EP (Invalid: Expired) | | | |
| FR-09 | TC-COUPON-BVA-001 | BVA (MIN: order value) | | | |
| FR-14 | TC-CAT-001 | EP (Valid: Create) | | | |
| FR-14 | TC-CAT-002 | EP (Invalid: Duplicate) | | | |
| FR-14 | TC-CAT-BVA-001 | BVA (MIN: name length) | | | |
| FR-06 (Mobile) | TC-MPROD-001 | EP (Valid: Active product) | | | |
| FR-06 (Mobile) | TC-MPROD-BVA-001 | BVA (MIN: price display) | | | |

---

## Coverage Summary

| Requirement | TCs Designed | TCs Passed | TCs Failed | Open Bugs |
|-------------|-------------|-----------|-----------|-----------|
| FR-02 Login | 4 | | | |
| FR-09 Coupons | 3 | | | |
| FR-14 Category | 3 | | | |
| FR-06 Mobile | 2 | | | |
| **Total** | **12** | | | |
