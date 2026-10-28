# Mô phỏng điều khiển mức nước bằng PID

Dự án mô phỏng điều khiển mức nước sử dụng **Factory I/O**, **Siemens TIA Portal** và bộ điều khiển **PID**.

> Repository hiện là khung tổ chức dự án. Chưa có chương trình PLC, scene mô phỏng hoặc kết quả thực nghiệm được tải lên.

## Mục tiêu

- Đọc mức nước từ cảm biến trong mô hình mô phỏng.
- So sánh mức nước thực tế (PV) với giá trị đặt (SP).
- Dùng bộ điều khiển PID để điều chỉnh cơ cấu cấp hoặc xả nước theo thiết kế.
- Quan sát đáp ứng và đánh giá sai lệch, độ quá điều chỉnh, thời gian xác lập.

## Cấu trúc thư mục

```text
.
├── README.md
├── tia-portal/         # Project hoặc bản archive TIA Portal
├── factory-io/         # Scene Factory I/O và cấu hình kết nối
├── plc-exports/        # Các khối PLC, bảng tag được xuất ra
├── docs/               # Hướng dẫn, bảng I/O và cấu hình PID
├── images/             # Ảnh mô hình, chương trình, đồ thị
└── results/            # Dữ liệu đo và kết quả thử nghiệm
```

Mỗi thư mục có README hướng dẫn loại file cần đưa vào để GitHub giữ lại cấu trúc thư mục.

## Phần mềm cần chuẩn bị

| Thành phần | Thông tin cần bổ sung |
| --- | --- |
| Windows | Phiên bản tương thích với các phần mềm sử dụng |
| TIA Portal | Phiên bản tạo project: **chưa cung cấp** |
| PLC hoặc S7-PLCSIM / PLCSIM Advanced | Model CPU và phiên bản: **chưa cung cấp** |
| Factory I/O | Phiên bản và driver kết nối: **chưa cung cấp** |

Cần chọn driver Factory I/O phù hợp với PLC hoặc phần mềm mô phỏng thực tế. Môi trường Linux đám mây này dùng để quản lý file và tài liệu; chưa thiết lập chạy TIA Portal, PLCSIM hoặc Factory I/O.

## Cách thêm dự án

1. Đưa project hoặc bản archive TIA Portal vào `tia-portal/`. Nên dùng chức năng Archive của TIA Portal để đóng gói đầy đủ.
2. Lưu scene Factory I/O vào `factory-io/`.
3. Nếu có, xuất các khối PLC và bảng tag vào `plc-exports/` để thuận tiện xem xét thay đổi.
4. Ghi phiên bản phần mềm, CPU, driver, địa chỉ I/O và tham số PID trong `docs/`.
5. Đưa ảnh minh họa vào `images/`, dữ liệu thử nghiệm vào `results/`.
6. Commit và đẩy các file lên repository GitHub. Nếu dùng giao diện web, chọn **Add file → Upload files**, kéo thả nội dung cần tải lên rồi chọn **Commit changes**.

## Quy trình chạy dự kiến

Sau khi bổ sung file dự án và thông tin cấu hình:

1. Mở hoặc Retrieve bản archive bằng phiên bản TIA Portal phù hợp.
2. Kiểm tra cấu hình CPU, compile chương trình và xử lý các lỗi được báo.
3. Khởi động PLC mô phỏng hoặc kết nối PLC dùng cho dự án, rồi nạp chương trình.
4. Mở scene Factory I/O, chọn driver và ánh xạ I/O theo tài liệu dự án.
5. Kiểm tra tín hiệu mức nước và chiều tác động của cơ cấu chấp hành.
6. Chạy mô phỏng, đặt SP, ghi lại PV và đầu ra PID theo thời gian.

Các bước trên là hướng dẫn chuẩn bị; chưa được kiểm chứng bằng file dự án thực tế.

## Kiểm chứng cần thực hiện

- [ ] Project TIA Portal compile thành công.
- [ ] Factory I/O kết nối được với PLC hoặc PLC mô phỏng.
- [ ] Tín hiệu cảm biến được scale đúng đơn vị và dải đo.
- [ ] Đầu ra điều khiển tác động đúng chiều và đúng giới hạn.
- [ ] PV bám SP; lưu đồ thị và thông số thử nghiệm.
- [ ] Kiểm tra đáp ứng khi thay đổi SP hoặc lưu lượng xả.

## Thông tin cần bổ sung

Tên tác giả, phiên bản phần mềm, model CPU, sơ đồ I/O, đơn vị đo, chu kỳ lấy mẫu, tham số PID và kết quả thực nghiệm.
