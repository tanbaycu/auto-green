# 🟢 GitHub Daily Contribution Bot

Dự án tự động hóa đóng góp (contributions) hàng ngày trên GitHub dành cho tác giả **tanbaycu**. Dự án sử dụng **GitHub Actions** để tự động cập nhật một file log, commit và push trở lại repo theo lịch trình hàng ngày, giúp duy trì chuỗi đóng góp màu xanh trên GitHub profile một cách hoàn toàn tự động và miễn phí.

---

## ✨ Điểm nổi bật
- **Tự động hóa hoàn toàn 100%:** Chạy trên hạ tầng đám mây của GitHub (GitHub Actions), không cần treo máy cá nhân, không tốn tài nguyên máy local.
- **Commit ngẫu nhiên tự nhiên (Anti-Bot):** Script tự động tạo một độ trễ ngẫu nhiên từ `0 đến 45 phút` trước khi commit. Nhờ vậy, khung giờ commit mỗi ngày sẽ khác nhau, trông giống như thao tác của người thật thay vì bot cố định giờ.
- **Tiện lợi & Bảo mật:** Sử dụng chính `GITHUB_TOKEN` được cấp sẵn bởi GitHub Actions để commit, không cần cấu hình Personal Access Token (PAT) hay SSH key phức tạp và kém an toàn.

---

## 🛠️ Hướng dẫn cài đặt & Cấu hình (5 bước đơn giản)

### Bước 1: Điều chỉnh Email GitHub của bạn
Mở file [.github/workflows/auto-commit.yml](file:///C:/Users/ACER/Documents/antigravity/friendly-newton/.github/workflows/auto-commit.yml) và thay thế email:
```yaml
git config --global user.email "tanbaycu@users.noreply.github.com"
```
> [!IMPORTANT]
> Thay `"tanbaycu@users.noreply.github.com"` bằng **email chính xác** liên kết với tài khoản GitHub **tanbaycu** của bạn. Nếu email này không khớp, GitHub sẽ không ghi nhận các commit này vào biểu đồ màu xanh (Contribution graph) của bạn.

---

### Bước 2: Tạo Repository mới trên GitHub
1. Truy cập [GitHub](https://github.com) và tạo một repo mới (ví dụ đặt tên là: `auto-green` hoặc bất kỳ tên nào bạn thích).
2. Hãy để trạng thái repo là **Public** (nếu để Private, bạn phải bật tùy chọn hiển thị đóng góp từ repo private trong phần cài đặt profile GitHub thì người khác mới thấy các ô màu xanh).

---

### Bước 3: Đẩy mã nguồn này lên GitHub
Trong thư mục này (`friendly-newton`), chạy các lệnh sau trong terminal để liên kết và push code lên repository mới của bạn:

```bash
# Thêm remote repository mới tạo của bạn (Thay URL dưới bằng URL repo của bạn)
git remote add origin https://github.com/tanbaycu/<tên-repo-của-bạn>.git

# Đổi tên branch chính thành main (nếu chưa phải)
git branch -M main

# Commit các file thiết lập ban đầu
git add .
git commit -m "chore: initial setup for daily contribution bot by tanbaycu"

# Đẩy code lên GitHub
git push -u origin main
```

---

### Bước 4: Cấp quyền Ghi cho GitHub Actions (Bắt buộc)
Mặc định, GitHub Actions chỉ có quyền đọc repo. Bạn cần cấp quyền ghi để script có thể push commit mới lên:
1. Vào repository của bạn trên GitHub.
2. Chọn tab **Settings** (Cài đặt) -> Chọn mục **Actions** ở menu bên trái -> Chọn **General**.
3. Cuộn xuống dưới cùng tìm mục **Workflow permissions**.
4. Chọn tùy chọn **Read and write permissions** (Quyền đọc và ghi).
5. Nhấn **Save** để lưu lại.

---

### Bước 5: Chạy thử nghiệm thủ công
Để kiểm tra xem hệ thống đã hoạt động chính xác chưa mà không cần đợi đến giờ hẹn:
1. Vào tab **Actions** trên repository GitHub của bạn.
2. Chọn workflow **Auto Commit - Daily Contribution Bot** ở danh sách bên trái.
3. Nhấp vào nút **Run workflow** -> Chọn branch `main` -> Nhấn nút **Run workflow** màu xanh.
4. Đợi vài phút để workflow chạy. Sau khi hoàn thành, hãy kiểm tra lại file `LAST_UPDATED.txt` trên repo xem đã được cập nhật nội dung mới chưa nhé!

---

## 📅 Lịch trình hoạt động
- Workflow được lên lịch chạy vào lúc **23:45 UTC** hàng ngày (tức là khoảng **06:45 sáng giờ Việt Nam**).
- Cộng thêm thời gian delay ngẫu nhiên (từ 0 đến 45 phút), commit thực tế sẽ xuất hiện trên GitHub của bạn trong khoảng từ **06:45 AM đến 07:30 AM** giờ Việt Nam.

---

*Dự án được thiết lập cho tác giả **tanbaycu**.*
