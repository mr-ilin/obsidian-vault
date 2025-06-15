- https://www.hackingwithswift.com/articles/179/capture-lists-in-swift-whats-the-difference-between-weak-strong-and-unowned-references
### Strong capturing

Unless you ask for something special, Swift uses _strong capturing_. This means the closure will capture any external values that are used inside the closure, and make sure they never get destroyed.
```swift
func sing() -> () -> Void {
    let taylor = Singer()

    let singing = {
        taylor.playSong()
        return
    }

    return singing
}
```

That `taylor` constant is made inside the `sing()` function, so normally it would be destroyed when the function ends. However, it gets used inside the closure, which means Swift will automatically make sure it stays alive for as long as the closure exists somewhere, even after the function has returned.

This is strong capturing in action. If Swift allowed `taylor` to be destroyed, then the closure would no longer be safe to call – its `taylor.playSong()` method wouldn’t be valid any more.