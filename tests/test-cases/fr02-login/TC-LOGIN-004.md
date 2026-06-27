# TC-LOGIN-004: Đăng nhập thất bại với email để trống

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (EP-EMAIL-04)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value           |
| -------- | --------------- |
| Email    | `""` (để trống) |
| Password | `Test1234!`     |

## Test steps

1. Mở trang `/login`
2. Để trống trường Email
3. Nhập Password: `Test1234!`
4. Bấm nút **Sign In**

## Expected result

- Trình duyệt hiển thị cảnh báo yêu cầu nhập trường này (HTML5 validation `required`).
- Không cho phép submit form.

## Status / Related bugs

Pass / None
