# 🎯 Tin2CN Quiz Patcher v1.0

![Type](https://img.shields.io/badge/Language-VB6_Native-blue)
![Tool](https://img.shields.io/badge/Tool-x32dbg-red)
![Level](https://img.shields.io/badge/Security-Bypass-yellow)

Dự án này hướng dẫn kỹ thuật Reverse Engineering để can thiệp vào bộ nhớ của ứng dụng trắc nghiệm Tin2CN, cho phép tùy chỉnh điểm số và kết quả bài thi một cách đồng nhất.

---

## 📍 Địa chỉ "Tử huyệt" (Target Addresses)

Dưới đây là 3 điểm cần can thiệp trong module `Tin2CN.exe` để thay đổi toàn bộ kết quả:

| Địa chỉ (VA) | Lệnh gốc | Lệnh Patch (ASM) | Tác dụng |
| :--- | :--- | :--- | :--- |
| **`00483B35`** | `movsx eax, [48637A]` | `mov eax, 0xXX` | Thay đổi điểm tổng (ví dụ: 9.75) |
| **`00483BEC`** | `mov ax, [48637A]` | `mov ax, 0xXX` | Thay đổi hiển thị "Số câu đúng" |
| **`00483C99`** | `movsx eax, [48637A]` | `mov eax, 0xXX` | Tính toán lại "Số câu sai" |

---

## 🧮 Bảng quy đổi Điểm -> Mã Hex (Cho 80 câu)

Thay `XX` ở bảng trên bằng giá trị Hex tương ứng với số điểm bạn muốn:

| Điểm mong muốn | Số câu đúng | Mã Hex (XX) |
| :--- | :--- | :--- |
| **10.0** | 80 câu | **`50`** |
| **9.75** | 78 câu | **`4E`** |
| **9.0** | 72 câu | **`48`** |
| **8.5** | 68 câu | **`44`** |
| **8.0** | 64 câu | **`40`** |

---

## 🚀 Các bước thực hiện (Cheat Sheet)

1. **Load:** Mở `Tin2CN.exe` bằng x32dbg.
2. **Select Module:** Nhấn `Alt + E` -> Chọn `Tin2CN.exe`.
3. **Patch:** Nhấn `Ctrl + G` đến từng địa chỉ ở bảng trên. Nhấn **Space** để sửa lệnh.
   * *Lưu ý:* Luôn tích chọn **"Fill with NOP's"** và sử dụng **XEDParse**.
4. **Finalize:** Nhấn `Ctrl + P` -> **Patch File** -> Lưu thành file `.exe` mới.

---

## ⚠️ Disclaimer
Tài liệu này chỉ phục vụ mục đích nghiên cứu học thuật về Reverse Engineering. Mọi hành vi sử dụng vào mục đích gian lận thi cử là vi phạm quy định và người dùng phải tự chịu trách nhiệm.

---
*Created by Minh - 2026*
