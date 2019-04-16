# Tables and Persistence - sdk

## Scroll views

* Can be added in IB by selecting scroll view in the object model and dragging to view controller.

![](images/scroll-view.png)

* Add constraints to make the scroll view fill the screen.

![](images/constraints.png)

* Add a stack view as a subview of scroll view
* Make it the same size as the scroll view

![](images/stack-view.png)

* Add constraints to all edges of the stack view

![](images/stack-view-constraints.png)

* Add a view as a subview of the stack view
* Move to top left corner
* In the Document outline, right-click drag from the view to the scroll view

![](images/view-length-drag.png)

* Select `Equal Widths`

![](images/view-length-equal.png)

### keyboard

When a keyboard displays it can block some of a scroll view. Use the following to push content up inside a scroll view when a keyboard shows.

```swift
func registerForKeyboardNotifications() {
        NotificationCenter.default.addObserver(self, selector: #selector(keyboardWasShown(_:)), name: UIResponder.keyboardDidShowNotification, object: nil)
        NotificationCenter.default.addObserver(self, selector: #selector(keyboardWillBeHidden(_:)), name: UIResponder.keyboardWillHideNotification, object: nil)
    }

    @objc func keyboardWasShown(_ notificiation: NSNotification) {
        guard let info = notificiation.userInfo, let keyboardFrameValue = info[UIResponder.keyboardFrameBeginUserInfoKey] as? NSValue else { return }
        let keyboardFrame = keyboardFrameValue.cgRectValue
        let keyboardSize = keyboardFrame.size
        let contentInsets = UIEdgeInsets(top: 0.0, left: 0.0, bottom: keyboardSize.height, right: 0.0)
        scrollView.contentInset = contentInsets
        scrollView.scrollIndicatorInsets = contentInsets
    }
    
    @objc func keyboardWillBeHidden(_ notification: NSNotification) {
        let contentInsets = UIEdgeInsets.zero
        scrollView.contentInset = contentInsets
        scrollView.scrollIndicatorInsets = contentInsets
    }
```