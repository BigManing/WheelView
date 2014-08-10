WheelView
=========

WheelView is an Android library that allows drawables to be placed on a rotatable wheel. It behaves like a Circular ListView where items rotate rather than scroll vertically. It isn't limited by the number of items that can fit on the wheel since it will cycle through each position when the wheel is rotated. The wheel can be rotated at any angle and from any position.

The `WheelView` can be used as a way to select one item from a list. The `SelectionAngle` determines what position on the wheel is selected. You can also receive a callback for when an item is clicked, and whether it is selected. Have a look at the sample for a working example!

The library is still in its infancy so if there are any bugs or missing features please let me know!

![1]
![2]

Note - Frame rate is much better than these poorly converted gifs!

Usage
-----

1) Add a custom view in xml
```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <com.lukedeighton.wheelview.WheelView
        android:id="@+id/wheelview"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:wheelColor="@color/grey_400"
        app:rotatableWheelDrawable="false"
        app:selectionAngle="90.0"
        app:wheelPosition="bottom"
        app:wheelOffsetY="60dp"
        app:repeatItems="true"
        app:wheelRadius="276dp"
        app:wheelItemCount="14"
        app:wheelPadding="13dp"
        app:wheelItemRadius="43dp"/>
</RelativeLayout>
```

2) Set a `WheelAdapter` similar to how you would set an adapter with a ListView
```java
wheelView.setAdapter(new WheelAdapter() {
    @Override
    public Drawable getDrawable(int position) {
        //return drawable here - the position can be seen in the gifs above
    }

    @Override
    public int getCount() {
        //return the count
    }
});
```

Listeners
---------

1) A listener for when the closest item to the `SelectionAngle` changes.
```java
wheelView.setOnWheelItemSelectedListener(new WheelView.OnWheelItemSelectListener() {
    @Override
    public void onWheelItemSelected(WheelView parent, int position) {
        //the adapter position that is closest to the selection angle
    }
});
```

2) A listener for when an item is clicked.
```java
wheelView.setOnWheelItemClickListener(new WheelView.OnWheelItemClickListener() {
    @Override
    public void onWheelItemClick(WheelView parent, int position, boolean isSelected) {
        //the position in the adapter and whether it is closest to the selection angle
    }
});
```

3) A listener for when the wheel's angle is changed.
```java
wheelView.setOnWheelAngleChangeListener(new WheelView.OnWheelAngleChangeListener() {
    @Override
    public void onWheelAngleChange(float angle) {
        //the new angle of the wheel
    }
});
```

Attributes
----------

The WheelView is highly customisable with many attributes that can be set via xml or programmatically (recommend using xml as programmatically set attributes is half implemented at the moment). Here are the custom attributes that can be declared in xml:

  * wheelDrawable
  * wheelColor
  * emptyItemDrawable
  * emptyItemColor
  * selectionDrawable
  * selectionColor
  * selectionPadding
  * selectionAngle
  * repeatItems
  * wheelRadius
  * wheelItemRadius
  * rotatableWheelDrawable
  * wheelOffsetX
  * wheelOffsetY
  * wheelItemCount
  * wheelItemAngle
  * wheelToItemDistance
  * wheelPosition
  * wheelPadding
  * wheelItemTransformer
  * selectionTransformer

License
-------

Apache License Version 2.0
http://apache.org/licenses/LICENSE-2.0.txt

[1]: ./Graphics/bottom_wheel.gif
[2]: ./Graphics/center_wheel.gif
