# Cấu hình TMUX

Cấu hình Tmux theo chuẩn XDG (`~/.config/tmux/`), sử dụng bảng màu Melange đồng bộ với Neovim, tích hợp điều hướng trực tiếp giữa các cửa sổ và hệ thống cửa sổ popup chức năng.

---

## 1. Phím Prefix

Phím kích hoạt lệnh (Prefix): `Ctrl + a` (thay thế cho mặc định `Ctrl + b`).

---

## 2. Điều hướng giữa Tmux và Neovim

Không cần bấm phím Prefix. Sử dụng trực tiếp các tổ hợp phím sau để di chuyển giữa các cửa sổ Neovim và các pane Tmux:

| Phím tắt | Hướng di chuyển |
| :--- | :--- |
| `Ctrl + h` | Sang trái |
| `Ctrl + j` | Xuống dưới |
| `Ctrl + k` | Lên trên |
| `Ctrl + l` | Sang phải |

Khi con trỏ chạm cạnh của một cửa sổ Neovim, lệnh sẽ tự động chuyển tiêu điểm sang pane Tmux liền kề.

---

## 3. Thao tác Pane

| Phím tắt | Chức năng |
| :--- | :--- |
| `Prefix` + `\|` hoặc `v` | Chia pane theo chiều dọc, giữ nguyên thư mục làm việc hiện tại |
| `Prefix` + `-` hoặc `s` | Chia pane theo chiều ngang, giữ nguyên thư mục làm việc hiện tại |
| `Prefix` + `m` | Bật hoặc tắt chế độ phóng to toàn màn hình cho pane hiện tại |
| `Prefix` + `x` | Đóng pane hiện tại ngay lập tức không cần xác nhận |
| `Prefix` + `b` | Tách pane hiện tại thành một window độc lập |
| `Prefix` + `H / J / K / L` | Thay đổi kích thước pane tương ứng 5 dòng hoặc cột |

---

## 4. Thao tác Window

| Phím tắt | Chức năng |
| :--- | :--- |
| `Prefix` + `c` | Tạo window mới tại thư mục làm việc hiện tại |
| `Prefix` + `Space` | Chuyển đổi qua lại giữa hai window sử dụng gần nhất |
| `Prefix` + `1, 2, 3...` | Nhảy trực tiếp đến window theo số thứ tự |
| `Prefix` + `,` | Đổi tên window |
| `Prefix` + `&` | Đóng window hiện tại |

Hệ thống tự động đánh số lại các window khi có một window bị đóng.

---

## 5. Cửa sổ Popup

| Phím tắt | Chức năng | Thao tác |
| :--- | :--- | :--- |
| `Prefix` + `w` | Menu chuyển đổi Session và Window | Hiển thị danh sách dạng cây qua fzf để tìm kiếm và chọn session |
| `Prefix` + `T` | Terminal nổi tạm thời | Cửa sổ dòng lệnh nổi ở giữa màn hình; đóng bằng phím `T` hoặc `q` |
| `Prefix` + `g` | Giao diện LazyGit | Mở LazyGit toàn màn hình; đóng bằng phím `q` trong LazyGit |
| `Prefix` + `S` | Menu kết nối SSH | Lấy danh sách máy chủ từ `~/.ssh/config` và kết nối qua fzf |

---

## 6. Chế độ sao chép (Copy Mode)

Sử dụng phím điều hướng theo phong cách Vim và tích hợp clipboard hệ thống (`wl-copy`):

| Phím tắt | Chức năng |
| :--- | :--- |
| `Prefix` + `[` | Vào chế độ cuộn và sao chép văn bản |
| `k` / `j` hoặc con lăn chuột | Di chuyển con trỏ lên / xuống |
| `v` | Bắt đầu chọn văn bản |
| `Ctrl + v` | Bắt đầu chọn khối văn bản dạng hình chữ nhật |
| `y` | Sao chép phần văn bản đã chọn vào clipboard hệ thống và thoát chế độ |
| `Prefix` + `]` | Dán nội dung bộ đệm của Tmux |

---

## 7. Tự động lưu và khôi phục Session

Hệ thống sử dụng hai plugin `tmux-resurrect` và `tmux-continuum`:
- Tự động lưu trạng thái toàn bộ session định kỳ mỗi phút.
- Tự động khôi phục phiên làm việc trước đó khi Tmux được khởi động lại.
- Lưu thủ công: `Prefix` + `Ctrl + s`.
- Khôi phục thủ công: `Prefix` + `Ctrl + r`.

---

## 8. Quản lý Plugins

Quản lý thông qua TPM (Tmux Plugin Manager) tại thư mục `~/.config/tmux/plugins/`:

- `Prefix` + `I`: Cài đặt các plugin mới khai báo trong cấu hình.
- `Prefix` + `U`: Cập nhật toàn bộ plugin.
- `Prefix` + `Alt + u`: Xóa các plugin không còn sử dụng.

---

## 9. Tùy biến cấu hình

Tệp cấu hình chính đặt tại `~/.config/tmux/tmux.conf`.

Sau khi chỉnh sửa, nạp lại cấu hình bằng phím tắt:
```
Prefix + r
```

### Các thông số chính trong `tmux.conf`:
- `set -g prefix C-a`: Thiết lập phím Prefix.
- `status-position top`: Đặt thanh trạng thái ở cạnh trên màn hình (đổi thành `bottom` nếu muốn ở dưới).
- Khối `Theme (Melange)`: Thiết lập màu sắc giao diện theo mã màu hex.
