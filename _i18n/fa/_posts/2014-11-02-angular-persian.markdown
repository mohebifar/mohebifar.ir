---
layout: post
title:  "ماژول فارسی Angular.js"
date:   2014-11-02 12:30:15
tags: [Angular, Persian]
categories: javascript
---

انگولار یک فریم‌ورک MV* سمت کلاینت است که به زبان جاوا اسکریپت نوشته شده است. با استفاده از این ماژول می‌توانید یک وب‌اپلیکیشن Single Page بنویسید. برای توضیحات بیشتر به وب‌سایت [angularjs.org](https://angularjs.org) مراجعه کنید.
 
از آن‌جایی که در انگولار داده‌ها به صورت خام و معمولا به وسیله یک سرویس RESTful از سرور دریافت می‌شود، برای نمایش یک خروجی مناسب برای کاربران فارسی‌زبان ابزارهایی لازم هست.
 
ماژول فارسی انگولار، یک مجموعه فیلتر کاربردی جهت محلی‌سازی نرم‌فزارهای فارسی، از جمله تبدیل اعداد انگلیسی به فارسی، تبدیل اعداد به حروف، تبدیل کاراکترهای عربی به فارسی، تغییر لی‌اوت کیبورد و ... در اختیار کاربران قرار می‌دهد.
 
برای نصب این ماژول ابتدا `bower` را نصب کنید سپس دستور زیر را اجرا کنید.
 
{% highlight bash %}
$ bower install angular-persian
{% endhighlight %}

سپس ماژول `ngPersian` را به app خود اضافه کنید.

{% highlight javascript %}
var app = angular.module('myApp', ['ngPersian', /* deps ... */]);
{% endhighlight %}

حالا می‌توانید از فیلترهای این ماژول در نماهای برنامه خود استفاده کنید.

{% highlight html %}
<input ng-model="someNumber"> {‌{ someNumber | pNumber }‌}
<input ng-model="price"> {‌{ price | pDigitWords }‌} ریال
{% endhighlight %}

قطعه کد بالا مقدار مدل `someNumber` را با کاراکترهای فارسی نمایش می‌دهد و مقدار مدل `price` را با حروف نمایش می‌دهد. (برای مثال: یک صد و بیست هزار ریال)

[برای خواندن جزئیات بشتر در مورد این ماژول، صفحه گیت‌هاب آن را دنبال کنید.](https://github.com/mohebifar/angular-persian)