# [Building record: Todo-list app using MVVM architecture](https://github.com/Jasmine-liang/gitblog/issues/9)

# Show case
code: [Todolist app](https://github.com/Jasmine-liang/todo-list-app)
https://user-images.githubusercontent.com/63624438/118086286-48d24a80-b3f6-11eb-80eb-8394bd686de8.mp4
## Day 1
### Why Coordianate Layout?
 - I want ToolBar to collapse or hide. Google made it really easy by introducing AppBarLayout & CollapsingToolbarLayout, which both work best under a CoordinatorLayout.
 
### Why Relative Layout?
- RelativeLayout enables you to specify how child views are positioned relative to each other.
### Trade-off using `@Parcelize` annotation
 We know implementing `Parcelable` on an entity class so the entity object will be put into an `Intent `object and passed between activities/fragment. Is it a good practice? What about Repository pattern? [android - Is it good practice implementing Parcelable on a Room database entity? - Stack Overflow](https://stackoverflow.com/questions/56058576/is-it-good-practice-implementing-parcelable-on-a-room-database-entity)
### Additional knowledge


- ellipsize: [What does ellipsize mean in android?](https://stackoverflow.com/questions/13313996/what-does-ellipsize-mean-in-android/13314069)
- tool-attributes: [Tools attributes reference](https://developer.android.com/studio/write/tool-attributes.html)  tldr: `tools:text ` means the text won't be generated into APK

---

## Day 2
## Room with ViewModel, Coordinate example
Reference:
- [Android Kotlin Fundamentals: 6.2 Coroutines and Room](https://developer.android.com/codelabs/kotlin-android-training-coroutines-and-room#3)
- [Android Room with a View - Kotlin](https://developer.android.com/codelabs/android-room-with-a-view-kotlin?index=..%2F..index#0)
## Dagger codelab
- [Using Dagger in your Android app - Kotlin](https://developer.android.com/codelabs/android-dagger#8)

---

## Day 3
### Add a Callback when the database object is initialized
There are two ways of adding a Callback:     
- one is adding it in `.addCallback( obejct : RoomDatabase.Callback(){// implementation})`
- one is adding it in Database class as a **nested** class 
### Add a Search Feature
Here are some refs that helps to understand some related code:
- [inline, noinline, crossinline — What do they mean? | by Ben Daniel A. | AndroidPub | Medium](https://medium.com/android-news/inline-noinline-crossinline-what-do-they-mean-b13f48e113c2)
- [Higher-Order Functions](https://play.kotlinlang.org/byExample/04_functional/01_Higher-Order%20Functions)
### Problem solved:
[android - RecycleView displaying only the first item - Stack Overflow](https://stackoverflow.com/questions/35906652/recycleview-displaying-only-the-first-item)

---

## Day 4
### Room vs DataStore, Why use DataSource for Menu ？
If you have a need for partial updates, referential integrity, or large/complex datasets, you should consider using Room instead of DataStore. DataStore is ideal for small or simple datasets and does not support partial updates or referential integrity.
### Preference
Preference DataStore, like SharedPreferences, accesses data based on keys, without defining a schema upfront.
- Codelab ref: [Working with Preferences DataStore](https://developer.android.com/codelabs/android-preferences-datastore#5)
- [Data and file storage overview  |  Android Developers](https://developer.android.com/training/data-storage#pref)

---

## Day 5 (Update checked Tasks)
- First make some changes to Adapter where we catch the **Click** action on a single item
- Then we send this click to Fragment
### Better way to handle onClickListener in RecycleView
- [A Better Way to Handle Click Action in a RecyclerVIew Item. | OOZOU](https://oozou.com/blog/a-better-way-to-handle-click-action-in-a-recyclerview-item-60)

---

## Day 6 (Add Swipe-Delete-And-Undo)
I followed this article [Step by Step: RecyclerView Swipe to Delete and Undo](https://medium.com/@zackcosborn/step-by-step-recyclerview-swipe-to-delete-and-undo-7bbae1fce27e), and learned how to implemented a custom UI for _Swipe-Delete_ feature, this article also helps: [Android RecyclerView Swipe To Delete And Undo](https://www.journaldev.com/23164/android-recyclerview-swipe-to-delete-undo)         
Also learned some insights about _SingleLiveEvent_: [Android SingleLiveEvent Redux with Kotlin Flow | by Michael Ferguson | ProAndroidDev](https://proandroiddev.com/android-singleliveevent-redux-with-kotlin-flow-b755c70bb055)


---

## Day 7 (Navigate between fragments)
### Use Safe Args to pass data between fragments
- Here we pass `task` object between `TaskFragment` and `Add/EditTaskFragment`, ref: [Pass data between destinations  |  Android Developers](https://developer.android.com/guide/navigation/navigation-pass-data)
### Use `SavedStateHandle` to restore UI state when app’s process being stopped 
The scenario usually is: while you editing a task, you receive a phone call and leave the app in the background. We want what you just edited stays the same when you come back to the app. So you don't need to type it again:)       
Ref: [ViewModels: Persistence, onSaveInstanceState(), Restoring UI State and Loaders | Android Developers](https://medium.com/androiddevelopers/viewmodels-persistence-onsaveinstancestate-restoring-ui-state-and-loaders-fc7cc4a6c090)