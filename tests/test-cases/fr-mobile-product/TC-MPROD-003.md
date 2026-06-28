# TC-MPROD-003: Thêm vào giỏ hàng với số lượng bằng 0

## Requirement ID
FR-06 (Mobile)

## Module / Test type / Technique
Mobile-Product / Functional / Domain Testing – EP (COMBO-02)

## Preconditions
- Đang ở màn hình chi tiết sản phẩm `iPhone 15 Pro Max` trên Mobile App.

## Test data
| Field | Value |
|-------|-------|
| Số lượng | `"0"` |

## Test steps
1. Nhập số lượng `"0"` vào ô số lượng.
2. Nhấn nút **Thêm vào giỏ hàng**.

## Expected result
- Spec: Yêu cầu thất bại, hệ thống chặn việc thêm vào giỏ hàng với số lượng bằng 0.
- *Lưu ý (SUT Bug):* Trên ứng dụng thực tế, hệ thống vẫn báo "Thành công - Đã thêm vào giỏ hàng" và tự động thêm số lượng bằng 1 vào giỏ do fallback logic ở hàm `normalizeQuantity` âm thầm chấp nhận.

## Status / Related bugs
Not Run / None
