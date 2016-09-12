Writing post that will be displayed in http://www.dubedout.eu, NOT FINAL.

Let's learn how to build a great ViewPager leveraging the support-v4 library for the Pager Indicator.
But what's a ViewPager? A ViewPager is a View letting user swiping left and right to display pages. Unlike ListViews and RecyclerViews, the swipe will stop on the next Page. We often see examples of FragmentViewPager but less often from his simpler View centric one.

We will learn here how to add a ViewPager on our Activity.

# ViewPager
## Data
For this example we will create an object that will hold the data that will be displayed in the ```TextView```.

```java
public class PageData {
    final String text;

    public PageData(String text) {
        this.text = text;
    }
}
```

## Layout
Now we write the MainActivity Layout including the ViewPager. *Do not forget to add support-v4 in your build.graddle.*

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

## Adapter
A ViewPager is not a lot different from a ListView and it need his own PagerAdapter that will handle the data.

To make it work we need to implement four methods:
- instantiateItem 
- getCount
- isViewFromObject
- destroyItem

If you forget isViewFromObject, your ViewPager will not display the view.  
If you forget destroyItem, you will get a crash when the ViewPager will try to remove unused Views.

Let's create the PagerAdapter.

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

In the instantiateItem I sometimes see inflating views like this: ```View view = container.inflate(context, R.layout.item_page_data, null);```. There is two "errors":
- Do not inject the activity's context into your ViewPager if you can get it from an other way (container.getContext() by example)
- Do not set null as root in your inflater

As Sean Farrell explains it weell in [Understanding Android's LayoutInflater.inflate()][layoutInflaterExplanation]

> Lint will now warn you not to pass in null for root. Your app won’t crash in this scenario, but it can misbehave. When your child View doesn’t know the correct LayoutParams for its root ViewGroup, it will try to determine them on its own using generateDefaultLayoutParams.
These default LayoutParams might not be what you desired. The LayoutParams that you specified in XML will get ignored. We might have specified that our child View should match the width of our parent View, but ended up with our parent View wrapping its own content and ending up much smaller than we expected. 

## Activity

The final step is to tie everything together. 

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

# Adding a Pager Indicator
A Pager Indicator is a View that displays the current page and let the user know where he is. It can be dots, tabs, titles, or other.
On the support-v4 library we can find ```PagerTabStrip```, ```PagerTitleStrip``` that we will study. You can find a lot more of other displays with the [ViewPagerIndicator][ViewPagerIndicator], [PagerSlidingTabStrip][PagerSlidingTabStrip], [CircleIndicator][CircleIndicator], etc...

## Android Support-v4 library
To be able to display a title we need to Override the ```getPageTitle(int position)``` method. To do so we need to provide a title in the adapter.
You can use a simple switch case with a title but I don't find this very clean. 
First, you will need to inject the activity context to be able to use the ressources and access the multiple languages version via the ```getString()```. 
Then, If you need to add a page in one point in time, you will have to modify the switch case and the ```itemList``` accordingly. In my opinion it's error prone.

So let's start by modifying our data holder.

```java
public class PageData {
    final String title;
    final String text;

    public PageData(String title, String text) {
        this.title = title;
        this.text = text;
    }
}
```

We need now to add the title when creating the data.

```java
// MainActivity
private List<PageData> getPageDataList() {
   List<PageData> dummyDataList = new ArrayList<>();
   dummyDataList.add(new PageData("Page 1", "This is going to be"));
   dummyDataList.add(new PageData("Page 2", "LEGEN"));
   dummyDataList.add(new PageData("Page 3", "... wait for it ..."));
   dummyDataList.add(new PageData("Page 4", "DARY"));

   return dummyDataList;
}
```

Finally we Override the getPageTitle method and return the correct title.

```java
// MainActivityPagerAdapter
@Override
public CharSequence getPageTitle(int position) {
    return itemList.get(position).title;
}
```

### v4.PagerTitleStrip
PagerTitleStrip will display the Title provided and display the previous and next page title and they are not clickable to scroll to the next/previous page.

![PagerTitleStrip rendering][pagerTitleStripAnimated]

To use it you will need to add it into the ViewPager like below.

```
<android.support.v4.view.ViewPager
    android:id="@+id/activity_main_viewpager"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <android.support.v4.view.PagerTitleStrip
        android:id="@+id/activity_main_pager_indicator"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        />
</android.support.v4.view.ViewPager>
```

### v4.PagerTabStrip
PagerTabStrip is similar with slight differences. It is separated from the content by a divider, it underlines the selected page and let the user click on the next and previous page to navigate. 

![PagerTabStrip rendering][pagerTabStripAnimated]

```xml
<android.support.v4.view.ViewPager
    android:id="@+id/activity_main_viewpager"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <android.support.v4.view.PagerTabStrip
        android:id="@+id/activity_main_pager_indicator"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        />
</android.support.v4.view.ViewPager>
```

## Offscreen Pages Buffer
By default a ViewPager will load the previous and next page. If you have a predefined number of pages, by example a list of Local, Country and World Ranking. It can be usefull to increase it to have a smooth scroll experience between them.

To do it, you will need to call ```public void setOffscreenPageLimit(int limit)``` and providing a higher limit (1 is the default setting). But always keep in mind the more you set, the more the device will have to retain in memory. On low end devices and complex Views it can cause OutOfMemory crash and burn your UI to ashes... 

To keep all tabs from previous example (4 pages), we will need to set it to 3 offscreen pages or list size minus one (current page viewed).

```java
//MainActivity
private void initializeViews() {
    List<PageData> pageDataList = getPageDataList();
    MainActivityPagerAdapter adapter = new MainActivityPagerAdapter(pageDataList);
    activityMainViewpager.setAdapter(adapter);
    activityMainViewpager.setOffscreenPageLimit(pageDataList.size() - 1); // <-- new line
}
```

## OnPageChangeListener
If you need to get an event each time the page is switched use the code below. ```SimpleOnPageChangeListener``` saves some boiler plate code.

```java
activityMainViewpager.addOnPageChangeListener(new ViewPager.SimpleOnPageChangeListener() {
    @Override
    public void onPageSelected(int position) {
        // your code 
        Toast.makeText(MainActivity.this, "New page selected: "+position, Toast.LENGTH_SHORT).show();
    }
});
```

# Wrap Up
Here we are, we have done a complete ViewPager with some basic informations. I'd like to speak about a lot of other tweaks on ViewPagers like the Auto Scroll Infinite View Pager that a future client will try to sneak in your UI but it will be for another day :)

Ow, If you want to learn about the FragmentViewPager, take a look to the [CodePath Android Guides][CodePathFragmentViewPager]. They have done an amazing job compiling all this data.

You can find the code in my [ViewPager-Code repo][GitCode]


<!-- Images -->
[viewPagerAnimated]:images/simpleviewpager-view.gif
[pagerTabStripAnimated]:images/pagertabstrip-view.gif
[pagerTitleStripAnimated]:images/pagertitlestrip-view.gif

<!-- LINKS -->
[layoutInflaterExplanation]:https://www.bignerdranch.com/blog/understanding-androids-layoutinflater-inflate/
[ViewPagerIndicator]:https://github.com/JakeWharton/ViewPagerIndicator
[PagerSlidingTabStrip]:https://github.com/astuetz/PagerSlidingTabStrip
[CircleIndicator]:https://github.com/ongakuer/CircleIndicator
[CodePathFragmentViewPager]:https://github.com/codepath/android_guides/wiki/ViewPager-with-FragmentPagerAdapter
[GitCode]:https://github.com/ViBlog/ViewPager-Code


