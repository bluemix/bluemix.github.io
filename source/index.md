---
title: Kotlin snippets
---

I'll try this 'kotlin' code :)


here is an `HTML` snippet
``` html
<html>
  <body> This HTML </body>
</html>

```

and here too,
``` html
<section id="main">
  <div>
    <h1 id="title">{{ .Title }}</h1>
    {{ range .Data.Pages }}
      {{ .Render "summary"}}
    {{ end }}
  </div>
</section>
```

and more
``` html
<section id="main">
  <div>
    <h1 id="title">{{ .Title }}</h1>
    {{ range .Data.Pages }}
      {{ .Render "summary"}}
    {{ end }}
  </div>
```

and...
``` html
  <section id="main">
    <div>
     <h1 id="title">{{ .Title }}</h1>
      {{ range .Data.Pages }}
          {{ .Render "summary"}}
      {{ end }}
    </div>
  </section>
```


`Kotlin` here :D 
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

