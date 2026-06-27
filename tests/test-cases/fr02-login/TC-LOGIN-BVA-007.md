# TC-LOGIN-BVA-007: Đăng nhập với mật khẩu dài 256 ký tự (MAX+1)

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / BVA (password length MAX+1)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value                                   |
| -------- | --------------------------------------- |
| Email    | `test@eshop.com`                        |
| Password | `A...[254 characters]...1!` (256 ký tự) |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: Mật khẩu dài 256 ký tự
4. Bấm nút **Sign In**

## Expected result

- Hệ thống từ chối hoặc báo lỗi "Đăng nhập thất bại. Vui lòng kiểm tra lại." (không bị lỗi 500 server crash do lưu quá giới hạn cột cơ sở dữ liệu nếu có).

## Status / Related bugs

Pass / None
