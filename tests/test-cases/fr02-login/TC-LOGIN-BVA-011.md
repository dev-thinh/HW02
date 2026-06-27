# TC-LOGIN-BVA-011: Đăng nhập sai khi login_attempts = 3

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / BVA (login_attempts MAX+1)

## Preconditions

- Tài khoản `test@eshop.com` đã bị khóa
- login_attempts = 3
- locked_until đang ở tương lai
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
- Nhận phản hồi lỗi 403 Forbidden trực tiếp.
- Hiển thị thông báo "Tài khoản đã bị khóa. Vui lòng thử lại sau."
- login_attempts trong database không tăng thêm.

## Status / Related bugs

Pass / None
