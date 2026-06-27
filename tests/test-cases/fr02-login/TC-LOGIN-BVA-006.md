# TC-LOGIN-BVA-006: Đăng nhập với mật khẩu dài 255 ký tự (MAX)

## Requirement ID
FR-02

## Module / Test type / Technique
Login / Functional / BVA (password length MAX)

## Preconditions
- Đang ở trang `/login`
- Đã đăng ký tài khoản với mật khẩu dài 255 ký tự thành công

## Test data
| Field | Value |
|-------|-------|
| Email | `user_255chars@eshop.com` |
| Password | `A...[253 characters]...1!` (255 ký tự) |

## Test steps
1. Mở trang `/login`
2. Nhập Email: `user_255chars@eshop.com`
3. Nhập Password: Mật khẩu dài 255 ký tự
4. Bấm nút **Sign In**

## Expected result
- Đăng nhập thành công, chuyển hướng về trang chủ.

## Status / Related bugs
Not Run / None
