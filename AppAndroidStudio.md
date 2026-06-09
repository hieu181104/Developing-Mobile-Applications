# BÀI TẬP 2 - VIẾT APP SỬ DỤNG ANDROID STUDIO

> Họ và tên: Nguyễn Trung Hiếu

> MSSV: K225480106019

---

# YÊU CẦU BÀI TẬP

####  Lý thuyết & Code mẫu cơ bản: Trả lời toàn bộ câu hỏi về AndroidManifest.xml, Vòng đời Activity (onCreate), Check quyền Runtime, Quản lý tài nguyên tránh hardcode (Location/Language/Theme), Layout (LinearLayout/Gravity), và xử lý Sự kiện (Click Event).

#### APP 1 - Ứng dụng Offline với Assets: Xây dựng một ứng dụng sử dụng dữ liệu chuẩn bị trước trong thư mục assets. Tự định nghĩa cấu trúc dữ liệu, thuật toán xử lý và giao diện hiển thị.

#### APP 2 - Ứng dụng đa màn hình:

- Activity 1 (About me): Hiển thị thông tin sinh viên và nút chuyển hướng.

- Activity 2 (Giải toán & Gọi API): Giải một bài toán (ví dụ: Phương trình bậc 2), sau đó POST kết quả dạng JSON lên API hệ thống.

- Activity 3 (WebView): Nhúng trang web theo đúng cấu trúc https://k58kmt.tdh.io.vn?masv=K225480106019.

---

# LÝ THUYẾT
## 1. AndroidManifest.xml là gì và Khai báo quyền.
Là file cấu hình bắt buộc của mọi ứng dụng Android. Nó cung cấp thông tin thiết yếu về ứng dụng cho hệ điều hành Android (như tên gói, các thành phần Activity/Service, quyền truy cập, phiên bản SDK tối thiểu...).

Khai báo quyền (Permission): Để ứng dụng thực hiện các hành động đặc biệt (như vào Internet, đọc bộ nhớ), ta khai báo trong thẻ `<uses-permission>`.

## 2. Vòng đời của một ứng dụng Android và Tại sao code tự sinh sau khi tạo 1 project có sẵn hàm onCreate.

Một ứng dụng Android hoạt động theo vòng đời (Lifecycle).

Các hàm quan trọng gồm:
- onCreate()
- onStart()
- onResume()
- onPause()
- onStop()
- onDestroy()

### Tại sao có sẵn hàm onCreate? 
Vì onCreate() là điểm khởi đầu (Entry Point) của một Activity. Khi hệ thống bắt đầu tạo Activity, hàm này sẽ được gọi đầu tiên. Tại đây, lập trình viên sẽ thiết lập giao diện (setContentView), khởi tạo các biến, gán sự kiện cho nút bấm. Nếu không có onCreate, Activity sẽ không có giao diện và không thể hoạt động.

## 3. Kiểm tra quyền trong Java
Từ Android 6.0 (API 23), các quyền nguy hiểm (như Camera, Vị trí) phải được người dùng cho phép khi đang chạy ứng dụng.

### Code minh họa check quyền:
```
if (ContextCompat.checkSelfPermission(MainActivity.this, Manifest.permission.ACCESS_FINE_LOCATION) 
        != PackageManager.PERMISSION_GRANTED) {
    // Nếu chưa có quyền, tiến hành yêu cầu cấp quyền
    ActivityCompat.requestPermissions(MainActivity.this, 
            new String[]{Manifest.permission.ACCESS_FINE_LOCATION}, 101);
} else {
    // Đã có quyền, thực hiện hành động tương ứng
    doSomethingWithLocation();
}
```

### Ý nghĩa: Bảo vệ quyền riêng tư của người dùng. Người dùng có quyền từ chối hoặc đồng ý cấp quyền ngay khi app cần sử dụng tính năng đó thay vì đồng ý mù quáng lúc cài đặt.

## 4. Quản lý tài nguyên Giao diện (res/layout) & Tham chiếu

Cú pháp tham chiếu giá trị trong XML: @string/tên_key hoặc @color/tên_màu.

Cú pháp tham chiếu trong code Java: R.string.tên_key.

### Ưu điểm: Tách biệt tầng dữ liệu (Text/Color) khỏi tầng giao diện (Layout). Dễ bảo trì, sửa một nơi - đổi toàn bộ app.

### Hỗ trợ tự động của OS (Location, Language, Theme): 
Khi ta tạo các thư mục tài nguyên tương ứng (Ví dụ: values-vi cho tiếng Việt, values-en cho tiếng Anh, values-night cho Dark Mode). Hệ điều hành sẽ tự động phát hiện cấu hình máy của người dùng để load đúng file tương ứng mà không cần code logic kiểm tra.

Lợi ích: Giúp ứng dụng dễ dàng Đa ngôn ngữ hóa (Localization) và hỗ trợ chế độ tối (Dark mode) một cách mượt mà, chuyên nghiệp.

## 5. Đối tượng chứa (ViewGroup) - LinearLayout & Gravity
### LinearLayout: 
Gom các đối tượng con nằm kề nhau theo chiều dọc (android:orientation="vertical") hoặc chiều ngang (android:orientation="horizontal").

### Gravity: 
- android:gravity: Sắp xếp các nội dung bên trong chính nó (ví dụ chữ bên trong Button).
- android:layout_gravity: Sắp xếp vị trí của chính đối tượng đó so với ViewGroup cha.

## 6. Code tương tác Layout tránh hardcode chữ
Để hiển thị text động theo thiết lập ngôn ngữ của máy:
```
// Thay vì hardcode: textView.setText("Xin chào");
// Hãy sử dụng:
textView.setText(getString(R.string.hello_text));
```

## 7. Xử lý Sự kiện Click (2 Cách viết)
Để khi Click vào nút bấm sẽ thực thi một đoạn code, ta có 2 cách phổ biến trên Java:

### Cách 1: Sử dụng Anonymous Inner Class (Khuyên dùng)

```
Button btn = findViewById(R.id.myButton);
btn.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // Đoạn code xử lý tại đây
        Toast.makeText(MainActivity.this, "Đã click cách 1!", Toast.LENGTH_SHORT).show();
    }
});
```

### Cách 2: Khai báo thuộc tính android:onClick trong file XML

Trong XML: <Button android:id="@+id/myButton" android:onClick="myButtonClickAction" ... />

Trong Java viết hàm trùng tên công khai:

```
public void myButtonClickAction(View v) {
    Toast.makeText(this, "Đã click cách 2 từ XML!", Toast.LENGTH_SHORT).show();
}
```
## 8. Truy cập file trong assets và lợi ích của việc app có sẵn các files
Ví dụ đọc một file:

```
InputStream inputStream =
        getAssets().open("data.json");
```

Ý nghĩa: Cho phép ứng dụng truy cập dữ liệu đã đóng gói sẵn trong app.

### Lợi ích của việc app có sẵn các files (kể cả offline)
- Ứng dụng có thể hoạt động kể cả khi không có Internet.
- Dữ liệu luôn sẵn trong ứng dụng

---

# TẠO APP 1
## 1. Ý tưởng
ỨNG DỤNG TRA CỨU ĐIỀU LUẬT GIAO THÔNG (OFFLINE - ASSETS)

- Vấn đề: Người tham gia giao thông cần tra cứu nhanh các lỗi vi phạm và mức phạt kể cả khi điện thoại không có kết nối Internet (mất mạng, đi vùng sâu vùng xa).

- Giải pháp: Xây dựng ứng dụng "Tra Cứu Lỗi Giao Thông Offline". Dữ liệu được biên soạn sẵn dưới dạng file JSON và lưu trong thư mục assets.

## 2. Đặc thù dữ liệu và Thuật toán xử lý

### Đặc thù dữ liệu: 
File traffic_rules.json chứa một mảng các đối tượng, gồm: id, ten_loi (Tên lỗi vi phạm), muc_phat (Số tiền phạt), và loai_xe (Xe máy/Ô tô).

### Thuật toán xử lý:
Khi người dùng nhập từ khóa vào ô tìm kiếm, ứng dụng dùng thuật toán Tìm kiếm tuyến tính (Linear Search) kết hợp hàm contains() để lọc ra các lỗi vi phạm trùng khớp với từ khóa, sau đó cập nhật lên giao diện.

### Đối tượng hiển thị: 
Dùng RecyclerView kết hợp CardView để hiển thị danh sách lỗi vi phạm một cách trực quan, hiện đại.

## 3. Xây dựng ứng dụng
### Bước 1: Tạo project mới
Chọn New Project => Empty Views Activity

<img width="3071" height="1733" alt="image" src="https://github.com/user-attachments/assets/d8082a53-0733-479b-99a5-a68f2f7d535c" />

### Bước 2: Tạo thư mục assets và file dữ liệu JSON
Theo đề bài, APP 1 cần đọc dữ liệu chuẩn bị trước nằm trong thư mục assets.

- Ở cột cấu trúc thư mục bên trái (Project), tìm đến thư mục main (đường dẫn: APP1 > app > src > main).
- Nhấp chuột phải vào thư mục main -> chọn New -> chọn Folder (hoặc Directory) -> chọn assets
- Bấm Finish ở bảng hiện ra. Lúc này, dưới thư mục main sẽ xuất hiện một thư mục mới tên là assets.
- Nhấp chuột phải vào thư mục assets vừa tạo -> chọn New -> chọn File. Đặt tên file là traffic_rules.json.

<img width="3071" height="1812" alt="image" src="https://github.com/user-attachments/assets/29d1b9ff-b827-484a-9374-96a27e7bc77f" />

### Bước 3: Thiết kế Giao diện (File activity_main.xml)
Giao diện gồm: 1 ô nhập để tìm kiếm (EditText), 1 nút bấm (Button) và 1 vùng hiển thị kết quả dạng danh sách hoặc văn bản

<img width="3071" height="1825" alt="image" src="https://github.com/user-attachments/assets/c87baed6-4ad4-4c43-90ee-962c38245080" />

### Bước 4: Viết logic xử lý dữ liệu
Vào file MainActivity.java. Viết code đọc file JSON từ thư mục assets và thực hiện thuật toán tìm kiếm tuyến tính khi người dùng bấm nút.

<img width="3071" height="1819" alt="image" src="https://github.com/user-attachments/assets/92abac5e-7dab-49f6-981f-b6dd8608c6ae" />

### Bước 5: Khai báo chuỗi vào file strings.xml

<img width="3071" height="1816" alt="image" src="https://github.com/user-attachments/assets/1a52bcbc-6a08-4088-a7ad-deda9ed0d8f7" />

## 4. Kiểm thử

### Màn hình chính hiển thị danh sách các lỗi giao thông:

<img width="3071" height="1825" alt="image" src="https://github.com/user-attachments/assets/75d8469b-4d7a-4831-b005-2db42eeb585a" />

### Tra cứu: "Vượt đèn đỏ"

<img width="3071" height="1820" alt="image" src="https://github.com/user-attachments/assets/ef12cab3-3e28-4858-88d4-8db27037759c" />

---



