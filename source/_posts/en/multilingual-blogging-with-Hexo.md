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


We'll assume you want to write in English (_en_) and Arabic (_ar_) posts or pages.

First of all, we'll modify your current `_config.yml` file

### `_config.yml`

The `_config.yml` of your blog should contain the language attributes, like
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

`locale: en` or `locale: ar` for example, determines the langauge of your blog. Now we should have the theme language files defined.

###  i18n theme localizations

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

> At the time of this writing, this blog uses [Rexo](https://github.com/bluemix/hexo-theme-rexo) theme, that has support for left-to-right (LTR) and right-to-left (RTL) writings. 


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

Unlike English, the Arabic language is written from right-to-left (RTL language). So, writing Arabic content inside English one will make the Arabic flows in the same as the English direction, which is wrong.

So, I've created two _tag_ plugins that foce RTL or LTR direction when writing.


### [hexo-tag-rtl](https://github.com/bluemix/hexo-tag-rtl) 
You can use it to force RTL layout direction when used in a mixed with LTR (e.g., English).

If you have an English text and you want to have Arabic inside it:

{% codeblock line_number:false highlight:true %}{% raw %}
    {% rtl %}
    مقتطفات من بعض الحكم
    {% endrtl %}

    “A small leak will sink a great ship.” - Benjamin Franklin

    {% rtl %}
    "لو أنك عشتَ في الماضي و تصرفت كأنك في الماضي ، سوف يكون صعباً على المُستقبلِ أن يراكَ." - Body of Lies
    {% endrtl %}{% endraw %}
{% endcodeblock %} 


### [hexo-tag-ltr](https://github.com/bluemix/hexo-tag-ltr)
Is the inverse to the above one.

Now, if you have an Arabic text and you want to write English inside:

{% codeblock lang:plain line_number:false highlight:true %}{% raw %}
    مقتطفات من بعض الحكم

    {% ltr %}
    “A small leak will sink a great ship.” - Benjamin Franklin
    {% endltr %}

    "لو أنك عشتَ في الماضي و تصرفت كأنك في الماضي ، سوف يكون صعباً على المُستقبلِ أن يراكَ." - Body of Lies
{% endraw %}
{% endcodeblock %}


And that is it! 
Please see this site source code in order to understand how I am writing mixed RTL and LTR languages.


 
> This is my first wirting since two years ago, so if you found anything unclear or there are discrepancies, please let me know about it in the comments 😇
