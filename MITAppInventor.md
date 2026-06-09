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
MIT App Inventor là nền tảng lập trình trực quan được phát triển bởi MIT cho phép người dùng xây dựng ứng dụng Android bằng cách kéo thả các thành phần giao diện và lập trình bằng các khối lệnh (Blocks).

Ưu điểm:
- Dễ học và dễ sử dụng, không yêu cầu quá cao kiến thức lập trình
- Phát triển ứng dụng nhanh chóng, tiện lợi.
- Hỗ trợ kiểm thử trực tiếp trên điện thoại.
Nhược điểm:
- Hiệu năng không cao khi xây dựng ứng dụng lớn, phức tạp
- Khả năng tùy biến thấp hơn Android Studio.

---

# XÂY DỰNG PHẦN MỀM
## 1. Xây dựng Screen 1: Giới thiệu bản thân
### Bước 1: Khởi tạo dự án
- Đăng nhập MIT App Inventor bằng Google Account
- Tạo project mới : Chọn New Project => Đặt tên project => OK

<img width="3071" height="1735" alt="image" src="https://github.com/user-attachments/assets/af8bc13b-65d3-4343-b1cd-bb4de76ff2a2" />

Giao diện ban đầu sẽ hiển thị chế độ Designer cho Screen gồm các thành phần:

- Palette chứa các thành phần giao diện như: Button, Label, TextBox, Image, WebViewer
- Viewer là khu vực thiết kế giao diện ứng dụng.
- Components là danh sách các thành phần đã được thêm vào màn hình
- Properties cho phép thay đổi thuộc tính của các thành phần như: Text, Width, Height, Front Size, Background Color.

<img width="3071" height="1647" alt="image" src="https://github.com/user-attachments/assets/9ebbdc3a-7787-4df0-940d-56cb7c0e83aa" />

### Bước 2: Xây dựng giao diện
#### Đặt tiêu đề Screen
- Tại cột properties kéo xuống bên dưới tìm thuộc tính Title và điền tên tiêu đề
- Tích chọn Scrollable để cho phép màn hình cuộn xuống. 
- AlignHorizontal điền giá trị Center để căn giữa.

<img width="3066" height="1656" alt="Screenshot 2026-06-09 095825" src="https://github.com/user-attachments/assets/5a477f6a-ecdb-4dd3-aaa2-e15d3ce657d0" />

<img width="3071" height="1653" alt="Screenshot 2026-06-09 100005" src="https://github.com/user-attachments/assets/b13766d9-22de-4e3e-b275-2575d6bf4c45" />

#### Tạo khung chứa giao diện với Vertical Arrangement
Thành phần này cho phép sắp xếp các đối tượng giao diện theo chiều dọc từ trên xuống dưới. Việc sử dụng Vertical Arrangement giúp giao diện dễ quản lý hơn, đồng thời tạo sự nhất quán khi bổ sung thêm các thành phần.

<img width="3071" height="1650" alt="Screenshot 2026-06-09 100335" src="https://github.com/user-attachments/assets/58de5f64-9b08-409c-b5f5-e70aec1036cb" />

#### Thêm tiêu đề bài viết

<img width="3071" height="1654" alt="Screenshot 2026-06-09 101005" src="https://github.com/user-attachments/assets/51bc2380-c783-4e80-8ab9-e8d63178763f" />

#### Thêm ảnh đại diện

<img width="3071" height="1659" alt="Screenshot 2026-06-09 101435" src="https://github.com/user-attachments/assets/7b0bb5fd-0702-429a-9d62-5cb65436cab3" />

<img width="3071" height="1652" alt="Screenshot 2026-06-09 101832" src="https://github.com/user-attachments/assets/e49ae719-2d67-43d7-b4b4-9de0f8521b68" />

#### Thực hiện kéo thả tương tự với các label để hiển thị tên, mssv, ...
Sau khi tạo thêm các label (rename nếu cần đễ dễ quản lý) , ta thu được màn hình chứa các thông tin cơ bản:

<img width="3068" height="1654" alt="image" src="https://github.com/user-attachments/assets/69be9386-8c4c-4835-82f0-cb3990a958ec" />

### Bước 3: Tạo Button để chuyển hướng tới hai màn hình còn lại
#### Kéo button vào màn hình mobile và cấu hình 

<img width="3071" height="1653" alt="Screenshot 2026-06-09 103519" src="https://github.com/user-attachments/assets/5b822390-41d0-4fdd-b291-3b8394bea13c" />

<img width="3060" height="1650" alt="image" src="https://github.com/user-attachments/assets/280497ab-76dd-47f9-b5ae-7123d4a95481" />

#### Thêm Screen 2 và 3

<img width="3070" height="1644" alt="Screenshot 2026-06-09 104159" src="https://github.com/user-attachments/assets/4e6e15d9-97f1-4277-b7bc-b235f081c6ce" />

<img width="3069" height="1648" alt="Screenshot 2026-06-09 104332" src="https://github.com/user-attachments/assets/84a1ba0c-3dc2-45f2-9dba-0fa07308ff76" />

#### Điều hướng sang Screen 2 và 3

- Chuyển từ chế độ Designer sang chế độ Blocks
- Bấm vào Button2 ở cột danh sách bên trái, kéo khối sự kiện when Button1.Click do ra không gian làm việc.
- Mở nhóm lệnh Control (màu cam), kéo khối open another screen screenName ghép vào trong thân khối Click.
- Mở nhóm lệnh Text, kéo khối chuỗi trống " " ghép vào sau khối control và gõ chính xác chữ Screen2.
- Làm tương tự cho Button3, nhập tên màn hình đích là Screen3.

<img width="3071" height="1646" alt="Screenshot 2026-06-09 105346" src="https://github.com/user-attachments/assets/30890e6e-247f-4089-95a8-b567cbba5473" />

<img width="3071" height="1646" alt="Screenshot 2026-06-09 105526" src="https://github.com/user-attachments/assets/2e6d455f-3300-4c9b-a080-09d32e3f6087" />

<img width="3071" height="1643" alt="Screenshot 2026-06-09 105643" src="https://github.com/user-attachments/assets/11be2c92-c3b6-4657-867f-d8681f679f63" />

#### Hai khối lệnh hoàn chỉnh

<img width="3071" height="1642" alt="image" src="https://github.com/user-attachments/assets/5443c5ff-1f70-422b-8044-fddba6cc8c5a" />

---

## 2. Xây dựng Screen 2: Giải toán
### Bước 1: Xây dựng giao diện
Ý tưởng: Bài toán chuyển đổi nhiệt độ
Bài toán này cho phép người dùng nhập vào một giá trị nhiệt độ, sau đó chọn đổi từ độ C sang độ F hoặc ngược lại.
#### Thực hiện kéo thả tương tự như việc xây dựng UI cho screen 1 và cấu hình tùy ý.
Thiết kế giao diện (Designer):
- 1 Label để hiển thị tiêu đề
- 1 TextBox để người dùng nhập số nhiệt độ.
- 2 Button: Nút 1 là "Đổi sang độ F", Nút 2 là "Đổi sang độ C".
- 1 Label để hiển thị kết quả.

<img width="3071" height="1655" alt="Screenshot 2026-06-09 130119" src="https://github.com/user-attachments/assets/a93d3e2b-a941-4c38-873a-dd9f4d3250f0" />

<img width="3070" height="1651" alt="image" src="https://github.com/user-attachments/assets/82bac6bf-39da-4424-b405-92cafd5b5c25" />

### Bước 2: Xây dựng Blocks
Chuyển sang tab Blocks

Công thức toán học:
- Từ C sang F: F = C x 1.8 + 32
- Từ F sang C: C = (F-32) / 1.8 

#### Lập trình cho nút C_Button (Đổi sang độ C)
- Kéo khối `when C_Button.Click` ra
- Nhìn vào danh mục bên trái, bấm vào thành phần Result, kéo khối `set Result.Text to` thả vào trong khối `when C_Button.Click`
- Bấm vào mục Math (màu xanh dương): Kéo khối phép chia (/) gắn vào ô trống của khối set.
- Kéo khối phép trừ (-) gắn vào nhánh bên trái của khối phép chia.
- Bấm vào thành phần `TextBox1` ở cột bên trái, kéo khối `TextBox1.Text` gắn vào nhánh bên trái của khối phép trừ.
- Vào lại mục Math, kéo 2 khối số 0 ra sửa thành số 32 (gắn vào bên phải phép trừ) và số 1.8 (gắn vào bên phải phép chia).


#### Lập trình cho nút F_Button (Đổi sang độ F)
- Làm hoàn toàn tương tự bằng cách kéo khối `when F_Button.Click ra` và lắp ráp các khối toán học:
- Kéo khối `set Result.Text to`.
- Vào mục Math, kéo khối phép cộng (+) gắn vào.
- Tiếp tục vào mục Math, kéo khối phép nhân (×) gắn vào nhánh bên trái của khối phép cộng.
- Gắn khối `TextBox1.Text` vào bên trái phép nhân.
- Lấy khối số điền 1.8 gắn vào bên phải phép nhân.
- Lấy khối số điền 32 gắn vào bên phải phép cộng.

<img width="3071" height="1643" alt="image" src="https://github.com/user-attachments/assets/ba26b5df-0181-4a6e-a1f2-7a887643358d" />

---

## 3. Xây dựng Screen 3: Webview

Mục tiêu của màn hình này là biến ứng dụng thành một "trình duyệt mini" để hiển thị một trang web có sẵn. Để hỗ trợ giao diện di động tốt nhất, nên chọn các trang web có tính chất "Responsive" (tự động co giãn theo màn hình điện thoại).

### Bước 1: Xây dựng giao diện

#### Thêm nút Quay lại:
- Kéo một Button vào trên cùng màn hình.
- Đặt tên là btnBack. Đổi Text thành "Quay lại Trang chủ".
- Mục đích: Để người dùng không bị "kẹt" ở Screen 3.

#### Thêm thành phần WebViewer:

- Tại cột Palette, tìm nhóm User Interface.

- Kéo WebViewer (thường nằm ở cuối danh sách) thả vào màn hình.

#### Cấu hình quan trọng ở cột Properties:

- Height (Chiều cao): Chọn Fill Parent (để nó chiếm hết phần còn lại của màn hình).

- Width (Chiều rộng): Chọn Fill Parent.

- HomeUrl: Đây là nơi dán link trang web muốn hiển thị.

- FollowLinks: Đảm bảo ô này được Tick chọn (để khi người dùng bấm vào các link bên trong trang web, nó vẫn chạy tiếp trong app).

<img width="3069" height="1649" alt="Screenshot 2026-06-09 135200" src="https://github.com/user-attachments/assets/b6ae048c-a314-48f2-8efc-2e1edaf8fbbc" />

### Bước 2: Xây dựng Blocks
#### Đảm bảo trang web luôn load khi mở màn hình:
Mặc dù đã điền HomeUrl, nhưng để chắc chắn trang web sẽ được tải ngay khi Screen 3 xuất hiện. Lắp block sau:

- Vào Screen3 chọn: when Screen3.Initialize do
- Vào WebViewer1 chọn: call WebViewer1.GoToUrl
- Gắn một khối Text chứa link trang web vào.

#### Lập trình nút Quay lại:
- Vào btnBack chọn: when btnBack.Click do
- Vào mục Control chọn: open another screen with screenName
- Gắn khối Text điền chữ "Screen1".

<img width="3071" height="1651" alt="image" src="https://github.com/user-attachments/assets/0a20ba20-4a9f-43e2-85a1-d91c3e992cf7" />

---

# KIỂM THỬ PHẦN MỀM
## Test trực tiếp trên Điện thoại thật (IPhone)
Cách này giúp vừa sửa code trên máy tính, vừa thấy app thay đổi ngay lập tức trên điện thoại.
### Bước 1: Lên điện thoại (Android hoặc iPhone), vào cửa hàng ứng dụng (CH Play hoặc App Store) tìm và tải ứng dụng có tên: MIT App Inventor.
### Bước 2: Đảm bảo cả máy tính và điện thoại đang kết nối chung một mạng Wi-Fi.
### Bước 3: Trên giao diện trang web MIT App Inventor trên máy tính, thanh menu trên cùng => bấm vào Connect => chọn AI Companion. Lúc này màn hình máy tính sẽ hiện ra một mã QR và một đoạn mã 6 ký tự.
### Bước 4: Mở ứng dụng trên điện thoại lên: Bấm nút scan QR code để quét mã trên màn hình máy tính. Hoặc gõ 6 ký tự vào ô trống rồi bấm connect with code.

Kết quả: Đợi khoảng 5 giây, toàn bộ giao diện app 3 màn hình sẽ xuất hiện trên điện thoại.



---

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
