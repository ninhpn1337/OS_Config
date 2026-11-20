Tắt toàn bộ máy ảo đang chạy và thoát hẳn phần mềm VMware Workstation.

Mở Notepad với quyền Admin (nhấn phím Windows, gõ Notepad, chuột phải chọn Run as administrator).

Trong Notepad, vào File -> Open, dán nguyên đường dẫn này vào ô File name rồi nhấn Open:

```
C:\ProgramData\VMware\VMware Workstation\config.ini
```
Kéo xuống cuối file, dán 4 dòng sau vào rồi nhấn Ctrl + S để lưu:

```ini
mainMem.useNamedFile = "FALSE"
MemTrimRate = "0"
sched.mem.pshare.enable = "FALSE"
prefvmx.minVmMemPct = "100"
```

### Ý nghĩa các dòng cấu hình:
- **`mainMem.useNamedFile = "FALSE"`**: Ép VMware cấp phát RAM của máy ảo trực tiếp trên RAM vật lý, ngăn việc tạo file `.vmem` (file tạm nặng bằng dung lượng RAM) trên ổ cứng, giúp tăng tốc độ máy ảo và tiết kiệm dung lượng SSD.
- **`MemTrimRate = "0"`**: Tắt tính năng thu hồi RAM tự động của VMware, giữ ổn định lượng RAM đã cấp cho máy ảo không bị hệ thống host bóp lại.
- **`sched.mem.pshare.enable = "FALSE"`**: Tắt tính năng Page Sharing (chia sẻ trang nhớ giữa các máy ảo), giảm tải CPU khi máy tính chạy nhiều máy ảo đồng thời.
- **`prefvmx.minVmMemPct = "100"`**: Đảm bảo 100% RAM cấp cho máy ảo luôn nằm trên RAM vật lý, không bị swap/paging ra ổ cứng.
Mở lại VMware và bật thử một máy ảo bất kỳ.
Kiểm tra: Vào thư mục chứa máy ảo đó trong lúc nó đang chạy; nếu không thấy file đuôi .vmem (nặng bằng dung lượng RAM cấp cho máy ảo) xuất hiện nữa là cấu hình tổng đã ăn thành công.
