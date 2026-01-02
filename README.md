# راهنمای کارگاه مقدماتی گیت (Git Workshop)

## چرا گیت یاد بگیریم؟

- کد شما هرگز گم نمی‌شود (همیشه نسخه پشتیبان دارید)
- همکاری تیمی بدون تداخل و فاجعه
- استاندارد صنعت نرم‌افزار (هر شرکت بزرگی از گیت استفاده می‌کند)

---

## نصب گیت

1. به سایت https://git-scm.com/ بروید و گیت را دانلود و نصب کنید.
2. در مراحل نصب:
   - **Default editor**: `Use Visual Studio Code as Git's default editor`
   - **PATH environment**: `Git from the command line and also from 3rd-party software`
   - **Line ending**: `Checkout Windows-style, commit Unix-style line endings`

پس از نصب، در ترمینال بزنید:
```bash
git --version
```

---

## تمرین ۱: زندگی بدون گیت (چالش نسخه‌ها)

```bash
mkdir version-hell
cd version-hell
echo "نسخه اولیه" > final.txt
cp final.txt final_fixed.txt
cp final.txt final_fixed_v2.txt
```

**سوال‌ها:**
- کدام فایل واقعاً نهایی است؟
- دیروز چه تغییری دادیم؟
- توسط چه کسی تغییر داده شده؟

---

## تمرین ۲: ساخت اولین مخزن محلی (Local Repository)

```bash
mkdir git-playground
cd git-playground
git init
echo "Hello Git" > readme.txt
git status
git add readme.txt
git commit -m "First commit"
```

> نکته مهم: گیت تا وقتی `commit` نکنید، چیزی را ذخیره نمی‌کند!

---

## تمرین ۳: تفاوت Working Directory و Staging Area

```bash
echo "Line 2" >> readme.txt
git add readme.txt          # حالا فایل در Staging است
echo "Line 3" >> readme.txt # این تغییر هنوز در Staging نیست
git status
```

**سوال:** فایل `readme.txt` الان در کدام محیط است؟ چرا؟

---

## تمرین ۴: مشاهده تاریخچه و بازگشت به عقب

```bash
git log --oneline

# خرابکاری عمدی
echo "BROKEN CODE" > readme.txt

# بازگشت به نسخه قبلی
git checkout -- readme.txt
```

---

## تمرین ۵: شاخه‌ها (Branching)

```bash
git branch                          # مشاهده شاخه‌ها
git checkout -b feature-about       # ساخت و جابجایی به شاخه جدید
echo "محتوای صفحه درباره ما" > about.txt
git add .
git commit -m "Add about page"
git checkout main                   # برگشت به main
ls                                  # فایل about.txt ناپدید شد!
```

**نتیجه:** هر شاخه یک دنیای مستقل است.

> تمرین تعاملی عالی: https://learngitbranching.js.org/

---

## تمرین ۶: کار با مخزن راه دور (Remote)

```bash
git clone https://github.com/Erfanm83/git-workshop-1404.git
cd git-workshop-1404

# ساخت شاخه شخصی
git checkout -b feature-yourname    # به جای yourname نام خودتان را بگذارید

# انجام دو تغییر و کامیت
echo "تغییر اول توسط من" >> CONTRIBUTIONS.md
git add .
git commit -m "اضافه کردن نام خودم به لیست"

echo "تغییر دوم" > my-file.txt
git add .
git commit -m "ایجاد فایل شخصی"

# ارسال به گیت‌هاب
git push origin feature-yourname
```

سپس در گیت‌هاب یک **Pull Request** باز کنید.

---

**سپاس از شرکت در کارگاه!**  
هر سوالی داشتید در Issues این مخزن بپرسید یا به من پیام دهید.

عرفان محمودی  
[@Erfanm83](https://github.com/Erfanm83)
