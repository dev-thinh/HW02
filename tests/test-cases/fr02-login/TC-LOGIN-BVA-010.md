# TC-LOGIN-BVA-010: Đăng nhập sai khi login_attempts = 2

## Requirement ID
FR-02

## Module / Test type / Technique
Login / Functional / BVA (login_attempts MAX)

## Preconditions
- Tài khoản `test@eshop.com` tồn tại và chưa bị khóa
- login_attempts = 2
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
- login_attempts trong database tăng lên 4 (2 + 2).
- Tài khoản bị khóa (do attempts $\ge 3$).
- locked_until được thiết lập.

## Status / Related bugs
Not Run / None
