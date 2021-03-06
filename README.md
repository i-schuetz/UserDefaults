# UserDefaults


[![Version](https://img.shields.io/cocoapods/v/UserDefaults.svg?style=flat)](http://cocoadocs.org/docsets/UserDefaults)
[![License](https://img.shields.io/cocoapods/l/UserDefaults.svg?style=flat)](http://cocoadocs.org/docsets/UserDefaults)
[![Platform](https://img.shields.io/cocoapods/p/UserDefaults.svg?style=flat)](http://cocoadocs.org/docsets/UserDefaults)

Convenient wrapper for NSUserDefaults. 

- Uses enum values as keys (safe!).
- Uses generics and type inference in order to avoid having to specify the value type, in most cases.

## Installation

UserDefaults is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

    pod "UserDefaults"
    
... or copy [UserDefaults.swift](Pod/Classes/UserDefaults.swift) in your project. 

## Usage

The keys have to comform to the StringRepresentable protocol. Normally you will declare an enum similar to this:

```swift
enum MyKeys:String, StringRepresentable {
    // give your keys a meaningful name
    case Key1 = "key1"
    case Key2 = "key2"
    case Key3 = "key3"
    case Key4 = "key4"
    case Key5 = "key5"
    
    var stringValue:String {return self.rawValue}
}
```

Examples:


```swift
UserDefaults.setValue(MyKeys.Key1, value: "hello")
let a:String? = UserDefaults.value(MyKeys.Key1)
println("String: \(a)")

UserDefaults.setValue(MyKeys.Key2, value: 2.46)
let b:Double? = UserDefaults.value(MyKeys.Key2)
println("Double: \(b)")

UserDefaults.setValue(MyKeys.Key3, value: 3)
let c:Int? = UserDefaults.value(MyKeys.Key3)
println("Int: \(c)")

UserDefaults.setValue(MyKeys.Key4, value: true)
let d:Bool? = UserDefaults.value(MyKeys.Key4)
println("Bool: \(d)")

// pass as parameter
func foo(a:String?) {}
UserDefaults.setValue(MyKeys.Key5, value: 3)
foo(UserDefaults.value(MyKeys.Key5))

// type inference not possible, use convenience accessors
println("String: \(UserDefaults.string(MyKeys.Key1))")
```

## Author

ischuetz

## License

UserDefaults is available under the MIT license. See the LICENSE file for more info.

