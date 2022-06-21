# Clean Code Developer Checklist

A developer checklist mostly derived from the book **Clean Code by Robert C Martin**

## Table of contents :bookmark_tabs:

- [Naming things](#naming-things-u5272)
- [Functions](#functions-microscope)
- [Formatting](#formatting-rainbow)
- [Objects and Data Structures](#objects-and-data-structures-two_men_holding_hands)
- [Error handling](#error-handling-interrobang)
- [Unit tests](#unit-tests-umbrella)
- [Class](#class-school_satchel)
- [Emergence](#emergence-green_book)
- [Concurrency](#concurrency-arrows_clockwise)
- [Code smells](#code-smells-speak_no_evil)
- [Honourable mentions](#honourable-mentions-basecamp)

<br/>

<hr>

## Naming things :u5272:

#### 🟢 **Name should reveal intent**

- It should tell you why it exists, what it does, and how it is used.
- Name should depict the context.

#### 🟢 **Avoid using abbreviations**

- Use `hypotenuse` instead of `hp`.

#### 🟢 **Do not encode name with data structure**

- Use `accounts` instead of `accountList`.

#### 🟢 **Do not use names which vary in small ways**

- Find the difference between `ControllerForEfficientHandlingOfStrings` and `ControllerForEfficientStorageOfStrings` :dancers:

#### 🟢 **Do not name variables just to satisfy the compiler**

- Don't name something `name1` cause `name` is already taken.

#### 🟢 **Avoid using noise words**

- `ProductData` and `ProductInfo` kind of means the same thing.
- Similarly words like `a`, `an`, `the` are also noise words, for example naming a variable `product` is sufficient, no need to `theProduct`
- Noise words are also **redundant**, use `name` instead of `nameString`.

#### 🟢 **Distinguish names in such a way that the reader knows which one to call.**

#### 🟢 **Use pronounceable names**

#### 🟢 **Use searchable names**

- Use constants instead of hard coding a value, `WORK_DAYS_PER_WEEK = 5` instead of just using 5.

#### 🟢 **Include units of a measurable entity to its variable name**

- Using `expiryTimeInSeconds` is better than `expiryTime`

#### 🟢 **The length of a name should correspond to the size of its scope**

- There can be a variable `i` inside a `for loop` but `i` should never be a `instance variable`.

#### 🟢 **Classes and objects should have noun or noun phrase names.**

- Avoid words like `Manager`, `Processor`, `Data`, or `Info` in the name of a class.
- If your class name ends with `er`, `or` or `utils`, you should consider re looking at the responsibility of the class.
- A class name should not be a verb.

#### 🟢 **Methods should have verb or verb phrase names**

#### 🟢 **When constructors are overloaded, try to use static factory methods with names that describe the** **arguments**

- `Complex fulcrumPoint = Complex.FromRealNumber(23.0)`is better than `Complex fulcrumPoint = new Complex(23.0)`

#### 🟢 **Pick one word for one abstract concept and stick with it**

    - For instance, it’s confusing to have `fetch`, `retrieve`, and `get` as equivalent methods of different classes.

#### 🟢 **Don’t add gratuitous context**

- For application "Gas Station Deluxe," it is a bad idea to prefix every class with `GSD`.
- For example use `AccountAddress` instead of `GSDAccountAddress`

#### 🟢 **It's okay to use computer science terms, algorithm names, pattern names, math terms**

- Always using the problem domain to get names might result in complication, hence we can use solution domain names on need.

#### 🟢 **Add no more context to a name than is necessary**

- Shorter names are generally better than longer ones, so long as they are clear.

<br/>
<hr>
<br/>

## Functions :microscope:

#### 🟢 **Function should be small**

- They should be smaller :stuck_out_tongue:

#### 🟢 **Blocks inside `if`, `else`, `while` should be one line long, and that should probably be a function call**

- This keep the enclosing function small.
- It also adds documentary value because the function called within the block can have a nicely descriptive name.

#### 🟢 **The indent level of a function should not be greater than one or two**

#### 🟢 **Functions should do one thing, they should do it well, they should do it only**

- If a function does only those steps that are one level below the stated name of the function, then the function is doing one thing.

#### 🟢 **Functions should not have sections inside them**

- If you are able to split a function into sections, then that function is probably doing multiple things.

#### 🟢 **Function should have one level of abstraction**

- We need to make sure that the statements within our function are all at the same level of abstraction.

#### 🟢 **The Stepdown Rule**

- The abstraction of a class should decrease as we go reading downwards.

#### 🟢 **Switch statement should be buried in a low-level class, should appear only once, to create polymorphic objects and is never repeated**

- For example it can be in an `Abstract Factory`, but not to be seen anywhere else.

#### 🟢 **Try to have functions with 3 arguments**

- Try to keep no of arguments to 3/4.
- The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification
- Practically it should never go beyond 4.

#### 🟢 **If a function is going to transform its input argument, the transformation should appear as the return value**

- If a function does transformation operation of it's input, then the output of that function should be the transformed value
- If a function is doing a transform of the input, it should do that that only.

#### 🟢 **Flag arguments should be avoided**

- It does one thing if the flag is `true` and another if the flag is `false`, hence violating Single Responsibility.
- We should split the function into 2 different functions and call them separately.

#### 🟢 **When a function need more than 2 or 3 arguments, if possible wrap some of those arguments into a class of their own**

#### 🟢 **Functions should not have any side-effects**

- Mutation of input parameters is to be avoided.

#### 🟢 **Function should do one thing, which the name suggests and not do anything else**

#### 🟢 **Functions should either do something or answer something (command query separation)**

- Either function should change the state of something, or it should return something.

#### 🟢 **Prefer exceptions to returning error codes**

- When you return an error code, you create the problem that the caller must deal with the error immediately.
- Also using Error `enum` is creating a dependency magnet, multiple classes must import and use them.

#### 🟢 **Extract Try/Catch Blocks**

- Error handing is one thing. Thus, a function that handles errors should do nothing else.
- If the keyword try exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.

#### 🟢 **Avoid code duplication**

- The DRY principle. `Don't Repeaty Yourself`

<br/>
<hr>
<br/>

## Formatting :rainbow:

#### 🟢 **Vertical size of a file should be typically be within the 200 lines limit**

#### 🟢 **We would like a source file to be like a newspaper article**

- The name should be simple but explanatory.
- The topmost parts of the source file should provide the high-level concepts and algorithms. i.e. the `public methods`
  - We should be able to tell what a class does by looking at the upper portion of the class.
  - We should be able to see how it does, when we scroll downwards.
- Detail should increase as we move downward we should see more implementation details i.e. the `private methods`
- The general rule for arranging methods
  - public
  - protected
  - private

#### 🟢 **Vertical Openness Between Concepts**

- Each line represents an expression or a clause, and each group of lines represents a complete thought. Those thoughts should be separated from each other with blank lines.
- i.e. methods should be vertically separated by breaks

#### 🟢 **Variables should be declared as close to their usage as possible**

#### 🟢 **Instance variables should be declared at the top of the class**

#### 🟢 **If one function calls another, they should be vertically close**

- The caller should be above the callee.
- The `private` method which is being called from a `public` method, should appear close to the `public` method.

#### 🟢 **Codes having strong conceptual affinity between them should have less vertical separation between them**

For example

```java
public static void assertTrue(boolean condition) {
assertThat(condition).isTrue();
}

public static void assertFalse(boolean condition) {
assertThat(condition).isFalse()
}
```

#### 🟢 **Lines should not be more than 120 characters**

#### 🟢 **Use spaces between `operators`, `parameters`, and `commas`**

#### 🟢 **Use a consistent formatting style across the team**

- Use the same `.editorconfig` file across the team.

#### 🟢 **Indentation**

- Collapsing everything in one line with short `ifs`, `loops`, `functions` is not a good idea.
- Even for one line `ifs`, one line `whiles` - expand them into multiline and add indent.

<br/>
<hr>
<br/>

## Objects and Data Structures :two_men_holding_hands:

#### 🟢 **Hide implementation of classes with Abstraction**

- Do not expose variables out through getters and setters. Rather have abstract interfaces that allow users to manipulate the data, without having to know its implementation.
- We do not want to expose the details of our data. Rather we want to express our data in abstract terms.

#### 🟢 **Data/object anti-symmetry**

- Objects should hide their data behind abstractions and expose functions that operate on that data.
- Data structure should expose their data and have no meaningful functions.

#### 🟢 **Choosing between Functional code and OO code**

- Functional code (code using data structures) makes it easy to add new functions without changing the existing data structures (using pattern matching).
- OO code, on the other hand, makes it easy to add new classes (using polymorphism) without changing existing functions.
- In any complex system there are going to be times when we want to add new data types rather than new functions. For these cases objects and OO are most appropriate.
- On the other hand, there will also be times when we’ll want to add new functions as opposed to data types. In that case procedural code and data structures will be more appropriate.
- Everything is an object is a myth. Sometimes you should just have simple data structures with procedures operating on them.

#### 🟢 **The law of demeter**

- a method f of a class C should only call the methods of these:
  - C
  - An object created by f
  - An object passed as an argument to f
  - An object held in an instance variable of C
- The method should not invoke methods on objects that are returned by any of the allowed functions.

#### 🟢 **Train Wrecks**

```java
final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();
```

This kind of chaining operations are called train wrecks and should be avoided.

- This is a violation of law of demeter as well, as we are invoking methods on objects that are returned.
- And this is only permitted if data structures are used instead of objects, as objects are not supposed to expose their data.
- But chained transformations are fine though

```javascript
someList.map(..).map(..).filter(..)
```

#### 🟢 **Hybrids, classes which have functions that do significant things, and they also have either public variables or public accessors and mutators**

- This might result in feature envy smell, as we are exposing access to variables, the caller might be tempted to use them.

#### 🟢 **DTOs should not have any behavior , i.e. they should be data-structure and not objects**

- DTOs/Value objects should have a `equals` method.
- Any operation in a value object should return a new instance of that class.

<br/>
<hr>
<br/>

## Error handling :interrobang:

#### 🟢 **Error handling is important, but if it obscures logic, it’s wrong**

- If your codebase has to many error handler spread across different modules, then by default the code becomes unreadable.

#### 🟢 **Use unchecked exceptions**

- Checked exceptions is an `Open/Closed Principle` violation. If you throw a checked exception from a method in your code and the catch is three levels above, you must declare that exception in the signature of each method between you and the catch. This means that a change at a low level of the code can force signature changes on many higher levels.
- `Encapsulation` is also broken because all functions in the path of a throw must know about details of that low-level exception.

#### 🟢 **Provide context with exceptions**

- Create informative error messages and pass them along with your exceptions.
- Mention the operation that failed and the type of failure.
- Pass on the stack trace.

#### 🟢 **Define exception classes in terms of a caller’s needs**

- Define the exception in such a way that the caller can take a decision based on the exception only.
- Use different classes only if there are times when you want to catch one exception and allow the other one to pass through.

#### 🟢 **If a portion of code throws many types of exception, wrap that part and throw a common exception**

- Using the information sent with the exception we should be able to distinguish the errors.

#### 🟢 **Wrap your third party API calls**

- When you wrap a third-party API, you minimize your dependencies upon it.
- You can choose to move to a different library in the future without much penalty.
- Wrapping also makes it easier to mock out third-party calls when you are testing your own code.

#### 🟢 **Instead of having a special flow for exception, use special case pattern**

- From this

```java
try {
  MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
  m_total += expenses.getTotal();
} catch (MealExpensesNotFound e) {
  m_total += getMealPerDiem();
}
```

- To this

```java
MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
m_total += expenses.getTotal();
```

```java
public class PerDiemMealExpenses implements MealExpenses {
  public int getTotal() {
    // return the per diem default
  }
}
```

- You basically create a class which it handles a special case for you. Hence the client code doesn’t have to deal with exceptional behavior.

#### 🟢 **Don’t return null**

- When we return null, the caller needs to have a null check.
- Remedy to this can be
  - Special case object.
  - Returning empty list.

#### 🟢 **Don’t pass null as arguments**

- If you pass null, then the callee has to always check for null args.

```java
public double xProjection(Point p1, Point p2) {
  if (p1 == null || p2 == null) {
      throw InvalidArgumentException(
        "Invalid argument for MetricsCalculator.xProjection");
  }
  return (p2.x – p1.x) * 1.5;
}
```

- a cleaner way to do this could be

```java
public double xProjection(Point p1, Point p2) {
    assert p1 != null : "p1 should not be null";
    assert p2 != null : "p2 should not be null";
    return (p2.x – p1.x) * 1.5;
}
```

But this also doesn't solve the problem, instead of `NullPointerException` we are going to get some different `RuntimeException`

- If your language supports it, use a `optional` pattern maybe.

<br/>
<hr>
<br/>

## Unit tests :umbrella:

#### 🟢 **Follow three laws of TDD**

- You may not write production code until you have written a failing unit test.
- You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
- You may not write more production code than is sufficient to pass the currently failing test.

#### 🟢 **Keep test clean**

- Tests should be first-class citizen. It must be kept as clean as production code
- Tests must change as the production code evolves. The dirtier the tests, the harder they are to change.

#### 🟢 **Follow the The Build-Operate-Check pattern**

- The first part builds up the test data, the second part operates on that test data, and the third part checks that the operation yielded the expected results.
- This is same as `given-when-then` pattern.

#### 🟢 **A Dual Standard**

- There are things that you might never do in a production environment that are perfectly fine in a test environment. Usually they involve issues of memory or CPU efficiency.

#### 🟢 **One assert per test (flexible)**

- Ideally there should be one assert per test.
- But it's okay if we have more, at the end of the day the number of asserts in a test ought to be minimized.
- The goal is to have one logical assert per test or to test a single behavior in a unit test.

#### 🟢 **Single Concept per Test**

- Do not operate on different data and then try to assert them in a single test.

#### 🟢 **F.I.R.S.T.**

- FAST: Tests should be fast.
- INDEPENDENT: Tests should not depend on each other.
- REPEATABLE: Tests should be repeatable in any environment.
- SELF-VALIDATING: The tests should have a boolean output.
- TIMELY: The tests need to be written in a timely fashion.
  - Unit tests should be written just before the production code that makes them pass.

<br/>
<hr>
<br/>

## Class :school_satchel:

#### 🟢 **Class organization** :arrow_down:

- Variables
  - Public static constants
  - private static variables
  - private instance variables
- Public function
  - Related private functions

#### 🟢 **Classes should maintain Encapsulation**

- Variables and utility functions should be private

#### 🟢 **Classes should be small and do only one thing**
- The name of a class should describe what responsibilities it fulfills.
- If we cannot derive a concise name for a class, then it’s likely too large.
- The more ambiguous the class name, the more likely it has too many responsibilities.
- We should also be able to write a brief description of the class in about 25 words, without using the words "if," "and," "or," or "but". If you have to use "and" then probably the class has multiple responsibilities.

#### 🟢 **Single Responsibility Principle**

- Classes should have only one reason to change.

#### 🟢 **Classes should have cohesion**

- Classes should have a small number of instance variables. Each of the methods of a class should manipulate one or more of those variables.
- When classes lose cohesion, split them.
- Private method behavior that applies only to a small subset of a class can be a useful heuristic, it's probably a hint that you need to extract that portion into a different class.

#### 🟢 **Classes should depend upon abstractions, not on concrete details (Dependency Inversion)**

<br/>
<hr>
<br/>

## Emergence :green_book:

#### 🟢 **Design must produce a system that runs all tests as writing tests leads to better designs**

- A system might have a perfect design on paper, but if there is no simple way to verify that the system actually works as intended, then all the paper effort is questionable.
- Making our systems testable pushes us toward a design where our classes are small and single purpose. It’s just easier to test classes that conform to the Single Responsibility Principle.
- The more tests we write, the more we’ll continue to push toward things that are simpler to test.
- Tight coupling makes it difficult to write tests. So, similarly, the more tests we write, the more we use principles like DIP and tools like dependency injection, interfaces, and abstraction to minimize coupling.
- The fact that we have these tests eliminates the fear that cleaning up the code will break it, and hence we can refactor and make changes with confidence.

#### 🟢 **No duplication**

- Duplication represents additional work, additional risk, and additional unnecessary complexity.

#### 🟢 **Expressive**

- You can express yourself by choosing good names.
- You can also express yourself by using standard nomenclature. Design patterns names, such as COMMAND or VISITOR.
- Well-written unit tests are also expressive. A primary goal of tests is to act as documentation by example.

#### 🟢 **Minimal classes and methods**

- Create small classes but create one when it's justifiable, creating classes just to reduce out on the no of lines of code is a bad practice.
- Creating an interface for each and every class should be avoided. Or fields and behavior must always separated into data classes and behavior classes.

<br/>
<hr>
<br/>

## Concurrency :arrows_clockwise:

#### 🟢 **Concurrency always doesn't improve performance**

#### 🟢 **To make a system concurrent we might need to change the overall design strategy**

#### 🟢 **Understanding potential concurrency issue is important even though it might not be the problem at hand**

#### 🟢 **Keep your concurrency-related code separate from other code**

#### 🟢 **Shared data between threads create synchronization problems, hence take data encapsulation to heart, limit the access of any data that may be shared**

#### 🟢 **Instead of sharing data, create copies of data for different thread and collect them at the end of processing**

#### 🟢 **Threads Should Be as Independent as Possible, and should not share data with any other thread**

#### 🟢 **Use thread safe library functions**

- Use the provided thread-safe collections.
- Use the executor framework for executing unrelated tasks.
- Use nonblocking solutions when possible.

#### 🟢 **Use producer consumer model for concurrent operation**

- One or more producer threads create some work and place it in a buffer or queue. One or more consumer threads acquire that work from the queue and complete it.

#### 🟢 **Use Readers-Writers model for concurrent operation**

- For read heavy systems
  - Makes writers wait until there are no readers before allowing the writer to perform an update.
- For write heavy systems
  - Writers should be given the priority

#### 🟢 **Use different locking strategies like**

- Client-Based Locking
- Server-Based Locking
- Adapted Server Locking

#### 🟢 **Keep your synchronized sections small and avoid side-effects**

#### 🟢 **Have a shutdown strategy in place which works**

#### 🟢 **Treat spurious failures as candidate threading issues**

- Do not ignore system failures as one-offs.

#### 🟢 **Get your non-threaded code working first**

- Do not try to chase down nonthreading bugs and threading bugs at the same time. Make sure your code works outside of threads.

#### 🟢 **Make your threaded code pluggable**

- Make your thread-based code especially pluggable so that you can run it in various configurations.

#### 🟢 **Make your threaded code tunable**

- Allow configurations like, number of threads to be easily tuned.

#### 🟢 **Run with more threads than processors**

#### 🟢 **Run on different platforms**

#### 🟢 **Instrument your code to try and force failures**

<br/>
<hr>
<br/>

## Code smells :speak_no_evil:

#### 🟢 **If you see commented out code. delete it**

#### 🟢 **Unused code should be deleted**

#### 🟢 **Implementation should be obvious**

#### 🟢 **Look for every boundary condition and write a test for it**

#### 🟢 **Base classes should know nothing about their derivatives**

#### 🟢 **Code should be consistent**

- If within a particular function you use a variable named response to hold an HttpServletResponse, then use the same variable name consistently in the other functions that use HttpServletResponse objects

#### 🟢 **Prefer nonstatic methods to static methods**

- If you really want a function to be static, make sure that there is no chance that you’ll want it to behave polymorphically.

#### 🟢 **Avoid Negative Conditionals**

- `if (buffer.shouldCompact())` is better than `if (!buffer.shouldNotCompact())`

#### 🟢 **Encapsulate Boundary Conditions**

```javascript
if(level + 1 < tags.length) {
  parts = new Parse(body, tags, level + 1, offset + endTag);
  body = null
}
```

`level + 1` is a boundary operation which is repeated so we can wrap that in a variable like `nextLevel = level + 1`

#### 🟢 **Avoid Long Import Lists by Using Wildcards**

#### 🟢 **Don’t Inherit Constants**

- Use static imports instead

#### 🟢 **Use enums and not `public static final ints/strings`**

<br/>
<hr>
<br/>

## Honourable mentions :basecamp:

In this section I am going to list down few things which are absolutely legendary but I missed mentioning them. There are tons of resources available online for these topics, you can read them from there.

#### 🟢 **The OG S.O.L.I.D principles, no clean code discussion is complete without them**

#### 🟢 **Object Calisthenics**
