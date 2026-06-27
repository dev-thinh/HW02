# TC-LOGIN-010: Đăng nhập thất bại khi tài khoản đang bị khóa

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (COMBO-04)

## Preconditions

- Tài khoản `test@eshop.com` đang bị khóa (locked_until ở tương lai)
- Đang ở trang `/login`

## Test data

| Field    | Value                            |
| -------- | -------------------------------- |
| Email    | `test@eshop.com`                 |
| Password | `Test1234!` (nhập đúng mật khẩu) |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: `Test1234!`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thất bại.
- Trả về mã lỗi 403 Forbidden.
- Hiển thị thông báo lỗi "Tài khoản đã bị khóa. Vui lòng thử lại sau." ở trên nút submit.

## Status / Related bugs

Pass / None
