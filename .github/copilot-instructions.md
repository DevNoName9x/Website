# Copilot instructions — interleaved English / Tiếng Việt

Quick context — Tóm tắt nhanh
- Small static website: `index.html` plus `Bagua.html`, `CellMark.html`, `CellMark10.html`.
- Website HTML tĩnh nhỏ: `index.html` và các trang phụ `Bagua.html`, `CellMark.html`, `CellMark10.html`.
- No build system or package manager; pages are plain HTML with inline CSS and Font Awesome via CDN.
- Không có hệ thống build hay package manager; các trang là HTML thuần, CSS nội tuyến, và Font Awesome qua CDN.

What an AI agent should know — Những điều AI agent cần biết
- Client-side only: no server code or JS frameworks. Edit files and links directly.
- Chỉ chạy phía client: không có server hay framework JS. Chỉnh sửa file và liên kết trực tiếp.
- Repeated layout classes: `.navbar`, `.sidebar`, `.content` — keep them to preserve layout and responsiveness in `index.html`'s `<style>`.
- Các class layout lặp lại: `.navbar`, `.sidebar`, `.content` — giữ nguyên để bảo toàn layout và responsive trong khối `<style>` của `index.html`.
- Font Awesome icons are referenced in the head of `index.html`; keep or update that CDN link when adding icons.
- Icon Font Awesome được link trong `index.html`; giữ hoặc cập nhật link CDN khi thêm icon.

Files to read first — Tệp nên đọc trước
- `index.html` — main layout, styles and nav pattern.
- `index.html` — nơi chứa layout chính, style và mẫu điều hướng.
- `Bagua.html`, `CellMark.html`, `CellMark10.html` — sidebar link examples.
- `Bagua.html`, `CellMark.html`, `CellMark10.html` — ví dụ cách thêm link trong sidebar.
- `README.md` — very short project description.
- `README.md` — mô tả dự án rất ngắn.

Developer workflows — Quy trình phát triển
- No build or test commands. To preview locally run a simple static server at repo root (PowerShell):

```powershell
# from project root
python -m http.server 8000
# or
py -3 -m http.server 8000
```

- Không có lệnh build/test. Để xem trước, chạy server tĩnh từ thư mục gốc (PowerShell):

```powershell
# từ thư mục gốc
python -m http.server 8000
# hoặc
py -3 -m http.server 8000
```
- Use VS Code Live Server for auto-reload during edits.
- Dùng VS Code Live Server để tự reload khi sửa file.
- Debug in browser DevTools; check Network for CDN failures.
- Gỡ lỗi bằng DevTools; kiểm tra tab Network nếu CDN không tải được.

Project patterns & conventions — Mẫu & quy ước dự án
- CSS is inline in `index.html`'s `<style>` block; prefer small local edits unless you intentionally extract a shared stylesheet.
- CSS chủ yếu ở khối `<style>` trong `index.html`; ưu tiên sửa nhỏ tại chỗ trừ khi tách ra file CSS chung.
- Sidebar links are relative (use `./`); update the sidebar on every page when adding a new page.
- Liên kết sidebar dùng đường dẫn tương đối (dùng `./`); khi thêm trang, cập nhật sidebar trên mọi trang.
- Responsive breakpoint at 768px: sidebar collapses from 250px to 70px — keep class names to preserve this behavior.
- Điểm phá vỡ responsive ở 768px: `.sidebar` co từ 250px xuống 70px — giữ tên class để bảo toàn hành vi.

Integration points — Điểm tích hợp
- Font Awesome CDN in `index.html` head; no other external scripts detected.
- Font Awesome ở `index.html`; không thấy script hay API ngoài khác.
- Assets use relative paths; keep links case-sensitive and consistent.
- Tài nguyên dùng đường dẫn tương đối; giữ phân biệt hoa thường và nhất quán.

When editing — Practical rules / Khi chỉnh sửa
- Keep `.navbar`, `.sidebar`, `.content` in new pages; include the Font Awesome `<link>` in the `<head>`.
- Giữ `.navbar`, `.sidebar`, `.content` khi tạo trang mới; giữ thẻ `<link>` Font Awesome trong `<head>`.
- If extracting CSS to a shared file, update all HTML pages to reference it.
- Nếu tách CSS ra file chung, cập nhật mọi trang để link tới file đó.
- Avoid changing global body/font defaults unless you update every page.
- Tránh thay đổi font-family hoặc mặc định body trừ khi cập nhật mọi trang.

Examples from repo — Ví dụ trong repo
- Layout classes used: `.navbar`, `.sidebar`, `.content` (see `index.html`).
- Các class layout: `.navbar`, `.sidebar`, `.content` (xem `index.html`).
- Sidebar link example: `<a href="./Bagua.html">...<span>Bagua</span></a>`
- Ví dụ link sidebar: `<a href="./Bagua.html">...<span>Bagua</span></a>`

What not to invent — Những điều không nên tự thêm
- There is no build pipeline, `package.json`, or server. Don’t add Node/bundlers/tests unless you also add install/run docs and update `README.md`.
- Không có pipeline build, `package.json`, hay server. Không thêm Node/bundler/test trừ khi bạn cập nhật `README.md` và tài liệu cài đặt.

If uncertain — Questions for maintainer / Nếu không chắc
- Should styles be centralized into `styles.css` and linked from all pages? If yes, update all HTML and mention in commit message.
- Có cần chuyển style vào `styles.css` chung không? Nếu có, cập nhật mọi trang và ghi chú trong commit.

End — Kết thúc
- Review and tell me if you want a scaffold, shared CSS, or a `preview.ps1` helper.
- Kiểm tra và cho biết nếu bạn muốn tôi tạo scaffold, CSS chung, hoặc script `preview.ps1`.
---

TI — Hướng dẫn (Tiếng Việt)

Tóm tắt nhanh
- Website HTML tĩnh nhỏ: trang chính `index.html` và các trang phụ `Bagua.html`, `CellMark.html`, `CellMark10.html`.
- Không tìm thấy hệ thống build, trình quản lý gói hay test — các trang là HTML thuần với CSS nội tuyến và CDN Font Awesome.
- Ngôn ngữ nội dung: tiếng Việt (`<html lang="vi">`).

Những điều AI agent cần biết (tổng quan)
- Đây là một site phía client, HTML tĩnh. Không có thành phần server hay framework JS; mọi thay đổi là chỉnh sửa file và liên kết tương đối.
- Cấu trúc giao diện lặp lại trên các trang: `.navbar` (trên cùng), `.sidebar` bên trái và `.content` chính. Giữ nguyên các class này khi thêm/sửa trang để bảo toàn layout và responsive được định nghĩa trong khối `<style>` của `index.html`.
- Icon dùng Font Awesome qua CDN (link trong `index.html`). Khi thêm icon, giữ hoặc cập nhật tham chiếu CDN nếu cần.

Tệp nên đọc trước
- `index.html` — ví dụ chính về layout, style và mẫu điều hướng.
- `Bagua.html`, `CellMark.html`, `CellMark10.html` — ví dụ trang phụ và cách thêm link trong sidebar.
- `README.md` — mô tả rất ngắn của dự án ("Build Html Website").

Quy trình phát triển (khả dụng / dễ tìm)
- Không có lệnh build/test. Để xem trước tại máy, chạy một server tĩnh từ thư mục gốc. Ví dụ (PowerShell / Windows):

```powershell
# từ thư mục gốc của dự án
python -m http.server 8000
# hoặc nếu dùng PowerShell với Python 3
py -3 -m http.server 8000
```

- Hoặc dùng extension Live Server của VS Code để phục vụ và tự reload khi thay đổi.
- Gỡ lỗi: dùng DevTools của trình duyệt để kiểm tra layout/CSS; kiểm tra tab Network để phát hiện lỗi tải CDN (Font Awesome).

Mẫu & quy ước riêng của dự án
- CSS chủ yếu đặt nội tuyến trong thẻ `<style>` của `index.html` — ưu tiên sửa nhỏ tại chỗ trừ khi bạn muốn tách ra file CSS chung. Nếu tách, phải cập nhật tất cả các trang để link tới stylesheet mới.
- Mẫu điều hướng: các liên kết sidebar là tương đối (ví dụ `./Bagua.html`). Khi thêm trang mới, nhớ thêm anchor tương ứng vào sidebar trên mọi trang (site không có header chung).
- Điểm phá vỡ responsive: 768px được dùng; `.sidebar` co từ 250px xuống 70px. Giữ tên class và cấu trúc này để đảm bảo hành vi trên mobile.
- Ngôn ngữ/nội dung: các trang đang dùng tiếng Việt; giữ `lang="vi"` và meta UTF-8 khi tạo file mới.

Điểm tích hợp / phụ thuộc bên ngoài
- Font Awesome CDN: nằm trong phần head của `index.html`. Không thấy script hay API ngoài nào khác.
- Tất cả tài nguyên được tham chiếu bằng đường dẫn tương đối; giữ quy tắc dùng `./` cho các tệp cùng thư mục.

Khi chỉnh sửa — quy tắc thực tế
- Giữ cấu trúc `.navbar`, `.sidebar`, và `.content` cho mọi trang mới. Mẫu khung theo `index.html`: giữ link Font Awesome, div navbar, div sidebar và div content có margin-left/margin-top tương ứng.
- Nếu thêm file trang mới, cập nhật sidebar trên mọi trang để thêm liên kết (không có include/partial chia sẻ header).
- Tránh thay đổi font-family toàn cục hoặc các mặc định body trừ khi bạn cập nhật trên mọi trang (hiện không có stylesheet tập trung).
- Giữ nguyên tên file và phân biệt chữ hoa/thường trong liên kết (ví dụ `CellMark10.html`).

Ví dụ từ repo
- Các class layout: `.navbar`, `.sidebar`, `.content` (xem khối style trong `index.html`).
- Thêm link sidebar: `<a href="./Bagua.html">...<span>Bagua</span></a>` — sao chép mẫu này khi tạo trang mới.

Không tự ý thêm
- Không có pipeline build, `package.json`, hay server. Đừng giả định có Node, bundler hay hệ thống test trừ khi bạn thêm chúng rõ ràng và cập nhật `README`.

Nếu không chắc / câu hỏi cho người bảo trì
- Có muốn chuyển các style vào một file CSS chung không? (Nếu có, cập nhật tất cả trang và ghi rõ thay đổi trong commit message.)
- Có quy ước đặt tên trang hay ngôn ngữ ưu tiên nào khác ngoài tiếng Việt không?

Kết thúc hướng dẫn — kiểm tra lại và cho biết nếu bạn muốn mở rộng thêm (ví dụ: tách CSS chung, thêm script deploy, hay lệnh preview khác ngoài Python HTTP server).