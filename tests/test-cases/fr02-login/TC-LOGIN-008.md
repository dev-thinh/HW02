# TC-LOGIN-008: Đăng nhập thất bại với mật khẩu chứa ký tự SQL Injection

## Requirement ID

FR-02, SEC-05

## Module / Test type / Technique

Login / Security / Domain Testing – EP (EP-PASS-04)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value                 |
| -------- | --------------------- |
| Email    | `test@eshop.com`      |
| Password | `password' OR '1'='1` |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: `password' OR '1'='1`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thất bại.
- Hệ thống báo lỗi "Đăng nhập thất bại. Vui lòng kiểm tra lại." (không bypass đăng nhập).

## Status / Related bugs

Pass / None
