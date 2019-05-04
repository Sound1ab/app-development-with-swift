# Tables and Persistence - swift

## Protocols

A protocol defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality. The protocol can then be adopted by another type, which provides the actual implementation for those requirements. Any type that satisfies the requirements of a protocol conforms to that protocol.

### Conforming to a protocol

```swift
class Shoe: CustomStringConvertible {
    let color: String
    let size: Int
    let hasLaces: Bool
 
    init(color: String, size: Int, hasLaces: Bool) {
        self.color = color
        self.size = size
        self.hasLaces = hasLaces
    }
 
    var description: String {
        return "Shoe(color: \(color), size: \(size), hasLaces: \
        (hasLaces))"
    }
}
```

Here `CustomStringConvertible` is a swift protocol that allows you to add a description that will be printed.

```swift
let myShoe = Shoe(color: "Black", size: 12, hasLaces: true)
print(myShoe) // Shoe(color: Black, size: 12, hasLaces: true)
```

Other swift protocols are availble too

* `Equatable` - check if two custom types are the same
* `Comparable` - sort custom types with `< <= > >=`

### Creating a protocol

When requiring a property, you must define whether the property is read-only or read/write. Read-only means you can get the variable, but you can't set it. Read/write means you can both get and set the value. If a property is read-only, you can implement it using a computed property. If it's read/write, it should be a regular property.

```swift
protocol FullyNamed {
  var fullName: String { get }
 
  func sayFullName()
}
```

```swift
struct Person: FullyNamed {
  var firstName: String
  var lastName: String
 
  var fullName: String {
    return "\(firstName) \(lastName)"
  }
 
  func sayFullName() {
    print(fullName)
  }
}
```
