## Programming Fundamentals in Swift
- [Swift Basics](#swift-basics)
  - [Swift Variable Examples](#swift-variable-examples)
  - [String Operations and Manipulation](#string-operations-and-manipulation)
  - [Control Flow](#control-flow)
  - [Loops](#loops)
  - [Loop Control with Conditional Statements](#loop-control-with-conditional-statements)
  - [Simple Authentication System Example](#simple-authentication-system-example)
  - [Array Usage in Swift](#array-usage-in-swift)
  - [Swift Tuple and Validation Examples](#swift-tuple-and-validation-examples)
  - [Swift Dictionary Example](#swift-dictionary-example)
  - [Swift Function Example](#swift-function-example)
  - [Different Usages of Functions](#different-usages-of-functions)
  - [Usages of Functions with inout Parameters](#usages-of-functions-with-inout-parameters)
  - [Closures](#closures)
  - [Swift Closure Example](#swift-closure-example)
  - [Swift Completion Handler Usage](#swift-completion-handler-usage)
  - [Different Closure Usage](#different-closure-usage)
  - [Struct](#struct)
  - [Class](#class)
  - [Class Example: Virtual Food Order System](#class-example-virtual-food-order-system)




## Swift Basics



####  Swift Variable Examples

```swift
//// This code uses variables to display weather temperatures.

let today = "Wednesday"
let currentTemperature = 80
print("Welcome to a new day!")

print("The temperature on \(today) is \(currentTemperature)°F")
var morningTemperature = 70
print("The temperature on \(today) morning is \(morningTemperature)°F")
morningTemperature  =  85
print("The temperature on \(today) evening is \(morningTemperature)°F")
let averageTemperature = 78
morningTemperature = averageTemperature
print("The average temperature this week is \(morningTemperature)°F")


```
#### Usage of Variables and Type Casting



```swift
///// the usage of variables and type casting in a game scenario.
//// Demonstrating Game Scores and Averages

let currentPlayer = "John"
var totalScore = 0

let currentLevelScore = 10
totalScore += currentLevelScore

print("\(currentPlayer) obtained a score of \(totalScore)")

var currentLevelBonus = 10.0
currentLevelBonus = 20
print("The bonus score for this level is \(currentLevelBonus).")

// Type casting
totalScore += Int(currentLevelBonus)

print("The final score for \(currentPlayer) is \(totalScore).")

let lowestLevelScore = 50
let highestLevelScore = 99
let totalLevels = 10
let levelScoreDifference = highestLevelScore - lowestLevelScore
let averageLevelScore = levelScoreDifference / totalLevels

print("The average score for each level is \(averageLevelScore).")

let averageScoreDouble = Double(levelScoreDifference) / Double(totalLevels)
print("The average score for each level is \(averageScoreDouble).")


```


#### String Operations and Manipulation

```swift

//// Time and Day Information

let today = "Tuesday"
print("Today is \(today)")
let currentHour = "8"
let currentMinutes = "45"
let timePeriod = "AM"

var currentTime = currentHour + ":" + currentMinutes + " " + timePeriod
print("It is \(currentTime)")
print("It is \(currentTime) on \(today)")

let timeZone = "EST"
currentTime += " \(timeZone)"
print("It is \(currentTime)")
print("It is \(currentTime) on \(today)")

let shortToday = today.prefix(3)

print("Today is \(shortToday)")
print("It is \(currentTime) on \(shortToday)")

print("The abbreviation has \(shortToday.count) characters.")

```

#### Control Flow 


```swift

let isLoggedIn = true
if isLoggedIn {
    print("You are currently logged in. Enjoy your personalized experience!")
} else {
    print("Please log in to access your account.")
}

let userAge = 25
let legalDrinkingAge = 21
if userAge >= legalDrinkingAge {
    print("You are legally allowed to purchase alcohol.")
} else {
    print("Sorry, you must be at least 21 years old to purchase alcohol.")
}

let userCountry = "USA"
if userCountry == "USA" {
    print("You are currently browsing the US version of the website.")
} else {
    print("You are currently browsing the international version of the website.")
}

let isPremiumMember = true
if isPremiumMember {
    print("Thank you for being a premium member. Enjoy exclusive benefits and content!")
} else {
    print("Upgrade to a premium membership to access premium features.")
}

let userRole = "Admin"
switch userRole {
    case "Admin":
        print("You have administrative privileges. Manage the system with care.")
    case "User":
        print("You are a regular user. Enjoy using the platform!")
    default:
        print("Your role is not recognized. Contact support for assistance.")
}


```


#### Loops

```swift
// For loop to roll a dice 6 times
for _ in 1...6 {
    let dice = Int.random(in: 1...6)
    print("Roll a \(dice).")
}

// While loop to roll two dice until they show the same value
var firstDice = Int.random(in: 1...6)
var secondDice = Int.random(in: 1...6)

while firstDice != secondDice {
    firstDice = Int.random(in: 1...6)
    secondDice = Int.random(in: 1...6)
}

print("You rolled a double \(firstDice).")

// Repeat-While loop to roll two dice until they show the same value
var thirdDice = 0
var fourthDice = 0

repeat {
    thirdDice = Int.random(in: 1...6)
    fourthDice = Int.random(in: 1...6)
} while thirdDice != fourthDice

print("You rolled a double \(thirdDice).")

```


#### Loop Control with Conditional Statements

```swift

let totalLevels = 12
let unlockedLevels = 6
let bonusLevel = 4

for currentLevel in 1...totalLevels {
    if currentLevel == bonusLevel {
        print("Skip bonus level \(bonusLevel).")
        continue
    }
    
    print("Play level \(currentLevel).")
    
    if currentLevel == unlockedLevels {
        let lockedLevels = totalLevels - unlockedLevels
        print("You have played all \(unlockedLevels) unlocked levels. Purchase the full game to play the remaining \(lockedLevels) levels.")
        break
    }
}


```


#### Simple Authentication System Example

```swift

let savedPassword = "password123"
var enteredPassword = "password123"

if enteredPassword == savedPassword {
    print("Authentication successful. Welcome!")
} else {
    print("Invalid password. Try again.")
}

enteredPassword = "hello"

if enteredPassword == savedPassword {
    print("Authentication successful. Welcome!")
} else {
    print("Invalid password. Try again.")
}

let newPassword = "newPassword"
let confirmPassword = "newPassword"

if newPassword == confirmPassword {
    print("Password has been successfully changed.")
} else {
    print("Password and confirmation do not match. Please try again.")
}

let pinCode = "1234"
let enteredPin = "4321"

if enteredPin == pinCode {
    print("Authentication successful. Welcome!")
} else {
    print("Invalid PIN. Try again.")
}




```


#### Array Usage in Swift

```swift

// Students and Their Grades

var studentGrades: [String: Int] = [:]

// Add grades for students
studentGrades["Alice"] = 90
studentGrades["Bob"] = 78
studentGrades["Charlie"] = 85

// Print the grades of all students
print("Grades of Students:")
for (name, grade) in studentGrades {
    print("\(name): \(grade)")
}

// Update a student's grade
let studentToUpdate = "Bob"
let newGrade = 85
if let oldGrade = studentGrades.updateValue(newGrade, forKey: studentToUpdate) {
    print("\(studentToUpdate)'s grade has been updated from \(oldGrade) to \(newGrade).")
} else {
    print("\(studentToUpdate) is not found in the list of students.")
}

// Print the updated grades
print("Updated Grades:")
for (name, grade) in studentGrades {
    print("\(name): \(grade)")
}

// Remove a student from the list
let studentToRemove = "Charlie"
if let removedGrade = studentGrades.removeValue(forKey: studentToRemove) {
    print("\(studentToRemove) has been removed from the list. Their grade was \(removedGrade).")
} else {
    print("\(studentToRemove) is not found in the list of students.")
}

// Check if the list is empty
if studentGrades.isEmpty {
    print("The list of students and grades is empty.")
} else {
    print("There are \(studentGrades.count) students in the list.")
}


```


#### Swift Tuple and Validation Examples

```swift

let userInfo = ("JohnDoe", 1234)
if userInfo.0 == "" || userInfo.1 < 0 {
  print("Invalid credentials!")
} else {
  print("The username is \(userInfo.0) and the password is \(userInfo.1).")
}

let fullUserInfo = (username: "AliceSmith", password: 5678)
if fullUserInfo.username == "" || fullUserInfo.password < 0 {
  print("Invalid credentials!")
} else {
  print("The username is \(fullUserInfo.username) and the password is \(fullUserInfo.password).")
}

```


#### Swift Dictionary Example

```swift


// Foods and their calorie values
let foodCalories = [
    "Apple": 52,
    "Banana": 89,
    "Orange": 62,
    "Grapes": 67,
    "Strawberries": 32,
]

// Finding the highest and lowest calorie foods
var highestCalorieFood = ""
var lowestCalorieFood = ""
var highestCalories = Int.min
var lowestCalories = Int.max

for (food, calories) in foodCalories {
    if calories > highestCalories {
        highestCalories = calories
        highestCalorieFood = food
    }
    if calories < lowestCalories {
        lowestCalories = calories
        lowestCalorieFood = food
    }
}

// Printing the results
print("Highest calorie food: \(highestCalorieFood), \(highestCalories) calories.")
print("Lowest calorie food: \(lowestCalorieFood), \(lowestCalories) calories.")

```


#### Swift Function Example

```swift

// Function to calculate total calories from an array of meal calories
func calculateTotalCalories(mealCalories: [Int]) -> Int {
  var totalCalories = 0
  for calories in mealCalories {
    totalCalories += calories
  }
  return totalCalories
}

// Daily meal calories
let breakfastCalories = 350
let lunchCalories = 550
let dinnerCalories = 700

// Calculate total calories for the day
let mealCalories = [breakfastCalories, lunchCalories, dinnerCalories]
let totalCalories = calculateTotalCalories(mealCalories: mealCalories)

print("Total calories for the day: \(totalCalories)")

```


####  Different Usages of Functions 

```swift
// Swift function examples with different parameter scenarios

// Example 1: Function with Underscore (_) for Parameter Names
// In this example, the "_" symbol for parameters indicates that we do not need to use the parameter names "fn" and "sn" when calling the function. We can call the function as follows:
func hiThere(_ fn: String, _ sn: String) {
  let fullname = fn + " " + sn
  print("Hi there \(fullname)")
}

// Example 2: Function with External Parameter Names
// In this example, the function uses external parameter names "firstname" and "surname," which must be used when calling the function:
func hiThere(firstname fn: String, surname sn: String) {
  let fullname = fn + " " + sn
  print("Hi there \(fullname)")
}

// Example 3: Function with Default Parameter Values
// In this example, the "score" parameter has a default value of 0, which means we can call the function with or without providing a value for "score":
func display(_ s1: String, _ s2: String, score: Int = 0) {
  let name_score = s1 + " " + s2 + " " + String(score)
  print("Hello \(name_score)")
}


```


#### Usages of Functions with inout Parameters

```swift

/// Incrementing Points with inout Parameter

var playerPoints = 0

func incrementPoints(_ points: inout Int, by amount: Int = 100) {
  points += amount
}

incrementPoints(&playerPoints)
print("Player points: \(playerPoints)")

incrementPoints(&playerPoints)
print("Player points: \(playerPoints)")

incrementPoints(&playerPoints)
print("Player points: \(playerPoints)")

incrementPoints(&playerPoints, by: 300)
print("Player points: \(playerPoints)")

incrementPoints(&playerPoints, by: 50)
print("Player points: \(playerPoints)")



```


#### Closures 

```swift

//Closures in Swift are self-contained blocks of code that can be assigned to variables or passed as arguments to functions. They are similar to functions but have a more concise syntax. Here's how closures are defined:

// Function:
func functionName(argument list) -> ReturnType {
    Execute some code
}

// Closure:
{ (argument list) -> ReturnType in
    Execute some code
}

//Closures are useful for tasks that require a block of code to be executed, such as sorting arrays, filtering data, or performing operations on collections. They can be particularly handy in scenarios where you need to define a short, inline piece of functionality without creating a separate function.


// Example 
// Using a closure to find the maximum of two numbers
let maximum = { (num1: Int, num2: Int) -> Int in
    return num1 > num2 ? num1 : num2
}
print(maximum(1, 6)) // Output: 6


// Example 

let letters = ["B", "D", "A", "C"]
// Sorting an array of strings using a closure
let myCollection = letters.sorted(by: { (string1: String, string2: String) -> Bool in
    return string1 < string2
})
print(myCollection) // Output: ["A", "B", "D", "C"]

// The same sorting operation with a shorter closure syntax
let myCollection2 = letters.sorted(by: { $0 < $1 })
print(myCollection2)  // Output: ["A", "B", "D", "C"]



```


#### Swift Closure Example 

```swift

// In this example, the variable waterBottles represents the amount of water bottles in a water dispenser, not gold bars. We have defined a closure named fillWaterDispenser. This closure takes an inout Int parameter called bottles, which means it can modify the value of bottles in its scope.

var waterBottles = 0
let fillWaterDispenser = { (bottles: inout Int) in
  bottles += 100 //ml
}
fillWaterDispenser(&waterBottles)
print(waterBottles)



```


#### Swift Completion Handler Usage 

```swift


// Drinking Water Example

var waterBottle = 1000 // We have 1000 ml (1L) water in the bottle

func drinkTenMLWater(from bottles: inout Int, completion: (Int) -> Void) {
bottles -= 10
completion(bottles)
}

print("You have (waterBottle) ml water in the bottle.")

drinkTenMLWater(from: &waterBottle) { remainingWater in
print("You drank ten ml of water.")
print("You have (remainingWater) ml of water left.")
}



```


#### Different Closure Usage 

```swift


///Example 1: Basic Usage of Closure


let sayHello = {
    print("Merhaba!")
}

sayHello() // Çıktı: Merhaba!


///Example 2: Closure with Parameters and Return Value

let multiply = { (a: Int, b: Int) -> Int in
    return a * b
}

let result = multiply(5, 3)
print(result) // Çıktı: 15


///Example 3: Passing a Closure as a Parameter to Another Function


func performOperation(a: Int, b: Int, operation: (Int, Int) -> Int) {
    let result = operation(a, b)
    print("Sonuç: \(result)")
}

let addition = { (a: Int, b: Int) -> Int in
    return a + b
}

performOperation(a: 5, b: 3, operation: addition) // Çıktı: Sonuç: 8


//Example 4: Closure Expression Shorthand


let numbers = [1, 2, 3, 4, 5]
let squaredNumbers = numbers.map { $0 * $0 }
print(squaredNumbers) // Çıktı: [1, 4, 9, 16, 25]


// https://docs.swift.org/swift-book/documentation/the-swift-programming-language/closures/

```


#### Struct
 

```swift


struct Vehicle {
    var color: String
    var name: String
    var topSpeed: Int
    var mileage: Int
    
    func drive() {
        print("\(color) \(name) can drive at a maximum speed of \(topSpeed)!")
    }
}

var newVehicle = Vehicle(color: "blue", name: "Car 1", topSpeed: 100, mileage: 5000)
newVehicle.drive()
print("The color of the vehicle is \(newVehicle.color).")


// Explanation of "mutating" Keyword
//The `mutating` keyword is used in a structure or class method to allow the method to modify the properties of the structure or class. By default, a method in a structure or class is not allowed to modify the properties; it can only read them. However, by marking a method with the `mutating` keyword, you can enable the method to modify the properties.

// Example 1: Using the "mutating" keyword in a structure

struct Point {
    var x: Int
    var y: Int

    mutating func moveByX(_ deltaX: Int, y deltaY: Int) {
        x += deltaX
        y += deltaY
    }
}

var point = Point(x: 10, y: 20)
point.moveByX(5, y: 10)
print(point) // Output: Point(x: 15, y: 30)


// Example 2: Using the "mutating" keyword in a structure

struct TableReservation {
    var name: String
    var tableNumber: Int

    mutating func updateBooking(updatedName: String) {
        name = updatedName
    }
}

var johnBooking = TableReservation(name: "John", tableNumber: 1)
print(johnBooking)
johnBooking.updateBooking(updatedName: "Maria")
print(johnBooking)

```


#### Class
 

```swift

class LocalFile {
  let name: String
  let fileExtension: String

  init(name: String, fileExtension: String) {
    self.name = name
    self.fileExtension = fileExtension
  }

  var fullFileName: String {
    return name + "." + fileExtension
  }
}

let file = LocalFile(name: "image", fileExtension: "png")
print(file.fullFileName)


```


#### Class Example : Virtual Food Order System
 

```swift
// Virtual Food Order System
// A virtual system that allows users to order meals and track calorie intake for breakfast, lunch, and dinner.

class VirtualFoodOrderSystem {
    var selectedMeal = ""
    var isOrdering = true

    func welcomeUser() {
        print("Welcome to your virtual food order system.")
    }

    func selectMealType() {
        print("What type of meal would you like to order?")
        print("1. Breakfast")
        print("2. Lunch")
        print("3. Dinner")
    }

    func orderMeal(mealNumber: Int) {
        print("You have selected option \(mealNumber).")
        switch mealNumber {
        case 1:
            selectedMeal = "Breakfast"
        case 2:
            selectedMeal = "Lunch"
        case 3:
            selectedMeal = "Dinner"
        default:
            print("Invalid input: \(mealNumber)")
            return
        }
        print("You are ordering \(selectedMeal).")
    }

    func addCalories(calorieCount: Int) {
        print("You've added \(calorieCount) calories to your \(selectedMeal) meal.")
    }

    func checkTotalCalories(calorieCount: inout Int) {
        print("Total calories in your meals: \(calorieCount)")
    }
}

struct MealCalories {
    var breakfastCalories = 0
    var lunchCalories = 0
    var dinnerCalories = 0

    var totalCalories: Int {
        breakfastCalories + lunchCalories + dinnerCalories
    }

    mutating func addCalories(for mealType: String, calories: Int) {
        switch mealType {
        case "Breakfast":
            breakfastCalories += calories
            print("Added \(calories) calories to breakfast.")
        case "Lunch":
            lunchCalories += calories
            print("Added \(calories) calories to lunch.")
        case "Dinner":
            dinnerCalories += calories
            print("Added \(calories) calories to dinner.")
        default:
            break
        }
    }
}

let virtualFoodOrderSystem = VirtualFoodOrderSystem()
virtualFoodOrderSystem.welcomeUser()

repeat {
    virtualFoodOrderSystem.selectMealType()
    let mealNumber = Int.random(in: 1...4)
    virtualFoodOrderSystem.orderMeal(mealNumber: mealNumber)
} while virtualFoodOrderSystem.selectedMeal == ""

var totalCaloriesInMeals = 0

repeat {
    print("What would you like to do?")
    print("1. Check total calories in meals")
    print("2. Add calories to selected meal")
    print("3. Exit the food order system")
    let option = Int.random(in: 1...4)
    print("Selected option: \(option).")
    switch option {
    case 1:
        virtualFoodOrderSystem.checkTotalCalories(calorieCount: &totalCaloriesInMeals)
    case 2:
        let calorieCount = Int.random(in: 200...800)
        virtualFoodOrderSystem.addCalories(calorieCount: calorieCount)
        MealCalories().addCalories(for: virtualFoodOrderSystem.selectedMeal, calories: calorieCount)
    case 3:
        virtualFoodOrderSystem.isOrdering = false
        print("Exiting the food order system.")
    default:
        break
    }
} while virtualFoodOrderSystem.isOrdering


```


#### State and Binding
 

```swift

```


#### Observable and Observed
 

```swift
