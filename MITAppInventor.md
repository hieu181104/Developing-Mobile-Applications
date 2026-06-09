# BÀI TẬP 1 - VIẾT PHẦN MỀM TRÊN CÔNG CỤ MIT APP INVENTOR
> Họ và tên: Nguyễn Trung Hiếu

> MSSV: K225480106019

---

# YÊU CẦU BÀI TẬP
Viết phần mềm trên công cụ Mit App inventor (tập trung vào quy trình tạo ra phần mềm). 

App có 3 screen:
- about về bản thân + nút gọi sang 2 screen còn lại
- giải 1 bài toán đơn giản
- sử dụng webview: hiển thị 1 trang web có sẵn, hỗ trợ giao diện điện thoại

Mô tả: thanh công cụ có gì? kéo thả + thay đổi thuộc tính: làm ntn, để làm gì?

Block: 
- mô tả bản chất việc kéo thả block ntn?
- ưu điểm gì so với viết code? nhược điểm?
- copy paste block ? (backpack)

---

# MỤC TIÊU
Xây dựng một ứng dụng di động đa màn hình bằng nền tảng MIT App Inventor với các chức năng chính sau:

- Screen 1 (Giới thiệu bản thân): Hiển thị thông tin bản thân và chứa các nút điều hướng gọi sang 2 màn hình còn lại.
- Screen 2 (Giải toán): Chứa giao diện và logic để giải một bài toán đơn giản.
- Screen 3 (WebView): Sử dụng component WebView để hiển thị một trang web có sẵn, hỗ trợ giao diện di động.

---

# GIỚI THIỆU CÔNG CỤ MIT APP INVENTOR


# BẢN CHẤT CỦA BLOCK & CÔNG CỤ BACKPACK
## 1. Bản chất của việc kéo thả Block là gì?
Bản chất của việc kéo thả block chính là Lập trình trực quan (Visual Programming). Đằng sau mỗi khối hình (Block) nhiều màu sắc thực chất là một đoạn mã nguồn (thường là Java hoặc JavaScript) đã được đóng gói sẵn. Thay vì phải gõ từng ký tự và nhớ cú pháp (Syntax), bạn chỉ cần lắp ghép các khối logic lại với nhau như chơi Lego. Nếu hai khối không hợp lệ về mặt logic (ví dụ: gắn một chuỗi chữ vào phép tính cộng), chúng sẽ không khớp được với nhau.

## 2. Ưu điểm và Nhược điểm so với viết code truyền thống

| Tiêu chí | Lập trình kéo thả (Blocks) | Viết code truyền thống |
| --- | --- | --- |
| Ưu điểm | Dễ học, dễ tiếp cận: Không lo bị sai cú pháp (thiếu dấu ;, dấu {}). Nhìn vào màu sắc và hình dáng là biết chức năng (vòng lặp, điều kiện, biến).Tạo ra sản phẩm mẫu cực kỳ nhanh. | Thao tác sâu vào phần cứng, tối ưu hiệu năng tốt. Khi ứng dụng lên tới hàng ngàn dòng code, đọc text dễ hơn nhìn ma trận blocks. Dễ tìm thư viện có sẵn bên ngoài. |
| Nhược điểm | Bị giới hạn tính năng: Chỉ làm được những gì nền tảng cung cấp sẵn. Rối mắt khi dự án lớn: Quá nhiều block đan xen sẽ cực kỳ khó quản lý và sửa lỗi (Debug). Thường nặng và chậm hơn code thuần. | Khó học: Đòi hỏi tư duy logic cao và thời gian làm quen với cú pháp phức tạp. Một lỗi chính tả nhỏ có thể làm sập cả hệ thống. |

## 3. Tính năng Copy - Paste Block bằng chiếc ba lô (Backpack)
Ba lô (Backpack) là biểu tượng hình chiếc ba lô nằm ở góc trên cùng bên phải của khu vực làm việc (Viewer) trong màn hình Blocks.

Cách hoạt động: 
- Khi bạn có một cụm block logic đã viết xong ở Screen này và muốn dùng lại ở Screen khác, bạn chỉ cần giữ chuột và kéo cụm block đó thả vào biểu tượng chiếc ba lô. Ba lô sẽ mở ra và "nuốt" block đó vào trong để lưu trữ.
- Khi sang Screen mới, bạn bấm click vào biểu tượng chiếc ba lô, một danh sách các block đã copy sẽ hiện ra, bạn chỉ cần kéo block đó ra ngoài màn hình để sử dụng lại.

Ý nghĩa: Đây chính là tính năng Sao chép - Dán (Copy - Paste) mã nguồn, giúp tiết kiệm thời gian, tăng hiệu suất làm việc và tái sử dụng code (Code reusability) giữa các màn hình khác nhau trong ứng dụng.
