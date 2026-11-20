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
Mở lại VMware và bật thử một máy ảo bất kỳ.
Kiểm tra: Vào thư mục chứa máy ảo đó trong lúc nó đang chạy; nếu không thấy file đuôi .vmem (nặng bằng dung lượng RAM cấp cho máy ảo) xuất hiện nữa là cấu hình tổng đã ăn thành công.
