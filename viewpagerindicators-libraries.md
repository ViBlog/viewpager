When we used to work on **View Pager Indicators** some years ago, we had only one library that we should know: ViewPagerIndicator. It was an awesome job at the time, but we have to let it go. With four years of inactivity and Material Design that have taken over, we should look to **better-suited libraries**. The good news? There is plenty of them, and I will cover some of them and show you how they look in this, _"I have no time to loose to check them all"_ blog post.

As usual, try to contribute to the libraries you use daily. It will help us all in the end.
  
  
# ViewPagerIndicator (Jake Wharton) 
8150 stars, 127 issues, 80 Pull Requests, no activity for 4 years. [Github,][vpi_github_lib] [_Sample code._][vpi_sample_code]  

Grandfather of all of them, this library haven't changed for the last four years. I would avoid it for the lack of material ripple effect, and the hard time for theming the TitlePageIndicator. The simple indicators still work well, are easily customizable but no commits for the last years makes me think twice before using it.

`compile 'com.github.JakeWharton:ViewPagerIndicator:2.4.1'`

## Title
Tab clickable but without ripple effect  
![ViewPagerIndicator Titles][vpi_titles]

## Simple Indicators
![ViewPagerIndicator Simple Indicators][vpi_simple]

## Icon
![ViewPagerIndicator Icons][vpi_icons] 
 
  
# PagerSlidingTabStrip (Andreas Stuetz)
5500 stars, 153 issues, 53 Pull Requests, no activity for 3 years. [Github,][pagerSlidingTabStrip_github_lib] [ _Sample Code._][pagerSlidingTabStrip_sample_code]

Same as the previous library, with three years without updates, it doesn't support Material Ripple effect, and you will have to create it by hand. I would prefer the Delight NavigationTabStrip (below) instead.

`compile 'com.astuetz:pagerslidingtabstrip:1.0.1'`


## Title
Tab clickable but without ripple effect  
![PagerSlidingTabStrip Title][psts_title]

# SpringIndicator (Chenupt)
1650 stars, 15 issues, 3 Pull Requests. [Github,][springIndicator_github_lib] [_Sample Code._][springIndicator_sample_code]

I didn't know this one, and I was impressed. Works flawlessly, really easy to configure. I love the sliding effect. Use it for simple indicators like picture libraries (without titles) where it shines.

`compile 'com.github.chenupt.android:springindicator:1.0.2@aar'`

## Simple Indicator
![Simple Spring Indicator][springindicator_simple_gif]

## Title
![Spring Indicator][springindicator_1_gif]  
![Spring Indicator][springindicator_2_gif]

# RubberIndicator (Lyndon Chin)
1315 stars, 6 issues, 1 Pull Request. [Github][androidRubberIndicator_github_lib]

Rubber indicator is a nice discovery too. Inspired by a web version it has a beautiful animation with rebound. I would love to use this library, but it has some drawback. One major bug is unsolved, and there is no activity for some time. If you want theming, only colors are available for now, and you will have a hard time for resizing this view. To finish, you can't find it on JCenter. Jitpack can help you there if you still want to use the gradle compile.

```
allprojects {
    repositories {
        [...]
        maven { url "https://jitpack.io" }
```

`compile 'com.github.LyndonChin:AndroidRubberIndicator:ea734614d3'`

## Design
![AndroidRubberIndicator][androidRubberIndicator_gif]

# DevLight NavigationTabTrip
1109 stars, 4 issues, [Github][devlight_navigationtabstrip_github_lib]

My favorite, I was looking for a material, good looking library for our last product. It's easy to configure in XML. It has some drawbacks; you need to send the title using their ```setTitle(String... args)``` method and you can't ```notifyDataSetChanged()```. But I prefer it this way instead of returning a getPageTitle in the adapter (and handling a ```Context``` to use the ```getString()```). It can be a problem if your ViewPager titles tend to change often. 

```
allprojects {
    repositories {
        [...]
        maven { url 'http://dl.bintray.com/gigamole/maven/' }
```
`compile 'com.github.devlight.navigationtabstrip:navigationtabstrip:1.0.4'`

## Title
![Navigation Tab Strip][devlight_navigationtabstrip]

# Stepper Indicator
830 Stars, 6 issues, 2 Pull Requests, [Github][stepperindicator_github_lib]

Stepper Indicator is the **perfect fit** for your Onboarding. This library is still young but very promising. Animations are perfect, well executed. Congrats to the developer. 

```
allprojects {
    repositories {
        [...]
        maven { url "https://jitpack.io" }
```
`compile 'com.github.badoualy:stepper-indicator:1.0.6'`

## Design
![Android Stepper Indicator][stepperindicator]

# Magic Indicator
1000 stars, 2 issues, [Github][magicindicator_github_link]

The most impressive of all the ViewPager Indicator libraries. Simple, it groups all the previous one in a single library. The saddest thing? All commits are in Chinese... I have to be able to see what is changing in the commits without reviewing the code. If you can speak Chinese, don't look further it's the library you need.

```
allprojects {
    repositories {
        [...]
        maven { url "https://jitpack.io" }
```
`compile 'com.github.hackware1993:MagicIndicator:1.4.0'`

## Designs
![Magic Indicator][magicindicator]

# Pager Indicator View (Roman Danylyk)
1017 stars, 0 issues, [Github][pageindicatorview_github_lib]

Circle Indicator library that si the perfect alternative to the ```ViewPagerIndicator.CircleIndicator```. The developer is very reactive, it can be configured easily via XML and the documentation is well written. _Just Use It_ 

`compile 'com.romandanylyk:pageindicatorview:0.0.7'`

## Designs

`AnimationType.NONE` added in 0.0.1  
![anim_prev_none][pageindicatorview_none]  

`AnimationType.COLOR` added in 0.0.1  
![anim_prev_color][pageindicatorview_color]  

`AnimationType.SCALE` added in 0.0.1  
![anim_prev_scale][pageindicatorview_scale]  

`AnimationType.SLIDE` added in 0.0.1  
![anim_prev_slide][pageindicatorview_slide]  

`AnimationType.WORM` added in 0.0.1  
![anim_prev_worm][pageindicatorview_worm]  

`AnimationType.FILL` added in 0.0.6  
![anim_prev_worm][pageindicatorview_fill]  

`AnimationType.THIN_WORM` added in 0.0.7  
![anim_prev_thin_worm][pageindicatorview_thinworm]  
     


 
# Ink Page Indicator (David Pacioianu)
200 stars, 8 issues, 1 Pull Request, [Github][inkpageindicator_github_lib]

Very similar to SpringIndicator, the only difference is that the plain circle move last in the animation. Some issues not solved and no activity for the past four months. It stills look like a possible candidate if you need this animation instead of Spring Indicator or PagerIndicatorView library.

`compile 'com.pacioianu.david:ink-page-indicator:1.2.0'`

## Design
![Ink Page Indicator][inkpageindicator]

# Pod Slider
60 stars, [Github][podslider_github_lib]

Pod Slider is a little library (not well known but promising) with no issues and a reactive developer. Used for paging and one letter titles.

`compile 'com.github.bhargavms:PodSLider:1.2.0'`

## Design
![Pod Slider][podslider_green]

# Conclusion
We have taken a look at the most used libraries for ViewPager Indicators. It should cover all your needs and if you want to know how to implement it, take a look at this little app I've done for this purpose [here on github.][LibrarySampleCode]


<!-- Images -->
[vpi_titles]:images/vpi_title_indicators.gif
[vpi_simple]:images/vpi_simple_indicators.gif
[vpi_icons]:images/vpi_icon_indicators.gif
[psts_title]:images/psts_title_indicators.gif
[springindicator_1_gif]:images/springindicator_title_indicators_1.gif
[springindicator_2_gif]:images/springindicator_title_indicators_2.gif
[springindicator_simple_gif]:images/springindicator_title_indicators_without_title.gif
[androidRubberIndicator_gif]:images/android_rubber_indicator_simple.gif
[devlight_navigationtabstrip]:images/devlight_navigation_tab_strip_title.gif
[magicindicator]:images/magicindicator.gif
[stepperindicator]:images/stepperindicator_simple.gif
[pageindicatorview_none]:images/pageindicatorview_anim_prev_none.gif
[pageindicatorview_color]:images/pageindicatorview_anim_prev_color.gif
[pageindicatorview_scale]:images/pageindicatorview_anim_prev_scale.gif
[pageindicatorview_slide]:images/pageindicatorview_anim_prev_slide.gif
[pageindicatorview_worm]:images/pageindicatorview_anim_prev_worm.gif
[pageindicatorview_fill]:images/pageindicatorview_anim_prev_fill.gif
[pageindicatorview_thinworm]:images/pageindicatorview_anim_thin_worm.gif
[inkpageindicator]:images/inkpageindicator_preview.gif

[podslider_green]:images/podslider_preview.gif

<!-- Links -->
[vpi_github_lib]:https://github.com/JakeWharton/ViewPagerIndicator/
[vpi_sample_code]:https://github.com/vdubedout/ViewPagerIndicators-Libraries/blob/master/ViewPagerIndicatorsLibraries/app/src/main/res/layout/activity_view_pager_indicator.xml
[pagerSlidingTabStrip_github_lib]:https://github.com/astuetz/PagerSlidingTabStrip
[pagerSlidingTabStrip_sample_code]:https://github.com/vdubedout/ViewPagerIndicators-Libraries/blob/master/ViewPagerIndicatorsLibraries/app/src/main/res/layout/activity_pager_sliding_tab_strip.xml
[springIndicator_github_lib]:https://github.com/chenupt/SpringIndicator
[springIndicator_sample_code]:https://github.com/vdubedout/ViewPagerIndicators-Libraries/blob/master/ViewPagerIndicatorsLibraries/app/src/main/res/layout/activity_spring_indicator.xml
[androidRubberIndicator_github_lib]:https://github.com/LyndonChin/AndroidRubberIndicator
[devlight_navigationtabstrip_github_lib]:https://github.com/DevLight-Mobile-Agency/NavigationTabStrip
[stepperindicator_github_lib]:https://github.com/badoualy/stepper-indicator
[pageindicatorview_github_lib]:https://github.com/romandanylyk/PageIndicatorView
[magicindicator_github_link]:https://github.com/hackware1993/MagicIndicator
[circlepagerindicator_github_lib]:https://github.com/THEONE10211024/CircleIndicator
[inkpageindicator_github_lib]:https://github.com/DavidPacioianu/InkPageIndicator
[podslider_github_lib]:https://github.com/bhargavms/PodSLider

[LibrarySampleCode]:https://github.com/vdubedout/ViewPagerIndicators-Libraries


























