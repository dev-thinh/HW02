# TC-LOGIN-001: Đăng nhập thành công với credentials hợp lệ

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (COMBO-01)

## Preconditions

- Tài khoản `test@eshop.com` tồn tại và chưa bị khóa
- failed_attempts (login_attempts) = 0
- Đang ở trang `/login`

## Test data

| Field    | Value            |
| -------- | ---------------- |
| Email    | `test@eshop.com` |
| Password | `Test1234!`      |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: `Test1234!`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thành công
- Hệ thống redirect về trang chủ `/`
- Trên header hiển thị thông tin hoặc tên của User (`Test User`)

## Status / Related bugs

Pass / None
