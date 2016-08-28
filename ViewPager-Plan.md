# Intro to ViewPager
- Like a listview that you swipe horizontally
- Need to write 3 (4?) methods to make it work
- finding the context inside to create view
- Page Left/Right buffer and increase it

# Basics:
## Views
## Fragment
## Pager Indicators
- ViewPager v4.PagerTabStrip
- ViewPager v4.PagerTitleStrip
- ViewPagerIndicator
    display title, different adapter

# Advanced
## Updating DataSet
    - Dirty trick : http://stackoverflow.com/a/7287121/1343997
    - using tag http://stackoverflow.com/questions/7263291/viewpager-pageradapter-not-updating-the-view/8024557#8024557
## Design
### Clickable tab, background selector, Ripple background selector
### Update title -> vpi.notifyDataSetChanged
### Update title color
update title color when selected -> xml color selector

## Architecture
### 



##############################
# ViewPager Dry
- Like listview evolving into recyclerView

# ViewPager Indicator -> Jake Wharton
- make it work
- Display title
- Update title -> 
- Change Title Color on selection
- Smooth highlight tab bottom change between tabs

# Custom View
## Same basic View repeated on each tab
- Handle like RecyclerVier

## Same List repeated on each tab

## Different View on each
- Provide View at creation via add


# Fragment ViewPager
## Same Fragment
## Different Fragment

a lire:
- articles sur ViewPager
- android doc, mentionne que c'est une classe vouee a changer?
- voir viewpager sur stack overflow, les plus grosses questions
- Google Architecture -> est-ce qu'il utilise un view pager dans sa structure?

https://developer.android.com/reference/android/support/v4/view/ViewPager.html


