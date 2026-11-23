# Khai báo dùng AI — Đỗ Hoàng Anh

Không đưa ảnh cabin hay ảnh tài xế (kể cả ảnh chụp màn hình) cho công cụ AI nào. AI không gán nhãn hộ.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Claude Code | Giải thích đề bài, Guideline Cabin v1.0, các label và thuộc tính (eye, gaze_zone, facing…) | Dùng để hiểu quy tắc, rồi tự gán nhãn trên CVAT | Đối chiếu lại với GUIDE.md và COMMON_ERRORS.md |
| 2 | Claude Code | Chạy `cabin_check` trên export_final.zip và đọc lỗi/cảnh báo | Sửa lỗi trên CVAT rồi export lại | Chạy lại `cabin_check` đến khi 0 lỗi |
| 3 | Claude Code | Sửa `scripts/cabin_schema.py` cho phép `occupied = yes` của child_seat theo hướng dẫn của thầy | Dùng để chạy kiểm | Ghi rõ ở TEAM/ghi chú, so với file nhãn thầy đưa (khác đúng một dòng) |
| 4 | Claude Code | Soạn nháp `class_list_v0.md`, khung `ir_log.csv`, `TEAM.md`, `prompts.md` và đóng gói thư mục nộp | Đọc lại, chỉnh sửa và xác nhận các chỗ ghi [XÁC NHẬN]/[ĐIỀN] bằng quan sát của mình | Đọc lại từng file trước khi nộp |
