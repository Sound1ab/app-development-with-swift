# UIKit - sdk

A view is a clear rectangular shape that can be customized to display anything on the screen. Text, images, lines, and graphics are all created using instances of UIView.

To display a view onscreen, you need to give it a frame—which consists of a size and a position—and add it to the view hierarchy. The area within the view is its bounds.

## Set initial view controller 

Select the view controller in the document outline and select `Is initial view controller` in attributes inspector.

![](initial-view-controller.png)

## Segues

Create a segue in the interface builder by right click and dragging from a button to in a screen to another another screen. 

![](seques.png)

### Unwinding

To unwind a bunch of segue transition back to the original screen. Add the following code to the original screen:

```swift
@IBAction func unwindSegue(unwindSegue: UIStoryboardSegue) {
  // Can send data back to the original screen
}
```

Then from the unwinding screen, right click and drag from a button to the `exit` button:

![](unwind-segue.png)

### Passing information between segues

To pass information from an original screen to the next when it segues, the following function is created in the original screen

```swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
    segue.destination.navigationItem.title = "New screen's title text"
}
```

This function makes available the incoming screen, so we can attached information to it.

### Programmatic segues

By naming segues created in IB we can prepare and call them in code. First create a generic segue from one view controller to another.

![](programmatic-segues-1.png)

Select the segue and name it in the attributes inspector

![](programmatic-segues-2.png)

In some function you can then push the segue by calling:

```swift
@IBAction func pushToYellow(_ sender: UIButton) {
    performSegue(withIdentifier: "yellow", sender: nil)
}
```

## Navigation controllers

Too embed an entire storyboard flow in a navigation controller. Select the view controller of the first screen in the Document Outline and choose `Editor > Embed In > Navigation Controller`.

![](navigation-cointroller.png)

When you add a navigation controller in this way, a `navigation item` is added to the root view controller in the Document outline. This allows you to edit the title of the controller as well as its back button. If you want to do a similar thing to other view controllers, navigation items can be taken from the object library and added to the Document outline.

![](navigation-item-1.png)
![](navigation-item-2.png)

### Bar button

If a `navigation item` has been added, you can add bar buttons to the navigation. These can be left or right handed buttons on the navigation controller for generic actions like `save` or `bookmark`.

![](bar-button-1.png)
![](bar-button-2.png)

### Large titles

Select the `Naviation Bar` in the `Navigation Controller Scene` and select `Prefer Large Titles` in the attributes inspector

![](large-titles.png)

## Tab bar controllers

Select the initial view controller in IB and choose `Editor > Embed In > Tabbar Controller`.

![](tabbar-1.png)

### Add more tabs

Create new view controller in IB then drag from the `tab bar controller` to the new view controller.

![](tabbar-2.png)

Select `view controllers` under `relationship segue` in the pop up menu.

![](tabbar-3.png)

### Customize tab bar

Select tab bar item in the Document outline and make changes in the attributes inspector.

![](tabbar-4.png)

### Badges

Can be added either in the attributes inspector or programmatically.

```swift
tabBarItem.badgeValue = "!"
```