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

### Initialize empty array

```swift
var items = [String]()

items.append("hello")
items.append("hi")

print(items)
```

### Multiply all numbers in array 

```swift
var numbers = [2,3,4]
var product = 1 
for n in numbers {
    //product = product * n   // alternate way
    product *= n
}
```

### 2D Array

```swift
let twoDArray = [
    [1, 2, 3],  // 0
    [1, 2, 3],  // 1
    [1, 2, 3]   // 2
] // 0  1  2
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
let v = Int.random(in: 2...5)
print("upper and lower bound included: \(v)")

let x = Int.random(in: 2..<5) // half open range
print("upper bound excluded: \(x)")

let z = Int.random(in: ...10)
print("print any number less than 10: \(z)")

var closedRange = 1...2

var halfOpenRange = 1..<10

var oneSidedRange = ...10

print(closedRange)

print(halfOpenRange)

print(oneSidedRange)
```

## Loops

```swift
var fruits = ["apple", "orange", "grapes"]

for fruit in fruits {
    print(fruit)
}

for number in 1...4 {
    print(number)
}

for _ in 1...3 {
    print("hello") // print hello 3 times
}

var name = "Tony"

for char in name {
    print(char) // prints each character in name
}
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


### Explicity defining data type

```swift
    var name: String
    var placesVisited: [String] // array of string
    var starsAndMovies: [String : String] // dictionary whose data type is string for both key and value
```

## Function

```swift
func greet(message: String) {
    print(message)
    func reply(name: String) {
        print(name)
    }
    reply(name: "I am good")
}

greet(message: "Hello, How are you?")
}
```


### Function Parameters 

```swift

// default
func checkAnswerOne(yourAnswer: String) {
}

checkAnswerOne(yourAnswer: "True")  // this is how we call

// here external parameter is answer
// here internal parameter is yourAnswer
func checkAnswerTwo(answer yourAnswer: String) 
}

checkAnswerTwo(answer: "True") // this is how we call

// no external parameter means _
func checkAnswerThree(_ yourAnswer: String) {
    
}

checkAnswerThree("True") // this is how we call

```

> Notice the difference above -- how we are passing arguments


#### Function with return type

```swift
func evaluateAnswer(answer: String, correctAnswer: String) -> Bool {
    if answer == correctAnswer {
        return true
    } else {
        return false
    }
}
```

## Condition

```swift

func loveCalculator() {
    
    let percent = Int.random(in: 10 ... 100)
    
    if percent > 80 {
        print("strong love")
    } else if percent > 40 && percent <= 80 {
        print("average love")
    } else {
        print("poor love")
    }
}

loveCalculator()
```

## Switch

```swift

func loveCalculator() {
    
    let percent = Int.random(in: 10 ... 100)
    
    switch percent {
    case 80...100:
        print("strong love")
    case 41..<80:
        print("average love")
    case ...41:
        print("poor love")
    default:
        print("error in percentage")
    }
}

loveCalculator()
```

## Dictionaries

```swift

var details: [String : String] = [ "a":"apple", "b":"ball", "c":"cat"]

var result = details["b"]

print(result)

details.updateValue("basket", forKey: "b")

print("\(details["b"])")
```

## Optional

The data could be present with specific data type or Nil

```swift
var hardness: String? = nil

// Here optional(?) is indicating that variable hardness can take `nil` value also
```

### Force unwrapping

Use this wisely. If your force unwrapping the `nil` property then the app will crash at some point.

```swift
var myOptionalString: String? = "hello"

// danger ahead
myOptionalString = nil

let forceUnwrapping = myOptionalString! // adding ! means force unwrapping

print(forceUnwrapping) // app is going to crash here

```

So, how to avoid in crash in **Force Unwrapping** ????

### Optional nil check 

To avoid crash during for unwrapping we can use optional nil check.

```swift
var myOptionalString: String? = "hello"

// danger ahead
myOptionalString = nil

if myOptionalString != nil {
    let forceUnwrapping = myOptionalString! // adding ! means force unwrapping
    print(forceUnwrapping)
}
```

So, how to improve the code relability and concise by avoiding `nil` check

### Optional binding

```swift
var myOptionalString1: String? = "hello"
var myOptionalString2: String? = "hello"

// danger ahead
myOptionalString1 =  nil
myOptionalString2 =  nil

if let safeOptional1 = myOptionalString1, let safeOptional2 = myOptionalString2 {
    print(safeOptional1)
    print(safeOptional2)
} else {
    print("optional was found to be nil")
}
```

Note that `if let safeOptional = myOptional` is important here. This line is checking whether
both the variables data type is not optional i.e `if let safeOptional: String = myOptional: String` 

### Nil Coalescing operator

```swift
var myOptionalString: String? = "hello"

// danger ahead
myOptionalString = nil

let text = myOptionalString ?? "use me"

print(text) // print use me
```

### Optional Chaining

Use optional chaining when we have to invoke some functions from the optional struct.

```swift
struct MyOptional {
    
    private var text: String = "hello"
    
    func getText() -> String {
        return text
    }
    
}

let myOptional: MyOptional? // optional struct

myOptional = MyOptional()

print(myOptional?.getText()) // here ?. is optional chaining and it saves us from crash also
```

### Swift Structure 

Strucutre helps to create custom data type

1. Variables declared inside struct is called **property** --- indicates the color or what it is like
2. functions declared inside struct is called **method**  -- indicate actions or what it can do
3. We can also use init() inside the struct to initialize the property
4. init() can have arugments that initialize the property
5. `self` keyword is similar to `this` keyword in kotlin
6. By default property and method in `struct` are immutable

```swift

struct User {
    
    var name: String  // var inside struct is called as property
    var email: String?
    var followers: Int
    var isActive: Bool
    
    init(n name: String, e email: String, f followers: Int, a isActive: Bool) {
        self.name = name
        self.email = email
        self.followers = followers
        self.isActive = isActive
    }
    
    // func inside struct is called as method
    func logStatus() {
        if isActive {
            print("\(name) is working hard")
        } else {
            print("\(name) has left earth")
        }
    }
    
    mutating func newFollowers(_ followers: Int) {
        self.followers = followers
    }
}

var user = User(n: "Dhoni", e: "msd@cricket.com", f: 1000, a: true)
print(user)
user.followers = 2000 // no issue mutation available from outside
print(user)
user.newFollowers(3000) // mutating keyword to be added to that function
print(user)

let kholi = User(n: "Kholi", e: "virat@cricket.com", f: 1000, a: true)
kholi.followers = 2000 // Error: not possible since let is constant

```

> Mutating a property inside `struct` is possible only by declaring **mutating** keyword 

### Immutability 

```swift

struct QuizManager {
    
    let questions = [
        Question(q: "A slug's blood is green.", a: "True"),
        Question(q: "Approximately one quarter of human bones are in the feet.", a: "True"),
        Question(q: "The total surface area of two human lungs is approximately 70 square metres.", a: "True") 
    ]
    
    var currentQuestionNumber = 0
    
    // mutating because it is changing one of the property(currentQuestionNumber) in struct during run time
    mutating func getQuestion() -> String {
        if currentQuestionNumber <= questions.count - 1 {
            let question = questions[currentQuestionNumber].text
            return question
        } else {
            currentQuestionNumber = 0
            let question = questions[currentQuestionNumber].text
            return question
        }
    }
    
    // mutating because it is changing one of the property(currentQuestionNumber) in struct during run time
    mutating func getCurrentProgress() -> Float {
        let progressValue = Float(currentQuestionNumber + 1)/Float(questions.count)
        currentQuestionNumber += 1
        if progressValue >= 1 {
            return 0
        } else {
            return progressValue
        }
    }
    
    func evaluateAnswer(answer: String) -> Bool {
        if answer == questions[currentQuestionNumber].answer {
            return true
        } else {
            return false
        }
    }
}

```

**Remember: 1** 

We **cannot** do

```swift
let questionManager = QuizManager()
questionManager.getCurrentProgress() 

// Cannot use mutating member(getCurrentProgress()) on immutable value: 'questionManager' is a 'let' constant
// Reason is -- 
// 1. QuizManager is of type struct 
// 2. The instance object is assigned to let property 
// 3. Once we assign an object of type struct to let then we cannot change its properties

// But the same case works fine if QuizManager is a class instead of struct
```

Therefore, you have to use  `var`

```swift
var questionManager = QuizManager()
questionManager.getCurrentProgress()

```

```swift
struct Story {
    
    let story: String
    let choiceOne: String
    let choiceTwo: String
    
    init(story: String, choiceOne: String, choiceTwo: String) {
        self.story = story
        self.choiceOne = choiceOne
        self.choiceTwo = choiceTwo
    }
}

// The above code works fine. Although I have declared the properties with let keyword, I am ensuring that all of them will be initalized
// during the init construct
```

### Class

```swift
class Enemy {
    
    var attackAccuracy = 8
    
    var attackStrenth = 89
    
    func move() {
        print("10 foot at a time")
    }
    
    func attack() {
        print("drags down oppontent to 30 %")
    }
}
```

#### Inherit class

```swift
class Dragon: Enemy {
    
    override func move() {
        print("fly to 10 m")
    }
    
    override func attack() {
        print("split fire")
    }
}

// OUTPUT:

// fly to 10 m
// split fire
```

> Most basic class is swift is `NSObject` and NS means Next Step

Example of inheritance: UIButton -> UIControl -> UIView -> UIResponder -> NSObject

### Difference between struct and class

1. `struct` cannot inherit whereas `class` can
2. `struct` cannot mutate property by default whereas `class` can mutate property
3. `struct` are pass by value whereas `class` are pass by reference

#### Nice example for Pass by value and Pass by reference

1. In `struct` case when my friend ask for a photo then I will provide a new copy of that photo. Here, since I am give a new copy 
   eventhough my friend accidently destroyed it, I will still have my own copy.
2. In `class` case when my friend ask for a photo then I will share the directory/address so that he can go and make use of it. If he 
   accidentaly delete that phone then it is total damage because we had only one photo which is shared by many.

```swift
// Let's us define enemy using `class` keyword
class Enemy {
    
    var health = 100
    var attackStrength = 10
    
    init(health: Int, attackStrength: Int) {
        self.health = health
        self.attackStrength = attackStrength
    }
    
    // here we are changing the property of health but didn't explicitly added mutating annotation
    func takeDamage() {
        health -= 10 // mutating property
    }
    
    func move() {
        print("10 foot at a time")
    }
    
    func attack() {
        print("drags down oppontent to 30 %")
    }
    
```
#### Classes operate by Object Reference

**Remember: 2** 

```swift
let enemy1 = Enemy.init(health: 100, attackStrength: 10)
let enemy2 = enemy1  // this line is creating a reference for enemy1 and assign to enemy2

enemy1.move()
enemy1.attack()
enemy1.takeDamage() // this func reduce health by 90
// also notice that enemy1 is declared using let keyword and still we were able to mutate

// do you think enemy2 health would have reduced to 90
print(enemy2.health)

// YES YES: Because classes operate of object reference

```

```swift

// Let us define same enemy class but changing class to struct

struct Enemy {
    
    var health = 100
    var attackStrength = 10
    
    init(health: Int, attackStrength: Int) {
        self.health = health
        self.attackStrength = attackStrength
    }
    
    mutating func takeDamager() {
        health -= 10
    }
    
    func move() {
        print("10 foot at a time")
    }
    
    func attack() {
        print("drags down oppontent to 30 %")
    }
}
```

```swift
var enemy1 = Enemy.init(health: 100, attackStrength: 10)
let enemy2 = enemy1  // this line is creating a new clone of enemy1 and assign to enemy2

enemy1.move()
enemy1.attack()
enemy1.takeDamager() // this func reduce health by 90

// do you think enemy2 health would have reduced to 90 ?????
print(enemy2.health)

// NOOOO: Because enemy2 created a new clone of enemy1 and thats how struct operate
```

> As per iOS, prefer to use `struct` instead of `class`

[ Refer: Struct vs Class ](https://docs.swift.org/swift-book/LanguageGuide/ClassesAndStructures.html)

### Protocol

```swift
import Foundation

protocol CanFly {
    func fly()
}

// reason to adapt protocol is All birds cannot fly. Example Penguin is a bird that cannot fly.
// therefore we cannot add fly function in the Bird(base) class. 
// If we inherit bird class to eagle, penguin each subclass will inherit those 
// characteristics also. But the problem is does Penguin fly?? Answer is   No..

// hence by defining the protocol we will add fly function only to the respective classes which has fly capability.

struct FlyingMuseum {
    
    func flyableObject(flyable: CanFly) {
        flyable.fly()
    }
}

class Bird {
    
    var isFemale = true
    
    func canLayEggs() {
        
        if isFemale {
            print("lay eggs")
        }
    }
}

class Eagle: Bird, CanFly {
    
    func fly() {
        print("eagle can fly")
    }
    
    func soar() {
        print("eagle flies in the air using air currents")
    }
}

class Penguin: Bird {
    
    func swim() {
        print("these bird can swim in water")
    }
}

class Aeroplane: CanFly {
    
    // although aeroplane can fly, it is not a bird
    
    func fly() {
        print("it flies with powered engines and artificial wings")
    }
}
```

> Protocol is like interfaces in java/kotlin -- My understanding

1. We can implement multiple protocols in single class
2. Protocol functions are abstract like we seen in interface


### Delegate things using protocol

```swift
import Foundation

protocol AdvancedLifeSupport {
    func performCPR()
}

struct Paramedic: AdvancedLifeSupport {
    
    init(emeHandler: EmergencyLineHandler) {
        emeHandler.delegate = self
    }
    
    func performCPR() {
        print("paramedic performing CPR")
    }
}

class Doctor: AdvancedLifeSupport {
    
    init(emeHandler: EmergencyLineHandler) {
        emeHandler.delegate = self
    }
    
    func performCPR() {
        print("doctor performing cpr")
    }
    
    func haveSteth() {
        print("check for internal sound")
    }
    
    func prescribeMedicine() {
        print("have these tab")
    }
}

class Surgeon: Doctor {
    
    override func performCPR() {
        super.performCPR()
        print("sing a lalabee")
    }
    
    func repairOrgans() {
        print("repairing organs")
    }
}

class EmergencyLineHandler {
    
    var delegate: AdvancedLifeSupport?
    
    func assesSituation() {
        print("tell us what is the situation")
    }
    
    func medicalEmergency() {
        delegate?.performCPR()
    }
}

let emilio =  EmergencyLineHandler()
let pete = Paramedic(emeHandler: emilio)
emilio.assesSituation()
emilio.medicalEmergency() // this function will delegate to paramedic
```

### Closures - Anonymous functions

1. We can pass function to another function
2. We can return function from another function

```swift
{
    (p1: P1Type, p2: P2Type) -> ReturnResultType in
    return p1 + p2
}
```

```swift
// passing function by reference
var result = calculate(n1: 2, n2: 3, operation: add)

print(result)

func add(n1: Int, n2: Int) -> Int {
    return n1 + n2
}

// anonymous function 
var result0 = calculate(n1: 2, n2: 3, operation: { (n1: Int, n2: Int) -> Int in
    return n1 + n2
})
print(result0)

// simplifying closure - 1 (argument data type is infered hence we don't need to declare it)
var result1 = calculate(n1: 2, n2: 3, operation: { (n1, n2) -> Int in
    return n1 + n2
})
print(result1)

// simplification closure - 2 (return type is infered hence we don't need to declare it)
var result2 = calculate(n1: 2, n2: 3, operation: { (n1, n2) in
    return n1 + n2
})
print(result2)

// simplification of closure - 3 (we can even remove return keyword also)
var result3 = calculate(n1: 2, n2: 3, operation: { (n1, n2) in
    n1 + n2
})
print(result3) 

// simplification of closure - 4 parameter definition not necessary
// n1 --> $0 , n2 --> $1, .... --> $n
var result5 = calculate(n1: 2, n2: 3, operation: {
    $0 + $1
})
print(result5)

// simplification of closure - 5 parameter label not necessary if closure is the last param
var result6 = calculate(n1: 2, n2: 3) {
    $0 + $1
}
print(result6)


// function by reference
let array0 = [3, 4, 5, 6]
func addOne(n: Int) -> Int {
    return n + 1
}
let arrayResult0 = array0.map(addOne)
print(arrayResult0)


// anonymous functions
let array1 = [3, 4, 5, 6]
let arrayResult1 = array1.map {$0 + 1}
print(arrayResult1)
```

## Networking

1. Create URL
2. Create URL Session
3. Assing URL session a task
4. Start the task

```swift

        //1. create url
        if let url = URL(string: getUrl()) {
            //2. create url session
            let session = URLSession(configuration: .default)
            //3. assign url session a task
            let task = session.dataTask(with: url) { data, response, error in
                if let error = error {
                    print(error)
                } else if let data = data {
                    self.parseData(data: data)
                }
            }
            //4. start task
            task.resume()
        }
```

## Computed Property

```swift
var temperatureInCelcius : String {
    // this line is executed every time we call this variable
    return String.init(format: "%.1f", temperature)
}
```

## Type alias

```swift
typealias Codable = Decodable & Encodable
```

We can mark the response schema `struct` as codeable which will allow us to serialize and deserialize JSON.

## Extension

### Extension functions 

```swift
extension Double {
    
    func round(to places: Int) -> Double {
        let precision = pow(10, Double(places))
        var n = self * precision
        n.round()
        return n / precision
    }
}

var number = 3.14578

var result = number.round(to: 2)
```

### Extension Protocol

```swift
import Foundation

protocol CanFly {
    func fly()
}

extension CanFly {

    // this function name should be same as of the one that was declared in protocol
    func fly() {
        print("object flies")
    }
}

// reason to adapt protocol is All birds cannot fly. Example Penguin is bird that cannot fly.
// therefore we cannot add fly function in the Bird class. If we do say all the birds like 
// eagle, penguin which are inheriting from the bird class will inherit those characteristics also.

// hence by defining the protocol we will add fly function only to the respective classes

struct FlyingMuseum {
    
    func flyableObject(flyable: CanFly) {
        flyable.fly()
    }
}

class Bird {
    
    var isFemale = true
    
    func canLayEggs() {
        
        if isFemale {
            print("lay eggs")
        }
    }
}

class Eagle: Bird, CanFly {
    
    func soar() {
        print("eagle flies in the air using air currents")
    }
}

class Penguin: Bird {
    
    func swim() {
        print("these bird can swim in water")
    }
}

class Aeroplane: CanFly {
    
    // although aeroplane can fly, it is not a bird
    // also thing to note we didn't add the fly function from the protocol
    // because we added extension protocol
    // and in the extension protocol we have implemented the function
}

var aeroplane = Aeroplane()
aeroplane.fly() // we are able to call this because of our extension protocol
```

1. Protocol can also be extended
2. When we extend the protocol we have to add the implementation for the function as declared in the protocol
3. Unlike normal protocol, extension protocol can have functions with implementation in it.


## Sections 

If we have to separate file with different sections then we can do as 

```swift
//MARK: - <Section Name In Single Line>
```


## Code Snippet (live templates)

1. To create code snippet, highlight the block and right click and create code snipped
2. Give a title and description
3. In snippet block add the below line

```swift
//MARK: - <#Section name#>
```

Also ensure you will need to add `keyword` in completion field


## Casting

#### `is` , `as!` , `as`, `as?`

```swift
class Animal {
    let name: String
    
    init(name: String) {
        self.name = name
    }
}

class Fish: Animal {
    func action() {
        print("I can breath in water")
    }
}

class Human: Animal {
    func action() {
        print("I can do programming")
    }
}

var john = Human.init(name: "John")
var nemo = Fish.init(name: "Nemo")
var pichai = Human.init(name: "Pichai")

var items = [john, nemo, pichai]

// usage of is
for item in items {
    if item is Fish {
        print("fishy")
        let fish = item as 
        // unless we force downcast `as!` we cannot use method of Fish class
        let fish: Fish = item as! Fish
        print(fish.action())
        // usage of upcasting - most least used
        let animal: Animal = item as Animal
        animal.callMe()
    }

    // usage of safe casting
     if item is Human {
        var human: Animal? = item
        let john = human as? Human
        john?.action()
    }
}
```


## Any

All the objects

```swift

var john = Human.init(name: "John")
var nemo = Fish.init(name: "Nemo")
var pichai = Human.init(name: "Pichai")

var number: Int = 12
var string: String = "hello"

// we cannot add number to the list because number is of Integer type
// and it is a struct
var items: [Any] = [john, nemo, pichai, number]
```

## AnyObject

All the objects that are derived from class

```swift
var john = Human.init(name: "John")
var nemo = Fish.init(name: "Nemo")
var pichai = Human.init(name: "Pichai")

var number: Int = 12
var string: String = "hello"

// we cannot add number to the list because number is of Integer type
// and it is a struct
var items: [AnyObject] = [john, nemo, pichai]

// cannot do this -- because number is of type Int and it is a struct
var items: [AnyObject] = [john, nemo, pichai, number]
```

## NSObject

Class that extends NSObject can only be grouped as any array like above.

```swift

var number: NSNumber = 12
var string: NSString = ""

var items: [NSObject] = [number, string]
```

## User Defaults

User defaults is like shared preference in android. We should only store for limited data in that. It is **not** like db.

1. User default is a .plist
2. The root type of the .plist is a dictionary. Hence we can store only key value pairs.
3. We **cannot** story an array of a custom type objects in user default plist.
4. **Attempting to set non property object list in user default error will we thrown if try to save array of custom objects**
5. Still we can save array of type string into user default plist.

```swift
let defaults = UserDefaults.standard

defaults.set(1, forKey: "Int")
defaults.set(Date(), forKey: "Date")

let arrays = [1,2,3]
defaults.set(arrays, forKey: "Arrays")

// result

if let int = defaults.object(forKey: "Int") {
    print(int)
}

if let date = defaults.object(forKey: "Date") {
    let d = date as! Date
    print(d.timeIntervalSince1970)
}


if let arrays = defaults.object(forKey: "Arrays") {
    print(arrays)
}
```

## Mutating

```swift
class Car {
    var color = "Red"
}

let car1 = Car()
car1.color = "green"

let car2 = Car()
car2.color = "yellow"

print(car1.color)
print(car2.color)


// speciality of struct

struct Bike {
    var color = "blue"
}

let bike = Bike()
bike.color = "brown" //error: Cannot assign to property: 'bike' is a 'let' constant


// to fix the error we need to check let to var

struct Bike {
    var color = "blue"
}

var bike = Bike()
bike.color = "brown"

print(bike)
```

## Singleton

We have only one object reference to that particular class.

```swift
class Car {
    var color = "Red"
    
    static let singletonCar = Car()
}

let car1 = Car.singletonCar
car1.color = "green"

let car2 = Car.singletonCar

print(car1.color) // prints green
print(car2.color) // prints green
```

## Ternary Operator

```swift
// finalResult = condition ? result : result
cell.accessoryType = item.done == true ? .checkmark : .none


// Bonus - avoid too many if

if items[indexPath.row].done {
    items[indexPath.row].done = false
} else {
    items[indexPath.row].done = true
}

// perfect way to simplify it is like below

items[indexPath.row].done = !items[indexPath.row].done
```

## Codable - Encoding and Decoding data in custom .plist file

Encoding -> converting from one data type to another
Decoding -> decode from one type to another

If we need to save small piece of custom data type then user .plist

```swift

//1. first get a path for the .plist file
let filePath = FileManager.default
        .urls(for: .documentDirectory, in: .userDomainMask)
        .first?.appendingPathComponent("todo.plist") // this will create the .plist file in that path

//2. encode and write data to path
func saveItems() {
        let encoder =  PropertyListEncoder()
        do {
            let data = try encoder.encode(items)
            try data.write(to: filePath!)
        } catch {
            print("error in data encoding")
        }
}

//3. fetch data from path and decode it
 func getItems() {
        let decoder = PropertyListDecoder()
        do {
            let safeData = try Data.init(contentsOf: filePath!)
            let result = try decoder.decode([Todo].self, from: safeData)
            items = result
        } catch {
            print("error in decoding data")
        }
}
```

## Keychain

To store very minimal sized data securely

## SQLite - Relational data

Lite weight, easy to user relational database and query large amount of data in ease.

### Core Data

In fact, if you’ve used Core Data before, you’ve already used SQLite. 
Core Data is just a layer on top of SQLite that provides a more convenient API.


### We use context to save 

```swift
import UIKit
import CoreData

class TodoListViewController: UITableViewController {
    
    var items = [Todo]()

    // the lazy property persistentContainer is declared in the AppDelegate.swift
    let context = (UIApplication.shared.delegate as! AppDelegate).persistentContainer.viewContext
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // if we want to debug the .plist file or the sqlite file then to find the path use this
        var path = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask).first
        print(path)
        loadItems()
    }
    
    @IBAction func addItemPressed(_ sender: UIBarButtonItem) {
        showAlert()
    }
    
    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return items.count
    }
    
    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(
            withIdentifier: "TodoCell",
            for: indexPath
        )
        let todo = items[indexPath.row]
        cell.textLabel?.text = todo.item
        
        cell.accessoryType = todo.done == true ? .checkmark : .none
        
        return cell
    }
    
    override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        items[indexPath.row].done = !items[indexPath.row].done // since the changes happens in the context
        // it is enough to call context.save only
        
        // or we can use the below function also to update and then call context.save
        //items[indexPath.row].setValue("Completed", forKey: "item")

        // to delete item from core data
        
        //context.delete(items[indexPath.row]) // after this context.save() should be called
        //items.remove(at: indexPath.row)


        updateItem() // this is calling context.save()
        tableView.reloadData()
        tableView.deselectRow(at: indexPath, animated: false)
    }
    
    func showAlert() {
        var item: String? = nil
        let alert = UIAlertController.init(
            title: "Add Item",
            message: "Add Item in List",
            preferredStyle: .alert
        )
        let action = UIAlertAction.init(title: "Add", style: .default) { (action) in
            item = alert.textFields?[0].text
            if let safeItem = item {
                self.saveItem(safeItem: safeItem)
                self.tableView.reloadData()
                
            }
        }
        alert.addTextField { (alertUITextField) in
            alertUITextField.placeholder = "Add your Item here"
        }
        alert.addAction(action)
        present(alert, animated: true, completion: nil)
    }
    
    func updateItem() {
        do {
            try context.save()
        } catch {
            print("error in data encoding")
        }
    }
    
    func saveItem(safeItem: String) {
        do {
            let todo = Todo.init(context: self.context)
            todo.item = safeItem
            todo.done = false
            self.items.append(todo)
            try context.save()
        } catch {
            print("error in data encoding")
        }
    }
    
    func loadItems() {
        do {
            let fetchRequest: NSFetchRequest<Todo> = Todo.fetchRequest()
            var result = try context.fetch(fetchRequest)
            items = result
        } catch  {
            print("fetching items failed")
        }
    }

}

```

## Finding Path to Custom plist and Data source model

Use the below function to know the path when the app is running in simulator

```swift
print(FileManager.default.urls(for: .documentDirectory, in: .userDomainMask).first)
```

So the .plist file will be in the path:

/Users/tonyy/Library/Developer/CoreSimulator/Devices/4B9D3BD7-90B6-4E13-807E-3898575D5074/data/Containers/Data/Application/46AEB4C7-F8CF-44FE-81C6-4514E87E1E84/Documents

Likewise, the sqlite file will be in the path:

/Users/tonyy/Library/Developer/CoreSimulator/Devices/4B9D2ED7-90B6-4E13-807E-3818575D5054/data/Containers/Data/Application/46AEB4C7-F8CF-44FE-81C6-4514E87E1E84/Library/Application Support
