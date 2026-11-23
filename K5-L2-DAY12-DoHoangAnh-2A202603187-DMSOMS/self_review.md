# Tự đánh giá — Đỗ Hoàng Anh · G04

## 1. Tự rà soát 4 cảnh

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_ir | frame_meta.light | guess | Để `night` trên ảnh SVIRO. Ảnh dựng nên guideline yêu cầu `unknown` (cabin_check cảnh báo) | Đã sửa |
| S03_rgb | object (cốc, rear_middle) | missing | S03_ir của mình có cốc nhưng S03_rgb thiếu. Lộ ra khi đối chiếu với bài của Huyền | Không sửa; giữ nguyên export_final.zip, ghi nhận lỗi ở đây (RULES §6) |
| D01 | hand | lr_flip | Hai tay `whose=driver` cùng `side=left`, trong khi mỗi người chỉ có một tay trái và một tay phải | Đã sửa |
| D02 | face13 | ok | Ảnh xoay 90°; đã kiểm toạ độ trong export: left_eye_outer y=838 lớn hơn right_eye_outer y=558, đúng quy ước | Không cần sửa |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: quên hoặc làm sai bước đầu tiên của mỗi ảnh, tức tag `frame_meta`: thiếu tag ở D01 và S03_ir, và để `light` khác `unknown` trên ảnh SVIRO (S01_ir, và nhiều ảnh S## lúc đầu).

Vì sao mình mắc: mình bắt đầu vẽ box ngay mà không đặt tag trước, và chọn `light` theo cảm giác ảnh tối hay sáng thay vì theo quy tắc ảnh dựng là `unknown`. Khi copy shape từ ảnh `_rgb` sang `_ir`, mình cũng không soát lại từng tag.

Lần sau tránh bằng cách: luôn đặt `frame_meta` trước box đầu tiên (đúng thứ tự guideline 4.3); ảnh SVIRO luôn `light = unknown`; và chạy `cabin_check` sau mỗi 2–3 ảnh thay vì để đến cuối.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai: `S03_rgb` có cốc (object, rear_middle) mà mình thiếu, dù `S03_ir` của mình đã có. Mình học được rằng sau khi copy shape giữa RGB và IR-sim phải đối chiếu lại số lượng đối tượng của cả hai ảnh trong cùng một cảnh.
