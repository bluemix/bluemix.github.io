---
title: قصاصات كوتلن
lang: ar
direction: rtl
contentId: kotlin-snippets
excerpt: تجربة في كود كوتلن
tags:
  - كوتلن
  - كود
  - اندرويد
---

أجزاء من كود `كوتلن`

{% raw %}
<div dir="ltr">
{% endraw %}

``` kotlin
package io.fomalhaut.shoppingiqdriver.Activities

import io.fomalhaut.shoppingiqdriver.Helpers.PrefsManager
import uk.co.chrisjenx.calligraphy.CalligraphyContextWrapper

open class BaseActivity : android.support.v7.app.AppCompatActivity() {

  override fun onCreate(savedInstanceState: android.os.Bundle?) {
    super.onCreate(savedInstanceState)
    PrefsManager.INSTANCE().reconfigureLayoutAndLocale(this, window)
  }

  override fun onResume() {
    super.onResume()
    PrefsManager.INSTANCE().reconfigureLayoutAndLocale(this, window)
  }

  override fun attachBaseContext(newBase: android.content.Context) {
    super.attachBaseContext(uk.co.chrisjenx.calligraphy.CalligraphyContextWrapper.wrap(newBase))
  }

}
```

{% raw %}
</div>
{% endraw %}

