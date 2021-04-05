# [Building record: Todo-list app using MVVM architecture](https://github.com/Jasmine-liang/gitblog/issues/9)

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