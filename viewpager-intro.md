
A ViewPager is a View letting user swiping left and right to display full pages. As the opposite of LinearLayout or RecyclerView, a swipe don't pass over multiple views. One swipe, one new page displayed. 

Let's start by the basics by implementing a really simple ViewPager.

# Basics
## ViewPager with views

We have to start by implementing the Main Activity layout, including the ViewPager.

```XML
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".activity.main.MainActivity">

    <android.support.v4.view.ViewPager
        android:id="@+id/activity_main_viewpager"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    </android.support.v4.view.ViewPager>
</RelativeLayout>
```

It's not that different from an old ListView, and as all lists it needs his Adapter. 
ViewPager have a particular one named PagerAdapter. To make it work we needs to implement at least 4 methods:
- instantiateItem 
- getCount
- isViewFromObject
- destroyItem

Without those, you will be in trouble.

Let's create the most basic PagerAdapter to display a single TextView.

```java
public class MainActivityPagerAdapter extends PagerAdapter {

    private final List<PageData> itemList;

    public MainActivityPagerAdapter(List<PageData> itemList) {
        this.itemList = itemList;
    }

    @Override // here we create the view that will be displayed at <position>
    public Object instantiateItem(ViewGroup container, int position) { 
        // inflates the view but not attaching it to his parent
        View view = LayoutInflater.from(container.getContext()).inflate(R.layout.item_page_data, container, false);
        bindData(view, position);
        container.addView(view);
        return view;
    }

    private void bindData(View view, int position) {
        PageData pageData = itemList.get(position);

        TextView textView = (TextView) view.findViewById(R.id.item_page_data_text);
        textView.setText(pageData.text);
    }

    @Override // let the ViewPager know how much items we display
    public int getCount() {
        return itemList.size(); 
    }

    @Override // in instantiateItem we return an object, so it compares it to the view added in the inflator
    public boolean isViewFromObject(View view, Object object) { 
        return view == object; 
    }

    @Override // when the item is not in the displayed page we remove it 
    public void destroyItem(ViewGroup container, int position, Object object) {
        container.removeView((View) object); 
    }
}
```

In the instantiateItem I sometimes see inflating view like this
```View view = container.inflate(context, R.layout.item_page_data, null);```:
- Avoid to inject the activity's context into your ViewPager if you can get it from an other way (container.getContext() by example)
- Avoid to set null as root in your inflater. 

> Lint will now warn you not to pass in null for root. Your app won’t crash in this scenario, but it can misbehave. When your child View doesn’t know the correct LayoutParams for its root ViewGroup, it will try to determine them on its own using generateDefaultLayoutParams.
These default LayoutParams might not be what you desired. The LayoutParams that you specified in XML will get ignored. We might have specified that our child View should match the width of our parent View, but ended up with our parent View wrapping its own content and ending up much smaller than we expected.
Sean Farrell in [Understanding Android's LayoutInflater.inflate()][layoutInflaterExplanation]

Finally we have to tie everything together. 
- get data we will display
- create adapter we wrote above
- and set it to the ViewPager

```java
public class MainActivity extends AppCompatActivity {
    @BindView(R.id.activity_main_viewpager) ViewPager activityMainViewpager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        ButterKnife.bind(this);

        initializeViews();
    }

    private void initializeViews() {
        List<PageData> pageDataList = getPageDataList();
        MainActivityPagerAdapter adapter = new MainActivityPagerAdapter(pageDataList);
        activityMainViewpager.setAdapter(adapter);
    }

    private List<PageData> getPageDataList() {
        List<PageData> dummyDataList = new ArrayList<>();
        dummyDataList.add(new PageData("This is going to be"));
        dummyDataList.add(new PageData("LEGEN"));
        dummyDataList.add(new PageData("... wait for it ..."));
        dummyDataList.add(new PageData("DARY"));

        return dummyDataList;
    }
}
```

Here we go, our ViewPager is displayed.

![Simple View pager animated][viewPagerAnimated]

## Adding a Pager Indicator
### 

Can be used with Fragments and Views

# To Speak about
- Like a listview that you swipe horizontally
- finding the context inside to create view
- Page Left/Right buffer and increase it

<!-- Images -->
[viewPagerAnimated]:images/simpleviewpager-view.gif

<!-- LINKS -->
[layoutInflaterExplanation]:https://www.bignerdranch.com/blog/understanding-androids-layoutinflater-inflate/


