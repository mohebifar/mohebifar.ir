---
layout: post
title:  "محتوای gzip در وب، مزایا و اشکال‌ها"
date:   2014-01-25 18:01:13
tags: [GZIP, HTTP Response GZIP, Accept-encoding, cache gzip]
categories: HTTP
---

 با توجه به [RFC2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.3) یک درخواست http می‌تواند شامل فیلد هدر `accept-encoding` باشد.

برای مثال: 

    Accept-Encoding: compress, gzip
    
چرا یک مرورگر چنین اطلاعاتی به وب‌سرور ارسال می‌کند ؟  خیلی ساده ! مرورگر به وب‌سرور اطلاع می‌دهد که قادر به decode کردن gzip هست. (بحث ما در این مطلب صرفاٌ در مورد gzip است.)

در این صورت می‌توان فایل‌های asset از قبیل JS و CSS و یا حتی HTML پاسخ را فشرده کرد. 

فشرده‌سازی محتوا مزیت‌ها و اشکال‌هایی هست. می‌خواهیم این سوال را بررسی کنیم که **چه زمانی باید محتوا را gzip کنیم؟**

**مزایا**

1. فشرده‌سازی زمان دریافت فایل توسط کاربران را کاهش می‌دهد.

2. مصرف پهنای باند و ترافیک شبکه را کاهش می‌دهد.

**اشکال‌ها**

1. عملیات فشرده‌سازی، بار پردازشی را افزایش می‌دهد.

در کل این کار هیچ ضرری برای کاربران ندارد !

نحوه فعال‌سازی در وب‌سرور آپاچی
--------------------------
 ابتدا مطمئن شوید که ماژول `mod_deflate` فعال است.

    LoadModule deflate_module modules/mod_deflate.so

سپس این قطه تنظیمات زیر را در فایل `httpd.conf` اضافه کنید.

    <IfModule mod_deflate.c>
      AddOutputFilterByType DEFLATE text/text text/html text/plain text/xml text/css application/x-javascript application/javascript application/json
    </IfModule>

اما این ماژول gzip محتواهای فایل‌های ایستا را cache نمی‌کند و به ازای هر درخواست عملیات فشرده‌سازی مجددا انجام می‌شود.
