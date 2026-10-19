# ANSWERS

## 1. GitHub repository link
https://github.com/irenetalictic-alt/flutter_basics_lab

## 2. Last three build() called lines (Activity 2)
```
build() called: 4 glasses
build() called: 5 glasses
build() called: 6 glasses
```

## 3. Observations

### Activity 2
When I moved `_glasses++` outside of `setState()`, the number on the screen did not change when I tapped +. The value changed in the code, but Flutter was not told to redraw the screen, so `build()` was not called.

### Activity 3
When I removed `Expanded` from the Humidity box, it became very narrow because it only used the space its text needed. The other three boxes shared the leftover space. So `Expanded` is what makes the boxes equal in width.

### Activity 5
I changed the button corner radius in `buildTheme()` from 8 to 20. The Elevated button became more rounded. The Outlined and Save buttons did not change because that setting only works for ElevatedButton.

## 4. Review questions

**1. What is the difference between a StatelessWidget and a StatefulWidget?**
A StatelessWidget never changes after it is drawn. A StatefulWidget has data that can change while the app runs. Example of stateless: `ProfileCard` in Activity 1. Example of stateful: `WaterTrackerPage` in Activity 2.

**2. Why is a StatefulWidget written as two classes?**
The first class (`WaterTrackerPage`) only creates the State object. The second class (`_WaterTrackerPageState`) keeps the data that changes (`_glasses`) and has the `build()` method. The State object stays alive, so the data is not lost when the screen is redrawn.

**3. In Activity 2, what happened when you changed `_glasses` outside `setState()`? Why?**
The number on the screen did not update. Without `setState()`, Flutter does not know the data changed, so it does not call `build()` again.

**4. When is `build()` called in the Debug Console?**
It is called when the screen is first drawn, and again every time `setState()` runs, such as after tapping +, - or Reset. It is also called after a hot reload.

**5. What are the main axis and cross axis of a Row and a Column?**
In a Row, the main axis is horizontal (left to right) and the cross axis is vertical. In a Column, the main axis is vertical (top to bottom) and the cross axis is horizontal.

**6. In Activity 3, what happened when you removed `Expanded`? What does `Expanded` do?**
The Humidity box became narrow and only as wide as its content. `Expanded` makes a widget fill the free space in a Row or Column. When several widgets use it, they share that space equally.

**7. Why use `GridView.builder` instead of a Column with many children?**
`GridView.builder` only builds the cards that are visible, so it is faster for long lists. It also scrolls by itself and arranges the items in columns. A Column builds everything at once and does not scroll, so it can overflow the screen.

**8. How do `Stack` and `Positioned` create the Best seller badge?**
A `Stack` places widgets on top of each other. The icon, name and price are the bottom layer. The badge is a `Positioned` widget (`top: 8, left: 8`) that sits on top in the top-left corner. It only appears when `item.bestSeller` is true.

**9. What is the difference between customizing with ThemeData and with a style on one widget?**
`ThemeData` changes the look of the whole app from one place. Example: `elevatedButtonTheme` in `buildTheme()` styles every ElevatedButton. A style on one widget only changes that widget. Example: the `CircleAvatar` in the ListTile has its own `backgroundColor`.

**10. When you flip the dark-mode switch, which widget holds the state and how does the change reach MaterialApp?**
`_ThemeDemoAppState` holds the state (`_isDark`). The switch calls `onDarkChanged`, which is the `_setDark` method passed down from the parent. `_setDark` calls `setState()`, so the app rebuilds and `MaterialApp` receives the new `themeMode` (dark).