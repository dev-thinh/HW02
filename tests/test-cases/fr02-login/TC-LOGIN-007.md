# TC-LOGIN-007: Đăng nhập thất bại với mật khẩu để trống

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (EP-PASS-03)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value            |
| -------- | ---------------- |
| Email    | `test@eshop.com` |
| Password | `""` (để trống)  |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Để trống trường Mật khẩu
4. Bấm nút **Sign In**

## Expected result

- Trình duyệt hiển thị cảnh báo yêu cầu nhập trường này (HTML5 validation `required`).
- Không cho phép submit form.

## Status / Related bugs

Pass / None
