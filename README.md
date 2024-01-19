# Swift_Notes
---- SWIFT NOTES ----

VARIABLE : -
var str = "Hello, World"

MULTI-LINE STRINGS :-
If you want multi-line strings you need slightly different syntax: start and end with three double quote marks, like this:
var str1 = """
This goes
over multiple
lines
"""

DOUBLE AND BOOLEANS :- 
DOUBLE -
“Double” is short for “double-precision floating-point number”, and it’s a fancy way of saying it holds fractional values such as 38.1, or 3.141592654.

BOOLEANS-
As for booleans, they are much simpler: they just hold either true or false, and Swift will automatically assign the boolean type to any variable assigned either true or false as its value.

var awesome = true

STRING INTERPOLATION :-
You can place any type of variable inside your string – all you have to do is write a backslash, \, followed by your variable name in parentheses. For example:
var score = 85
var str = "Your score was \(score)"

CONSTANTS :- 
However, very often you want to set a value once and never change it, and so we have an alternative to the var keyword called let.
The let keyword creates constants, which are values that can be set once and never again. For example:
let taylor = "swift"

TYPE ANNOTATIONS :- 
If you want you can be explicit about the type of your data rather than relying on Swift’s type inference, like this:
let album: String = "Reputation"
let year: Int = 1989
let height: Double = 1.78
let taylorRocks: Bool = true

ARRAY :- 
Arrays are collections of values that are stored as a single value. For example, John, Paul, George, and Ringo are names, but arrays let you group them in a single value called The Beatles.
For example -
let john = "John Lennon"
let paul = "Paul McCartney"
let george = "George Harrison"
let ringo = "Ringo Starr"

let beatles = [john, paul, george, ringo]

That last line makes the array: it starts and ends with brackets, with each item in the array separated by a comma.
array access with position number
For Example -
beatles[1]

SETS :- 
Sets are collections of values just like arrays, except they have two differences:
1. Items aren’t stored in any order; they are stored in what is effectively a random order.
2. No item can appear twice in a set; all items must be unique.
You can create sets directly from arrays, like this:
let colors = Set(["red", "green", "blue"])

If you try to insert a duplicate item into a set, the duplicates get ignored. For example:
let colors2 = Set(["red", "green", "blue", "red", "blue"])

TUPLES :-
Tuples allow you to store several values together in a single value. That might sound like arrays, but tuples are different:
1. You can’t add or remove items from a tuple; they are fixed in size.
2. You can’t change the type of items in a tuple; they always have the same types they were created with.
3. You can access items in a tuple using numerical positions or by naming them, but Swift won’t let you read numbers or names that don’t exist.
Tuples are created by placing multiple items into parentheses, like this:
var name = (first: "Taylor", last: "Swift")
You then access items using numerical positions starting from 0:
name.0
Or you can access items using their names:
name.first

ARRAY vs SETS vs TUPLES :- 
Arrays, sets, and tuples can seem similar at first, but they have distinct uses. To help you know which to use, here are some rules.

If you need a specific, fixed collection of related values where each item has a precise position or name, you should use a tuple:
let address = (house: 555, street: "Taylor Swift Avenue", city: "Nashville")

If you need a collection of values that must be unique or you need to be able to check whether a specific item is in there extremely quickly, you should use a set:
let set = Set(["aardvark", "astronaut", "azalea"])

If you need a collection of values that can contain duplicates, or the order of your items matters, you should use an array:
let pythons = ["Eric", "Graham", "John", "Michael", "Terry", "Terry"]

DICTIONARIES :-
Dictionaries are collections of values just like arrays, but rather than storing things with an integer position you can access them using anything you want.

The most common way of storing dictionary data is using strings. For example, we could create a dictionary that stores the height of singers using their name:
let heights = [
    "Taylor Swift": 1.78,
    "Ed Sheeran": 1.73
]

Just like arrays, dictionaries start and end with brackets and each item is separated with a comma. However, we also use a colon to separate the value you want to store (e.g. 1.78) from the identifier you want to store it under (e.g. “Taylor Swift”).
These identifiers are called keys, and you can use them to read data back out of the dictionary:
heights["Taylor Swift"]

Note: When using type annotations, dictionaries are written in brackets with a colon between your identifier and value types. For example, [String: Double] and [String: String].


DICTIONARIES DEFAULT VALUES :-
If you try to read a value from a dictionary using a key that doesn’t exist, Swift will send you back nil – nothing at all. While this might be what you want, there’s an alternative: we can provide the dictionary with a default value to use if we request a missing key.

To demonstrate this, let’s create a dictionary of favorite ice creams for two people:
let favoriteIceCream = [
    "Paul": "Chocolate",
    "Sophie": "Vanilla"
]

We can read Paul’s favorite ice cream like this:
favoriteIceCream["Paul"]

But if we tried reading the favorite ice cream for Charlotte, we’d get back nil, meaning that Swift doesn’t have a value for that key:
favoriteIceCream["Charlotte"]

We can fix this by giving the dictionary a default value of “Unknown”, so that when no ice cream is found for Charlotte we get back “Unknown” rather than nil:
favoriteIceCream["Charlotte", default: "Unknown"]

CREATING EMPTY COLLECTIONS :- 
Arrays, sets, and dictionaries are called collections, because they collect values together in one place.
If you want to create an empty collection just write its type followed by opening and closing parentheses. For example, we can create an empty dictionary with strings for keys and values like this:
var teams = [String : String] () 

We can then add entries later on, like this:
teams["paul"] = "Red"

Similarly, you can create an empty array to store integers like this:
var results = [Int]()

The exception is creating an empty set, which is done differently:
var word = Set<String>()
var numbers = Set<Int>()

This is because Swift has special syntax only for dictionaries and arrays; other types must use angle bracket syntax like sets.
If you wanted, you could create arrays and dictionaries with similar syntax:
var scores = Dictionary<String,Int>()
var results = Array<Int>()

ENUMERATIONS :-
Enumerations – usually called just enums – are a way of defining groups of related values in a way that makes them easier to use.
For example, if you wanted to write some code to represent the success or failure of some work you were doing, you could represent that as strings:
let result = "failure"

But what happens if someone accidentally uses different naming?
let result2 = "failed"
let result3 = "fail"

All those three are different strings, so they mean different things.
With enums we can define a Result type that can be either success or failure, like this:
enum Result {
case success
case failure
}

And now when we use it we must choose one of those two values:
let result4 = Result.failure

ENUM ASSOCIATED VALUES :- 
As well as storing a simple value, enums can also store associated values attached to each case. This lets you attach additional information to your enums so they can represent more nuanced data.
For example, we might define an enum that stores various kinds of activities:
enum Activity {
case bored
case running
case talking
case singing
}

That lets us say that someone is talking, but we don’t know what they are talking about, or we can know that someone is running, but we don’t know where they are running to.
Enum associated values let us add those additional details:
enum Activity {
case bored
case running(destination: String)
case talking(topic: String)
case singing(volume: Int)
}

Now we can be more precise – we can say that someone is talking about football:
let talking = Activity.talking(topic:"football")

ENUM RAW VALUES :-
Sometimes you need to be able to assign values to enums so they have meaning. This lets you create them dynamically, and also use them in different ways.

For example, you might create a Planet enum that stores integer values for each of its cases:
enum Planet: Int {
    case mercury
    case venus
    case earth
    case mars
}

Swift will automatically assign each of those a number starting from 0, and you can use that number to create an instance of the appropriate enum case. For example, earth will be given the number 2, so you can write this:
let earth = Planet(rawValue: 2)

If you want, you can assign one or more cases a specific value, and Swift will generate the rest. It’s not very natural for us to think of Earth as the second planet, so you could write this:
enum Planet: Int {
    case mercury = 1
    case venus
    case earth
    case mars
}

Now Swift will assign 1 to mercury and count upwards from there, meaning that earth is now the third planet.


ARITHMETIC OPERATORS :-
Now you know all the basic types in Swift, we can start to put them together using operators. Operators are those little mathematical symbols like + and -, and Swift has a huge range of them.

Here are a couple of test variables for us to work with:
let firstScore = 12
let secondScore = 4

We can add and subtract using + and -:
let total = firstScore + secondScore
let difference = firstScore - secondScore

And we can multiply and divide using * and /:
let product = firstScore * secondScore
let divided = firstScore / secondScore

Swift has a special operator for calculating remainders after division: %. It calculates how many times one number can fit inside another, then sends back the value that’s left over.

For example, we set secondScore to 4, so if we say 13 % secondScore we’ll get back one, because 4 fits into 13 three times with remainder one:
let remainder = 13 % secondScore


OPERATOR OVERLOADING :- 
Swift supports operator overloading, which is a fancy way of saying that what an operator does depends on the values you use it with. For example, + sums integers like this:
let meaningOfLife = 42
let doubleMeaning = 42 + 42

But + also joins strings, like this:
let fakers = "Fakers gonna "
let action = fakers + "fake"

You can even use + to join arrays, like this:
let firstHalf = ["John", "Paul"]
let secondHalf = ["George", "Ringo"]
let beatles = firstHalf + secondHalf

Remember, Swift is a type-safe language, which means it won’t let you mix types. For example, you can’t add an integer to a string because it doesn’t make any sense.

COMPOUND ASSIGNMENT OPERATORS :- 
Swift has shorthand operators that combine one operator with an assignment, so you can change a variable in place. These look like the existing operators you know – +, -, *, and /, but they have an = on the end because they assign the result back to whatever variable you were using.
For example, if someone scored 95 in an exam but needs to be penalized 5 points, you could write this:
var score = 95
score -= 5

Similarly, you can add one string to another using +=:
var quote = "The rain in Spain falls mainly on the "
quote += "Spaniards"

COMPARISON OPERATORS :- 
Swift has several operators that perform comparison, and these work more or less like you would expect in mathematics.
Let’s start with a couple of example variables so we have something to work with:
let firstScore = 6
let secondScore = 4

There are two operators that check for equality: == checks two values are the same, and != (pronounced “not equals”) checks two values are not the same:
firstScore == secondScore
firstScore != secondScore

There are four operators for comparing whether one value is greater than, less than, or equal to another. These are just like in mathematics:
firstScore < secondScore
firstScore >= secondScore

Each of these also work with strings, because strings have a natural alphabetical order:
"Taylor" <= "Swift"

CONDITIONS :- 
Now you know some operators you can write conditions using if statements. You give Swift a condition, and if that condition is true it will run code of your choosing.
To try this out, I want to use a Swift function called print(): you run it with some text, and it will be printed out.

We can use conditions to check for a winning Blackjack hand:
let firstCard = 11
let secondCard = 10

if firstCard + secondCard == 21 {
    print("Blackjack!")
}

The code inside the braces – { and } – will be run if the condition is true. If you want you can provide alternative code to run if the condition is false, using else:
if firstCard + secondCard == 21 {
    print("Blackjack!")
} else {
    print("Regular cards")
}

You can also chain conditions together using else if:
if firstCard + secondCard == 2 {
    print("Aces – lucky!")
} else if firstCard + secondCard == 21 {
    print("Blackjack!")
} else {
    print("Regular cards")
}

COMBINING CONDITIONS : -
Swift has two special operators that let us combine conditions together: they are && (pronounced “and”) and || (pronounced “or”).

For example, we could check that the age of two people are both over a certain value like this:
let age1 = 12
let age2 = 21

if age1 > 18 && age2 > 18 {
    print("Both are over 18")
}

That print() call will only happen if both ages are over 18, which they aren’t. In fact, Swift won’t even bother checking the value of age2 because it can see that age1 already failed the test.

The alternative to && is ||, which evaluates as true if either item passes the test. For example we could print a message if either age is over 18:
if age1 > 18 || age2 > 18 {
    print("At least one is over 18")
}

You can use && and || more than once in a single condition, but don’t make things too complicated otherwise it can be hard to read!

THE TERNARY OPERATOR : -
Swift has a rarely used operator called the ternary operator. It works with three values at once, which is where its name comes from: it checks a condition specified in the first value, and if it’s true returns the second value, but if it’s false returns the third value.

The ternary operator is a condition plus true or false blocks all in one, split up by a question mark and a colon, all of which which makes it rather hard to read. Here’s an example:
let firstCard = 11
let secondCard = 10
print(firstCard == secondCard ? "Cards are the same" : "Cards are different")

That checks whether the two cards are the same, then prints “Cards are the same” if the condition is true, or “Cards are different” if it’s false. We could write the same code using a regular condition:
if firstCard == secondCard {
    print("Cards are the same")
} else {
    print("Cards are different")
}

SWITCH STATEMENTS : -
If you have several conditions using if and else if, it’s often clearer to use a different construct known as switch case. Using this approach you write your condition once, then list all possible outcomes and what should happen for each of them.

To try this out, here’s a weather constant containing the string sunny:
let weather = "sunny"
We can use a switch block to print one of four different messages:
switch weather {
case "rain":
    print("Bring an umbrella")
case "snow":
    print("Wrap up warm")
case "sunny":
    print("Wear sunscreen")
default:
    print("Enjoy your day!")
}

In that example, the last case – default – is required because Swift makes sure you cover all possible cases so that no eventuality is missed off. If the weather is anything other than rain, snow, or sun, the default case will be run.

Swift will only run the code inside each case. If you want execution to continue on to the next case, use the fallthrough keyword like this:
switch weather {
case "rain":
    print("Bring an umbrella")
case "snow":
    print("Wrap up warm")
case "sunny":
    print("Wear sunscreen")
    fallthrough
default:
    print("Enjoy your day!")
}


RANGE OPERATORS : -
Swift gives us two ways of making ranges: the ..< and ... operators. The half-open range operator, ..<, creates ranges up to but excluding the final value, and the closed range operator, ..., creates ranges up to and including the final value.

For example, the range 1..<5 contains the numbers 1, 2, 3, and 4, whereas the range 1...5 contains the numbers 1, 2, 3, 4, and 5.

Ranges are helpful with switch blocks, because you can use them for each of your cases. For example, if someone sat an exam we could print different messages depending on their score:
let score = 85

switch score {
case 0..<50:
    print("You failed badly.")
case 50..<85:
    print("You did OK.")
default:
    print("You did great!")
}
As before, the default case must be there to ensure all possible values are covered.


FOR LOOPS : -
Swift has a few ways of writing loops, but their underlying mechanism is the same: run some code repeatedly until a condition evaluates as false.

The most common loop in Swift is a for loop: it will loop over arrays and ranges, and each time the loop goes around it will pull out one item and assign to a constant.
For example, here’s a range of numbers:
let count = 1...10

We can use a for loop to print each item like this:
for number in count {
    print("Number is \(number)")
}

We can do the same with arrays:
let albums = ["Red", "1989", "Reputation"]

for album in albums {
    print("\(album) is on Apple Music")
}
If you don’t use the constant that for loops give you, you should use an underscore instead so that Swift doesn’t create needless values:
print("Players gonna ")

for _ in 1...5 {
    print("play")
}


WHILE LOOPS : -
A second way of writing loops is using while: give it a condition to check, and its loop code will go around and around until the condition fails.

For example, we could use a while loop to simulate a child counting in a game of hide and seek: we start at one, count up to and including 20 while printing each number out, then after the loop print “Ready or not”.

Here’s how that looks in Swift:
var number = 1

while number <= 20 {
    print(number)
    number += 1
}

print("Ready or not, here I come!")


REPEAT LOOPS : -
The third way of writing loops is not commonly used, but it’s so simple to learn we might as well cover it: it’s called the repeat loop, and it’s identical to a while loop except the condition to check comes at the end.

So, we could rewrite our hide and seek example like this:
var number = 1

repeat {
    print(number)
    number += 1
} while number <= 20

print("Ready or not, here I come!")
Because the condition comes at the end of the repeat loop the code inside the loop will always be executed at least once, whereas while loops check their condition before their first run.
For example, this print() function will never be run, because false is always false:
while false {
    print("This is false")
}

Xcode will even warn us that the print() line will never be executed.
On the other hand, this print() function will be run once, because repeat only fails the condition after the loop runs:
repeat {
    print("This is false")
} while false


EXITING LOOPS : -
You can exit a loop at any time using the break keyword. To try this out, let’s start with a regular while loop that counts down for a rocket launch:
var countDown = 10

while countDown >= 0 {
    print(countDown)
    countDown -= 1
}

print("Blast off!")
In this case, the astronaut in command gets bored part-way through the countdown and decides to skip the remainder and launch straight away:
while countDown >= 0 {
    print(countDown)

    if countDown == 4 {
        print("I'm bored. Let's go now!")
        break
    }

    countDown -= 1
}
With that change, as soon as countDown reaches 4 the astronaut’s message will be printed, and the rest of the loop gets skipped.


EXITING MULTIPLE LOOPS : -
If you put a loop inside a loop it’s called a nested loop, and it’s not uncommon to want to break out of both the inner loop and the outer loop at the same time.

As an example, we could write some code to calculate the times tables from 1 through 10 like this:
for i in 1...10 {
    for j in 1...10 {
        let product = i * j
        print ("\(i) * \(j) is \(product)")
    }
}
If we wanted to exit part-way through we need to do two things. First, we give the outside loop a label, like this:
outerLoop: for i in 1...10 {
    for j in 1...10 {
        let product = i * j
        print ("\(i) * \(j) is \(product)")
    }
}
Second, add our condition inside the inner loop, then use break outerLoop to exit both loops at the same time:
outerLoop: for i in 1...10 {
    for j in 1...10 {
        let product = i * j
        print ("\(i) * \(j) is \(product)")

        if product == 50 {
            print("It's a bullseye!")
            break outerLoop
        }
    }
}
With a regular break, only the inner loop would be exited – the outer loop would continue where it left off.


SKIPPING ITEMS : -
As you’ve seen, the break keyword exits a loop. But if you just want to skip the current item and continue on to the next one, you should use continue instead.

To try this out, we can write a loop from 1 through 10, then use Swift’s remainder operator to skip any numbers that are odd:
for i in 1...10 {
    if i % 2 == 1 {
        continue
    }

    print(i)
}
Remember, the remainder operator figures out how many times 2 fits into each number in our loop, then returns whatever is left over. So, if 1 is left over, it means the number is odd, so we can use continue to skip it.


INFINITE LOOPS : - 
It’s common to use while loops to make infinite loops: loops that either have no end or only end when you’re ready. All apps on your iPhone use infinite loops, because they start running, then continually watch for events until you choose to quit them.

To make an infinite loop, just use true as your condition. true is always true, so the loop will repeat forever. Warning: Please make sure you have a check that exits your loop, otherwise it will never end.
As an example, we’re going to use while true to print the music of John Cage’s piece 4’33” – if you didn’t know, it’s famous because it’s 4 minutes and 33 seconds of complete silence.

We can write the “music” for this piece using while true, with a condition that exits the loop when we’ve gone around enough times:
var counter = 0

while true {
    print(" ")
    counter += 1

    if counter == 273 {
        break
    }
}

== FUNCTIONS ==
WRITING FUNCTIONS : -
Functions let us re-use code, which means we can write a function to do something interesting then run that function from lots of places. Repeating code is generally a bad idea, and functions help us avoid doing that.

To start with, we’re going to write a function that prints help information for users of our app. We might need this anywhere in our app, so having it as a function is a good idea.

Swift functions start with the func keyword, then your function name, then open and close parentheses. All the body of your function – the code that should be run when the function is requested – is placed inside braces.

Let’s write the printHelp() function now:
func printHelp() {
    let message = """
Welcome to MyApp!

Run this app inside a directory of images and
MyApp will resize them all into thumbnails
"""

    print(message)
}
We can now run that using printHelp() by itself:
printHelp()


ACCEPTING PARAMETERS : -
Functions become more powerful when they can be customized each time you run them. Swift lets you send values to a function that can then be used inside the function to change the way it behaves. We’ve used this already – we’ve been sending strings and integers to the print() function, like this:
print("Hello, world!")

Values sent into functions this way are called parameters.
To make your own functions accept parameters, give each parameter a name, then a colon, then tell Swift the type of data it must be. All this goes inside the parentheses after your function name.

For example, we can write a function to print the square of any number:
func square(number: Int) {
    print(number * number)
}
That tells Swift we expect to receive an Int, and it should be called number. This name is used both inside the function when you want to refer to the parameter, but also when you run the function, like this:
square(number: 8)


RETURNING VALUES : - 

As well as receiving data, functions can also send back data. To do this, write a dash then a right angle bracket after your function’s parameter list, then tell Swift what kind of data will be returned.
Inside your function, you use the return keyword to send a value back if you have one. Your function then immediately exits, sending back that value – no other code from that function will be run.
We could rewrite our square() function to return a value rather than print it directly:
func square(number: Int) -> Int {
    return number * number
}
Now we can grab that return value when the function is run, and print it there:
let result = square(number: 8)
print(result)
If you need to return multiple values, this is a perfect example of when to use tuples.

PARAMETER LABELS : -
We wrote our square() function like this:
func square(number: Int) -> Int {
    return number * number
}

That names its parameter number, so we can use number inside the function to refer to it, but we must also use the name when running the function, like this:
let result = square(number: 8)

Swift lets us provide two names for each parameter: one to be used externally when calling the function, and one to be used internally inside the function. This is as simple as writing two names, separated by a space.
To demonstrate this, here’s a function that uses two names for its string parameter:
func sayHello(to name: String) {
    print("Hello, \(name)!")
}

The parameter is called to name, which means externally it’s called to, but internally it’s called name. This gives variables a sensible name inside the function, but means calling the function reads naturally:
sayHello(to: "Taylor")


OMITTING PARAMETER LABELS : -
You might have noticed that we don’t actually send any parameter names when we call print() – we say print("Hello") rather than print(message: "Hello").

You can get this same behavior in your own functions by using an underscore, _, for your external parameter name, like this:
func greet(_ person: String) {
    print("Hello, \(person)!")
}

You can now call greet() without having to use the person parameter name:
greet("Taylor")

This can make some code more natural to read, but generally it’s better to give your parameters external names to avoid confusion. For example, if I say setAlarm(5) it’s hard to tell what that means – does it set an alarm for five o’clock, set an alarm for five hours from now, or activate pre-configured alarm number 5?


DEFAULT PARAMETERS : -
The print() function prints something to the screen, but always adds a new line to the end of whatever you printed, so that multiple calls to print() don’t all appear on the same line.

You can change that behavior if you want, so you could use spaces rather than line breaks. Most of the time, though, folks want new lines, so print() has a terminator parameter that uses new line as its default value.

You can give your own parameters a default value just by writing an = after its type followed by the default you want to give it. So, we could write a greet() function that can optionally print nice greetings:
func greet(_ person: String, nicely: Bool = true) {
    if nicely == true {
        print("Hello, \(person)!")
    } else {
        print("Oh no, it's \(person) again...")
    }
}

That can be called in two ways:
greet("Taylor")
greet("Taylor", nicely: false)


VARIADIC FUNCTIONS : -
Some functions are variadic, which is a fancy way of saying they accept any number of parameters of the same type. The print() function is actually variadic: if you pass lots of parameters, they are all printed on one line with spaces between them:
print("Haters", "gonna", "hate")

You can make any parameter variadic by writing ... after its type. So, an Int parameter is a single integer, whereas Int... is zero or more integers – potentially hundreds.

Inside the function, Swift converts the values that were passed in to an array of integers, so you can loop over them as needed.
To try this out, let’s write a square() function that can square many numbers:
func square(numbers: Int...) {
    for number in numbers {
        print("\(number) squared is \(number * number)")
    }
}
Now we can run that with lots of numbers just by passing them in separated by commas:
square(numbers: 1, 2, 3, 4, 5)


WRITING THROWING FUNCTIONS : -
Sometimes functions fail because they have bad input, or because something went wrong internally. Swift lets us throw errors from functions by marking them as throws before their return type, then using the throw keyword when something goes wrong.

First we need to define an enum that describes the errors we can throw. These must always be based on Swift’s existing Error type. We’re going to write a function that checks whether a password is good, so we’ll throw an error if the user tries an obvious password:
enum PasswordError: Error {
    case obvious
}

Now we’ll write a checkPassword() function that will throw that error if something goes wrong. This means using the throws keyword before the function’s return value, then using throw PasswordError.obvious if their password is “password”.

Here’s that in Swift:
func checkPassword(_ password: String) throws -> Bool {
    if password == "password" {
        throw PasswordError.obvious
    }

    return true
}


RUNNING THROWING FUNCTIONS : - 
Swift doesn’t like errors to happen when your program runs, which means it won’t let you run an error-throwing function by accident.

Instead, you need to call these functions using three new keywords: do starts a section of code that might cause problems, try is used before every function that might throw an error, and catch lets you handle errors gracefully.

If any errors are thrown inside the do block, execution immediately jumps to the catch block. Let’s try calling checkPassword() with a parameter that throws an error:
do {
    try checkPassword("password")
    print("That password is good!")
} catch {
    print("You can't use that password.")
}
When that code runs, “You can’t use that password” is printed, but “That password is good” won’t be – that code will never be reached, because the error is thrown.


INOUT PARAMETERS : -
All parameters passed into a Swift function are constants, so you can’t change them. If you want, you can pass in one or more parameters as inout, which means they can be changed inside your function, and those changes reflect in the original value outside the function.

For example, if you want to double a number in place – i.e., change the value directly rather than returning a new one – you might write a function like this:
func doubleInPlace(number: inout Int) {
    number *= 2
}

To use that, you first need to make a variable integer – you can’t use constant integers with inout, because they might be changed. You also need to pass the parameter to doubleInPlace using an ampersand, &, before its name, which is an explicit recognition that you’re aware it is being used as inout.
In code, you’d write this:
var myNum = 10 
doubleInPlace(number: &myNum)
