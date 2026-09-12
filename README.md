# 🪟 Cẩm Nang Sử Dụng Cấu Hình TMUX (Melange Theme)

Tài liệu này được biên soạn ngắn gọn, trực quan và đầy đủ để bạn **tra cứu nhanh và sử dụng hàng ngày**, cũng như biết cách tự tinh chỉnh lại theo ý muốn.

Cấu hình được thiết kế theo phong cách hiện đại (chuẩn XDG `~/.config/tmux/`), đồng bộ màu sắc **Melange** với Neovim, tích hợp **vim-tmux-navigator** và 4 cửa sổ **Popup tiện ích**.

---

## ⚡ Phím Prefix Chính
> **`Ctrl + a`** *(Đã thay thế cho phím mặc định `Ctrl + b` của Tmux)*.
> Mọi tổ hợp phím bên dưới có chữ **`Prefix`** nghĩa là bạn bấm **`Ctrl + a`**, thả tay ra rồi bấm phím tiếp theo.

---

## 1. 🧭 Điều hướng siêu tốc giữa Tmux và Neovim
Bạn **KHÔNG CẦN** bấm Prefix! Chỉ cần bấm trực tiếp:

| Phím tắt | Tác vụ |
| :--- | :--- |
| **`Ctrl + h`** | Nhảy sang cửa sổ / pane bên **Trái** |
| **`Ctrl + j`** | Nhảy xuống cửa sổ / pane bên **Dưới** |
| **`Ctrl + k`** | Nhảy lên cửa sổ / pane bên **Trên** |
| **`Ctrl + l`** | Nhảy sang cửa sổ / pane bên **Phải** |

> 💡 **Điểm đặc biệt**: Khi bạn đang mở Neovim, các phím này sẽ chuyển đổi giữa các split trong Neovim. Khi con trỏ chạm mép Neovim, nó sẽ **tự động nhảy mượt mà sang pane Tmux kế bên**!

---

## 2. 🪟 Quản lý Pane (Chia màn hình)

| Phím tắt | Tác vụ |
| :--- | :--- |
| **`Prefix` + `\|`** hoặc **`v`** | Chia đôi pane theo chiều **Dọc** (giữ nguyên thư mục đang đứng) |
| **`Prefix` + `-`** hoặc **`s`** | Chia đôi pane theo chiều **Ngang** (giữ nguyên thư mục đang đứng) |
| **`Prefix` + `m`** | Phóng to (Zoom) pane hiện tại toàn màn hình / Thu nhỏ lại |
| **`Prefix` + `x`** | Đóng pane hiện tại ngay lập tức (không cần hỏi xác nhận) |
| **`Prefix` + `b`** | Tách pane hiện tại thành một Window (tab) riêng biệt |
| **`Prefix` + `H / J / K / L`** | Tăng/giảm kích thước pane (Resize 5 ký tự) |

---

## 3. 📑 Quản lý Window (Tab làm việc)

| Phím tắt | Tác vụ |
| :--- | :--- |
| **`Prefix` + `c`** | Tạo Window mới (tự động mở đúng thư mục hiện tại) |
| **`Prefix` + `<Space>`** | Nhảy nhanh qua lại giữa 2 Window gần nhất |
| **`Prefix` + `1, 2, 3...`** | Chuyển trực tiếp tới Window số 1, 2, 3... |
| **`Prefix` + `,`** | Đổi tên cho Window hiện tại |
| **`Prefix` + `&`** | Đóng Window hiện tại |

*(Cấu hình đã bật tự động đánh số lại: Khi bạn đóng Window số 2 thì Window số 3 sẽ tự động chuyển thành số 2).*

---

## 4. 🚀 4 Cửa sổ Popup đặc biệt (Rất tiện lợi)

| Phím tắt | Popup được mở | Cách sử dụng & Thoát |
| :--- | :--- | :--- |
| **`Prefix` + `w`** | **Menu chuyển Session / Window** | Danh sách dạng cây mở ra qua `fzf`. Gõ vài ký tự rồi ấn `Enter` để nhảy tới bất kỳ Session/Window nào. |
| **`Prefix` + `T`** | **Scratchpad Terminal nổi** | Mở một terminal tạm thời ở giữa màn hình (80% kích thước). Để đóng, bấm **`T`** hoặc **`q`**. |
| **`Prefix` + `g`** | **LazyGit toàn màn hình** | Mở giao diện Git trực quan để stage, commit, push cực nhanh. Bấm `q` trong LazyGit để thoát. |
| **`Prefix` + `S`** | **Menu kết nối nhanh SSH** | Đọc danh sách máy chủ trong `~/.ssh/config` và mở kết nối trong window mới qua `fzf`. |

---

## 5. 📋 Copy Mode chuẩn Vim (Sao chép vào Clipboard hệ thống)

| Phím tắt | Tác vụ |
| :--- | :--- |
| **`Prefix` + `[`** | Bắt đầu vào chế độ Copy Mode (để cuộn xem log, copy chữ) |
| **`k / j`** hoặc cuộn chuột | Di chuyển con trỏ lên / xuống |
| **`v`** | Bắt đầu bôi đen văn bản (Visual mode) |
| **`Ctrl + v`** | Bôi đen theo khối hình chữ nhật (Block visual) |
| **`y`** | Sao chép đoạn đã chọn vào **Clipboard hệ thống** (`wl-copy`) và thoát mode |
| **`Prefix` + `]`** | Dán nội dung vừa copy của Tmux |

---

## 6. 💾 Tự động lưu & Khôi phục Session (Resurrect & Continuum)

- **Tự động lưu**: Hệ thống tự động sao lưu trạng thái các session, window, pane **mỗi 1 phút** một lần.
- **Tự động khôi phục khi khởi động**: Khi bạn tắt máy bật lại hoặc mở Tmux lần đầu, toàn bộ layout và session cũ sẽ được **tự động phục hồi nguyên vẹn**.
- **Thao tác thủ công (nếu cần)**:
  - `Prefix` + **`Ctrl + s`**: Lưu session thủ công ngay lập tức.
  - `Prefix` + **`Ctrl + r`**: Khôi phục session thủ công.

---

## 7. 🔌 Quản lý Plugins (TPM)

Plugins được quản lý qua [TPM](https://github.com/tmux-plugins/tpm) tại `~/.config/tmux/plugins/`:

- **`Prefix` + `I`** *(Shift + i)*: Cài đặt các plugin mới thêm vào `tmux.conf`.
- **`Prefix` + `U`** *(Shift + u)*: Cập nhật toàn bộ plugin lên bản mới nhất.
- **`Prefix` + `Alt + u`**: Gỡ bỏ các plugin đã xóa khỏi `tmux.conf`.

---

## 8. 🛠️ Hướng dẫn tự chỉnh sửa cấu hình

Tệp cấu hình chính nằm tại: **`~/.config/tmux/tmux.conf`**.

Sau khi sửa bất kỳ dòng nào, bạn chỉ cần bấm:
> **`Prefix` + `r`** ➔ Tmux sẽ tải lại cấu hình ngay lập tức và hiện thông báo `󰑓 Config reloaded`.

### Các vị trí thường muốn chỉnh sửa:
1. **Đổi phím Prefix**:
   Tìm dòng `set -g prefix C-a` và đổi `C-a` thành phím bạn muốn (ví dụ `C-Space`).
2. **Đổi màu Status Bar (Theme Melange)**:
   Tìm phần `##### Theme (Melange) #####` (khoảng dòng 83):
   - `bg='#292522'`: Màu nền chính (nâu đen ấm)
   - `fg='#ece1d7'`: Màu chữ chính (trắng be)
   - `accent='#ebc06d'`: Màu viền active và tên session (vàng)
3. **Đổi vị trí thanh trạng thái**:
   - Mặc định đang ở trên đỉnh: `set-option -g status-position top`
   - Đổi xuống đáy màn hình: sửa `top` thành `bottom`.
