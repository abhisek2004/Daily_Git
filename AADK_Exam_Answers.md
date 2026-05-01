# Android App Development using Kotlin — Complete Exam Answers
### GIET University | B.Tech 6th Sem | CSE / CSE(AIML) / CSE(DS)
### Covers: AY 21 Set-1, Set-2 | April 2025 Paper

---

# PART – A (Short Answer Questions — 2 Marks Each)

---

## Q. What is a Toast? Write its syntax.

**Toast** is a small pop-up message that appears on the screen for a short time and then disappears automatically. It is used to show quick feedback to the user without any interaction.

**Syntax:**
```kotlin
Toast.makeText(context, "Your message here", Toast.LENGTH_SHORT).show()
```

- `Toast.LENGTH_SHORT` — shows for 2 seconds
- `Toast.LENGTH_LONG` — shows for 3.5 seconds

**Example:**
```kotlin
Toast.makeText(this, "Login Successful!", Toast.LENGTH_SHORT).show()
```

---

## Q. What do you mean by Adapter?

An **Adapter** is a bridge between data (like a list or array) and a UI component (like ListView or RecyclerView). It takes data from a data source and converts each item into a View that can be displayed in the list.

**Types:**
- `ArrayAdapter` — for simple string lists
- `BaseAdapter` — customizable for complex layouts
- `RecyclerView.Adapter` — modern, efficient adapter for RecyclerView

**Example:**
```kotlin
val adapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, listOf("Item1","Item2"))
listView.adapter = adapter
```

---

## Q. Differentiate between Activity and Fragment

| Feature | Activity | Fragment |
|---|---|---|
| Definition | A single screen with UI | A reusable part/portion of a screen |
| Independence | Independent, has its own lifecycle | Depends on Activity |
| Reusability | Cannot be reused easily | Can be reused in multiple Activities |
| Back Stack | Managed by system | Managed by FragmentManager |
| XML File | activity_main.xml | fragment_login.xml |

---

## Q. What do you mean by Intent? Explain different types of Intent.

**Intent** is a messaging object used to request an action from another component (Activity, Service, etc.) in Android.

**Types of Intent:**

**1. Explicit Intent** — used to start a specific Activity by name.
```kotlin
val intent = Intent(this, SecondActivity::class.java)
startActivity(intent)
```

**2. Implicit Intent** — used to perform an action without specifying the exact component (system chooses the best app).
```kotlin
val intent = Intent(Intent.ACTION_VIEW, Uri.parse("https://www.google.com"))
startActivity(intent)
```

---

## Q. What do you mean by Companion Object? Give an example.

A **companion object** is an object declared inside a class using the `companion` keyword. It is used to define members that belong to the class (similar to `static` in Java), so they can be accessed without creating an object.

**Example:**
```kotlin
class MathHelper {
    companion object {
        fun square(n: Int): Int = n * n
    }
}

// Access without creating object:
println(MathHelper.square(5))  // Output: 25
```

---

## Q. Demonstrate the use of Elvis Operator for Null Safety.

The **Elvis operator `?:`** returns the value on its left if it is not null, otherwise returns the value on its right.

**Syntax:** `val result = value ?: defaultValue`

**Example:**
```kotlin
val name: String? = null
val displayName = name ?: "Guest"
println(displayName)  // Output: Guest

val length = name?.length ?: 0
println(length)  // Output: 0
```

---

## Q. Differentiate between a Class and a Data Class

| Feature | Class | Data Class |
|---|---|---|
| Declaration | `class Person` | `data class Person` |
| Purpose | General purpose | Mainly to hold data |
| `toString()` | Not auto-generated | Auto-generated |
| `equals()` and `hashCode()` | Not auto-generated | Auto-generated |
| `copy()` | Not available | Available |

**Example:**
```kotlin
data class Student(val name: String, val age: Int)
val s = Student("Ravi", 20)
println(s)  // Output: Student(name=Ravi, age=20)
val s2 = s.copy(age = 21)
```

---

## Q. Explain Fragment in Android App.

A **Fragment** is a modular section of an Activity that has its own layout and lifecycle. Multiple fragments can be placed in a single Activity to build a multi-pane UI (like tablet layouts).

**Key Points:**
- Fragments can be added, replaced, or removed at runtime.
- They must be hosted inside an Activity.
- Fragment lifecycle methods: `onAttach()`, `onCreate()`, `onCreateView()`, `onStart()`, `onResume()`, `onPause()`, `onStop()`, `onDestroyView()`, `onDetach()`

---

## Q. Explain the need of RecyclerView in Kotlin.

**RecyclerView** is an advanced and flexible version of ListView. It is used to display large sets of data efficiently.

**Why RecyclerView is needed:**
- It **recycles** views that are no longer visible, saving memory.
- It supports **horizontal, vertical, and grid** layouts via `LayoutManager`.
- It allows custom animations on items.
- Better performance than ListView for large lists.

**Main components:** `RecyclerView.Adapter`, `ViewHolder`, `LayoutManager`

---

## Q. Explain the Real-time Database (Firebase).

**Firebase Realtime Database** is a cloud-hosted NoSQL database provided by Google (Firebase). Data is stored as JSON and synced in real-time to all connected clients.

**Key Features:**
- Data is synced instantly across all devices.
- Works offline — stores data locally and syncs when online.
- Data stored as a JSON tree.
- Easy to integrate in Android with Firebase SDK.

**Use Case:** Chat apps, live score updates, collaborative apps.

---
---

# PART – B (Long Answer Questions)

---

# UNIT 1 — Kotlin Programming

---

## Q. Explain All Features / Key Features of Kotlin

Kotlin is a modern, statically typed programming language developed by JetBrains and officially supported by Google for Android development.

**1. Concise Syntax**
Less boilerplate code compared to Java. For example, data classes automatically generate `equals()`, `hashCode()`, `toString()`, and `copy()`.

**2. Null Safety**
Kotlin prevents NullPointerException by distinguishing nullable (`String?`) and non-nullable (`String`) types at compile time.
```kotlin
var name: String? = null  // nullable
var city: String = "Delhi"  // non-nullable
```

**3. Object-Oriented**
Supports classes, objects, inheritance, interfaces, and encapsulation.

**4. Functional Programming**
Supports lambda expressions, higher-order functions, and function types.
```kotlin
val double = { x: Int -> x * 2 }
```

**5. Extension Functions**
Add new functions to existing classes without modifying them.
```kotlin
fun String.shout() = this.uppercase() + "!!!"
println("hello".shout())  // HELLO!!!
```

**6. Smart Casts**
Automatically casts types after a type check — no explicit casting needed.

**7. Coroutines**
Supports asynchronous programming (like background tasks) in a simple way.

**8. Interoperability**
100% interoperable with Java — you can use Java libraries in Kotlin.

**9. Data Classes**
Special classes to hold data — auto-generates useful methods.

**10. Companion Object**
Provides static-like behavior inside a class.

---

## Q. Write Kotlin Code for Function Overloading — Area of Circle, Rectangle, Triangle

```kotlin
fun area(radius: Double): Double {
    return Math.PI * radius * radius
}

fun area(length: Double, breadth: Double): Double {
    return length * breadth
}

fun area(base: Double, height: Double, isTriangle: Boolean): Double {
    return 0.5 * base * height
}

fun main() {
    println("Area of Circle: ${area(7.0)}")
    println("Area of Rectangle: ${area(5.0, 4.0)}")
    println("Area of Triangle: ${area(6.0, 3.0, true)}")
}
```

---

## Q. Write Kotlin Code to Print Armstrong Numbers Between 100 to 500

```kotlin
fun main() {
    println("Armstrong numbers between 100 and 500:")
    for (num in 100..500) {
        var sum = 0
        var temp = num
        while (temp > 0) {
            val digit = temp % 10
            sum += digit * digit * digit
            temp /= 10
        }
        if (sum == num) {
            print("$num  ")
        }
    }
}
// Output: 153  370  371  407
```

---

## Q. What is Inheritance? Explain with Example (Program)

**Inheritance** allows a class (child/subclass) to acquire the properties and methods of another class (parent/superclass). It promotes code reusability.

In Kotlin, a class must be declared `open` to allow inheritance.

**Example:**
```kotlin
open class Animal(val name: String) {
    fun eat() {
        println("$name is eating")
    }
}

class Dog(name: String) : Animal(name) {
    fun bark() {
        println("$name is barking")
    }
}

fun main() {
    val dog = Dog("Bruno")
    dog.eat()   // Inherited from Animal
    dog.bark()  // Dog's own method
}
// Output:
// Bruno is eating
// Bruno is barking
```

**Types:** Single, Multi-level, Hierarchical (Multiple and Hybrid not directly supported in Kotlin classes, but possible via interfaces)

---

## Q. Explain Object-Oriented Concepts Supported in Kotlin

**1. Class and Object**
```kotlin
class Car(val brand: String)
val c = Car("Toyota")
```

**2. Encapsulation**
Hiding data using `private`, `protected`, `public` modifiers.

**3. Inheritance**
Child class gets properties of parent using `:` symbol. Parent must be `open`.

**4. Polymorphism**
Same method behaves differently. Achieved through method overriding and overloading.
```kotlin
open class Shape { open fun draw() = println("Drawing shape") }
class Circle : Shape() { override fun draw() = println("Drawing circle") }
```

**5. Abstraction**
Abstract classes and interfaces hide implementation details.
```kotlin
abstract class Vehicle { abstract fun fuel() }
class Car : Vehicle() { override fun fuel() = println("Uses Petrol") }
```

**6. Interface**
Defines a contract that classes must follow.
```kotlin
interface Flyable { fun fly() }
class Bird : Flyable { override fun fly() = println("Bird flying") }
```

---

## Q. Demonstrate Higher Order Function in Kotlin

A **higher-order function** is a function that takes another function as a parameter or returns a function.

**Example 1 — Function as parameter:**
```kotlin
fun operate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

fun main() {
    val sum = operate(5, 3) { x, y -> x + y }
    val product = operate(5, 3) { x, y -> x * y }
    println("Sum: $sum")        // Sum: 8
    println("Product: $product") // Product: 15
}
```

**Example 2 — Function returning a function:**
```kotlin
fun multiplier(factor: Int): (Int) -> Int {
    return { number -> number * factor }
}

fun main() {
    val triple = multiplier(3)
    println(triple(5))  // Output: 15
}
```

---

## Q. Demonstrate Single Inheritance in Kotlin

```kotlin
open class Person(val name: String, val age: Int) {
    fun introduce() {
        println("Hi, I am $name and I am $age years old.")
    }
}

class Student(name: String, age: Int, val rollNo: Int) : Person(name, age) {
    fun displayRoll() {
        println("Roll Number: $rollNo")
    }
}

fun main() {
    val s = Student("Amit", 20, 101)
    s.introduce()     // Inherited method
    s.displayRoll()   // Student's own method
}
// Output:
// Hi, I am Amit and I am 20 years old.
// Roll Number: 101
```

---
---

# UNIT 2 — Android Basics

---

## Q. Describe Layered Architecture of Android with Diagram

Android architecture has **5 layers** (from bottom to top):

```
 ┌─────────────────────────────────────────┐
 │          APPLICATIONS LAYER             │  ← User Apps (WhatsApp, Camera, etc.)
 ├─────────────────────────────────────────┤
 │       APPLICATION FRAMEWORK             │  ← Activity Manager, Content Provider,
 │                                         │    Window Manager, Notification Manager
 ├─────────────────────────────────────────┤
 │   ANDROID RUNTIME + NATIVE LIBRARIES    │  ← ART (Android Runtime), SQLite,
 │                                         │    WebKit, OpenGL, Media Framework
 ├─────────────────────────────────────────┤
 │        HARDWARE ABSTRACTION LAYER       │  ← HAL (connects hardware & software)
 ├─────────────────────────────────────────┤
 │              LINUX KERNEL               │  ← Drivers, Memory Mgmt, Power Mgmt
 └─────────────────────────────────────────┘
```

**Layer Explanation:**

1. **Linux Kernel** — Core of Android. Handles memory, processes, security, hardware drivers.
2. **HAL (Hardware Abstraction Layer)** — Interface between hardware and higher software layers.
3. **Native Libraries + Android Runtime** — SQLite (database), WebKit (browser), ART (runs apps).
4. **Application Framework** — Provides APIs to developers: Activity Manager, Content Providers, Views.
5. **Applications** — Top layer where user-installed apps run (Contacts, Camera, etc.).

---

## Q. Create Android App to Enter 2 Numbers and Display Result on Button Click

**activity_main.xml:**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <EditText android:id="@+id/etNum1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter first number"
        android:inputType="number"/>

    <EditText android:id="@+id/etNum2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter second number"
        android:inputType="number"/>

    <Button android:id="@+id/btnAdd"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Add"/>

    <TextView android:id="@+id/tvResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="20sp"/>
</LinearLayout>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etNum1 = findViewById<EditText>(R.id.etNum1)
        val etNum2 = findViewById<EditText>(R.id.etNum2)
        val btnAdd = findViewById<Button>(R.id.btnAdd)
        val tvResult = findViewById<TextView>(R.id.tvResult)

        btnAdd.setOnClickListener {
            val num1 = etNum1.text.toString().toInt()
            val num2 = etNum2.text.toString().toInt()
            tvResult.text = "Result: ${num1 + num2}"
        }
    }
}
```

---

## Q. Describe Android App File Structure in Android Studio

```
MyApp/
├── app/
│   ├── manifests/
│   │   └── AndroidManifest.xml       ← App name, permissions, activities declared here
│   ├── java/
│   │   └── com.example.myapp/
│   │       └── MainActivity.kt       ← Kotlin source code files
│   └── res/
│       ├── layout/
│       │   └── activity_main.xml     ← UI layout files
│       ├── values/
│       │   ├── strings.xml           ← String resources
│       │   └── colors.xml            ← Color definitions
│       ├── drawable/                 ← Images and icons
│       └── mipmap/                   ← App launcher icons
├── Gradle Scripts/
│   ├── build.gradle (Project)        ← Project-level build settings
│   └── build.gradle (Module: app)    ← App-level dependencies
```

**Important Files:**
- `AndroidManifest.xml` — Declares activities, permissions, app name.
- `MainActivity.kt` — Main logic file.
- `activity_main.xml` — Main screen layout.
- `build.gradle` — Manages dependencies (like Firebase, RecyclerView).

---

## Q. Explain Activity Life Cycle with Callback Functions

An **Activity** goes through various states during its lifetime. Android provides callback methods for each state.

```
    ┌──────────────┐
    │   onCreate() │ ← Activity is created, setContentView() called here
    └──────┬───────┘
           ↓
    ┌──────────────┐
    │   onStart()  │ ← Activity becomes visible
    └──────┬───────┘
           ↓
    ┌──────────────┐
    │  onResume()  │ ← Activity is in foreground, user can interact
    └──────┬───────┘
           ↓ (user presses back or another app opens)
    ┌──────────────┐
    │  onPause()   │ ← Partially visible, save data here
    └──────┬───────┘
           ↓
    ┌──────────────┐
    │   onStop()   │ ← No longer visible
    └──────┬───────┘
           ↓
    ┌──────────────┐
    │ onDestroy()  │ ← Activity is destroyed
    └──────────────┘
```

| Method | When Called |
|---|---|
| `onCreate()` | When Activity is first created |
| `onStart()` | When Activity becomes visible |
| `onResume()` | When Activity starts interacting with user |
| `onPause()` | When another Activity comes to foreground |
| `onStop()` | When Activity is no longer visible |
| `onRestart()` | When Activity is coming back from stopped state |
| `onDestroy()` | Before Activity is destroyed |

---

## Q. Write Android Program to Change Background Color Using Radio Button

**activity_main.xml:**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/mainLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <RadioGroup android:id="@+id/radioGroup"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <RadioButton android:id="@+id/rbRed"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Red"/>

        <RadioButton android:id="@+id/rbGreen"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Green"/>

        <RadioButton android:id="@+id/rbBlue"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Blue"/>
    </RadioGroup>
</LinearLayout>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val layout = findViewById<LinearLayout>(R.id.mainLayout)
        val radioGroup = findViewById<RadioGroup>(R.id.radioGroup)

        radioGroup.setOnCheckedChangeListener { _, checkedId ->
            when (checkedId) {
                R.id.rbRed   -> layout.setBackgroundColor(Color.RED)
                R.id.rbGreen -> layout.setBackgroundColor(Color.GREEN)
                R.id.rbBlue  -> layout.setBackgroundColor(Color.BLUE)
            }
        }
    }
}
```

---
---

# UNIT 3 — Fragments & Architecture

---

## Q. Explain MVC, MVP, and MVVM App Architecture

**1. MVC (Model-View-Controller)**
- **Model** — Data and business logic
- **View** — UI (XML layout)
- **Controller** — Activity/Fragment (handles user input)
- Drawback: Controller becomes too large and complex.

**2. MVP (Model-View-Presenter)**
- **Model** — Data layer
- **View** — UI (Activity/Fragment)
- **Presenter** — Middle layer between Model and View (no Android dependencies)
- Advantage: Easier to test than MVC.

**3. MVVM (Model-View-ViewModel)** ← Recommended by Google
- **Model** — Data (Repository, Database, API)
- **View** — Activity/Fragment (observes ViewModel)
- **ViewModel** — Holds and manages UI-related data; survives screen rotation.
- Uses **LiveData** and **Data Binding**.

| Feature | MVC | MVP | MVVM |
|---|---|---|---|
| Coupling | Tight | Moderate | Loose |
| Testability | Low | Medium | High |
| Recommended | No | Sometimes | Yes (Google) |

---

## Q. What is Fragment? Describe Fragment Life Cycle.

**Fragment** is a reusable UI component that represents a portion of the user interface in an Activity. Multiple fragments can be combined in one Activity to build a multi-pane UI.

**Fragment Lifecycle Methods:**

```
onAttach()       ← Fragment attached to Activity
    ↓
onCreate()       ← Fragment created (no UI yet)
    ↓
onCreateView()   ← Fragment creates its layout (UI is inflated here)
    ↓
onViewCreated()  ← View is ready, initialize views here
    ↓
onStart()        ← Fragment becomes visible
    ↓
onResume()       ← Fragment is active (user can interact)
    ↓
onPause()        ← Fragment partially hidden
    ↓
onStop()         ← Fragment not visible
    ↓
onDestroyView()  ← Fragment's view destroyed
    ↓
onDestroy()      ← Fragment destroyed
    ↓
onDetach()       ← Fragment detached from Activity
```

---

## Q. Create Android App with 3 Fragments (Login, Register, Home)

**LoginFragment.kt:**
```kotlin
class LoginFragment : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, 
                               savedInstanceState: Bundle?): View? {
        val view = inflater.inflate(R.layout.fragment_login, container, false)
        
        view.findViewById<Button>(R.id.btnLogin).setOnClickListener {
            requireActivity().supportFragmentManager.beginTransaction()
                .replace(R.id.fragmentContainer, HomeFragment())
                .commit()
        }
        
        view.findViewById<Button>(R.id.btnRegister).setOnClickListener {
            requireActivity().supportFragmentManager.beginTransaction()
                .replace(R.id.fragmentContainer, RegisterFragment())
                .addToBackStack(null)
                .commit()
        }
        return view
    }
}
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        supportFragmentManager.beginTransaction()
            .replace(R.id.fragmentContainer, LoginFragment())
            .commit()
    }
}
```

**activity_main.xml:**
```xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/fragmentContainer"
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```

---

## Q. Write Android Program for Registration Activity with Validation

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etName   = findViewById<EditText>(R.id.etName)
        val etEmail  = findViewById<EditText>(R.id.etEmail)
        val etMobile = findViewById<EditText>(R.id.etMobile)
        val btnSubmit = findViewById<Button>(R.id.btnSubmit)

        btnSubmit.setOnClickListener {
            val name   = etName.text.toString().trim()
            val email  = etEmail.text.toString().trim()
            val mobile = etMobile.text.toString().trim()

            if (name.isEmpty()) {
                etName.error = "Name is required"
            } else if (email.isEmpty() || !android.util.Patterns.EMAIL_ADDRESS.matcher(email).matches()) {
                etEmail.error = "Enter valid email"
            } else if (mobile.isEmpty() || mobile.length != 10) {
                etMobile.error = "Enter valid 10-digit mobile number"
            } else {
                Toast.makeText(this, "Registration Successful!", Toast.LENGTH_SHORT).show()
            }
        }
    }
}
```

---
---

# UNIT 4 — Storage, Menus, and Database

---

## Q. Describe Different Types of Menu in Android. Steps to Create Option Menu.

**Types of Menus:**

**1. Options Menu** — Appears in the App Bar (top right corner with 3-dot icon). Most common menu.

**2. Context Menu** — Appears when user long-presses on a View element.

**3. Popup Menu** — A floating menu attached to a View. Appears when a specific button is clicked.

---

**Steps to Create Options Menu:**

**Step 1:** Create a menu XML file in `res/menu/menu_main.xml`:
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/action_settings"
          android:title="Settings"
          android:orderInCategory="100"/>
    <item android:id="@+id/action_about"
          android:title="About"/>
</menu>
```

**Step 2:** Override `onCreateOptionsMenu()` in Activity:
```kotlin
override fun onCreateOptionsMenu(menu: Menu?): Boolean {
    menuInflater.inflate(R.menu.menu_main, menu)
    return true
}
```

**Step 3:** Handle menu item clicks with `onOptionsItemSelected()`:
```kotlin
override fun onOptionsItemSelected(item: MenuItem): Boolean {
    return when (item.itemId) {
        R.id.action_settings -> {
            Toast.makeText(this, "Settings Clicked", Toast.LENGTH_SHORT).show()
            true
        }
        R.id.action_about -> {
            Toast.makeText(this, "About Clicked", Toast.LENGTH_SHORT).show()
            true
        }
        else -> super.onOptionsItemSelected(item)
    }
}
```

---

## Q. List the Steps to Connect Android App with SQLite Database

**Steps:**

1. **Create a Helper class** that extends `SQLiteOpenHelper`.
2. **Override `onCreate()`** — runs when DB is created for first time. Write `CREATE TABLE` here.
3. **Override `onUpgrade()`** — runs when DB version changes. Write `DROP TABLE` and recreate.
4. **Write CRUD methods** — insert, read, update, delete data.
5. **Create an instance** of the helper class in your Activity.
6. **Call methods** to perform database operations.

---

## Q. Explain Shared Preference in Android with Example

**SharedPreferences** is used to store small amounts of key-value data (like settings, login status, username) in a persistent way. Data is stored even after the app is closed.

**Storing Data:**
```kotlin
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val editor = sharedPref.edit()
editor.putString("username", "Ravi")
editor.putInt("age", 21)
editor.putBoolean("isLoggedIn", true)
editor.apply()  // or editor.commit()
```

**Retrieving Data:**
```kotlin
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val name = sharedPref.getString("username", "Guest")  // "Guest" is default
val age = sharedPref.getInt("age", 0)
val loggedIn = sharedPref.getBoolean("isLoggedIn", false)

Toast.makeText(this, "Welcome $name", Toast.LENGTH_SHORT).show()
```

**Use Cases:** Remember login state, save dark/light mode preference, save language selection.

---

## Q. Write Android Program to Store Employee Data in SQLite Database

**DatabaseHelper.kt:**
```kotlin
class DatabaseHelper(context: Context) : SQLiteOpenHelper(context, "EmployeeDB", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        val createTable = """
            CREATE TABLE Employee (
                empno INTEGER PRIMARY KEY,
                name TEXT,
                department TEXT,
                designation TEXT
            )
        """.trimIndent()
        db.execSQL(createTable)
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        db.execSQL("DROP TABLE IF EXISTS Employee")
        onCreate(db)
    }

    fun insertEmployee(empno: Int, name: String, dept: String, desig: String): Long {
        val db = writableDatabase
        val values = ContentValues().apply {
            put("empno", empno)
            put("name", name)
            put("department", dept)
            put("designation", desig)
        }
        return db.insert("Employee", null, values)
    }

    fun getAllEmployees(): Cursor {
        return readableDatabase.rawQuery("SELECT * FROM Employee", null)
    }
}
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val db = DatabaseHelper(this)
        val result = db.insertEmployee(101, "Ramesh", "IT", "Developer")

        if (result > 0) {
            Toast.makeText(this, "Employee saved!", Toast.LENGTH_SHORT).show()
        }
    }
}
```

---

## Q. Explain Storing and Retrieving Data in SharedPreferences in Another Activity

**Activity 1 — Save data:**
```kotlin
// In FirstActivity.kt
val pref = getSharedPreferences("AppData", Context.MODE_PRIVATE)
pref.edit().putString("city", "Bhubaneswar").apply()

// Navigate to second activity
startActivity(Intent(this, SecondActivity::class.java))
```

**Activity 2 — Retrieve data:**
```kotlin
// In SecondActivity.kt
val pref = getSharedPreferences("AppData", Context.MODE_PRIVATE)
val city = pref.getString("city", "Unknown")
Toast.makeText(this, "City: $city", Toast.LENGTH_SHORT).show()
```

**Key Points:**
- Use the **same preference file name** in both activities (`"AppData"`).
- `MODE_PRIVATE` means only your app can access this data.
- `apply()` saves asynchronously; `commit()` saves synchronously and returns boolean.

---

## Q. Design Android App to Store User Contacts Using SQLite

**DatabaseHelper.kt:**
```kotlin
class ContactDB(context: Context) : SQLiteOpenHelper(context, "ContactDB", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        db.execSQL("""
            CREATE TABLE contacts (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                name TEXT,
                phone TEXT,
                email TEXT
            )
        """)
    }

    override fun onUpgrade(db: SQLiteDatabase, old: Int, new: Int) {
        db.execSQL("DROP TABLE IF EXISTS contacts")
        onCreate(db)
    }

    fun addContact(name: String, phone: String, email: String): Boolean {
        val values = ContentValues().apply {
            put("name", name)
            put("phone", phone)
            put("email", email)
        }
        return writableDatabase.insert("contacts", null, values) > 0
    }
}
```

---

## Q. Create Android App Using All Types of Menus with Submenus

**res/menu/menu_main.xml:**
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/file"
          android:title="File">
        <menu>
            <item android:id="@+id/new_file" android:title="New"/>
            <item android:id="@+id/open"     android:title="Open"/>
            <item android:id="@+id/save"     android:title="Save"/>
        </menu>
    </item>
    <item android:id="@+id/edit"  android:title="Edit"/>
    <item android:id="@+id/help"  android:title="Help"/>
</menu>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Context Menu
        val textView = findViewById<TextView>(R.id.tvContext)
        registerForContextMenu(textView)

        // Popup Menu
        val btnPopup = findViewById<Button>(R.id.btnPopup)
        btnPopup.setOnClickListener {
            val popup = PopupMenu(this, btnPopup)
            popup.menuInflater.inflate(R.menu.menu_main, popup.menu)
            popup.setOnMenuItemClickListener { item ->
                Toast.makeText(this, "Clicked: ${item.title}", Toast.LENGTH_SHORT).show()
                true
            }
            popup.show()
        }
    }

    // Options Menu
    override fun onCreateOptionsMenu(menu: Menu?): Boolean {
        menuInflater.inflate(R.menu.menu_main, menu)
        return true
    }

    override fun onOptionsItemSelected(item: MenuItem): Boolean {
        Toast.makeText(this, "Selected: ${item.title}", Toast.LENGTH_SHORT).show()
        return true
    }

    // Context Menu
    override fun onCreateContextMenu(menu: ContextMenu?, v: View?, menuInfo: ContextMenu.ContextMenuInfo?) {
        menuInflater.inflate(R.menu.menu_main, menu)
    }

    override fun onContextItemSelected(item: MenuItem): Boolean {
        Toast.makeText(this, "Context: ${item.title}", Toast.LENGTH_SHORT).show()
        return true
    }
}
```

---

## Q. Explain Different Types of Intent and Create App with Button for Each Intent

**Types of Intent:**

**1. Explicit Intent** — Starts a specific component (Activity) by class name.

**2. Implicit Intent** — Requests an action; system finds the best component (opens browser, camera, etc.).

**3. Sticky Intent** — Broadcast intent that stays in memory.

**4. Pending Intent** — Intent to be triggered in future (used in notifications, alarms).

---

**MainActivity.kt with buttons for each intent:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // 1. Explicit Intent
        findViewById<Button>(R.id.btnExplicit).setOnClickListener {
            val intent = Intent(this, SecondActivity::class.java)
            startActivity(intent)
        }

        // 2. Implicit Intent — Open Website
        findViewById<Button>(R.id.btnBrowser).setOnClickListener {
            val intent = Intent(Intent.ACTION_VIEW, Uri.parse("https://www.google.com"))
            startActivity(intent)
        }

        // 3. Implicit Intent — Call Phone
        findViewById<Button>(R.id.btnCall).setOnClickListener {
            val intent = Intent(Intent.ACTION_DIAL, Uri.parse("tel:9876543210"))
            startActivity(intent)
        }

        // 4. Implicit Intent — Send Email
        findViewById<Button>(R.id.btnEmail).setOnClickListener {
            val intent = Intent(Intent.ACTION_SEND)
            intent.type = "text/plain"
            intent.putExtra(Intent.EXTRA_EMAIL, arrayOf("test@gmail.com"))
            intent.putExtra(Intent.EXTRA_SUBJECT, "Hello")
            startActivity(intent)
        }
    }
}
```

---
---

# UNIT 5 — Firebase

---

## Q. Build Android App to Store User Feedback in Firebase Realtime Database

**Steps:**
1. Go to Firebase Console → Create Project → Add Android App.
2. Download `google-services.json` and place in `app/` folder.
3. Add dependencies in `build.gradle`:
```gradle
implementation 'com.google.firebase:firebase-database:20.3.0'
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    private lateinit var database: DatabaseReference

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        database = FirebaseDatabase.getInstance().getReference("feedback")

        val etFeedback = findViewById<EditText>(R.id.etFeedback)
        val btnSubmit  = findViewById<Button>(R.id.btnSubmit)

        btnSubmit.setOnClickListener {
            val feedback = etFeedback.text.toString().trim()
            if (feedback.isNotEmpty()) {
                val id = database.push().key!!
                database.child(id).setValue(feedback)
                    .addOnSuccessListener {
                        Toast.makeText(this, "Feedback saved!", Toast.LENGTH_SHORT).show()
                    }
                    .addOnFailureListener {
                        Toast.makeText(this, "Error: ${it.message}", Toast.LENGTH_SHORT).show()
                    }
            }
        }
    }
}
```

---

## Q. Design Android App with Multiple SharedPreferences (username, language, notifications)

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val pref = getSharedPreferences("UserSettings", Context.MODE_PRIVATE)

        val etUsername = findViewById<EditText>(R.id.etUsername)
        val spinnerLang = findViewById<Spinner>(R.id.spinnerLang)
        val switchNotif = findViewById<Switch>(R.id.switchNotif)
        val btnSave = findViewById<Button>(R.id.btnSave)
        val tvDisplay = findViewById<TextView>(R.id.tvDisplay)

        // Load existing preferences
        etUsername.setText(pref.getString("username", ""))
        switchNotif.isChecked = pref.getBoolean("notifications", true)

        btnSave.setOnClickListener {
            pref.edit().apply {
                putString("username", etUsername.text.toString())
                putString("language", spinnerLang.selectedItem.toString())
                putBoolean("notifications", switchNotif.isChecked)
                apply()
            }

            tvDisplay.text = """
                Saved!
                Username: ${pref.getString("username", "")}
                Language: ${pref.getString("language", "")}
                Notifications: ${pref.getBoolean("notifications", true)}
            """.trimIndent()
        }
    }
}
```

---

*End of Answer Sheet*

---
> **Tip for Exam:** For 7-mark questions write 4-5 points with short code. For 8-mark questions write detailed explanation with a working code example. Always include comments in code for clarity.
