# MAD - Exercise 01
## Tasks
* Watch the Kotlin Crashcourse Video in Moodle or complete the tutorials **[Introduction to programming in Kotlin](https://developer.android.com/courses/pathways/android-basics-compose-unit-1-pathway-1)** and **[Kotlin fundamentals](https://developer.android.com/courses/pathways/android-basics-compose-unit-2-pathway-1
)**.
* Answer the questions inside this Readme.md file and push it to your repository.
* Submit your coding solution of the Number Guessing Game inside the repository.
* Submit the link to your repository in Moodle.

## Questions
### Describe how Kotlin handles null safety. What are nullable types and non-null types in Kotlin? (0,5 points)

<span style="color:blue">To avoid NullPointerException, we need to write defensive code that checks if an object is null before using it. Many modern programming languages, including Kotlin, made steps to convert runtime errors into compile time errors to improve programming language safeness. </span>  

<span style="color:blue">One of the way to do it in Kotlin is by adding nullability safeness mechanisms to language type systems. This is possible because Kotlin type system distinguishes between references that can hold null (nullable references) and those that cannot (non-nullable references). This single feature of Kotlin allows us to detect many errors related to NullPointerException at very early stages of development. Compiler together with IDE will prevent many NullPointerException. In many cases compilation will fail instead of application failing at runtime. </span>  

<span style="color:blue">So basically to put in simple points, </span>  

1. Kotlin allows to store “Null” values in a variable.
2. In Kotlin, the variables can be made of Null types by just adding a “?” symbol to the right side of the data type.
3. A nullable type variable means it can also hold “Null” as a value in it.
4. A non-nullable type variable means that it can not hold “Null” as a value in it. </span>
> The compiler can detect whether the variable being referred to is nullable or not. If it is nullable, then the compiler makes sure that the Null safety checks are being used. If null safety checks are not being used then the compilation error occurs. Thus safes the user from run time NullPointerExceptions.
```kotlin 
var name: String = "Name" // Non Nullable String variable 

var name: String? = null // Nullabe String variable
```
> Note*: If a type is nullable, then any operation which can be performed on it. Can be only performed after “Null safety checks” are being done on it.

#### Let us see different operators which help the programmers to ensure “Null Safety Checks” on the nullable variables.
##### Safe Call Operator ( ?. )
* The safe call operator is simply a question mark followed by a dot ( ?. )
* The safe call operator in Kotlin, is one of the methods to impose “Null Safety Checks” on the nullable variables.
* If the left-hand side of the operator is null, then it will return null value.
* If the left-hand side of the operator is not null, then it will return the result of the right-hand side expression.
```kotlin 
var title: String? = "Title"
var len: Int? = title?.length // It will return title's length i.e '5'

var title: String? = null
var len: Int? = title?.length // It will return null
```
##### Elvis Operator ( ?: ) 
* The elvis operator is represented by a question mark followed by a colon ( ?: )
* The elvis operator in Kotlin, is one of the methods to impose “Null Safety Checks” on the nullable variables.
* If the first operand is not null, then this operand will be returned by the elvis operator.
* If the first operand is null, then second operand will be returned by the elvis operator.
```kotlin 
val ans: Boolean = true ?: false  // returns true (1st Operand)

val ans: Boolean = null ?: true // return true (2nd Operand)
```
##### Not Null Assertion ( !! ) 
* The Not Null Assertion is represented by a double exclamation mark (!!)
* The Not Null Assertion in Kotlin, is another tool to deal with nullity.
* This operator explicitly casts nullable variables to non-nullable variables. </span>
```kotlin 
var myString: String? = "foo"
var size: Int = myString!!.length
```
> Normally, we would not be able to assign a value from a nullable property length to a non-nullable variable size like we have done in the above example.

> However, as a developer, we can assure the compiler that this nullable variable will have a value here. If we are right, our application will work correctly, but if we are wrong, and the variable has a null value, the application will throw NullPointerException.
##### Safe casts (as?)
* Performs a safe cast, returning null if the cast is not possible.
```kotlin 
val anyValue: Any? = "This is a string"
val stringValue: String? = anyValue as? String
```

### What are lambda expressions and higher order functions in Kotlin? Why would you store a function inside a variable? (0,5 points)

<span style="color:blue">Provide your answer here!</span>

### Provide a solution for the following number guessing game inside `App.kt`. (3 points)

## Number Guessing Game in Kotlin
The game is a simple number guessing game. The task is to generate a random, max 9-digit, number. The number must **not contain repeating digits**. Valid digits are 1-9.
Ask the user to guess the max 9-digit number. The game is finished when the user guesses the correct digits in the correct order.
In each round, the user gets feedback about the number of correct digits and the number of correct digits in the correct position.
The output should be in the format "n:m", where "n" is the number of digits guessed correctly regardless of their position, 
and "m" is the number of digits guessed correctly at their correct position. Here are some examples:

This example shows the game flow with 4-digits to guess (the default argument)

Generated number: 8576
-	User input: 1234, Output: 0:0
-	User input: 5678, Output: 4:1
-	User input: 5555, Output: 1:1
-	User input: 3586, Output: 3:2
-	User input: 8576, Output: 4:4 -> user wins

Take a look into the provided code structure in `src/main/kotlin/App.kt`. Implement the following methods (lambda expressions):
- _playNumberGame(digitsToGuess: Int = 4)_ (1 point): The main game loop that handles user input and game state. Make use of _generateRandomNonRepeatingNumber_ and _checkUserInputAgainstGeneratedNumber_ here. This function also utilizes a default argument 
- _generateRandomNonRepeatingNumber_ (1 point): A lambda expression that generates a random number with non-repeating digits of a specified length.
- _checkUserInputAgainstGeneratedNumber_ (1 point): A lambda expression that compares the user's input against the generated number and provides feedback.

``CompareResult.kt`` This class is a data structure which helps with bundling the result of the comparison of the user input and the generated number. Look at the toSting() and use it in your output.

Run the project with `./gradlew run` and test your implementation with the provided tests in `src/test/kotlin/AppTest.kt` with `./gradlew test`.

# Project Structure
The project is structured into two main Kotlin files:

**App.kt**: Contains the main game logic and functions.

**AppTest.kt**: Contains unit tests for the various functions in App.kt.

