# The Swift Programming Language (5.9)

![rw-book-cover](https://docs.swift.org/swift-book/developer-og.jpg)

## Metadata
- Author: [[Documentation]]
- Full Title: The Swift Programming Language (5.9)
- Category: #articles
- Summary: In Swift, you can print "Hello, world!" in a single line of code. Constants are created using "let" and variables are created using "var." You can use constants to name a value that you determine once but use in many places. Swift provides a simpler way to include values in strings, using parentheses and a backslash. You can use if and let together to work with values that might be missing. Functions, closures, and enumerations are also introduced in the document.
- URL: https://docs.swift.org/swift-book/documentation/the-swift-programming-language/guidedtour/

## Highlights
- Tradition suggests that the first program in a new language should print the words “Hello, world!” on the screen. In Swift, this can be done in a single line:
  print("Hello, world!")
  // Prints "Hello, world!"
  If you have written code in C or Objective-C, this syntax looks familiar to you — in Swift, this line of code is a complete program. You don’t need to import a separate library for functionality like input/output or string handling. Code written at global scope is used as the entry point for the program, so you don’t need a `main()` function. You also don’t need to write semicolons at the end of every statement.
  This tour gives you enough information to start writing code in Swift by showing you how to accomplish a variety of programming tasks. Don’t worry if you don’t understand something — everything introduced in this tour is explained in detail in the rest of this book.
  Use `let` to make a constant and `var` to make a variable. The value of a constant doesn’t need to be known at compile time, but you must assign it a value exactly once. This means you can use constants to name a value that you determine once but use in many places.
  var myVariable = 42
  myVariable = 50
  let myConstant = 42
  A constant or variable must have the same type as the value you want to assign to it. However, you don’t always have to write the type explicitly. Providing a value when you create a constant or variable lets the compiler infer its type. In the example above, the compiler infers that `myVariable` is an integer because its initial value is an integer.
  If the initial value doesn’t provide enough information (or if there isn’t an initial value), specify the type by writing it after the variable, separated by a colon.
  let implicitInteger = 70
  let implicitDouble = 70.0
  let explicitDouble: Double = 70
  Values are never implicitly converted to another type. If you need to convert a value to a different type, explicitly make an instance of the desired type.
  let label = "The width is "
  let width = 94
  let widthLabel = label + String(width)
  There’s an even simpler way to include values in strings: Write the value in parentheses, and write a backslash (`\`) before the parentheses. For example:
  let apples = 3
  let oranges = 5
  let appleSummary = "I have \(apples) apples."
  let fruitSummary = "I have \(apples + oranges) pieces of fruit."
  Use three double quotation marks (`"""`) for strings that take up multiple lines. Indentation at the start of each quoted line is removed, as long as it matches the indentation of the closing quotation marks. For example:
  let quotation = """
  Even though there's whitespace to the left,
  the actual lines aren't indented.
  Except for this line.
  Double quotes (") can appear without being escaped.
  I still have \(apples + oranges) pieces of fruit.
  """
  Create arrays and dictionaries using brackets (`[]`), and access their elements by writing the index or key in brackets. A comma is allowed after the last element.
  var fruits = ["strawberries", "limes", "tangerines"]
  fruits[1] = "grapes"
  var occupations = [
  "Malcolm": "Captain",
  "Kaylee": "Mechanic",
  ]
  occupations["Jayne"] = "Public Relations"
  Arrays automatically grow as you add elements.
  fruits.append("blueberries")
  print(fruits)
  // Prints "["strawberries", "grapes", "tangerines", "blueberries"]"
  You also use brackets to write an empty array or dictionary. For an array, write `[]`, and for a dictionary, write `[:]`.
  fruits = []
  occupations = [:]
  If you’re assigning an empty array or dictionary to a new variable, or another place where there isn’t any type information, you need to specify the type.
  let emptyArray: [String] = []
  let emptyDictionary: [String: Float] = [:]
  Use `if` and `switch` to make conditionals, and use `for`-`in`, `while`, and `repeat`-`while` to make loops. Parentheses around the condition or loop variable are optional. Braces around the body are required.
  let individualScores = [75, 43, 103, 87, 12]
  var teamScore = 0
  for score in individualScores {
  if score > 50 {
  teamScore += 3
  } else {
  teamScore += 1
  }
  }
  print(teamScore)
  // Prints "11"
  In an `if` statement, the conditional must be a Boolean expression — this means that code such as `if score { ... }` is an error, not an implicit comparison to zero.
  You can write `if` or `switch` after the equal sign (`=`) of an assignment or after `return`, to choose a value based on the condition.
  let scoreDecoration = if teamScore > 10 {
  "🎉"
  } else {
  ""
  }
  print("Score:", teamScore, scoreDecoration)
  // Prints "Score: 11 🎉"
  You can use `if` and `let` together to work with values that might be missing. These values are represented as optionals. An optional value either contains a value or contains `nil` to indicate that a value is missing. Write a question mark (`?`) after the type of a value to mark the value as optional.
  var optionalString: String? = "Hello"
  print(optionalString == nil)
  // Prints "false"
  var optionalName: String? = "John Appleseed"
  var greeting = "Hello!"
  if let name = optionalName {
  greeting = "Hello, \(name)"
  }
  Change `optionalName` to `nil`. What greeting do you get? Add an `else` clause that sets a different greeting if `optionalName` is `nil`.
  If the optional value is `nil`, the conditional is `false` and the code in braces is skipped. Otherwise, the optional value is unwrapped and assigned to the constant after `let`, which makes the unwrapped value available inside the block of code.
  Another way to handle optional values is to provide a default value using the `??` operator. If the optional value is missing, the default value is used instead.
  You can use a shorter spelling to unwrap a value, using the same name for that unwrapped value.
  if let nickname {
  print("Hey, \(nickname)")
  }
  // Doesn't print anything, because nickname is nil.
  Switches support any kind of data and a wide variety of comparison operations — they aren’t limited to integers and tests for equality.
  let vegetable = "red pepper"
  switch vegetable {
  case "celery":
  print("Add some raisins and make ants on a log.")
  case "cucumber", "watercress":
  print("That would make a good tea sandwich.")
  case let x where x.hasSuffix("pepper"):
  print("Is it a spicy \(x)?")
  default:
  print("Everything tastes good in soup.")
  }
  // Prints "Is it a spicy red pepper?"
  Notice how `let` can be used in a pattern to assign the value that matched the pattern to a constant.
  After executing the code inside the switch case that matched, the program exits from the switch statement. Execution doesn’t continue to the next case, so you don’t need to explicitly break out of the switch at the end of each case’s code.
  You use `for`-`in` to iterate over items in a dictionary by providing a pair of names to use for each key-value pair. Dictionaries are an unordered collection, so their keys and values are iterated over in an arbitrary order.
  let interestingNumbers = [
  "Prime": [2, 3, 5, 7, 11, 13],
  "Fibonacci": [1, 1, 2, 3, 5, 8],
  "Square": [1, 4, 9, 16, 25],
  ]
  var largest = 0
  for (_, numbers) in interestingNumbers {
  for number in numbers {
  if number > largest {
  largest = number
  }
  }
  }
  print(largest)
  // Prints "25"
  Use `while` to repeat a block of code until a condition changes. The condition of a loop can be at the end instead, ensuring that the loop is run at least once.
  var n = 2
  while n < 100 {
  n *= 2
  }
  print(n)
  // Prints "128"
  var m = 2
  repeat {
  m *= 2
  } while m < 100
  print(m)
  // Prints "128"
  Change the condition from `m < 100` to `m < 0` to see how ` ([View Highlight](https://read.readwise.io/read/01hekgkznxnteyk4b90r0jghzd))
