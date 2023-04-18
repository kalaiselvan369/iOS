## Naming convention

1. camelCase
2. kebab-case
3. snake_case

## Comments

```swift

print("Hello World")

// This is single line comment

/*
 This is multi line comment
 */
```

## Print Statements

```swift
print("Hello World")
print(2==3) // output is false
print(2+3)  // output is 5
```

## String

```swift
var floatValue = 2.45343
var roundOffToTwoDecimal = String(format: "%.2f", floatValue)
print(floatValue) // prints 2.45
```

## String Concatenation

```swift

var alphabets = ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l"]

var password: String = alphabets[3] + alphabets[5] + alphabets[1] + alphabets[8]

print(password)
```

## String Interpolation

```swift
print("Add 2+3 = \(2+3)")

print("Multiply 11*5 = \(2+3)\(2+3)")
```

## Array


```swift

var numbers = [1, 2, 3, 4, 5]

print(numbers[1])

let result = [numbers[0]*numbers[1], numbers[1]*numbers[2], numbers[2]*numbers[3], numbers[3]*numbers[4], numbers[4]*numbers[0]]

print(result)
```

## Variable

```swift

var a = 4

var b = 5

var c = a

a = b

b = c

print("Value of a is \(a)")
print(b)
```

## Constant

```swift

let pi = 3.14

//below line won't compile hence commented

// pi = 2.3

// cannot assign to value: pi since pi is a constant

```

## Range

```swift

var closedRange = 1...2

var openRange = 1..<10


print(closedRange)

print(openRange)

```

## Randomization

```swift

var random = Int.random(in: 1...10)

print(random)


var randomFromArray = ["a", "b", "c"]

print(randomFromArray.randomElement() ?? "a")

```

## Operators

```swift

var a = 12

var b = 3

a = a + 1

print(a)

b += 3

print(b)

a -= 1

var sum = a + b

print(sum)

```

## Data type

1. Int refers to Integer which is a whole number.
2. Float refers to Floating point number which can have decimal place.
3. Double refers to decimal number with double the amount of accuracy then floating point number.
4. Bool refers to boolean which has only two values true or false

```swift

var number: Int = 1

print(number)

var name: String = "Hello"

var precision: Float = 1.35

var doublePrecision: Double = 1.35253

var flag: Bool = false
```

## Function

```swift
func greeting1(greet: String) {
    print(greet)
    func greeting2(salute: String){
        print(salute)
    }
    greeting2(salute: "mr.")
}
// function can be called as
greeting1(greet: "hello")
```
