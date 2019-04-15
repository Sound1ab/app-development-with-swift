# Working with the web - swift

## Closures

Closures in swift are comparable to anonymous functions in JavaScript. Closure expressions are a way to write inline closures in a brief, focused syntax.

```swift
let sumClosure = { (numbers: [Int]) -> Int in
  // Code that adds together the numbers array.
  return total
}
```

When passed as arguments, the closure syntax can be simplified. 

### Func only takes a single closure argument

```swift
let sortedTracks = tracks.sorted { (firstTrack, secondTrack) -> 
Bool in
    return firstTrack.trackNumber < secondTrack.trackNumber
}
```

### Removing closure parameters

```swift
let sortedTracks = tracks.sorted { return $0.starRating <
$1.starRating }
```

### Single line return

```swift
let sortedTracks = tracks.sorted { $0.starRating < $1.starRating }
```

### Trailing closure

```swift
func performRequest(url: String, response: (code: Int) -> Void) 
{ }

performRequest(url: "https://www.apple.com") { (data) in
    print(data)
}
```

## Map, Filter, Reduce

The three greatest functions invented take a closure to transform data, just like JS!

### Map

```swift
let fullNames = names.map { (name) -> String in
    return name + " Smith"
}
```

### Filter

```swift
let numbersLessThan20 = numbers.filter { (number) -> Bool in
 
    return number < 20
}
```

### Reduce

Takes a starting value and a closure that dictates how to combine the items.

```swift
let total = numbers.reduce(0) { (currentTotal, newValue) -> 
Int in
    return currentTotal + newValue
}
```