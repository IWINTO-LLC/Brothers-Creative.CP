# إعداد reCAPTCHA لـ Firebase Phone Authentication

## 🚨 المشكلة الحالية
```
Failed to initialize reCAPTCHA Enterprise config. Triggering the reCAPTCHA v2 verification.
❌ Verification failed: The phone verification request contains an invalid application verifier. The reCAPTCHA token response is either invalid or expired.
```

## 🔧 الحلول المطبقة

### 1. ✅ تحديث `web/index.html`
- تغيير reCAPTCHA من `normal` إلى `invisible`
- إضافة دالة إعادة تهيئة reCAPTCHA
- تحسين معالجة الأخطاء

### 2. ✅ تحديث `otp_login_controller.dart`
- إضافة معالجة خاصة لأخطاء reCAPTCHA
- تحسين رسائل الخطأ
- إضافة أكواد خطأ جديدة

## 🛠️ خطوات إعداد Firebase Console

### 1. تفعيل Phone Authentication
1. اذهب إلى [Firebase Console](https://console.firebase.google.com/)
2. اختر مشروع `brothers-creative`
3. اذهب إلى **Authentication** > **Sign-in method**
4. فعّل **Phone** provider
5. أضف رقم هاتف للاختبار في **Test phone numbers**

### 2. إعداد reCAPTCHA
1. اذهب إلى **Authentication** > **Settings** > **Authorized domains**
2. أضف النطاقات التالية:
   - `localhost` (للاختبار المحلي)
   - `brothers-creative.firebaseapp.com`
   - `brothers-creative.web.app`
   - أي نطاق آخر تستخدمه

### 3. إعداد App Check (اختياري)
1. اذهب إلى **App Check**
2. فعّل **App Check** لحماية أفضل
3. أضف **reCAPTCHA Enterprise** للويب

### 4. إعداد Quotas
1. اذهب إلى **Authentication** > **Usage**
2. اضبط **SMS daily quota** حسب احتياجاتك
3. الافتراضي: 10,000 رسالة يومياً

## 🔍 اختبار الحل

### 1. اختبار محلي
```bash
# تشغيل التطبيق محلياً
flutter run -d chrome

# أو
flutter run -d web-server --web-port 3000
```

### 2. اختبار OTP
1. اذهب إلى صفحة تسجيل الدخول
2. اختر "تسجيل الدخول برقم الهاتف"
3. أدخل رقم هاتف مصرح له
4. اضغط "إرسال رمز التحقق"
5. تحقق من ظهور reCAPTCHA (invisible)
6. أدخل رمز التحقق المرسل

### 3. أرقام الاختبار
```
رقم الهاتف: +966501234567
رمز التحقق: 123456
```

## 🚨 استكشاف الأخطاء

### 1. أخطاء reCAPTCHA
```
invalid-app-credential: خطأ في إعدادات التطبيق
invalid-recaptcha-token: خطأ في reCAPTCHA token
missing-recaptcha-token: مفقود reCAPTCHA token
```

### 2. حلول
- تأكد من إضافة النطاق في **Authorized domains**
- تحقق من إعدادات reCAPTCHA في Firebase Console
- أعد تحميل الصفحة إذا فشل reCAPTCHA
- تأكد من تفعيل Phone Authentication

### 3. رسائل الخطأ الجديدة
- `خطأ في reCAPTCHA. يرجى إعادة تحميل الصفحة والمحاولة مرة أخرى.`
- `خطأ في إعدادات التطبيق. يرجى إعادة تحميل الصفحة`
- `مفقود reCAPTCHA token. يرجى إعادة تحميل الصفحة`

## 📱 الميزات المضافة

### 1. reCAPTCHA Invisible
- لا يظهر للمستخدم إلا عند الحاجة
- تحسين تجربة المستخدم
- معالجة أفضل للأخطاء

### 2. إعادة تهيئة reCAPTCHA
- دالة `window.resetRecaptcha()` متاحة
- إعادة تهيئة تلقائية عند انتهاء الصلاحية
- معالجة أخطاء التحميل

### 3. رسائل خطأ محسنة
- رسائل واضحة باللغة العربية
- إرشادات للمستخدم
- معالجة شاملة للأخطاء

## 🔄 الخطوات التالية

### 1. اختبار التطبيق
- [ ] اختبار أرقام الاختبار
- [ ] اختبار أرقام حقيقية
- [ ] اختبار معالجة الأخطاء
- [ ] اختبار الأداء

### 2. النشر
- [ ] إعداد Production
- [ ] ضبط Security Rules
- [ ] مراقبة الاستخدام
- [ ] تحسين الأداء

## 📞 الدعم

- 📖 [Firebase Phone Auth Documentation](https://firebase.google.com/docs/auth/flutter/phone)
- 🔧 [Firebase Console](https://console.firebase.google.com/)
- 📚 [FlutterFire Documentation](https://firebase.flutter.dev/)
- 🐛 [Report Issues](https://github.com/your-repo/issues)

## ✅ النتيجة المتوقعة

بعد تطبيق هذه الحلول، يجب أن يعمل OTP بشكل صحيح مع:
- ✅ reCAPTCHA invisible يعمل بشكل صحيح
- ✅ رسائل خطأ واضحة
- ✅ معالجة شاملة للأخطاء
- ✅ تجربة مستخدم محسنة
