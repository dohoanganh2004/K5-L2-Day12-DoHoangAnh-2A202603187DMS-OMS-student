# Danh sách lớp v0 — Đỗ Hoàng Anh · G04

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_left / eye_right | open / closed / unknown | Phát hiện buồn ngủ qua mắt nhắm kéo dài, gán riêng từng mắt | Có, trừ khi kính phản xạ LED hoặc kính râm tối |
| 2 | gaze_zone | road, mirror_l/r/c, cluster, center, lap, other | Biết tài xế đang nhìn đâu, cảnh báo mất tập trung khi không nhìn đường | Có (theo hướng đầu và mắt), kém đi khi mắt bị che |
| 3 | face13 (13 điểm mặt) | tọa độ + cờ occluded/outside | Ước lượng tư thế đầu, độ mở mắt và miệng (ngáp) | Có khi mặt đủ lớn (≥ 60 px); điểm bị che phải có cờ |
| 4 | hand (whose, side, on_wheel) | driver/passenger; left/right; yes/no/unknown | Biết tay có trên vô lăng không, phục vụ cảnh báo takeover khi lái tự động | Có (hình dạng), khó khi tay nằm ngoài khung |
| 5 | phone (state) | held / mounted / lap | Phát hiện dùng điện thoại khi lái | Có nếu thấy cạnh, góc hoặc màn hình; vật tối trong tay thì không chắc |
| 6 | glasses | none / clear / sun / unknown | Chọn cách xử lý mắt (kính phản xạ, kính râm che mắt) cho model eye-state | Hạn chế: kính râm có thể trông trong suốt trên NIR |

## OMS (6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person + seat | driver, front_passenger, rear_left/middle/right | Đếm người và biết ai ngồi ghế nào (nhắc thắt dây, tắt túi khí ghế trống) | Có (hình dạng, vị trí) |
| 2 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Nhắc thắt dây an toàn cho từng chỗ ngồi | Hạn chế: dây trên áo tối dễ thành unknown |
| 3 | child_seat (+ occupied) | no / unknown (+ yes theo hướng dẫn mới) | Nhận biết có ghế trẻ em để cảnh báo túi khí và quên trẻ | Có (hình dạng) |
| 4 | infant_seat (+ facing) | rear / front | Ghế em bé quay sau ở ghế trước thì phải tắt túi khí; nhắc quên trẻ trong xe | Có (hình dạng lớn) |
| 5 | object (+ type) | bag / box / cup / other | Phát hiện đồ bỏ quên và vật nằm trong ghế trẻ em | Có (hình dạng), nhưng không phân biệt vật bằng màu |
| 6 | face (OMS) | chỉ box | Xác nhận có người thật ngồi ghế (không phải vật), giúp đếm người | Có |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời.

1. Câu hỏi: Khi trong ghế trẻ em có vật hoặc người, thuộc tính `occupied` của `child_seat` nên là gì? Bản guideline v1.0 chỉ cho `no`/`unknown`, còn hướng dẫn mới của thầy cho thêm `yes`. Khi có `yes`, vật trong ghế vẫn cần box `object` riêng không, hay `yes` đã đủ?
   Khung ví dụ: G04 S01_rgb (child_seat bên phải ảnh).
   Bạn tạm gán thế nào và vì sao: tạm gán `occupied = yes` theo hướng dẫn của thầy và vẫn giữ box `object` riêng cho vật nằm trong ghế để không mất thông tin.
2. Câu hỏi: Ranh giới giữa các `gaze_zone` khi tài xế nhìn vào một vùng ở giữa hai vùng (ví dụ nhìn xuống màn hình giữa nhưng đầu hơi cúi) thì chọn `center`, `lap` hay `other`? Guideline chưa nói ngưỡng.
   Khung ví dụ: G04 D05 (mình gán gaze_zone = other).
   Bạn tạm gán thế nào và vì sao: tạm gán `other` và ghi lý do vì không chắc vùng nào, theo quy tắc "không chắc thì other".
