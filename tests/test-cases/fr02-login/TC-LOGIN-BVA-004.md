# TC-LOGIN-BVA-004: Đăng nhập với mật khẩu dài 12 ký tự (NOM)

## Requirement ID
FR-02

## Module / Test type / Technique
Login / Functional / BVA (password length NOM)

## Preconditions
- Đang ở trang `/login`
- Đã đăng ký tài khoản với mật khẩu dài 12 ký tự thành công

## Test data
| Field | Value |
|-------|-------|
| Email | `user_12chars@eshop.com` |
| Password | `Abc@12345678` (12 ký tự) |

## Test steps
1. Mở trang `/login`
2. Nhập Email: `user_12chars@eshop.com`
3. Nhập Password: `Abc@12345678`
4. Bấm nút **Sign In**

## Expected result
- Đăng nhập thành công, chuyển hướng về trang chủ.

## Status / Related bugs
Not Run / None
