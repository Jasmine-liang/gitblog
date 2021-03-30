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