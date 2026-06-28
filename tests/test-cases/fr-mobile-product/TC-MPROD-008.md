# TC-MPROD-008: Thêm vào giỏ hàng với số lượng là chuỗi chữ hoàn toàn (Non-numeric)

## Requirement ID
FR-06 (Mobile)

## Module / Test type / Technique
Mobile-Product / Functional / Domain Testing – EP (COMBO-07)

## Preconditions
- Đang ở màn hình chi tiết sản phẩm `iPhone 15 Pro Max` trên Mobile App.

## Test data
| Field | Value |
|-------|-------|
| Số lượng | `"abc"` |

## Test steps
1. Nhập `"abc"` vào ô số lượng.
2. Nhấn nút **Thêm vào giỏ hàng**.

## Expected result
- Spec: Yêu cầu thất bại, hệ thống chặn việc thêm vì không phải số nguyên dương.
- *Lưu ý (SUT Bug):* Trên ứng dụng thực tế, hệ thống vẫn báo "Thành công - Đã thêm vào giỏ hàng" và tự động thêm số lượng bằng 1 vào giỏ do fallback logic.

## Status / Related bugs
Not Run / None
