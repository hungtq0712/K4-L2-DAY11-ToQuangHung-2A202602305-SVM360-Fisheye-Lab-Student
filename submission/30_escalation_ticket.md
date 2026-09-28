# Escalation ticket

## Ticket 1

- **Frame:** adasind_258420.jpg
- **Ảnh chụp:** submission/screenshots/ref_defect_258420.png
- **Expected impact:** Reference ground truth (`R`) bỏ sót nhãn ô tô (`Car`) tại vị trí `L3+M6`, làm sai lệch chỉ số đánh giá mAP/Precision của mô hình AI (`M`) và tính sai lỗi dư nhãn cho Annotator (`L`).
- **Owner:** data_ops
- **Recommendation:** Cập nhật lại bộ dữ liệu Reference Ground Truth bằng cách bổ sung khung nhãn `Car` cho đối tượng `L3+M6` trên frame `adasind_258420.jpg`.