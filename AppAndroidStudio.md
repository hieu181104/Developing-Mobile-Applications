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
## 8. 


