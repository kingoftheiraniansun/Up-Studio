# UP Studio — ساخت APK و IPA

این پروژه برای Capacitor آماده شده است. پوشه‌های `android/` و `ios/` عمداً داخل ZIP اولیه نیستند؛ اسکریپت‌ها در اولین اجرا آن‌ها را می‌سازند. این کار حجم پروژه را کمتر و ساخت را قابل تکرار نگه می‌دارد.

## پیش‌نیازها

### Android
- Node.js 20+ (پیشنهاد: 22)
- JDK 17
- Android Studio + Android SDK
- Android SDK Platform/Build Tools مطابق نسخه Capacitor/Gradle تولیدشده

### iOS
- macOS
- Xcode
- Node.js 20+
- Apple Developer account برای IPA قابل نصب/انتشار

## ساخت APK با یک دستور

macOS / Linux:

```bash
./scripts/build-android.sh
```

Windows PowerShell:

```powershell
./scripts/build-android.ps1
```

خروجی معمولاً در این مسیر است:

`android/app/build/outputs/apk/debug/`

این APK برای تست و نصب مستقیم روی دستگاه Android مناسب است. برای نسخه Release باید keystore و signing تنظیم شود.

## آماده‌سازی iOS

روی Mac:

```bash
./scripts/build-ios.sh
```

سپس پروژه `ios/App/App.xcworkspace` را در Xcode باز کنید، Team و Bundle Identifier را تنظیم کنید و از Xcode Archive/Export بگیرید.

## ساخت Archive و IPA با خط فرمان

```bash
./scripts/build-ios-archive.sh
```

این دستور Archive می‌سازد. برای خروجی IPA باید `ExportOptions.plist` داشته باشید؛ نمونه آن در `ExportOptions.plist.template` قرار دارد. مقدار `teamID` و روش export/signing باید مطابق Apple Developer account شما تنظیم شود.

**نکته مهم:** IPA قابل نصب بدون امضای معتبر Apple ساخته نمی‌شود. برای Ad Hoc باید دستگاه‌های مجاز در پروفایل باشند؛ برای App Store/TestFlight باید روش انتشار مربوطه را انتخاب کنید.

## GitHub Actions

دو workflow هم آماده شده است:

- `.github/workflows/android-apk.yml` → با Push یا اجرای دستی، APK تستی را می‌سازد و به عنوان Artifact می‌دهد.
- `.github/workflows/ios-archive.yml` → روی macOS یک iOS Archive بدون signing می‌سازد. برای IPA signed باید گواهی و provisioning profile/credentials را به workflow اضافه کنید.

## شناسه اپ

- App ID: `com.uplabstudio.app`
- App Name: `UP Studio`

قبل از انتشار، Bundle ID را با شناسه‌ای که در Apple Developer ثبت کرده‌اید هماهنگ کنید و برای Android Release نیز keystore اختصاصی بسازید.
