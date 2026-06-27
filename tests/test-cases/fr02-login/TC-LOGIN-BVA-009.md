# TC-LOGIN-BVA-009: Đăng nhập sai khi login_attempts = 1

## Requirement ID
FR-02

## Module / Test type / Technique
Login / Functional / BVA (login_attempts MIN+1)

## Preconditions
- Tài khoản `test@eshop.com` tồn tại và chưa bị khóa
- login_attempts = 1
- Đang ở trang `/login`

## Test data
| Field | Value |
|-------|-------|
| Email | `test@eshop.com` |
| Password | `WrongPass123!` |

## Test steps
1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: `WrongPass123!`
4. Bấm nút **Sign In**

## Expected result
- Đăng nhập thất bại.
- login_attempts trong database tăng lên 3 (1 + 2).
- Tài khoản bị khóa (do attempts $\ge 3$).
- locked_until được thiết lập.

## Status / Related bugs
Not Run / None
