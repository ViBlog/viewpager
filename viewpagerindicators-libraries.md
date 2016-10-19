Let's have a sneak peak about the ViewPager Indicator libraries you should now and what happened for some. In this article, we will start from the most starred one to the least one.

# ViewPagerIndicator (Jake Wharton) 
8150 stars, 127 issues, 80 Pull Requests, no activity for 4 years. [Library,][vpi_github_lib][ _Sample code._][vpi_sample_code]  

Grandfather of all of them, this library haven't changed for the last 4 years. I would avoid it for the lack of material ripple effect, and the hard time theming the TitlePageIndicator. On the other hand, the simple indicators still works well and are easily customisable.

```compile 'com.github.JakeWharton:ViewPagerIndicator:2.4.1'```

## Title
Tab clickable but without ripple effect  
![ViewPagerIndicator Titles][vpi_titles]

## Simple Indicators
![ViewPagerIndicator Simple Indicators][vpi_simple]

## Icon
![ViewPagerIndicator Icons][vpi_icons] 

# PagerSlidingTabStrip (Andreas Stuetz)
5500 stars, 153 issues, 53 Pull Requests, no activity for 3 years. [Library,][pagerSlidingTabStrip_github_lib][ _Sample Code._][pagerSlidingTabStrip_sample_code]

Same as the previous library, with 3 years without updates, it doesn't support Material Ripple effect and you will have to create it by hand. I would prefer the Delight NavigationTabStrip (below) instead.

```compile 'com.astuetz:pagerslidingtabstrip:1.0.1'```


## Title
Tab clickable but without ripple effect  
![PagerSlidingTabStrip Title][psts_title]

# SpringIndicator (Chenupt)
1650 stars, 15 issues, 3 Pull Requests. [Library,][springIndicator_github_lib][ _Sample Code._][springIndicator_sample_code]

I didn't know this one and I was really impressed by it. Works flawlessly, really easy to configure. I love the effect by sliding. It doesn't really fit with titles, I would use it for simple indicators without titles where it shines.

```compile 'com.github.chenupt.android:springindicator:1.0.2@aar'```

## Title
![Spring Indicator][springindicator_gif]

## Simple Indicator
<!-- Create example without titles -->

# RubberIndicator (Lyndon Chin)
1315 stars, 6 issues, 1 Pull Request. [Library, ][androidRubberIndicator_github_lib]

Rubber indicator is a nice discovery too. Inspired by a web version it have a nice animation we some rebound. This library have some drawback. One major bug is unsolved and there is no activity for some time. Unfortunately you can't find it on JCenter. Jitpack can help you there if you still want to use the gradle compile.

```
allprojects {
    repositories {
        [...]
        maven { url "https://jitpack.io" }
```

```compile 'com.github.LyndonChin:AndroidRubberIndicator:ea734614d3'```

## Design
![AndroidRubberIndicator][androidRubberIndicator_gif]
<!-- Needs self example -->

# DevLight NavigationTabTrip
1109 stars, 4 issues, [Library, ][devlight_navigationtabstrip_github_lib]

This is my little favorite, I was looking for a slick, material, good looking library for our last product. It's really easy to configure in XML. It has some drawbacks, first you need to send the title using their ```setTitle(String... args)``` method and you can't ```notifyDataSetChanged()```. But I actually prefer it this way instead of returning a getPageTitle in the adapter, handling a ```Context``` to use the ```getString()```. It can be a problem if your ViewPager titles tend to change often. 
```
allprojects {
    repositories {
        [...]
        maven { url 'http://dl.bintray.com/gigamole/maven/' }
```
```compile 'com.github.devlight.navigationtabstrip:navigationtabstrip:1.0.4'```

## Title
![Navigation Tab Strip][devlight_navigationtabstrip]

# Stepper Indicator
830 Stars, 6 issues, 2 Pull Requests, [Library,][stepperindicator_github_lib]

Stepper Indicator is the **perfect fit** for your Onboarding. This library is still young but very promising. Animations are perfect, well executed. Congrats to the developer. 

```
allprojects {
    repositories {
        [...]
        maven { url "https://jitpack.io" }
```
```compile 'com.github.badoualy:stepper-indicator:1.0.6'```

## Design
![Android Stepper Indicator][stepperindicator]

# Magic Indicator
1000 stars, 2 issues, [Library.][magicindicator_github_link]

This is the most impressive of all the ViewPager Indicator libraries. Simple, it groups all the previous one in a single library. The saddest thing? All commits are in chinese... I have to be able to see what have been changed in the commits without spending time in the code. If you can speak Chinese, don't look further it's the library you need.

```
allprojects {
    repositories {
        [...]
        maven { url "https://jitpack.io" }
```
```compile 'com.github.hackware1993:MagicIndicator:1.4.0'```

## Designs
![Magic Indicator][magicindicator]

# Circle Indicator
215 stars, 4 issues, [Library. ][circlepagerindicator_github_lib]

Classic circle indicator, It can be an alternative of the ViewPagerIndicator from Jake Wharton with some drawbacks. No JCenter, No JitPack, you will have to do this manually. It can be configured easily via XML with some little mode changes. Only 10 commits on the lib, low activity with some issues. I would probably use Jake Wharton library for something like this. I have created a jitpack build if you want to use it (waiting that my pull request in his library will be merged)

```
allprojects {
    repositories {
        [...]
        maven { url "https://jitpack.io" }
```
```compile 'com.github.ViFork:CircleIndicator:234db76d94'```


## Design
 <!-- add it -->
 
# Ink Page Indicator (David Pacioianu)
200 stars, 8 issues, 1 Pull Request, [Library, ][inkpageindicator_github_lib]

Very similar to SpringIndicator, the only difference is that the plain circle move last in the animation. Some issues not solved and no activity for the past 4 months. It stills look as a possible candidate if you really need this animation instead of Spring Indicator library.

```compile 'com.pacioianu.david:ink-page-indicator:1.2.0'```

## Design
![Ink Page Indicator][inkpageindicator]

# Toolbar Indicator
161 stars, [Library, ][toolbarindicator_github_lib]

Simple ActionBar Indicator with title that works well with beautiful fade in. 

## Design
create it

# Pod Slider
60 stars, [Library, ][podslider_github_lib]

Pod Slider is a little library not well known featuring no issues and a reactive developer. It can be used for paging.

## Design
![Pod Slider][podslider_green]

# Ultra Indicator
25 stars, [Library, ][ultraindicator_github_lib]

Little extra for your weird developer side. I don't know where you can implement this but it's a funny indicator.

## Design
![Ultra Indicator][ultraindicator]


<!-- Images -->
[vpi_titles]:images/vpi_title_indicators.gif
[vpi_simple]:images/vpi_simple_indicators.gif
[vpi_icons]:images/vpi_icon_indicators.gif
[psts_title]:images/psts_title_indicators.gif
[springindicator_gif]:images/springindicator_title_indicators.gif
[androidRubberIndicator_gif]:images/androidrubberindicator.gif
[devlight_navigationtabstrip]:images/devlight_navigationtabstrip.gif
[stepperindicator]:images/stepperindicator.gif
[magicindicator]:images/magicindicator.gif
<!--  Circle indicator image -->
[inkpageindicator]:images/inkpageindicator.gif
[podslider_green]:images/podslider_green.gif
[ultraindicator]:images/ultraindicator.gif

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

[magicindicator_github_link]:https://github.com/hackware1993/MagicIndicator

[circlepagerindicator_github_lib]:https://github.com/THEONE10211024/CircleIndicator

[inkpageindicator_github_lib]:https://github.com/DavidPacioianu/InkPageIndicator

[toolbarindicator_github_lib]:https://github.com/nekocode/ToolbarIndicator

[ultraindicator_github_lib]:https://github.com/andyxialm/UltraIndicator


























