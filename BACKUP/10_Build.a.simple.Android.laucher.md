# [Build a simple Android laucher](https://github.com/Jasmine-liang/gitblog/issues/10)

## What it looks like
![laucher](https://user-images.githubusercontent.com/63624438/115945642-36e44280-a4ef-11eb-99c1-f8d6edcf381d.jpg)


---

## Challenge from _Android Programming: The Big Nerd Ranch Guild, 4th Edition_
Show also icons in RecyclerView.
### Chapter 23
Steps to consider to make a laucher:
- Find launchable activities which are simply activities with intent filters that include a **MAIN** `action `and a **LAUNCHER** `category`
- Create an implicit intent and get a list of activities that match the intent from `PackageManager`
- Query the activities through **PackageManager.queryIntentActivities** and get a list containing **ResolveInfo**  object, which contains lables, along with other metadata like icon in it
- Create a explicit intent to start the selected activity

---
### Code
_**MainActivity.kt**_
```kotlin
import android.content.Intent
import android.content.pm.ResolveInfo
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.util.Log
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.ImageView
import android.widget.TextView
import androidx.recyclerview.widget.LinearLayoutManager
import androidx.recyclerview.widget.RecyclerView
private const val TAG = "MainActivity"
class MainActivity : AppCompatActivity() {


    private lateinit var recyclerView: RecyclerView


    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        recyclerView = findViewById(R.id.app_recycler_view)
        recyclerView.layoutManager = LinearLayoutManager(this)
        setupAdapter()
    }

    private fun setupAdapter() {
        val startupIntent = Intent(Intent.ACTION_MAIN).apply {
            addCategory(Intent.CATEGORY_LAUNCHER)
        }

        val packageManager = packageManager
        val activities = packageManager.queryIntentActivities(startupIntent, 0)
        activities.sortWith { a, b ->
            String.CASE_INSENSITIVE_ORDER.compare(
                a.loadLabel(packageManager).toString(),
                b.loadLabel(packageManager).toString()
            )
        }
        recyclerView.adapter = ActivityAdapter(activities)
    }

    private  class ActivityHolder(itemView: View) :
            RecyclerView.ViewHolder(itemView),
            View.OnClickListener {

        val appIcon: ImageView = itemView.findViewById(R.id.app_icon)
        val appName: TextView = itemView.findViewById(R.id.app_name)
        private lateinit var resolveInfo: ResolveInfo

        init {
           itemView.setOnClickListener(this)
        }

        fun bindActivity(resolveInfo: ResolveInfo) {
            this.resolveInfo = resolveInfo
            val packageManager = itemView.context.packageManager
            appName.text = resolveInfo.loadLabel(packageManager).toString()
            appIcon.setImageDrawable(resolveInfo.loadIcon(packageManager))

        }

        override fun onClick(view: View) {
            val activityInfo = resolveInfo.activityInfo

            val intent = Intent(Intent.ACTION_MAIN).apply {
                setClassName(activityInfo.applicationInfo.packageName,
                        activityInfo.name)
                addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
            }

            val context = view.context
            context.startActivity(intent)
        }
    }

    private class ActivityAdapter(val activities: List<ResolveInfo>) :
            RecyclerView.Adapter<ActivityHolder>() {

        override fun onCreateViewHolder(container: ViewGroup, viewType: Int):
                ActivityHolder {
            val layoutInflater = LayoutInflater.from(container.context)
            val view = layoutInflater
                    .inflate(R.layout.list_of_apps, container, false)

            return ActivityHolder(view)
        }

        override fun onBindViewHolder(holder: ActivityHolder, position: Int) {
            val resolveInfo = activities[position]
            holder.bindActivity(resolveInfo)
        }

        override fun getItemCount(): Int {
            return activities.size
        }
    }
}
```