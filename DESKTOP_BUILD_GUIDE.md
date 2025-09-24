# 🖥️ دليل بناء التطبيق لسطح المكتب

## 📋 متطلبات النظام

### Windows
- Windows 10 أو أحدث
- Visual Studio 2022 مع C++ development tools
- Flutter SDK مع دعم Windows

### macOS
- macOS 10.14 أو أحدث
- Xcode 12 أو أحدث
- Flutter SDK مع دعم macOS

### Linux
- Ubuntu 18.04 أو أحدث (أو توزيعة مماثلة)
- GTK+ 3.0 development libraries
- Flutter SDK مع دعم Linux

## 🛠️ تحضير البيئة

### تفعيل دعم Desktop في Flutter:

```bash
# تفعيل دعم Windows
flutter config --enable-windows-desktop

# تفعيل دعم macOS
flutter config --enable-macos-desktop

# تفعيل دعم Linux
flutter config --enable-linux-desktop

# التحقق من الإعدادات
flutter doctor
```

### تثبيت المتطلبات على Linux:
```bash
sudo apt-get update
sudo apt-get install clang cmake ninja-build pkg-config libgtk-3-dev liblzma-dev
```

## 🏗️ بناء التطبيق

### تلقائياً باستخدام السكريبتات:

#### Windows:
```cmd
scripts\build_desktop.bat
```

#### macOS/Linux:
```bash
./scripts/build_desktop.sh
```

### يدوياً:

#### Windows:
```bash
flutter clean
flutter pub get
flutter build windows --release
```

#### macOS:
```bash
flutter clean
flutter pub get
flutter build macos --release
```

#### Linux:
```bash
flutter clean
flutter pub get
flutter build linux --release
```

## 📁 مواقع الملفات المبنية

### Windows:
- **المسار:** `build\windows\x64\runner\Release\`
- **الملف التنفيذي:** `brother_admin_panel.exe`
- **الملفات المطلوبة:** جميع الملفات في المجلد مطلوبة للتشغيل

### macOS:
- **المسار:** `build/macos/Build/Products/Release/`
- **التطبيق:** `brother_admin_panel.app`

### Linux:
- **المسار:** `build/linux/x64/release/bundle/`
- **الملف التنفيذي:** `brother_admin_panel`
- **الملفات المطلوبة:** جميع الملفات في المجلد مطلوبة للتشغيل

## ✨ مميزات Desktop

### 🖼️ إعدادات النافذة:
- **الحجم الافتراضي:** 1400x900 بكسل
- **الحد الأدنى:** 1000x700 بكسل
- **قابلة للتغيير:** نعم
- **توسيط تلقائي:** نعم

### 🎯 إعدادات خاصة:
- عنوان النافذة باللغة العربية والإنجليزية
- دعم RTL كامل
- تحسينات أداء للشاشات الكبيرة
- إدارة متقدمة للنوافذ

### 🔧 أدوات مساعدة:
- إغلاق التطبيق عند إغلاق النافذة الأخيرة
- دعم اختصارات لوحة المفاتيح
- قوائم سياق متطورة (macOS)

## 🚀 تشغيل التطبيق

### Development Mode:
```bash
# Windows
flutter run -d windows

# macOS
flutter run -d macos

# Linux
flutter run -d linux
```

### Production Mode:
- شغّل الملف التنفيذي المبني مباشرة
- تأكد من وجود جميع الملفات المطلوبة في نفس المجلد

## 🔧 استكشاف الأخطاء

### مشاكل شائعة:

#### Windows:
- **خطأ Visual Studio:** تأكد من تثبيت C++ build tools
- **مشاكل Firebase:** تحقق من إعدادات الشبكة وFirewall

#### macOS:
- **مشاكل الصلاحيات:** استخدم `sudo` عند الحاجة
- **أخطاء Xcode:** تحديث Xcode لآخر إصدار

#### Linux:
- **مكتبات مفقودة:** تثبيت GTK development packages
- **صلاحيات التنفيذ:** استخدم `chmod +x` للسكريبتات

## 📦 التوزيع

### Windows:
- احزم مجلد `Release` كاملاً
- أو استخدم أدوات إنشاء Windows Installer

### macOS:
- احزم `.app` في DMG
- أو استخدم App Store Connect للتوزيع

### Linux:
- أنشئ AppImage أو Snap package
- أو احزم كـ .deb/.rpm package

## 🔄 التحديثات

عند تحديث التطبيق:
1. احتفظ بنسخة احتياطية من الإعدادات
2. أعد بناء التطبيق
3. اختبر على منصات مختلفة
4. تحقق من التوافق مع Firebase

## 📞 الدعم

عند مواجهة مشاكل:
1. تحقق من `flutter doctor`
2. راجع logs في Debug mode
3. تأكد من إعدادات Firebase
4. فحص متطلبات النظام
