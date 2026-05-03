# Bài 3: CI/CD Automation với GitHub Actions

**1. Đường dẫn kho lưu trữ (Repository URL):**
https://github.com/caoduongle/mathutils

**2. Giải thích Workflow :**
- **Trigger:** Tự động kích hoạt khi có lệnh `push` hoặc `pull_request` lên nhánh `main`.
- **Build Lifecycle:** Sử dụng môi trường Ubuntu, JDK 17, thực thi lệnh `mvn clean package` để chạy Unit Test và đóng gói.
- **Upload Artifact:** Tự động lưu trữ file `.jar` sinh ra từ thư mục `target/` lên GitHub sau khi build thành công.

**3. Chứng minh khả năng Debug (Cố tình gây lỗi):**
- **Hành động:** Đã sửa sai logic hàm `max(int a, int b)` để trả về giá trị sai (`a - 100`).
- **Quan sát GitHub Actions:** Workflow bị đánh dấu FAILED (❌). Tiến trình dừng lại ở bước "Build with Maven".
- **Phân tích Execution Logs:** 
  Dựa vào log do GitHub Actions cung cấp, hệ thống báo lỗi rõ ràng: `org.opentest4j.AssertionFailedError: expected: <5> but was: <-95> at MathUtilsTest.testMax_AGreaterThanB`. Điều này chứng tỏ CI đã bắt được lỗi logic trước khi đóng gói thành công.