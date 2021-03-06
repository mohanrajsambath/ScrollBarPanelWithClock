ScrollBarPanelWithClock
==================

Path 2.0  like scrollbar with clock widget for Android.

This is an open source library which uses the scroll bar library. I have added a Clock widget inside the scroll bar panel which gives a Path 2.0  like effect and can be customised according to your needs. Please see the screenshots below to get a better idea.

Screenshot
=========

![without second hand](https://dl.dropboxusercontent.com/u/61919232/learnNcode/ScrollBarPanelWithClock/without_second_hand.png "without second hand")


![with second hand](https://dl.dropboxusercontent.com/u/61919232/learnNcode/ScrollBarPanelWithClock/with_second_hand.png "with second hand")



[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-ScrollBarPanelWithClock-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/1029)


Usage
=====

Check the attached demo sample app.
    
Layout
=====
   
The ExtendedListView replaces a standard ListView widget and provides the ScrollBarPanel capability.
    
```xml
<com.learnNcode.android.ExtendedListView
    xmlns:clock="http://schemas.android.com/apk/res-auto"
    android:id="@android:id/list"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:choiceMode="singleChoice"
    clock:hand_second="@drawable/ic_timer_clock_minute_hand"
    clock:scrollBarPanel="@layout/scrollbarpanel"
    clock:scrollBarPanelInAnimation="@anim/in"
    clock:scrollBarPanelOutAnimation="@anim/out" />
```    

 You can use/edit the clock widget the following way, this should be done in the layout for scrollbar panel:

```xml
<com.learnNcode.android.Clock
    xmlns:clock="http://schemas.android.com/apk/res-auto"
    android:id="@+id/analogClockScroller"
    android:layout_width="25dp"
    android:layout_height="25dp"
    clock:hand_second="@drawable/ic_timer_clock_minute_hand"
    clock:hand_minute="@drawable/ic_timer_clock_minute_hand"
    clock:hand_hour="@drawable/ic_timer_clock_hour_hand"
    clock:hand_dial="@drawable/ic_timer_clock_dialer"/>
```        

Activity
=====

Set your scrollBarPanel
```java
ExtendedListView mListView = (ExtendedListView) findViewById(android.R.id.list);
```

You can attach a position changed listener on the listview and write your desired implementation.

```java
mListView.setOnPositionChangedListener(new OnPositionChangedListener() {

    @Override
    public void onPositionChanged(ExtendedListView listView, int firstVisiblePosition, View scrollBarPanel) {
         Clock analogClockInstance = (Clock) scrollBarPanel.findViewById(R.id.analogClockScroller);

        Time time = new Time();
        analogClockInstance.setSecondHandVisibility(true);  // to visible second hand
        time.set(position+3, position, 5, 0, 0, 0);
        analogClockInstance.onTimeChanged(time);

        }
    }
```

You can also directly implement the OnPositionChangedListener, and write your implementation in the overridden method.

```java
public class MainActivity extends Activity implements OnPositionChangedListener {

    @Override
    public void onPositionChanged(ExtendedListView listView, int position, View scrollBarPanel) {
        Clock analogClockInstance = (Clock) scrollBarPanel.findViewById(R.id.analogClockScroller);
            
        Time time = new Time();
        analogClockInstance.setSecondHandVisibility(true);
        time.set(position+3, position, 5, 0, 0, 0);
        analogClockInstance.onTimeChanged(time);
        }
     }
```
        
 This is how you initialize the clock widget, this should be done inside the OnPositionChanged().
```java
Time timeObj = new Time();
analogClockObj.setSecondHandVisibility(true);
analogClockObj.setVisibility(View.VISIBLE);
timeObj.set(position+3, position, 5, 0, 0, 0); //pass respective values to the clock here.
analogClockObj.onTimeChanged(timeObj);
```

NOTE :
=====

__1]__ You can set visibility for the seconds hand by using setSecondHandVisibility method.
Example: `analogClockObj.setSecondHandVisibility(true); // To show second hand` 

__2]__ You can set visibility for the clock widget by using setVisibility method.
Example: `analogClockObj.setVisibility(View.VISIBLE);`

      
Acknowledgements
==============
 [Android-ScrollBarPanel](https://github.com/rno/Android-ScrollBarPanel) 

License
======

    Copyright 2013 learnNcode

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

Thankyou
=======

  If you like our work say a hi :)
  Happy coding.
      


