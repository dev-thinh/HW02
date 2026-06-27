# TC-LOGIN-BVA-003: Đăng nhập với mật khẩu dài 9 ký tự (MIN+1)

## Requirement ID
FR-02

## Module / Test type / Technique
Login / Functional / BVA (password length MIN+1)

## Preconditions
- Đang ở trang `/login`
- Đã đăng ký tài khoản với mật khẩu dài 9 ký tự thành công

## Test data
| Field | Value |
|-------|-------|
| Email | `user_9chars@eshop.com` |
| Password | `Abc@12345` (9 ký tự) |

## Test steps
1. Mở trang `/login`
2. Nhập Email: `user_9chars@eshop.com`
3. Nhập Password: `Abc@12345`
4. Bấm nút **Sign In**

## Expected result
- Đăng nhập thành công, chuyển hướng về trang chủ.

## Status / Related bugs
Not Run / None
