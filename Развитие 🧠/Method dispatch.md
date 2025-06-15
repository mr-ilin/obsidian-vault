- https://habr.com/ru/articles/714830/
- https://akhmedovgg.medium.com/navigating-the-depths-a-comprehensive-guide-to-method-dispatch-in-swift-for-ios-engineers-23ea140eefa3
##  Inline dispatch

Inline dispatch is the fastest and most efficient type of method dispatch in Swift, as it replaces the method call with the method body at compile time. This eliminates the overhead of indirect calls and enables the compiler to perform optimizations such as constant propagation, dead code elimination, and loop unrolling1.

Пример: все виды диспетчиризации
```swift
// MARK: Example 7 - All types of dispatching
protocol ProtocolExample7 {
    func doSomethingWithWitnessTable()
}
class ClassExample7: NSObject {
    @objc dynamic func doSomething() {
        print("Example 7 - Message Dispatch")
    }
}
class SubclassExample7: ClassExample7, ProtocolExample7 {
    private func doSomethingWithDirectDispatch() {
        print("Direct Dispatch")
    }
    func doSomethingWithVirtualTable() {
        print("Virtual Table")
    }
    func doSomethingWithWitnessTable() {
        print("Witness Table")
    }  
    @objc override dynamic func doSomething() {
        print("Override with Message Dispatch")
    }
}
```