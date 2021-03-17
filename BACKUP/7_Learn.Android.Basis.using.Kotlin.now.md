# [Learn Android Basis using Kotlin now](https://github.com/Jasmine-liang/gitblog/issues/7)

Got more familiar using Material theme now, and learned a lot about:
- write clear and clean code
- user experience, like adding `ScrollView` to prevent element from being truncated . This websize helps with Material tools: [Resources - Material Design](https://material.io/resources)     

             
Also I made an app along the course named TipTime which calculates the tip. Ref: [Android-basis: TipTime](https://github.com/Jasmine-liang/Android-basis)

---

Now into the second App, **Affirmations app**. Here are the notes token.
- In Kotlin, the `vararg` modifier allows you to pass a variable number of arguments of the same type into a function or constructor.
- _Adapter_ is a design pattern that adapts the data into something that can be used by RecyclerView, [Use RecyclerView to display a scrollable list](https://developer.android.com/codelabs/basic-android-kotlin-training-recyclerview-scrollable-list?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-2-pathway-3%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-training-recyclerview-scrollable-list#3)

Finally done! I added the seven affirmations that I always recall during meditation.
Ok I push my finished code in here: [Jasmine-liang/Android-basis](https://github.com/Jasmine-liang/Android-basis)

---

Notes about intent and lifecycle:
- 
![intent](https://user-images.githubusercontent.com/63624438/111322050-7a9f8d00-86a3-11eb-914e-38315006e15f.png)
-  function with no name that can immediately be used as an expression—is a really useful concept called a lambda expression
## lambda
```kotlin
costOfServiceEditText.setOnKeyListener { view, keyCode, event -> handleKeyEvent(view, keyCode) }
```
When we look up `OnKeyListener,` the abstract method has the following parameters o`nKey(View v, int keyCode, KeyEvent event)` and returns a `Boolean`. Because of SAM conversions in Kotlin, we can pass in a lambda to `setOnKeyListener()`. Just be sure the lambda has the function type `(View, Int, KeyEvent) -> Boolean`.        

The function body consists of `handleKeyEvent(view, keyCode)`which uses the parameters passed in and returns a `Boolean`
## Lifecycle
when an app is started and `onStart()` is called, the app becomes visible on the screen. When the app is resumed and `onResume()` is called, the app gains the user focus, that is, the user can interact with the app. The part of the lifecycle in which the app is fully on-screen and has user focus is called the interactive lifecycle.

When the app goes into the background, the focus is lost after `onPause()`, and the app is no longer visible after `onStop()`.
### Partially hide the activity
The difference between focus and visibility is important because it is possible for an activity to be **partially visible** on the screen, but not have the user focus. Both onResume() and onPause() have to do with focus. The onResume() method is called when the activity has focus, and onPause() is called when the activity loses focus.
- A `Bundle` is a collection of key-value pairs, where the keys are always strings
-
Notice that `onCreate()` gets a Bundle each time it is called. When your activity is restarted due to a process shut down, the bundle that you saved is passed to `onCreate()`. If your activity was starting fresh, this Bundle in `onCreate() `is null. So if the bundle is not null, you know you're "re-creating" the activity from a previously known point.