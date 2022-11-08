### Убираем строку состояния (./res/values/themes.xml):
```xml
<resources xmlns:tools="http://schemas.android.com/tools">
    <style name="..." parent="...">
        <item name="android:windowFullscreen">true</item>
        <item name="android:windowNoTitle">true</item>
    </style>
</resources>
```

### Убираем ActionBar (./res/values/themes.xml):
```xml
<resources xmlns:tools="http://schemas.android.com/tools">
    <style name="..." parent="Theme.MaterialComponents.Light.NoActionBar">
        <!-- code... -->
    </style>
</resources>
```

### Убираем оставшееся место для строки состояния (на некоторых устройствах):
#### ./res/values/themes.xml
```xml
<resources xmlns:tools="http://schemas.android.com/tools">
    <style name="..." parent="...">
        <item name="android:windowLayoutInDisplayCutoutMode">shortEdges</item>
    </style>
</resources>
```
#### ./main/*/Activity.java
```java
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.view.WindowCompat;
import androidx.core.view.WindowInsetsCompat;
import androidx.core.view.WindowInsetsControllerCompat;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        WindowCompat.setDecorFitsSystemWindows(getWindow(), false);
        WindowInsetsControllerCompat windowInsetsCompat = new WindowInsetsControllerCompat(getWindow(), getWindow().getDecorView());
        windowInsetsCompat.hide(WindowInsetsCompat.Type.statusBars());
        windowInsetsCompat.setSystemBarsBehavior(WindowInsetsControllerCompat.BEHAVIOR_SHOW_TRANSIENT_BARS_BY_SWIPE);
    }
}
```
