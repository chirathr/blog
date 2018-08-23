---
layout: post
title: Android - List of Cards using RecyclerView
categories: Android
tags: Android, Cards, Material Card, List, RecyclerView, Adapter, ViewHolder
comments: true
---

![RecyclerView](/public/images/2018-08-23-android-recycler-view/main_image.jpg)

<div class="message">
    RecyclerView is used to display a scrolling list of elements based on a large data set or data that 
    changes frequently.  
</div>

### Add the support library for RecyclerView and MaterialDesign.

To Access RecyclerView and MaterialCard we need the v7 support library and the material design library.

{% highlight bash %}
dependencies {
    implementation 'com.android.support:recyclerview-v7:28.0.0-rc01'
    implementation 'com.google.android.material:material:1.0.0-rc01'
}
{% endhighlight %}

<div class="message">
    <strong>Note: </strong> The above dependencies are for Android P(SDK 28). For more details on using material design
    in your app, visit the 
    <a href="https://github.com/material-components/material-components-android/blob/master/docs/getting-started.md">getting started guide</a>.
</div>

### Inherit app theme from MaterialComponents

Change the parent of you main `AppTheme` to `Theme.MaterialComponents.Light.DarkActionBar` in your `styles.xml`.

{% highlight xml %}

<!-- Base application theme. -->
<style name="AppTheme" parent="Theme.MaterialComponents.Light.DarkActionBar">
    <!-- Customize your theme here. -->
    <item name="colorPrimary">@color/colorPrimary</item>
    <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
    <item name="colorAccent">@color/colorAccent</item>
</style>

{% endhighlight %}

### Add RecyclerView to layout

{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/recycler_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:scrollbars="vertical"/>

</androidx.constraintlayout.widget.ConstraintLayout>

{% endhighlight %}

### Create the layout for a single card list item

We will create the layout for each card list item in the `list_item.xml` file. Here the `MaterialCardView`
and `MaterialButton` is used to create the layout.

##### A single list item

<img src="/public/images/2018-08-23-android-recycler-view/list-item.png" alt="Card List Item" style="border: 1px solid #e8e8e8; margin-top: 20px" width="350px"/>

##### list_item.xml

{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<?xml version="1.0" encoding="utf-8"?>
<com.google.android.material.card.MaterialCardView
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    app:cardCornerRadius="3dp"
    app:cardElevation="2dp">
    <androidx.constraintlayout.widget.ConstraintLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginBottom="8dp">

        <ImageView
            android:id="@+id/imageView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            android:adjustViewBounds="true"
            app:srcCompat="@drawable/list_image" />

        <TextView
            android:id="@+id/card_title"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginStart="16dp"
            android:layout_marginLeft="16dp"
            android:layout_marginTop="16dp"
            android:text="Title goes here"
            style="@style/TextAppearance.MaterialComponents.Headline6"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/imageView" />

        <TextView
            android:id="@+id/card_subtitle"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:text="Subtitle goes here"
            style="@style/TextAppearance.MaterialComponents.Caption"
            app:layout_constraintStart_toStartOf="@+id/card_title"
            app:layout_constraintTop_toBottomOf="@+id/card_title" />

        <com.google.android.material.button.MaterialButton
            android:id="@+id/action_button_1"
            style="@style/Widget.MaterialComponents.Button.TextButton"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="16dp"
            android:text="ACTION 1"
            android:textSize="15sp"
            android:textAppearance="
            @style/TextAppearance.MaterialComponents.Headline6"
            app:layout_constraintStart_toStartOf="@+id/card_subtitle"
            app:layout_constraintTop_toBottomOf="@+id/card_subtitle" />

        <com.google.android.material.button.MaterialButton
            android:id="@+id/action_button_2"
            style="@style/Widget.MaterialComponents.Button.TextButton"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginStart="32dp"
            android:layout_marginLeft="32dp"
            android:text="ACTION 2"
            android:textSize="15sp"
            android:textAppearance="
            @style/TextAppearance.MaterialComponents.Headline6"
            app:layout_constraintBottom_toTopOf="@+id/action_button_1"
            app:layout_constraintStart_toEndOf="@+id/action_button_1"
            app:layout_constraintTop_toBottomOf="@+id/action_button_1" />
    </androidx.constraintlayout.widget.ConstraintLayout>
</com.google.android.material.card.MaterialCardView>

{% endhighlight %}

### Create a simple data model

We will create a simple class that will hold the data for each of the Card list items.

{% highlight java %}
public class DataModel {
    private int imageDrawable;
    private String title;
    private String subTitle;

    public DataModel(int id) {
        imageDrawable = R.drawable.list_image;
        title = String.format(Locale.ENGLISH, "Title %d Goes Here", id);
        subTitle = String.format(Locale.ENGLISH, "Sub title %d goes here", id);
    }

    public int getImageDrawable() {
        return imageDrawable;
    }

    public String getTitle() {
        return title;
    }

    public String getSubTitle() {
        return subTitle;
    }
}
{% endhighlight %}


### Create the View Holder

Inside your Adapter class create a public static `ViewHolder` class that extents `RecyclerView.ViewHolder`.
The ViewHolder will be used to cache the the view objects, this improves the performance as it reduces the expensice task 
of `findViewById` each time the user scrolls.

{% highlight java %}
public class MyAdapter extends RecyclerView.Adapter<MyAdapter.MyViewHolder> {

    private List<DataModel> dataModelList;
    private Context mContext;

    // View holder class whose objects represent each list item
    public static class MyViewHolder extends RecyclerView.ViewHolder {
        public ImageView cardImageView;
        public TextView titleTextView;
        public TextView subTitleTextView;

        public MyViewHolder(@NonNull View itemView) {
            super(itemView);
            cardImageView = itemView.findViewById(R.id.imageView);
            titleTextView = itemView.findViewById(R.id.card_title);
            subTitleTextView = itemView.findViewById(R.id.card_subtitle);
        }

        public void bindData(DataModel dataModel, Context context) {
            cardImageView.setImageDrawable(ContextCompat.getDrawable(context, R.drawable.list_image));
            titleTextView.setText(dataModel.getTitle());
            subTitleTextView.setText(dataModel.getSubTitle());
        }
    }
{% endhighlight %}

Here we have a ImageView and two TextViews which we will use to update the Image, Title and subtitle.

### Complete the List Adapter

The `MyAdapter` class should extend `RecyclerView.Adapter` and we need to override the functions 
`onCreateViewHolder()`, `onBindViewHolder()` and `getItemCount()`.

Create a constructor that takes in a List of DataModel objects. This list will be used to populate our RecyclerView.

{% highlight java %}
public class MyAdapter extends RecyclerView.Adapter<MyAdapter.MyViewHolder> {

    private List<DataModel> dataModelList;
    private Context mContext;

    // View holder class whose objects represent each list item
    public static class MyViewHolder extends RecyclerView.ViewHolder {...}

    public MyAdapter(List<DataModel> modelList, Context context) {
        dataModelList = modelList;
        mContext = context;
    }

    @NonNull
    @Override
    public MyViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        // Inflate out card list item
        View view = LayoutInflater.from(parent.getContext())
                .inflate(R.layout.list_item, parent, false);
        // Return a new view holder
        return new MyViewHolder(view);
    }

    @Override
    public void onBindViewHolder(@NonNull MyViewHolder holder, int position) {
        // Bind data for the item at position
        holder.bindData(dataModelList.get(position), mContext);
    }

    @Override
    public int getItemCount() {
        // Return the total number of items
        return dataModelList.size();
    }
}
{% endhighlight %}

### Set the RecyclerView in the activity.

{% highlight java %}

public class MainActivity extends AppCompatActivity {

    private RecyclerView mRecyclerView;
    private RecyclerView.Adapter mAdapter;
    private RecyclerView.LayoutManager mLayoutManager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mRecyclerView = findViewById(R.id.recycler_view);

        List<DataModel> dataModelList = new ArrayList<>();
        for (int i = 1; i <= 20; ++i) {
            dataModelList.add(new DataModel(i));
        }

        // use this setting to improve performance if you know that changes
        // in content do not change the layout size of the RecyclerView
        mRecyclerView.setHasFixedSize(true);

        // use a linear layout manager
        mLayoutManager = new LinearLayoutManager(this);
        mRecyclerView.setLayoutManager(mLayoutManager);

        // specify an adapter and pass in our data model list
        mAdapter = new MyAdapter(dataModelList, this);
        mRecyclerView.setAdapter(mAdapter);
    }
}

{% endhighlight %}


##### Final Layout

<img src="/public/images/2018-08-23-android-recycler-view/recycler_view.png" alt="Card List Item" style="border: 1px solid #e8e8e8; margin-top: 20px" width="350px"/>
