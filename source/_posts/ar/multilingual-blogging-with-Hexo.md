---
title: التدوين بأكثر من لغة مع هيكسو
lang: ar
direction: rtl
date: 2017-08-01 22:48:28
tags:
    - تدوين
    - هيكسو
    - عربي
    - انشاء مدونة
    - موقع ثابت
    - ستاتك سايت
---

> قبل أن تبدء ، يفضل أن تكون لديك معرفة بسيطة في آلية عمل [هيكسو](https://hexo.io). الرجاء قراءة [التنصيب](https://hexo.io/docs/setup.html) و [الإستخدام](https://hexo.io/docs/writing.html) و [ اللغات (i18n)](https://hexo.io/docs/internationalization.html).

سنفترض أنك تريد كتابة مقالات باللغتين الإنگليزية و العربية. في بالبداية ، سنغيِّر  `_config.yml` لإضافة بعض الخيارات.


### `_config.yml`

هذا الفايل ، يجب أن يحتوي على البعض من الخيارات لدعم أكثر من لغة
{% ltr %}
{% codeblock line_number:false highlight:true %}
language:
  - en
  - ar
locale: en
i18n:
  type: [page, post]
  generator: [index, archive, category, tag]
permalink_defaults:
  lang: en
i18n_dir: :lang

{% endcodeblock %}
{% endltr %}

مثلاً ، `locale: en` أو `locale: ar` ، يحددان لغة المدونة. في نفس الوقت ، علينا الآن أن نضيف ملفات اللغة للثيم.

###  لغات الثيم (i18n)

لأجل عمل هذهِ الخطوة ، لابد من وجود مجلد `languages` في داخل مجلد الثيم.

{% ltr %}
{% codeblock line_number:false highlight:true %}
.
├── themes
|   └── theme-name
|   |   └── languages
|   |   |   └── en.yml
|   |   |   └── ar.yml

{% endcodeblock %}
{% endltr %}

طبعاً ، إن لم تجد ملف اللغة العربية مثلاً ، تستطيع تكرار ملف اللغة الإنگليزية `en.yml` و تسميته إلى `ar.yml` و من ثم قُم بترجمة الكلمات.

> حالياً ، هذهِ المدونة تستخدم ثيم [ريكسو](https://github.com/bluemix/hexo-theme-rexo) الذي يدعم الكتابة من اليسار إلى اليمين و العكس أيضاً.



### التدوين بأكثر من لغة

   لنفرض الأن أنك تريد كتابة مقالة باللغة العربية حول الـ lambdas في [الكوتلن](http://kotlinlang.org) 
   
`hexo new 'Kotlin lambdas' --lang ar`

هذا الإيعاز سيقوم بإنشاء نسخة اللغة العربية في `_posts/ar/Kotlin-lambdas.md`


أما إذا أردت كتابةِ النسخة الإنگليزية
`hexo new 'Kotlin lambdas' --lang en`

و بالتالي فإن هيكلية الفايلات ستكون بالشكل التالي
{% ltr %}
{% codeblock line_number:false highlight:true %}
.
├── source
|   └── _posts
|   |   └── en
|   |   |   └── Kotlin-lambdas.md
|   |   └── ar
|   |   |   └── Kotlin-lambdas.md
{% endcodeblock %}
{% endltr %}


### كتابة الإنگليزية و العربية في مقالة واحدة

تكتب اللغة العربية من اليمين لليسار ، أما الإنگليزية فالعكس، أي من اليسار لليمين ، و هذهِ تشكِّل مشكلةً أثناء الكتابة في المقالة المخصصة للغة العربية مثلاً ، حيث لابد من مراعاة إتجاه اللغة الإنگليزية في النص.

لذلك ، هناك أدوات (أو tags) تسهل كتابتك للغتين في النص الواحد.



### [hexo-tag-ltr](https://github.com/bluemix/hexo-tag-ltr)
يمَكِّنُكَ هذا الـ tag من إجبار تحويل إتجاه النص من اليسار إلى اليمين. إي عندما تكون المقالة عربية و تود كتابة الإنگليزية.


{% codeblock lang:plain line_number:false highlight:true %}{% raw %}
    مقتطفات من بعض الحكم

    {% ltr %}
    “A small leak will sink a great ship.” - Benjamin Franklin
    {% endltr %}

    "لو أنك عشتَ في الماضي و تصرفت كأنك في الماضي ، سوف يكون صعباً على المُستقبلِ أن يراكَ." - Body of Lies
{% endraw %}
{% endcodeblock %}


### [hexo-tag-rtl](https://github.com/bluemix/hexo-tag-rtl) 

هذا الـ tag هو عكس الذي سبق ذكره.


{% codeblock line_number:false highlight:true %}{% raw %}
    {% rtl %}
    مقتطفات من بعض الحكم
    {% endrtl %}

    “A small leak will sink a great ship.” - Benjamin Franklin

    {% rtl %}
    "لو أنك عشتَ في الماضي و تصرفت كأنك في الماضي ، سوف يكون صعباً على المُستقبلِ أن يراكَ." - Body of Lies
    {% endrtl %}{% endraw %}
{% endcodeblock %} 



و هذا كل شيء :)


يفضل أن تنظر إلى [كود](https://github.com/bluemix/bluemix.github.io/tree/rexo-theme) هذهِ المدونة لأجل فهم كيفية كتابة العربية و الإنگليزية معاً في مقالٍ واحد.

> لو كانت هناك ضبابية أو غموض في الشرح ، الرجاء أعلمني بذلك في التعليقات. و شكراً جزيلاً 😇
