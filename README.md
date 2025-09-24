# 📱 Sdelivery

تطبيق توصيل الطلاب للمدارس 🚍  
واجهة عصرية وسهلة الاستخدام، مع دعم النمط **الداكن والفاتح** 🌙☀️.  
يدعم **السائق / ولي الأمر / الطالب / المدرسة** مع مزامنة فورية عبر **Firebase**.

---

## ✨ المميزات
- تسجيل الدخول مع OTP 📲
- واجهة حديثة وسهلة الاستخدام 🎨
- دعم النمط الداكن والفاتح 🌓
- ربط الطلاب بالفصول والمدارس 🏫
- مزامنة فورية مع Firebase ⚡
- إشعارات عند وصول السائق / تأخره / عودة الطالب 🛎️

---

## ⚡ تشغيل المشروع (محليًا)

```bash
flutter pub get
flutter run
```

---

## 🛠️ بناء التطبيق

### بناء APK (للتثبيت على Android)
```bash
flutter build apk --release
```

الملف الناتج:  
```
build/app/outputs/flutter-apk/app-release.apk
```

### بناء AAB (للنشر على Google Play)
```bash
flutter build appbundle --release
```

الملف الناتج:  
```
build/app/outputs/bundle/release/app-release.aab
```

---

## 🚀 تنزيل أحدث إصدار تلقائيًا (APK + AAB)

### 1) Linux / MacOS (Bash)
احفظ الملف التالي باسم `download_latest.sh`:

```bash
#!/bin/bash
REPO="waslnysoft/Sdelivery"   # ضع اسم حسابك والمستودع هنا
ASSET_APK="app-release.apk"
ASSET_AAB="app-release.aab"

LATEST_TAG=$(curl -s https://api.github.com/repos/$REPO/releases/latest | grep -Po '"tag_name": "\K.*?(?=")')

echo "📦 أحدث إصدار هو: $LATEST_TAG"

curl -L -o $ASSET_APK https://github.com/$REPO/releases/download/$LATEST_TAG/$ASSET_APK
curl -L -o $ASSET_AAB https://github.com/$REPO/releases/download/$LATEST_TAG/$ASSET_AAB

echo "✅ تم تنزيل الملفات: $ASSET_APK و $ASSET_AAB"

# التثبيت التلقائي للـ APK
if command -v adb &> /dev/null; then
  echo "📲 جاري تثبيت التطبيق..."
  adb install -r $ASSET_APK
  echo "✅ تم تثبيت التطبيق بنجاح!"
else
  echo "⚠️ لم يتم العثور على ADB. يرجى تثبيت Android SDK Platform Tools."
fi
```

تشغيل:
```bash
chmod +x download_latest.sh
./download_latest.sh
```

---

### 2) Windows (PowerShell)
احفظ الملف التالي باسم `download_latest.ps1`:

```powershell
$Repo = "waslnysoft/Sdelivery"
$ApkName = "app-release.apk"
$AabName = "app-release.aab"

$LatestTag = (Invoke-RestMethod "https://api.github.com/repos/$Repo/releases/latest").tag_name
Write-Host "📦 أحدث إصدار هو: $LatestTag"

Invoke-WebRequest -Uri "https://github.com/$Repo/releases/download/$LatestTag/$ApkName" -OutFile $ApkName
Invoke-WebRequest -Uri "https://github.com/$Repo/releases/download/$LatestTag/$AabName" -OutFile $AabName

Write-Host "✅ تم تنزيل الملفات: $ApkName و $AabName"

if (Get-Command adb -ErrorAction SilentlyContinue) {
    Write-Host "📲 جاري تثبيت التطبيق..."
    adb install -r $ApkName
    Write-Host "✅ تم تثبيت التطبيق بنجاح!"
} else {
    Write-Host "⚠️ لم يتم العثور على ADB. يرجى تثبيت Android SDK Platform Tools."
}
```

تشغيل:
```powershell
.\download_latest.ps1
```

---

## 📂 GitHub Actions (CI/CD)

تم تجهيز **Workflow** داخل المشروع:
- يبني **APK + AAB** تلقائيًا عند إصدار Tag جديد (مثل `v1.0.0`).
- يرفع الملفات مباشرة إلى صفحة **Releases**.
- روابط التحميل المباشرة:

```
https://github.com/<username>/Sdelivery/releases/download/vX.X.X/app-release.apk
https://github.com/<username>/Sdelivery/releases/download/vX.X.X/app-release.aab
```

---

## 📝 المتطلبات
- Flutter (الإصدار المستقر)
- Android Studio أو VS Code
- Firebase (مع ملف `google-services.json`)
- ADB لتثبيت APK تلقائيًا (اختياري)

---
# tawseeel
