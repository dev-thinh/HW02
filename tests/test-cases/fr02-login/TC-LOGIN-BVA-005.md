# TC-LOGIN-BVA-005: Đăng nhập với mật khẩu dài 254 ký tự (MAX-1)

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / BVA (password length MAX-1)

## Preconditions

- Đang ở trang `/login`
- Đã đăng ký tài khoản với mật khẩu dài 254 ký tự thành công

## Test data

| Field    | Value                                   |
| -------- | --------------------------------------- |
| Email    | `user_254chars@eshop.com`               |
| Password | `A...[252 characters]...1!` (254 ký tự) |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `user_254chars@eshop.com`
3. Nhập Password: Mật khẩu dài 254 ký tự
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thành công, chuyển hướng về trang chủ.

## Status / Related bugs

Pass / None
