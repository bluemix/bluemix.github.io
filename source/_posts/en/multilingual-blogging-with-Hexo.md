---
title: Multilingual blogging with Hexo
lang: en
direction: ltr
date: 2017-08-01 22:48:23
tags:
    - blogging
    - hexo
    - multilingual
    - rtl
    - right-to-left
    - arabic
    - hebrew
    - persian
    - create
    - static site generator
    - nodejs
---

> Before your start, you should have a basic understanding of [Hexo](https://hexo.io). Please see Hexo [setup](https://hexo.io/docs/setup.html), [usage](https://hexo.io/docs/writing.html) and [Internationalization (i18n)](https://hexo.io/docs/internationalization.html).



I don't want to say that it is easy to write articles of different
languages in Hexo, but it is easy 😁

### `_config.yml`

Let's suppose you want to write posts in both English and Arabic, then
`_config.yml` of your blog should contain the language attributes, like
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

`locale: en` or `locale: ar` for example, determines the langauge of your blog; and in this case
you should have the theme language files defined.

### Theme i18n localizations

To do this, inside your current `themes` directory, you should have the languages of your site in the `languages` directory.

{% codeblock line_number:false highlight:true %}
.
├── themes
|   └── theme-name
|   |   └── languages
|   |   |   └── en.yml
|   |   |   └── ar.yml

{% endcodeblock %}

If you don't find the target language you want, for example, the Arabic language is not found, you can duplicate the `en.yml` file to `ar.yml` and translate its words.

> At the time of this writing, this blog uses [Rexo](https://github.com/bluemix/hexo-theme-rexo) theme, that has support for RTL and LTR 


### Creating multilingual posts 

Let's suppose we want to write a new English article about [Kotlin](http://kotlinlang.org) lambdas,
`hexo new 'Kotlin lambdas' --lang en`
that will create a new post at `_posts/en/Kotlin-lambdas.md`

and then 
`hexo new 'Kotlin lambdas' --lang ar`
that creates the _Arabic_ version in `_posts/ar/Kotlin lambdas.md`,

and so the files structure will be like this

{% codeblock line_number:false highlight:true %}
.
├── source
|   └── _posts
|   |   └── en
|   |   |   └── Kotlin-lambdas.md
|   |   └── ar
|   |   |   └── Kotlin-lambdas.md
{% endcodeblock %}


### Mixed left-to-right (LTR) and right-to-left (RTL) wirtings

[rtl](https://github.com/bluemix/hexo-tag-rtl)


{% codeblock lang:javascript %} if (rHighlight.test(arg)) {
    arg = arg.replace(rHighlight, function() {
    enable = arguments[1] === 'true';
    return '';
    });
}
{% endcodeblock %} 


{% codeblock line_number:false highlight:true %}{% raw %}
    {% rtl %}
    مقتطفات من بعض الحكم
    {% endrtl %}

    “A small leak will sink a great ship.” - Benjamin Franklin

    {% rtl %}
    "لو أنك عشتَ في الماضي و تصرفت كأنك في الماضي ، سوف يكون صعباً على المُستقبلِ أن يراكَ." - Body of Lies
    {% endrtl %}{% endraw %}
{% endcodeblock %} 


[ltr](https://github.com/bluemix/hexo-tag-ltr)
{% codeblock lang:plain line_number:false highlight:true %}{% raw %}
    مقتطفات من بعض الحكم

    {% ltr %}
    “A small leak will sink a great ship.” - Benjamin Franklin
    {% endltr %}

    "لو أنك عشتَ في الماضي و تصرفت كأنك في الماضي ، سوف يكون صعباً على المُستقبلِ أن يراكَ." - Body of Lies
{% endraw %}
{% endcodeblock %}