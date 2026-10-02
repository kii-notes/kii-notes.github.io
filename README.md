# 📚 KII Notes — kii-notes.github.io

> Không gian xuất bản tĩnh chuyên sâu về khảo cứu văn bản, đính chính dị bản sách học thuật và ghi chép tri thức số.

Dự án được xây dựng trên nền tảng **Python MkDocs** kết hợp theme **Material for MkDocs**, tự động hóa quy trình kiểm thử và xuất bản lên **GitHub Pages** thông qua **GitHub Actions**.

---

## 📂 Cấu Trúc Dự Án

```text
kii-notes.github.io/
├── .github/
│   └── workflows/
│       └── deploy.yml          # Pipeline GitHub Actions tự động build & deploy Pages
├── docs/                       # Toàn bộ nội dung bài viết định dạng Markdown
│   ├── index.md                # Trang chủ blog / Lời ngỏ
│   ├── khao-cuu/               # Chuyên mục khảo cứu văn bản học thuật
│   │   └── dao-mau-vn/
│   │       ├── index.md        # Giới thiệu chuỗi bài khảo cứu Đạo Mẫu Việt Nam
│   │       └── ky-01.md        # Bài mẫu khảo dị, bảng đối chiếu 3 cột & footnotes
│   └── ky-thuat/               # Chuyên mục ghi chép kỹ thuật & Second Brain
│       └── index.md
├── requirements.txt            # Danh sách gói thư viện Python (mkdocs-material, pymdown)
├── mkdocs.yml                  # Toàn bộ cấu hình giao diện, navigation, extensions
├── .gitignore                  # Bỏ qua venv, site/, cache và file nhạy cảm
└── README.md                   # Sổ tay hướng dẫn vận hành & triển khai
```

---

## 🚀 Hướng Dẫn Vận Hành Tại Local (Xem Trước Trang Web)

### Bước 1: Khởi tạo và kích hoạt môi trường ảo Python

Mở Terminal tại thư mục `kii-notes.github.io`:

```powershell
# Tạo môi trường ảo .venv
python -m venv .venv

# Kích hoạt trên Windows PowerShell:
.\.venv\Scripts\Activate.ps1

# (Hoặc nếu dùng Command Prompt):
# .\.venv\Scripts\activate.bat

# (Hoặc nếu dùng Linux/macOS):
# source .venv/bin/activate
```

> [!TIP]
> Nếu PowerShell báo lỗi `Execution_Policies` khi kích hoạt venv, hãy chạy:
> ```powershell
> Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
> ```

### Bước 2: Cài đặt các thư viện cần thiết

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Bước 3: Chạy máy chủ xem trước (Hot-reloading Server)

```bash
mkdocs serve
```

Mở trình duyệt và truy cập: **`http://127.0.0.1:8000/`**  
Mỗi khi bạn chỉnh sửa hoặc lưu bất kỳ file nào trong thư mục `docs/` hoặc sửa `mkdocs.yml`, trình duyệt sẽ tự động cập nhật ngay lập tức.

---

## 🌐 Hướng Dẫn Thiết Lập Git & Push Lên GitHub Lần Đầu

### Bước 1: Khởi tạo Git Repo & Commit dữ liệu ban đầu

Tại thư mục `kii-notes.github.io`:

```bash
git init
git branch -M main
git add .
git commit -m "feat: initialize kii-notes site with MkDocs Material"
```

### Bước 2: Cấu hình Remote & Đẩy code lên GitHub

Repo mục tiêu: `https://github.com/kii-notes/kii-notes.github.io.git`

#### Cách 1: Sử dụng GitHub Personal Access Token (PAT)
Bạn có thể nhúng trực tiếp PAT vào lệnh push lần đầu hoặc thiết lập remote:

```powershell
# Cấu hình remote với PAT (thay <YOUR_GITHUB_PAT> bằng token của bạn):
git remote add origin https://<YOUR_GITHUB_PAT>@github.com/kii-notes/kii-notes.github.io.git

# Đẩy mã nguồn lên nhánh main:
git push -u origin main
```

> [!NOTE]
> Sau khi push thành công, nếu muốn bảo mật không để lộ PAT trong URL của Git remote, bạn có thể chuyển URL về dạng chuẩn:
> ```bash
> git remote set-url origin https://github.com/kii-notes/kii-notes.github.io.git
> ```
> Khi đó Git Credential Manager trên Windows sẽ tự động lưu thông tin xác thực.

#### Cách 2: Sử dụng SSH (Nếu máy bạn đã cấu hình SSH Key)
```bash
git remote add origin git@github.com:kii-notes/kii-notes.github.io.git
git push -u origin main
```

---

## ⚙️ Kích Hoạt GitHub Pages (Bắt Buộc Trên GitHub Repo)

Để GitHub Actions có quyền triển khai và website hoạt động tại `https://kii-notes.github.io/`:

1. Truy cập vào Repo trên trình duyệt:  
   👉 **`https://github.com/kii-notes/kii-notes.github.io/settings/pages`**
2. Tại mục **Build and deployment**:
   - Ở trường **Source**: Nhấp chọn **`GitHub Actions`** (mặc định thường là *Deploy from a branch*).
3. Sau khi chọn `GitHub Actions`, quy trình CI/CD trong file `.github/workflows/deploy.yml` sẽ tự động đón nhận các commit mới trên nhánh `main`, tiến hành build trang và xuất bản tự động.
4. Kiểm tra tiến trình build tại tab **Actions** của Repo:  
   👉 `https://github.com/kii-notes/kii-notes.github.io/actions`

---

## 🎨 Điểm Nổi Bật Về Giao Diện & Tính Năng Đã Cấu Hình

- **Giao diện Song hành Light / Dark:** Tự động phát hiện theme hệ điều hành và cung cấp nút bấm chuyển đổi thủ công nhanh (màu *Teal* & *Amber* trang nhã, dịu mắt cho văn bản học thuật).
- **Bộ phông chữ chuyên đọc dài:** Phông chữ văn bản `Literata` (tối ưu cho sách văn bản học) và phông code `JetBrains Mono`.
- **Hỗ trợ Admonitions & Callouts:** Cảnh báo (`!!! warning`), Mẹo (`!!! tip`), Ghi chú (`!!! note`), Câu hỏi (`!!! question`).
- **Chú thích học thuật (Footnotes):** Hỗ trợ cú pháp `[^1]` tự động tạo link nhảy xuống chân trang và quay ngược lại văn bản.
- **Sơ đồ Mermaid:** Hỗ trợ vẽ biểu đồ luồng tư duy, phả hệ, quy trình khảo dị trực tiếp bằng khối code `mermaid`.
- **Bảng Markdown GFM:** Hiển thị trực quan, căn lề và hỗ trợ kẻ bảng đối chiếu đa cột.
