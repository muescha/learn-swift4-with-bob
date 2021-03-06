# Failable Init
<div align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/rtIOOw-QTzQ" frameborder="0" allowfullscreen></iframe>
</div>

## Introduction
Welcome to Lesson 4 of Object Oriented Swift. You will learn how to design an init method that, first, possibly returns no object, but `nil`, second, throws an error.

## Problem
Can initialization fail?

## Error Handling (Review)

### Design Error

```swift
enum NameError: Error {
  case noName
}
```

### Design Struct

```swift
struct UdemyCourse {
  let courseName: String

  init(name: String) throws {
    if name.isEmpty {
      throw NameError.noName
    }
    self.courseName = name
  }
}
```

### Initialize and Handle Error

```swift
do {
  let myCourse = try UdemyCourse(name: "Bob")
  myCourse.courseName

} catch NameError.noName {
  print("Bob, please enter the name")
}
```

## Design Failable Init
Insert `?` after the `init` keyword . It may return `nil` or an object whose type is `optional`.

```swift
class Blog {
  let name: String
  init?(name: String) {
    if name.isEmpty {
      // handle error
      return nil
    }
    self.name = name
  }
}

let blog = Blog(name: "") // nil

if let myBlog = blog {
  print(myBlog.name)
}
```

> I personally prefer the error-handling approach over failable init due to modularized code and no unwrapping.


### Source Code
> [2004-failable-init.playground](https://www.dropbox.com/sh/673z6s57ka3d9tx/AACyH8kWa3s2UIEMdiMQlhyXa?dl=0)

## Conclusion
First, you've learned how design an init method that may return `nil` or an optional object by putting a `?` right to the `init` keyword. As we've discussed many times, anything that has to do with `?` in the Swift Programming Language will give you an optional value. Second, you reviewed the Swift `error handling` approach. Remember, the `throw` keyword is not only used within an `else-if` or `guard` block, but also within an `init` method.

In the following lesson, you will learn how to override everything while subclassing.

> **Note:** Learn Swift with Bob is available on [Udemy](https://udemy.com/learn-swift-with-bob/). If you wish to receive a discount link, you may sign up [here](https://goo.gl/RR4K27).
