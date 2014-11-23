---
layout: post
title:  "پردازش SMILES با رازی"
date:   2014-02-15 20:28:13
tags: [Razi, SMILES, SMILES Parser, Chemistry Library, Chemistry Java Library]
categories: chemistry
---

رازی یک کتابخانه برای جاوا است که برای توسعه نرم‌افزارهای شیمی کاربرد دارد.
در حال حاضر رازی می‌تواند فایل‌های SMILES را پردازش کند و یک مدل شی‌گرا از مولکول را برگرداند.

1. کتابخانه را [دانلود][1] کنیدو آن را در پروژه وارد کنید.
2. یک وهله از `com.razi.formats.smiles.Reader` بسازید.
3. متد `set` را فرا بخوانید مقدار ورودی را به آن تزریق کنید.
4. متد `process` را صدا بزنید.
5. تمام شد !

کد آن به این شکل خواهد بود :

{% highlight java %}
Reader sr = new Reader();
sr.set("C(=O)O");
sr.process();

Molecule mol = sr.get();
{% endhighlight %}

حالا می‌توانید از توصیف‌کننده‌ها استفاده کنید. در حال حاضر رازی یک توصیف‌کننده‌ی شمارشی برای مولکول دارد. از کلاس `com.razi.descriptor.molecular.CountDescriptor` برای این کار استفاده کنید.

{% highlight java %}
cd.countAtoms(); // Number of all atoms
cd.countBonds(); // Number of all bonds
cd.countBondsByOrder(2); // Number of bonds with order 2
cd.countAtomsByElement(element); // Number of all atoms which are the same with given element
{% endhighlight %}

اگر به شیمی‌فناوری‌اطلاعات علاقه‌مند هستید، رازی را در [گیت‌هاب](https://github.com/mohebifar/Razi) دنبال کنید.


  [1]: https://github.com/mohebifar/Razi/tree/master/dist "Download"
