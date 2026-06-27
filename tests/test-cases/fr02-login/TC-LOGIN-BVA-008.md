# TC-LOGIN-BVA-008: Đăng nhập sai khi login_attempts = 0

## Requirement ID
FR-02

## Module / Test type / Technique
Login / Functional / BVA (login_attempts MIN)

## Preconditions
- Tài khoản `test@eshop.com` tồn tại và chưa bị khóa
- login_attempts = 0
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
- login_attempts trong database tăng lên 2 (do SUT cộng thêm 2 thay vì 1).
- Tài khoản không bị khóa.

## Status / Related bugs
Not Run / None
