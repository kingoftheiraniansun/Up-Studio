# UP Studio — Mobile App

پروژه‌ی mobile-first برای UP Studio با PWA + Capacitor. شامل لوگو، ۱۷ تصویر نمونه‌کار، Reel اصلی، نسخه‌ی بدون صدا برای Launch، و فایل‌های مرجع Booking و AI است.

## اجرای وب

پوشه‌ی `www/` را روی یک HTTPS static host سرو کنید. Service Worker در HTTPS (یا localhost) فعال می‌شود.

## ساخت Android / iOS

برای دستورهای آماده‌ی ساخت به `BUILD.md` مراجعه کنید.

### سریع‌ترین مسیر Android

macOS / Linux:

```bash
./scripts/build-android.sh
```

Windows PowerShell:

```powershell
./scripts/build-android.ps1
```

### سریع‌ترین مسیر iOS

روی macOS:

```bash
./scripts/build-ios.sh
```

برای IPA امضاشده، Apple Developer signing و provisioning لازم است. نمونه‌ی `ExportOptions.plist` در پروژه قرار دارد.

## قابلیت‌های native که نیاز به تنظیم نهایی دارند

- Android wallpaper API برای ذخیره مستقیم روی Home/Lock screen نیاز به پیاده‌سازی native دارد؛ نسخه‌ی وب fallback دارد.
- iOS Live Activities / Dynamic Island نیازمند plugin و entitlements اختصاصی است.
- Push notification برای production نیازمند backend و credentials است.
