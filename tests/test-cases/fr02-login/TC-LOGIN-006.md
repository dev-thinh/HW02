# TC-LOGIN-006: Đăng nhập thất bại với mật khẩu sai (1st attempt)

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (COMBO-02)

## Preconditions

- Tài khoản `test@eshop.com` tồn tại và chưa bị khóa
- login_attempts = 0
- Đang ở trang `/login`

## Test data

| Field    | Value            |
| -------- | ---------------- |
| Email    | `test@eshop.com` |
| Password | `WrongPass123!`  |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: `WrongPass123!`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thất bại.
- Hiển thị thông báo lỗi "Đăng nhập thất bại. Vui lòng kiểm tra lại." ở trên nút submit.
- Số lần đăng nhập sai `login_attempts` trong database tăng lên (SUT tăng thêm 2 đơn vị thành 2).
- Tài khoản không bị khóa và vẫn có thể thử lại.

## Status / Related bugs

Pass / None
