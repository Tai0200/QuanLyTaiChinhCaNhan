# Quản Lý Tài Chính Cá Nhân (Personal Finance Management)

Dự án web ứng dụng chuyên dùng để quản lý tài chính, theo dõi thu chi cá nhân hàng ngày. Giúp người dùng ghi chép lại biến động số dư, phân tích thói quen tiêu dùng và hiển thị báo cáo thống kê trực quan qua các biểu đồ.

## 🚀 Công Nghệ Sử Dụng (Tech Stack)

*   **Ngôn ngữ lập trình:** Java (JSP / Servlet)
*   **Giao diện người dùng (Frontend):** HTML, CSS, JavaScript
*   **Thư viện Frontend:** [Chart.js](https://www.chartjs.org/) (Sử dụng biểu đồ thống kê)
*   **Cơ sở dữ liệu:** MySQL
*   **Thư viện Backend:** 
    *   JDBC (Kết nối cơ sở dữ liệu)
    *   Jackson (Parse và xử lý định dạng JSON cho API)
    *   BCrypt (Mã hóa mật khẩu người dùng ở mức bảo mật cao)
*   **IDE khuyên dùng:** Eclipse / Spring Tool Suite (STS)
*   **Server / Máy chủ ứng dụng:** Apache Tomcat (Phiên bản tương thích với Jakarta EE / Java EE)

## 📁 Cấu trúc thư mục của dự án

```text
├── database/                   # Chứa file script SQL (.sql) để import cấu trúc và dữ liệu mẫu vào MySQL
├── QuanLyTaiChinhCaNhan/       # Thư mục mã nguồn chính của web app (Java Dynamic Web Project)
│   ├── build/                  # Các file bytecode .class sau khi biên dịch
│   └── src/
│       ├── main/java/          # Mã nguồn Java (Controllers, Models, DAOs, helper)
│       └── main/webapp/        # Mã nguồn Frontend (JSP, HTML, CSS, JS, Image) và cấu hình WEB-INF
├── Servers/                    # Cấu hình máy chủ Tomcat sinh ra từ IDE (Eclipse)
└── .gitignore                  # Các file/thư mục không đưa lên Git
```

## ⚙️ Các Tính Năng Chính (Features)

1.  **Quản lý Tài Khoản:** Đăng ký, đăng nhập và bảo mật mật khẩu an toàn với BCrypt.
2.  **Quản lý Thu - Chi (Incomes/Expenses):** Thêm, sửa, xóa các giao dịch thu chi cá nhân.
3.  **Quản lý Danh Mục (Categories):** Cấu hình các danh mục thu, chi để dễ dàng phân bổ dòng tiền.
4.  **Bảng Điều Khiển (Dashboard) & Báo cáo:** Cung cấp biểu đồ thống kê trực quan thể hiện tổng quan số tiền đã chi, số tiền kiếm được theo các mốc thời gian (hiện tại, quá khứ, tương lai dự kiến).
5.  **Cập nhật dữ liệu thời gian thực:** Kết hợp JavaScript và AJAX API để tải và hiển thị lại biểu đồ mà không cần load lại toàn bộ trang.

## 🛠️ Hướng Dẫn Cài Đặt (Installation & Setup)

Để chạy dự án này trên môi trường Local, vui lòng làm theo các bước dưới đây:

### Bước 1: Clone dự án
```bash
git clone <đường-dẫn-repo-của-bạn>
cd QuanLyTaiChinhCaNhan
```

### Bước 2: Khởi tạo Cơ sở dữ liệu (Database)
1. Cài đặt và mở **XAMPP**, **WAMP** hoặc **MySQL Workbench**.
2. Tạo một Database mới trong MySQL với tên: `quanlychitieu`
3. Tìm đến thư mục `database/` trong dự án. Import file script `quanlychitieu.sql` vào cơ sở dữ liệu vừa tạo để thiết lập các bảng và dữ liệu có sẵn.

### Bước 3: Import dự án vào Eclipse
1. Mở Eclipse IDE.
2. Chọn **File** -> **Import...**
3. Tìm mở mục **General** -> Chọn **Existing Projects into Workspace** -> **Next**.
4. Browse tới thư mục gốc chứa source code dự án (`QuanLyTaiChinhCaNhan`) và nhấn **Finish**.

### Bước 4: Cấu hình kết nối Database (Nếu cần)
Mở file `src/main/java/com/handle/dao/ConnectDB.java` và kiểm tra cấu hình. Nếu cấu hình MySQL của bạn khác mặc định, hãy cập nhật lại:
```java
private static final String URL = "jdbc:mysql://localhost:3306/quanlychitieu";
private static final String USER = "root";       // Thay đổi username nếu cần
private static final String PASSWORD = "";       // Nhập mật khẩu database của bạn
```
*(Lưu ý: Bạn cũng cần đảm bảo thư viện Connector J (JDBC cho MySQL) đã được thêm trong Build Path của dự án, hoặc chép nó vào lib của Tomcat).*

### Bước 5: Chạy ứng dụng
1. Click chuột phải vào Project `QuanLyTaiChinhCaNhan` trong tab Project Explorer.
2. Chọn **Run As** -> **Run on Server**.
3. Chọn máy chủ Apache Tomcat bạn đã cài và hoàn thành.
4. Truy cập giao diện tại trình duyệt: `http://localhost:8080/QuanLyTaiChinhCaNhan/index`
