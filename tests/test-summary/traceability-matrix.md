# Traceability Matrix – HW02 Domain Testing

| Requirement | Test Case | Technique | Result | Bug Issue | Status |
|-------------|-----------|-----------|--------|-----------|--------|
| FR-02 | TC-LOGIN-001 | EP (Valid Login) | Pass | None | Passed |
| FR-02 | TC-LOGIN-002 | EP (Invalid: Email non-exist) | Pass | None | Passed |
| FR-02 | TC-LOGIN-003 | EP (Invalid: Email format) | Pass | None | Passed |
| FR-02 | TC-LOGIN-004 | EP (Invalid: Email empty) | Pass | None | Passed |
| FR-02 | TC-LOGIN-005 | EP (Security: SQLi Email) | Pass | None | Passed |
| FR-02 | TC-LOGIN-006 | EP (Invalid: Wrong password) | Pass | None | Passed |
| FR-02 | TC-LOGIN-007 | EP (Invalid: Password empty) | Pass | None | Passed |
| FR-02 | TC-LOGIN-008 | EP (Security: SQLi Password) | Pass | None | Passed |
| FR-02 | TC-LOGIN-009 | EP (Combination: Locked attempts) | Pass | None | Passed |
| FR-02 | TC-LOGIN-010 | EP (Combination: Login when locked) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-001 | BVA (MIN-1: password length 7) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-002 | BVA (MIN: password length 8) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-003 | BVA (MIN+1: password length 9) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-004 | BVA (NOM: password length 12) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-005 | BVA (MAX-1: password length 254) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-006 | BVA (MAX: password length 255) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-007 | BVA (MAX+1: password length 256) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-008 | BVA (MIN: attempts 0) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-009 | BVA (MAX-1: attempts 1) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-010 | BVA (MAX: attempts 2) | Pass | None | Passed |
| FR-02 | TC-LOGIN-BVA-011 | BVA (MAX+1: attempts 3) | Pass | None | Passed |
| FR-09 | TC-COUPON-001 | EP (Valid Percent Coupon) | Fail | #1 | Open Bug |
| FR-09 | TC-COUPON-002 | EP (Valid Fixed Coupon) | Pass | None | Passed |
| FR-09 | TC-COUPON-003 | EP (Invalid: Code non-exist) | Pass | None | Passed |
| FR-09 | TC-COUPON-004 | EP (Invalid: Code inactive) | Pass | None | Passed |
| FR-09 | TC-COUPON-005 | EP (Invalid: Code empty) | Pass | None | Passed |
| FR-09 | TC-COUPON-006 | EP (Security: SQLi Coupon) | Pass | None | Passed |
| FR-09 | TC-COUPON-007 | EP (Access Control: Guest) | Pass | None | Passed |
| FR-09 | TC-COUPON-008 | EP (Invalid: Order total below min) | Pass | None | Passed |
| FR-09 | TC-COUPON-009 | EP (Invalid: Coupon expired) | Pass | None | Passed |
| FR-09 | TC-COUPON-010 | EP (Invalid: Coupon max usage) | Pass | None | Passed |
| FR-09 | TC-COUPON-011 | EP (Calculation: Percent formula) | Fail | #1 | Open Bug |
| FR-09 | TC-COUPON-012 | EP (Calculation: Fixed formula) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-001 | BVA (MIN-1: order_total 299k) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-002 | BVA (MIN: order_total 300k) | Fail | #2 | Open Bug |
| FR-09 | TC-COUPON-BVA-003 | BVA (MIN+1: order_total 300.001k) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-004 | BVA (MIN-1: order_total 499k) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-005 | BVA (MIN: order_total 500k) | Fail | #2 | Open Bug |
| FR-09 | TC-COUPON-BVA-006 | BVA (MIN+1: order_total 500.001k) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-007 | BVA (MIN-1: order_total 299k VIP100) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-008 | BVA (MIN: order_total 300k VIP100) | Fail | #2 | Open Bug |
| FR-09 | TC-COUPON-BVA-009 | BVA (MIN+1: order_total 300.001k VIP100) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-010 | BVA (MAX: usage_count 1) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-011 | BVA (MAX+1: usage_count 2) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-012 | BVA (MAX-1: expired yesterday) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-013 | BVA (MAX+1: expiry tomorrow) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-014 | BVA (MIN: usage_count 0) | Pass | None | Passed |
| FR-09 | TC-COUPON-BVA-015 | BVA (MAX: expiry today) | Pass | None | Passed |
| FR-14 | TC-CAT-001 | EP (Valid Admin Create) | Pass | None | Passed |
| FR-14 | TC-CAT-002 | EP (Invalid: Create duplicate name) | Fail | #3 | Open Bug |
| FR-14 | TC-CAT-003 | EP (Invalid: Create empty name) | Fail | #4 | Open Bug |
| FR-14 | TC-CAT-004 | EP (Invalid: Create whitespace name) | Fail | #4 | Open Bug |
| FR-14 | TC-CAT-005 | EP (Access Control: Normal User Create) | Fail | #5 | Open Bug |
| FR-14 | TC-CAT-006 | EP (Access Control: Token invalid) | Pass | None | Passed |
| FR-14 | TC-CAT-007 | EP (Valid: Delete parent category) | Pass | None | Passed |
| FR-14 | TC-CAT-008 | EP (Access Control: Normal User Delete) | Fail | #6 | Open Bug |
| FR-14 | TC-CAT-009 | EP (Access Control: Guest User Delete) | Pass | None | Passed |
| FR-14 | TC-CAT-010 | EP (Invalid: Delete non-existent ID) | Pass | None | Passed |
| FR-14 | TC-CAT-011 | EP (Invalid: Delete already deleted) | Pass | None | Passed |
| FR-14 | TC-CAT-012 | EP (Invalid: Delete negative ID) | Fail | #7 | Open Bug |
| FR-14 | TC-CAT-013 | EP (Invalid: Delete non-numeric ID) | Fail | #8 | Open Bug |
| FR-14 | TC-CAT-SEC-001 | EP (Security: Stored XSS Name) | Pass | None | Passed |
| FR-14 | TC-CAT-BVA-001 | BVA (MIN-1: name length 0) | Fail | #4 | Open Bug |
| FR-14 | TC-CAT-BVA-002 | BVA (MIN: name length 1) | Pass | None | Passed |
| FR-14 | TC-CAT-BVA-003 | BVA (MIN+1: name length 2) | Pass | None | Passed |
| FR-14 | TC-CAT-BVA-004 | BVA (MIN-1: id 0) | Fail | #7, #8 | Open Bug |
| FR-14 | TC-CAT-BVA-005 | BVA (MIN: id 1) | Pass | None | Passed |
| FR-14 | TC-CAT-BVA-006 | BVA (MIN+1: id 2) | Pass | None | Passed |
| FR-06 | TC-MPROD-001 | EP (Valid: View Active Product) | Pass | None | Passed |
| FR-06 | TC-MPROD-002 | EP (Valid: Add to cart positive qty) | Pass | None | Passed |
| FR-06 | TC-MPROD-003 | EP (Invalid: Add to cart qty 0) | Fail | #9 | Open Bug |
| FR-06 | TC-MPROD-004 | EP (Invalid: Add to cart qty negative) | Fail | #10 | Open Bug |
| FR-06 | TC-MPROD-005 | EP (Invalid: Add to cart qty decimal) | Fail | #11 | Open Bug |
| FR-06 | TC-MPROD-006 | EP (Invalid: Add to cart qty empty) | Fail | #12 | Open Bug |
| FR-06 | TC-MPROD-007 | EP (Invalid: Add to cart qty mixed) | Fail | #13 | Open Bug |
| FR-06 | TC-MPROD-008 | EP (Invalid: Add to cart qty alpha) | Fail | #14 | Open Bug |
| FR-06 | TC-MPROD-009 | EP (Valid: View loading state) | Pass | None | Passed |
| FR-06 | TC-MPROD-010 | EP (Invalid: View non-exist product) | Pass | None | Passed |
| FR-06 | TC-MPROD-011 | EP (Invalid: View product missing fields) | Pass | None | Passed |
| FR-06 | TC-MPROD-BVA-001 | BVA (MIN-1: quantity 0) | Fail | #9 | Open Bug |
| FR-06 | TC-MPROD-BVA-002 | BVA (MIN: quantity 1) | Pass | None | Passed |
| FR-06 | TC-MPROD-BVA-003 | BVA (MIN+1: quantity 2) | Pass | None | Passed |
| FR-06 | TC-MPROD-BVA-004 | BVA (NOM: quantity 5) | Pass | None | Passed |

---

## Coverage Summary

| Requirement | TCs Designed | TCs Passed | TCs Failed | Open Bugs |
|-------------|-------------|-----------|-----------|-----------|
| FR-02 Login | 21 | 21 | 0 | 0 |
| FR-09 Coupons | 27 | 22 | 5 | 2 |
| FR-14 Category | 19 | 10 | 9 | 6 |
| FR-06 Mobile | 15 | 8 | 7 | 6 |
| **Total** | **82** | **61** | **21** | **14** |
