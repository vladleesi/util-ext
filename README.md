# kutilicious

[![MavenCentral](https://img.shields.io/maven-central/v/dev.vladleesi.kutilicious/base?versionPrefix=0.5.0)](https://central.sonatype.com/namespace/dev.vladleesi.kutilicious)

Small Kotlin and Android extensions for a better development experience

## Setup

``` groovy
// build.gradle

repositories {
    mavenCentral()
}

dependencies {
    implementation 'dev.vladleesi.kutilicious:base:0.5.0'
    implementation 'dev.vladleesi.kutilicious:android-preferences:0.5.0'
    implementation 'dev.vladleesi.kutilicious:android-view:0.5.0'
}
```

## Base

### Base Extensions
- `tag()`: Returns the tag (simple name) of the class.
### Boolean Extensions
- `ifTrue(block: Boolean.() -> Unit)`: Executes the specified block of code if the Boolean value is true.
- `ifFalse(block: Boolean?.() -> Unit)`: Executes the specified block of code if the Boolean value is false.
- `nullOrFalse()`: Checks if the Boolean value is null or false.
- `orFalse()`: Returns the Boolean value if it is not null, or false if it is null.
### Integer Extensions
- `orZero()`: Returns the integer value if it is not null, or zero if it is null.
- `takePositiveOrNull()`: Returns the positive integer value if it is greater than zero, or null if it is not.
- `isZero()`: Checks if the integer value is zero.
- `isNotZero()`: Checks if the integer value is not zero.
- `divideToPercent(divideTo: Int)`: Divides the integer value by the specified divisor and returns the result as a percentage. Returns 0 if the divisor is 0.
### Float Extensions
- `orZero()`: Returns the float value if it is not null, or zero if it is null.
- `isZero()`: Checks if the float value is zero.
- `isNotZero()`: Checks if the float value is not zero.
### Double Extensions
- `orZero()`: Returns the double value if it is not null, or zero if it is null.
- `isZero()`: Checks if the double value is zero.
- `isNotZero()`: Checks if the double value is not zero.
### BigDecimal Extensions
- `orZero()`: Returns the BigDecimal value if it is not null, or BigDecimal.ZERO if it is null.
- `isZero()`: Checks if the BigDecimal value is zero.
- `isNotZero()`: Checks if the BigDecimal value is not zero.
- `same(value: BigDecimal?)`: Checks if two BigDecimal values are equal.
### String Extensions
- `isNullOrEmptyAfterTrim()`: Implements deprecated logic from PojoUtils.isNull(). Checks if the string is null or the trimmed string is empty.
- `isNotNullOrEmptyAfterTrim()`: Implements deprecated logic from PojoUtils.isNotNull(). Checks if the string is not null and the trimmed string is not empty.
- `firstLetterUpperCase()`: Converts the first letter of the string to uppercase.
- `addMissingPrefix(prefix: String, ignoreCase: Boolean = false)`: Adds a prefix to the string if it doesn't already start with it.
- `isNotNullOrEmpty()`: Checks if the string is not null and not empty.
##### String as URL
- `isUrl()`: Checks if the string is a valid URL.
- `isUrlWithCustomScheme()`: Checks if the string is a URL with a custom scheme.
- `getQueryMap()`: Extracts the query parameters from the string URL and returns them as a map.
- `removeQueries(vararg queryKeys: String)`: Removes the specified query parameters from the string URL and returns the updated URL.

## Android Preferences

1. `editSync`

Synchronously edits SharedPreferences. Changes made using this function are immediately committed using `commit()`.

```kotlin
sharedPreferences.editSync {
    putString("key", "value")
    putInt("count", 5)
}
```

2. `editAsync`

Asynchronously edits SharedPreferences. Changes made using this function are applied using `apply()`.

```kotlin
sharedPreferences.editAsync {
    putBoolean("isFirstLaunch", false)
}
```

3. `get` retrieves a value from SharedPreferences based on a given key and returns it. If the value is not found or is null, it returns a default value.
```kotlin
// Assuming you have an instance of SharedPreferences called "sharedPrefs"
val sharedPreferences = context.getSharedPreferences("mySharedPreferences", Context.MODE_PRIVATE)
// Retrieve a boolean value with the key "isDarkModeEnabled", providing a default value of false
val isDarkModeEnabled = sharedPreferences.get("isDarkModeEnabled", false)
```

4. `putSync` stores a value in SharedPreferences synchronously using a specified key. It returns `true` if the value is successfully stored, and `false` otherwise.
```kotlin
// Assuming you have an instance of SharedPreferences called "sharedPrefs"
val sharedPreferences = context.getSharedPreferences("mySharedPreferences", Context.MODE_PRIVATE)
// Store a boolean value with the key "isDarkModeEnabled"
sharedPreferences.putSync("isDarkModeEnabled", true)
```

5. `putAsync` stores a value in SharedPreferences asynchronously with a specified key. It performs the storage operation in the background and does not return a value.
```kotlin
// Assuming you have an instance of SharedPreferences called "sharedPrefs"
val sharedPreferences = context.getSharedPreferences("mySharedPreferences", Context.MODE_PRIVATE)
// Store a boolean value with the key "isDarkModeEnabled" asynchronously
sharedPreferences.putAsync("isDarkModeEnabled", true)
```

## View Extensions

- `visible()`: Sets the visibility of a View to VISIBLE.
- `gone()`: Sets the visibility of a View to GONE.
- `invisible()`: Sets the visibility of a View to INVISIBLE.
- `addRipple()`: Adds a ripple effect to the background of a View using the theme's selectableItemBackground attribute.
- `addCircleRipple()`: Adds a circular ripple effect to the background of a View using the theme's selectableItemBackgroundBorderless attribute (available for API level 21 and higher).
- `onFocus(block: (hasFocus: Boolean) -> Unit)`: Sets a callback function to be invoked when the focus state of a View changes.

## License

This project is licensed under the [MIT License](LICENSE).