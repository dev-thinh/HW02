# TC-LOGIN-005: Đăng nhập thất bại với email chứa ký tự SQL Injection

## Requirement ID

FR-02, SEC-05

## Module / Test type / Technique

Login / Security / Domain Testing – EP (EP-EMAIL-05)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value                        |
| -------- | ---------------------------- |
| Email    | `test' OR 1=1 -- @eshop.com` |
| Password | `Test1234!`                  |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test' OR 1=1 -- @eshop.com`
3. Nhập Password: `Test1234!`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thất bại.
- Hệ thống báo lỗi "Đăng nhập thất bại. Vui lòng kiểm tra lại." (không để lộ lỗi cú pháp SQL hoặc bypass đăng nhập thành công).

## Status / Related bugs

Pass / None
