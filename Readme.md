A3_231A290111 – Thiết kế giao diện với XML Layout & Tài nguyên

1. Mô tả dự án (Project Description)
   Dự án A3_231A290111 là ứng dụng Android minh họa màn hình Đăng nhập của "Cổng thực hành LTDD" kết hợp hiển thị thẻ hồ sơ sinh viên.   
   Mục tiêu cốt lõi của dự án là thực hành tách biệt phần giao diện (XML) khỏi phần xử lý logic (Java), quản lý tập trung các tài nguyên hệ thống (strings, colors, dimens, drawable), đồng thời đối chiếu hai phương pháp dựng giao diện phổ biến trong Android: sử dụng LinearLayout lồng nhau và ConstraintLayout phẳng. Bên cạnh đó, ứng dụng còn áp dụng cơ chế Resource Qualifiers để tự động thích ứng bố cục khi xoay ngang màn hình (layout-land), dùng trên máy tính bảng (layout-sw600dp) hoặc chuyển sang chế độ tối (values-night)
2. Công nghệ sử dụng (Technologies)
   Ngôn ngữ lập trình: Java (xử lý logic sự kiện, chuyển màn hình, ghi log) & XML (thiết kế giao diện và tài nguyên).   
   Môi trường phát triển (IDE): Android Studio.   
   Android SDK: Minimum SDK API 24 (Android 7.0 Nougat).  
   Thư viện giao diện (UI Components):
      Material Design 3 (com.google.android.material): Sử dụng TextInputLayout (OutlinedBox), TextInputEditText, MaterialCardView, Button (Filled, Outlined, TextButton), và Snackbar.  
      AndroidX Core & AppCompat: AppCompatActivity, EdgeToEdge, WindowInsetsCompat.   
      AndroidX ConstraintLayout: Xây dựng giao diện phẳng với Guideline và Chain. 
      Quản lý phiên bản: Git & GitHub.   
3. Cấu trúc dự án (Project Structure)
   app/src/main/
   ├── AndroidManifest.xml                  # Khai báo các Activity của ứng dụng
   ├── java/vn/edu/vhu/ltdd/a3layout/
   │   ├── MainActivity.java                # Xử lý sự kiện màn hình chính, Snackbar, Logcat và chuyển Activity
   │   └── ConstraintDemoActivity.java      # Activity hiển thị bản dựng bằng ConstraintLayout
   └── res/
   ├── drawable/
   │   ├── bg_header.xml                # Shape nền gradient chuyển màu, bo tròn 2 góc dưới 24dp
   │   ├── bg_avatar.xml                # Shape hình tròn (oval) cho ảnh đại diện có viền trắng 4dp
   │   └── bg_stat.xml                  # Shape bo góc 12dp cho 2 ô thống kê kết quả Lab
   ├── layout/
   │   ├── activity_main.xml            # Giao diện dọc chính dựng bằng ScrollView + LinearLayout + FrameLayout
   │   ├── view_profile_card.xml        # Thẻ hồ sơ sinh viên tách riêng để tái sử dụng qua thẻ <include>
   │   └── activity_constraint_demo.xml # Giao diện form đăng nhập dựng phẳng bằng ConstraintLayout
   ├── layout-land/
   │   └── activity_main.xml            # Giao diện bố cục 2 cột dành riêng cho màn hình ngang (Landscape)
   ├── layout-sw600dp/
   │   └── activity_main.xml            # Giao diện bố cục 2 cột tối ưu cho máy tính bảng (Bài nâng cao NC2)
   ├── values/
   │   ├── colors.xml                   # Bảng màu chuẩn chế độ sáng (Light Mode)
   │   ├── dimens.xml                   # Thang khoảng cách dùng chung (space_sm, space_md, space_lg, space_xl)
   │   ├── strings.xml                  # Toàn bộ chuỗi văn bản và thông tin cá nhân sinh viên
   │   └── themes.xml                   # Cấu hình giao diện Material 3
   └── values-night/
   └── colors.xml                   # Bảng màu tối ưu cho chế độ tối - Dark Mode (Bài nâng cao NC1)
4. Hướng dẫn cài đặt và chạy dự án (Setup Instructions)
   Yêu cầu hệ thống:
   Đã cài đặt Android Studio (khuyến nghị bản Iguana / Jellyfish / Koala trở lên).   
   Đã cấu hình JDK 17 (tích hợp sẵn trong Android Studio) và Android SDK (API 24+).
   Có sẵn máy ảo Android (AVD Emulator) hoặc thiết bị Android thật bật chế độ USB Debugging.  
5. Các tính năng có trong dự án (Features)
   Thiết kế Header chồng lớp với FrameLayout & Custom XML Drawable: Khối ảnh bìa cao 150dp dùng nền chuyển màu (gradient) bo góc dưới 24dp, kết hợp ảnh đại diện hình tròn 92dp xếp chồng chính xác lên mép dưới ảnh bìa mà không cần dùng file ảnh bitmap bên ngoài.   
   Biểu mẫu đăng nhập chuẩn Material Design 3:
   Ô nhập MSSV giới hạn bàn phím số (inputType="number").  
   Ô nhập Mật khẩu tích hợp sẵn nút ẩn/hiện mật khẩu (app:endIconMode="password_toggle").  
   Căn chỉnh linh hoạt hàng CheckBox "Ghi nhớ đăng nhập" và nút "Quên mật khẩu?" bằng thẻ <Space> kết hợp layout_weight="1".   
   Thẻ hồ sơ sinh viên tái sử dụng (<include>): Hiển thị đầy đủ thông tin sinh viên (Họ tên, MSSV, Lớp, Email VHU) và 2 ô thống kê (Lab đã nộp, Điểm TB lab) chia đôi đều chiều ngang bằng 0dp + layout_weight="1", được đóng gói trong view_profile_card.xml để nhúng vào nhiều màn hình khác nhau.  
   Tương tác sự kiện & Phản hồi người dùng:
   Bấm nút ĐĂNG NHẬP hiển thị thanh thông báo Snackbar ở đáy màn hình, tự động kiểm tra trạng thái tích chọn của ô "Ghi nhớ đăng nhập" để hiển thị nội dung tương ứng.
   Ghi log tự động vào Logcat (TAG = "A3_231A290111") để theo dõi thư mục layout nào (res/layout hay res/layout-land) đang được hệ thống nạp khi chạy và khi xoay màn hình.   
   Chuyển đổi và đối chiếu bản dựng ConstraintLayout: Cho phép mở màn hình ConstraintDemoActivity trực tiếp từ màn hình chính để kiểm nghiệm cách dựng form phẳng 1 tầng duy nhất với Guideline và chuỗi ngang (Horizontal Chain).  
   Đa cấu hình giao diện (Responsive & Adaptive UI):
   Màn hình ngang (res/layout-land): Tự động chuyển từ bố cục 1 cột dọc sang bố cục 2 cột (cột trái: Header + Thẻ hồ sơ, cột phải: Form đăng nhập) khi xoay ngang thiết bị mà không cần sửa đổi mã Java.
   Hỗ trợ Máy tính bảng (res/layout-sw600dp - Bài nâng cao NC2): Tự động hiển thị giao diện 2 cột trên các thiết bị có bề rộng tối thiểu từ 600dp trở lên.  
   Hỗ trợ Chế độ tối (res/values-night - Bài nâng cao NC1): Tự động chuyển đổi toàn bộ bảng màu ứng dụng sang tông màu tối dịu mắt khi người dùng bật Dark Theme trên hệ thống.  
