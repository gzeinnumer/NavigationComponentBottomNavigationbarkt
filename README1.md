# RecyclerviewCountAllValue

```gradle
//todo 1
implementation 'androidx.navigation:navigation-fragment-ktx:2.3.0'
implementation 'androidx.navigation:navigation-ui-ktx:2.3.0'
```

```kotlin
//todo 2 make fragment
class HomeFragment : Fragment() {
    ...
}
```

```kotlin
//todo 3 make fragment
class CartFragment : Fragment() {
    ...
}
```

```kotlin
//todo 4 make fragment
class ProfileFragment : Fragment() {
    ...
}
```

- res->menu->menu.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
<!--todo 5-->
    <item
        android:id="@+id/homeFragment"
        android:icon="@drawable/ic_home_black_24dp"
        android:title="Home" />
    <item
        android:id="@+id/cartFragment"
        android:icon="@drawable/ic_shopping_cart_black_24dp"
        android:title="Cart" />
    <item
        android:id="@+id/profileFragment"
        android:icon="@drawable/ic_person_black_24dp"
        android:title="Profile" />
</menu>
```

- res->navigation->my_nav.xml
```
<?xml version="1.0" encoding="utf-8"?>
<navigation xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/my_nav"
    app:startDestination="@id/homeFragment">
<!--todo 6-->
    <fragment
        android:id="@+id/homeFragment"
        android:name="com.gzeinnumer.navigationcomponentbottomnavigationbarkt.fr.HomeFragment"
        android:label="fragment_home"
        tools:layout="@layout/fragment_home" />
    <fragment
        android:id="@+id/cartFragment"
        android:name="com.gzeinnumer.navigationcomponentbottomnavigationbarkt.fr.CartFragment"
        android:label="fragment_cart"
        tools:layout="@layout/fragment_cart" />
    <fragment
        android:id="@+id/profileFragment"
        android:name="com.gzeinnumer.navigationcomponentbottomnavigationbarkt.fr.ProfileFragment"
        android:label="fragment_profile"
        tools:layout="@layout/fragment_profile" />
</navigation>
```

- res->layout->activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

<!--todo 7-->
    <fragment
        android:id="@+id/fragment"
        android:name="androidx.navigation.fragment.NavHostFragment"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:defaultNavHost="true"
        app:navGraph="@navigation/my_nav" />

    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/bottom_navigation"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:menu="@menu/menu" />
</LinearLayout>
```

```
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        //todo 8
        val navController = findNavController(R.id.fragment)
        val bottomNavigationView = findViewById<BottomNavigationView>(R.id.bottom_navigation)
        bottomNavigationView.setupWithNavController(navController)
    }
}
```

---

```
Copyright 2021 M. Fadli Zein
```
