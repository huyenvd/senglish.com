# S English — Website (GitHub Pages)

Folder tĩnh, không cần build. Publish xong sẽ có 3 URL:

| Nội dung | URL (sau khi bật Pages) |
|---|---|
| Giới thiệu app | `https://huyenvd.github.io/senglish/` |
| JSON cấu hình cho app | `https://huyenvd.github.io/senglish/api/config.json` |
| Chính sách & quyền riêng tư | `https://huyenvd.github.io/senglish/privacy.html` |

> URL trên đúng khi repo là `huyenvd/senglish` và Pages phục vụ từ folder
> `/site`. Nếu đổi tên repo/user, thay domain tương ứng trong file
> `lib/services/ad_config.dart` (`remoteConfigUrl`) và mã QR.

## Cách publish (2 phút)

1. Commit + push folder `site/` lên GitHub.
2. Vào repo → **Settings → Pages** → **Build and deployment**:
   - Source: **Deploy from a branch**
   - Branch: **develop** (hoặc `main` sau khi merge) — Folder: **`/site`**
3. Chờ ~1 phút, mở `https://huyenvd.github.io/senglish/` để kiểm tra.

## Checklist khi app lên store (làm 1 lần)

- [ ] `index.html`: dán link Google Play thật vào nút “Tải cho Android”.
- [ ] `index.html`: dán link App Store thật vào nút “Tải cho iPhone”.
- [ ] Tạo lại 2 ảnh QR từ link thật, ghi đè `assets/qr-android.png`,
      `assets/qr-ios.png` (giữ nguyên tên file để khỏi sửa HTML).
- [ ] `index.html` + `privacy.html`: thay `support@senglish.app` bằng
      email liên hệ thật (tìm chữ `TODO`).
- [ ] `api/config.json`: điền `update_url_ios` thật; nâng
      `min_version_*` + bật `force_update_*` khi muốn ép cập nhật;
      đặt `ads_enabled: false` khi muốn tắt toàn bộ quảng cáo.
- [ ] Test thật: mở JSON trên trình duyệt, quét QR bằng điện thoại.

## Quy ước

- Mọi link/ảnh tạm đều được đánh dấu `TODO` (HTML) hoặc chữ
  “TEMP LINK” (trong ảnh QR).
- Test `test/site_config_test.dart` đảm bảo `api/config.json` luôn parse
  được bằng `RemoteAppConfig` của app — sửa JSON xong chạy
  `flutter test test/site_config_test.dart`.
