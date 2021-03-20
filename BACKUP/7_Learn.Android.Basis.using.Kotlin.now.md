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

---

## Notes about Fragement:        
Ref: 
- [Fragments and the Navigation Component](https://developer.android.com/codelabs/basic-android-kotlin-training-fragments-navigation-component?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-3-pathway-2%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-training-fragments-navigation-component#2)
-[Pass data between destinations  |  Android Developers](https://developer.android.com/guide/navigation/navigation-pass-data) 


😃Also I just finished the example app called Word App: [Word App](https://github.com/Jasmine-liang/Android-basis#word-app)
😆 Now moving to **_Learn how to use Android Jetpack Architecture components_**  ->  Unscramble App 

---

## Notes about ViewModel
### 👋🏻Update: I finished the Unscramble app, it was so much fun buiding it! [unscramble-app](https://github.com/Jasmine-liang/Android-basis#unscramble-app)
### delegate class
- provides getter and setter functions of the property and handles its changes.
- Property delegation in Kotlin helps you to handoff the getter-setter responsibility to a different class


A delegate property is defined using the by clause and a delegate class instance:
```kotlin
var <property-name> : <property-type> by <delegate-class>()

```
In the Unscramble App:
```kotlin
private val viewModel: GameViewModel by viewModels()
```
use the property delegate approach and delegate the responsibility of the `viewModel `object to a separate class called viewModels. That means when you access the viewModel object, it is handled internally by the delegate class, viewModels. The delegate class creates the `viewModel `object for you on the first access, and retains its value through configuration changes and returns the value when requested.
### backing property
A backing property allows you to return something from a getter other than the exact object.
```kotlin
// Declare private mutable variable that can only be modified
// within the class it is declared.
private var _count = 0 

// Declare another public immutable field and override its getter method. 
// Return the private property's value in the getter method.
// When count is accessed, the get() function is called and
// the value of _count is returned. 
val count: Int
   get() = _count
   
```
Ref: [Store data in ViewModel](https://developer.android.com/codelabs/basic-android-kotlin-training-viewmodel?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-3-pathway-3%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-training-viewmodel#14)
### LiveData observers and binding expressions
- LiveData is an observable data holder class that is lifecycle-aware.



---

### Update: I finished the Cupcake app in the Advanced Navigation codelab😁 [Cupcake App](https://github.com/Jasmine-liang/Android-basis#cupcake-app)
### ViewModel best practices
In a **ViewModel**, it is a recommended practice to not expose view model data as **public** variables. Otherwise the app data can be modified in unexpected ways by the external classes and create edge cases your app didn't expect to handle. Instead, make these mutable properties **private**, implement a **backing property**, and expose a public immutable version of each property, if needed. The convention is to prefix the name of the private mutable properties with an underscore (_).
### Apply scope function
apply is a scope function in the Kotlin standard library. It executes a block of code within the context of an object. It forms a temporary scope, and in that scope, you can access the object without its name. The common use case for apply is to configure an object. Such calls can be read as "apply the following assignments to the object."
```kotlin
clark.apply {
    firstName = "Clark"
    lastName = "James"
    age = 18
}

// The equivalent code without apply scope function would look like the following.

clark.firstName = "Clark"
clark.lastName = "James"
clark.age = 18
```
### Navigation and the back stack
- Android keeps a back stack of all the destinations you've visited, with each new destination being pushed onto the stack.
- By tapping the **Up** or **Back** button, you can pop destinations off the back stack.
Using the **Jetpack Navigation component** helps you push and pop fragment destinations off the back stack, so that the default Back button behavior comes for free.
- Specify the `app:popUpTo` attribute on an action in the navigation graph, in order to pop destinations off the back stack until the specified one in the attribute value.
- Specify `app:popUpToInclusive="true" `on an action when the destination specified in` app:popUpTo` should also be popped off the back stack.
- Use a `plurals `resource if you want to use different string resources based on quantity, such as the singular or plural case.

---

## Now learning about **Room** and **RecycleView**
### Room
- Room is a database library that's part of Android Jetpack. Under the hood, the Room library is an abstraction layer on top of a SQLite database
- Room does all the hard work to get from Kotlin data classes to entities that can be stored in SQLite tables, and from function declarations to SQL queries.      
- @Volatile. The value of a volatile variable will never be cached, and all writes and reads will be done to and from the main memory.
### coroutine
- Kotlin coroutines let you convert callback-based code to sequential code. Code written sequentially is typically easier to read and maintain. 


I like the this example about **asynchronous**

> let's say you have a question that requires research, and you politely request to ask a colleague to find the answer. Your colleague then starts to work on it by themselves. You can continue to do other unrelated work that doesn't depend on the answer until your colleague returns with an answer. In this example, your colleague is doing the work asynchronously "on a separate thread".

### Transformations
- Use a Transformations map to create a string from a LiveData object every time the object changes.
### CDATA
CDATA means that the data in between these strings includes data that could be interpreted as XML markup, but should not be.
I also learned that `TextView `can render html: [HtmlCompat](https://developer.android.com/reference/androidx/core/text/HtmlCompat). And the return at lables: [Returns and jumps—Kotlin](https://kotlinlang.org/docs/returns.html#return-at-labels)