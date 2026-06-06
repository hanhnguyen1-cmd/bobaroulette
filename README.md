# 🧋 Quay Trà Sữa · Đống Đa

Web app "vòng quay may mắn" giúp chọn quán trà sữa để uống mỗi ngày khi không biết uống gì.
Dữ liệu: **100 quán trà sữa / cà phê ở quận Đống Đa, Hà Nội**, cào từ Google Maps qua Apify.

## ✨ Tính năng

- **Bảng 7 mood cảm xúc** — chọn tâm trạng hôm nay (chill, vui, mệt, buồn, tụ tập, khám phá, tự thưởng). Mỗi mood lọc ra kiểu quán phù hợp.
- **Bộ lọc thông minh:**
  - 📍 **Khoảng cách thật** từ vị trí hiện tại (dùng GPS trình duyệt → tính theo đường chim bay)
  - ⭐ Điểm đánh giá tối thiểu
  - 🏷️ Lọc theo kiểu quán (trà trân châu, cà phê, phòng trà...)
- **Vòng quay** — quay để chốt 1 quán trong số ứng viên hợp ý.
- **Kết quả chi tiết** — tên, điểm, khoảng cách, địa chỉ, SĐT (gọi luôn được), website, nút chỉ đường Google Maps.
- Chạy hoàn toàn ở client, không cần backend. Mobile-friendly.

## 🚀 Cách deploy

### 1. Đẩy lên GitHub
```bash
git init
git add .
git commit -m "Quay trà sữa Đống Đa"
git branch -M main
git remote add origin https://github.com/<username>/tea-roulette.git
git push -u origin main
```

### 2. Deploy lên Vercel
- Vào [vercel.com](https://vercel.com) → **Add New → Project** → chọn repo `tea-roulette`.
- Framework Preset: **Other** (đây là static site, không cần build).
- Build Command: để trống. Output Directory: để trống (mặc định root).
- Bấm **Deploy**. Xong!

> Hoặc dùng Vercel CLI: `npm i -g vercel` rồi chạy `vercel` trong thư mục này.

## 📁 Cấu trúc

```
tea-roulette/
├── index.html      # Toàn bộ app (HTML + CSS + JS + dữ liệu nhúng sẵn)
├── places.json     # Dữ liệu gốc 100 quán (tham khảo / cập nhật)
├── vercel.json     # Cấu hình Vercel
└── README.md
```

## 🔄 Cập nhật dữ liệu

App đọc dữ liệu nhúng trực tiếp trong `index.html` (biến `const PLACES = [...]`).
Khi có file CSV mới từ Apify, geocode lại ra tọa độ rồi thay mảng `PLACES` trong `index.html`
(hoặc thay `places.json` và viết lại đoạn nhúng).

## ⚠️ Lưu ý

- Khoảng cách là **ước lượng** (một số quán dùng tọa độ trung tâm tuyến đường/phường vì dữ liệu Apify không kèm lat/lng chính xác).
- Tính năng định vị cần **HTTPS** — Vercel cấp sẵn HTTPS nên chạy tốt khi deploy.
