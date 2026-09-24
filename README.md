# Tài Liệu Phân Tích Kỹ Thuật & Bảng Kiểm Thử (App.js)

## 1. Phân Tích Nguyên Nhân Lỗi Kỹ Thuật

- **Dòng lệnh gây lỗi:**
  ```javascript
  totalFare = baseFare + distanceKm * pricePerAdditionalKm;

  Hằng số baseFare (12.000 VNĐ) vốn đã là khoản cước phí trọn gói dành riêng cho 2 km mở cửa đầu tiên.

  Tuy nhiên, trong nhánh else (khi distanceKm > 2), biểu thức cũ lại lấy toàn bộ quãng đường distanceKm nhân trực tiếp với pricePerAdditionalKm (4.500 VNĐ/km).

  Hành vi này khiến cho 2 km đầu tiên bị tính tiền trùng lặp 2 lần (vừa nằm trong baseFare, vừa nằm trong phép nhân tổng distanceKm * 4500).

Lấy tổng quãng đường trừ đi 2 km mở cửa ban đầu (distanceKm - 2) trước khi nhân với đơn giá km phụ trội pricePerAdditionalKm.