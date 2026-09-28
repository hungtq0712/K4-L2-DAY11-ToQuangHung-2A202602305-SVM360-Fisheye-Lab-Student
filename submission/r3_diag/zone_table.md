# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone   | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
| ------ | ----: | --------: | ---------: | ----------------------------------: | --------------------------------: | ------------------------ |
| center |     6 |         0 |          0 |                                   4 |                                 5 | —                       |
| mid    |     7 |         1 |          3 |                                   3 |                                10 | SPURIOUS (2)             |
| edge   |     7 |         0 |          0 |                                   1 |                                 1 | —                       |

## Nhận xét

- **Zone gãy nhiều nhất đối với Người (L) và Model (M):**

  - **Vùng `mid` (trung gian):** Là zone gãy nặng nhất cho cả Người lẫn Model[cite: 6]. Đối với Người (L), vùng này ghi nhận 1 lỗi `L missing` và 3 lỗi `L spurious` (trong đó lỗi chính là `SPURIOUS` xuất hiện 2 lần)[cite: 6]. Đối với Model (M), vùng `mid` bộc lộ điểm yếu lớn nhất khi xuất hiện tới 10 lỗi `M thừa` (`LM_noR` + `M_only`) và 3 lỗi `M missing`[cite: 6].
  - **Vùng `center` (trung tâm):** Người gán nhãn đạt độ chính xác cao (0 missing, 0 spurious)[cite: 6]. Tuy nhiên, Model (M) gãy mạnh với 4 lỗi `M missing` (trượt 4/6 đối tượng reference) và 5 lỗi `M thừa`[cite: 6].
  - **Vùng `edge` (viền ảnh):** Đạt độ ổn định tốt nhất. Người gán nhãn không mắc lỗi nào (0 missing, 0 spurious)[cite: 6], trong khi Model chỉ bị lỗi nhẹ với 1 `M missing` và 1 `M thừa`[cite: 6].
- **Giả thuyết nguyên nhân và Giới hạn của slice 3 frame:**

  - **Giả thuyết nguyên nhân:**
    - *Vùng `mid`:* Cấu trúc vật thể ở khoảng cách trung bình bị ảnh hưởng bởi bóng rôm, nhiễu nền và vạch kẻ đường, làm Annotator vẽ nhầm box dư (`L spurious = 3`) và khiến Model phát hiện nhầm hàng loạt tín hiệu giả (`M thừa = 10`)[cite: 6].
    - *Vùng `center`:* Model trượt 4/6 box do các đối tượng xe ba gác (`ThreeWheeler`) ở khu vực trung tâm có góc nhìn và hình dạng chưa được mô hình tối ưu tốt.
    - *Vùng `edge`:* Nhờ thực hiện đúng quy tắc gán nhãn ống kính fisheye (tích đủ thuộc tính `edge_zone` và `truncated`), Người gán nhãn kiểm soát hoàn toàn vùng viền mép ảnh[cite: 6].
  - **Giới hạn của slice 3 frame:**
    - Mẫu dữ liệu chỉ vỏn vẹn 3 frame trong slice `B4-dense` nên mang tính cục bộ cao, chưa phản ánh đầy đủ phân phối thực tế của toàn bộ bộ dữ liệu fisheye.
    - Quy mô mẫu nhỏ khiến các chỉ số lỗi tỉ lệ dễ bị thổi phồng (ví dụ: chỉ cần 2-3 box Spurious ở vùng `mid` đã làm thay đổi đáng kể tỉ lệ lỗi của zone)[cite: 6].
