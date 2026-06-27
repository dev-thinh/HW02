# TC-LOGIN-BVA-002: Đăng nhập với mật khẩu dài 8 ký tự (MIN)

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / BVA (password length MIN)

## Preconditions

- Đang ở trang `/login`
- Đã đăng ký tài khoản với mật khẩu dài 8 ký tự thành công

## Test data

| Field    | Value                   |
| -------- | ----------------------- |
| Email    | `user_8chars@eshop.com` |
| Password | `Abc@1234` (8 ký tự)    |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `user_8chars@eshop.com`
3. Nhập Password: `Abc@1234`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thành công, chuyển hướng về trang chủ.

## Status / Related bugs

Pass / None
