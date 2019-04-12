# Navigation and Workflows - swift

## Optionals

Optionals are useful in situations when a value may or may not be present. An optional represents two possibilities: Either there is a value and you can use it, or there isn't a value at all, in which case you would get back `nil`.

They can be specified with a `?` after a variable declaration.

```swift
struct Book {
  var name: String
  var publicationYear: Int?
}
```

### Safetly check an optional

```swift
if let constantName = someOptional {
  //constantName has been safely unwrapped for use within the braces.
}
```

When unwrapping an optional it's common to shadow the original variable name with the new name

```swift
func exclaim(name: String?) {
  if let name = name {
    // Inside the braces, `name` is the unwrapped `String` 
    Value 
    print("Exclaim function was passed: \(name)")
  }
}
```

### Optionals in function parameters

```swift
func printFullName(firstName: String, middleName: String?, lastName: String) -> String? {
    
}
```

### Failable initializers

Initializers in structs can return nil to prevent the creation of the struct.

```swift
struct Toddler {
  var name: String
  var monthsOld: Int
 
  init?(name: String, monthsOld: Int) {
    if monthsOld < 12 || monthsOld > 36 {
      return nil
    } else {
      self.name = name
      self.monthsOld = monthsOld
    }
  }
}
```

### Optional chaining

Some optionals can themselves contain optionals. To unwrap these easily we can use optional chaining.

```swift
if let theApartmentNumber =
person.residence?.address?.apartmentNumber {
  print("He/she lives in apartment number \
  (theApartmentNumber).")
}
```

### Implicitly unwrapped optionals

If you know a value exists inside an optional you can unwrap it without using if let

```swift
class ViewController: UIViewController {
  @IBOutlet weak var label: UILabel!
}
```

## Type casting and inspection

You can use the as? operator to try and downcast the value to a more specific type and store it in a new constant. This operation is known as a conditional cast, because it casts the instance to the specified type if it's possible to do so.

```swift
let pets = allClientAnimals()
 
for pet in pets {
if let dog = pet as? Dog {
    walk(dog: dog)
  } else if let cat = pet as? Cat {
    cleanLitterBox(cat: cat)
  } else if let bird = pet as? Bird {
    cleanCage(bird: bird)
  }
}
```

When you know that the returned object will be a more specific type, you can use the as! operator to cast the value immediately.

```swift
let alansDog = fetchPet(for: "Alan") as! Dog
```

### Any

Swift provides two special types: Any and AnyObject. Any, as the name implies, can represent an instance of any type: strings, doubles, functions, or whatever. AnyObject can represent any class within Swift, but not a structure.

```swift
var items: [Any] = [5, "Bill", 6.7, true]
if let firstItem = items[0] as? Int {
  print(firstItem+4) //9
}
```

### Guard

Provides a way of returning from a function early instead of using nested if-else statements or inverted if statements

```swift
func singHappyBirthday() {
  guard birthdayIsToday else {
    print("No one has a birthday today.")
    return
  }
 
  guard invitedGuests > 0 else {
    print("It's just a family party.")
    return
  }
 
  guard cakeCandlesLit else {
    print("The cake's candles haven't been lit.")
    return
  }
 
  print("Happy Birthday to you!")
}
```

It can also be used to bind the value within an optional to a constant that's accessible outside the braces.

```swift
guard let eggs = goose.eggs else { return }
//`eggs` is accessible hereafter 
print("The goose laid \(eggs.count) eggs.")
```

```swift
func processBook(title: String?, price: Double?, pages: Int?) {
  guard let theTitle = title, let thePrice = price, let 
  thePages = pages else { return }
  print("\(theTitle) costs $\(thePrice) and has \(thePages) pages.")
}
```

## Enum

An enumeration, or enum, is a special Swift type that allows you to represent a named set of options.

```swift
enum CompassPoint {
  case north
  case east
  case south
  case west
}
```

```swift
var compassHeading = CompassPoint.west
```

```swift
var compassHeading: CompassPoint = .west
```