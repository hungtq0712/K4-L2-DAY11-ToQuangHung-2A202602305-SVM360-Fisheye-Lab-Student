# QA review · B4-dense

Mã khóa: 950A-2463

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_258420.jpg | L7+L8 | R_Overlap_Merge | L7 và L8 đè lên cùng một đối tượng xe hai bánh, cần kiểm tra gộp hoặc xóa box trùng. |
| adasind_270517.jpg | L2 | R_Edge_Zone | L2 nằm sát mép viền ngoài ảnh fisheye (x > 1000), cần kiểm tra thuộc tính edge_zone và truncated. |
| adasind_270517.jpg | L3 | R_BBox_Geometry | L3 (ThreeWheeler) có kích thước lớn ở vùng center, cần rà soát lại viền ôm sát cấu trúc xe. |
| adasind_310008.jpg | L4+L5 | R_Duplicate_BBox | L4 và L5 vi phạm trùng lặp vị trí người đi bộ sát lề trái, cần loại bỏ khung thừa. |