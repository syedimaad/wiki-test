## **1. Variables & Constants**

**Kotlin Syntax:**

val pi = 3.14 // Immutable (like Swift\'s \`let\`) var age = 30 //
Mutable (like Swift\'s \`var\`)

**Types are inferred**, but can be explicit:

val name: String = \"Sam\" var count: Int = 5

**⚠️ Note:**

- `val` makes the *reference* immutable, not the object itself if it\'s
  mutable.

- Like Swift, Kotlin is strongly typed with type inference.

------------------------------------------------------------------------

## **2. Basic Types**

Common types:

val name: String = \"John\" val age: Int = 25 val height: Double = 1.75
val isActive: Boolean = true

**Nullable Types:**\
Similar to Swift Optionals, Kotlin uses `?`:

var email: String? = null email = \"abc@example.com\"

Safe Access:

println(email?.length) // Prints length if not null

Force Unwrapping (use cautiously):

println(email!!.length) // Crashes if \`email\` is null

------------------------------------------------------------------------

## **3. Functions**

Function Syntax:

fun greet(name: String): String { return \"Hello, \$name\" }

Single-expression function:

fun square(x: Int) = x \* x

Default Arguments:

fun greet(name: String = \"Guest\") { println(\"Hello, \$name\") }

------------------------------------------------------------------------

## **4. String Interpolation**

val name = \"Sam\" println(\"Hello, \$name\") println(\"Length of name:
\${name.length}\")

------------------------------------------------------------------------

## **5. Control Flow**

### **If-Else**

val max = if (a \> b) a else b

### **When (Like Switch in Swift, but more powerful)**

val result = when (score) { 10 -\> \"Perfect\" in 5..9 -\> \"Good\" else
-\> \"Needs Improvement\" }

------------------------------------------------------------------------

# 🛠️ **Mini Project: BMI Calculator (CLI)**

fun main() { val height = 1.75 // meters val weight = 70.0 // kg val bmi
= weight / (height \* height) println(\"Your BMI is \$bmi\") when { bmi
\< 18.5 -\> println(\"Underweight\") bmi in 18.5..24.9 -\>
println(\"Normal weight\") bmi in 25.0..29.9 -\> println(\"Overweight\")
else -\> println(\"Obese\") } }

------------------------------------------------------------------------

# 📚 **Reference Links**

1.  **Official Kotlin Language Basics**\
    [https://kotlinlang.org/docs/basic-syntax.html](https://kotlinlang.org/docs/basic-syntax.html){card-appearance="inline"}

2.  **Kotlin Playground (Try Code Online)**\
    [https://play.kotlinlang.org/](https://play.kotlinlang.org/){card-appearance="inline"}

3.  **Kotlin for Swift Developers (Comparison Guide)**\
    <https://kotlinlang.org/docs/comparison-to-swift.html>

------------------------------------------------------------------------

# 🎯 **Next Step**

Would you like:\
✅ A small coding exercise to practice today?\
✅ Or should we directly continue to Day 2: Collections & Lambdas?

Your pick!

**Next Prompt: Let\'s continue with day 2. In addition to your material,
give me reference links too.**
