# MAYBAE Check-in (Cloudflare Pages)

Hệ thống soát vé check-in sự kiện MAYBAE triển khai trên Cloudflare Pages.

## Các tệp chính
- `index.html`: Giao diện web quét QR camera thời gian thực, chụp/chọn ảnh và nhập mã thủ công.
- `_worker.js`: Cloudflare Pages Advanced Worker xử lý xác thực Cloudflare Access và kết nối an toàn tới Google Apps Script.

## Hướng dẫn triển khai Cloudflare Pages

1. Trên Cloudflare Dashboard, vào **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**.
2. Chọn repository `phuocptps31829/maybae-checkin`.
3. Cấu hình build:
   - **Framework preset**: None
   - **Build command**: *(để trống)*
   - **Build output directory**: `/` *(hoặc để trống)*
4. Nhấn **Save and Deploy**.

## Biến môi trường (Variables and Secrets)

Trong **Settings** → **Variables and Secrets** của dự án Pages, cấu hình:

| Tên biến | Loại | Mô tả |
| :--- | :--- | :--- |
| `MB_APPS_SCRIPT_URL` | Plain text | URL Web App `/exec` của Google Apps Script |
| `MB_CLOUDFLARE_SHARED_SECRET` | Secret | Mã bí mật chia sẻ với Apps Script (`MB_CLOUDFLARE_SHARED_SECRET`) |
| `MB_ACCESS_AUD` | Plain text | Application Audience (AUD) Tag từ Cloudflare Access |
| `MB_ACCESS_TEAM_DOMAIN` | Plain text | Domain Cloudflare Access team (vd: `https://ten-nhom.cloudflareaccess.com`) |
