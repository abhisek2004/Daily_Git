# Android App Development using Kotlin — Complete Exam Answers
### 21BCSOE36011/22BCSOE36011 | B.Tech 6th Semester | GIET University

---

# PART – A (Short Answers – 2 Marks Each)

---

## Q1a. Elvis Operator for Null Safety in Kotlin

The **Elvis operator** (`?:`) is used to handle null values safely.

**Syntax:** `val result = value ?: defaultValue`

If `value` is **not null**, it returns `value`. If `value` **is null**, it returns `defaultValue`.

**Example:**
```kotlin
val name: String? = null
val result = name ?: "Unknown"
println(result)  // Output: Unknown
```

---

## Q1b. Difference Between Class and Data Class

| Feature | Class | Data Class |
|---|---|---|
| Declaration | `class Person` | `data class Person` |
| `toString()` | Not auto-generated | Auto-generated |
| `equals()` / `hashCode()` | Not auto-generated | Auto-generated |
| `copy()` function | Not available | Available |
| Purpose | General purpose | Holds data/model objects |

**Example:**
```kotlin
data class Student(val name: String, val age: Int)
val s = Student("Raj", 20)
println(s)  // Output: Student(name=Raj, age=20)
```

---

## Q1c. Fragment in Android App

A **Fragment** is a reusable part of the UI inside an Activity. It has its own layout and lifecycle.

- Fragments are used to build flexible and responsive UIs.
- Multiple fragments can be shown in one Activity.
- It has lifecycle methods like `onCreate()`, `onCreateView()`, `onPause()`.

**Example use:** A tablet showing a list on the left and details on the right — each is a Fragment.

---

## Q1d. Need of RecyclerView in Kotlin

**RecyclerView** is used to display a large list of items efficiently.

- It **recycles** (reuses) views that scroll off screen — saves memory.
- Better performance than the older `ListView`.
- Uses `RecyclerView.Adapter` and `ViewHolder` pattern.
- Supports vertical, horizontal, and grid layouts.

**Use case:** Displaying contacts list, products list, chat messages, etc.

---

## Q1e. Real-Time Database (Firebase)

**Firebase Realtime Database** is a cloud-hosted NoSQL database provided by Google.

- Data is stored as **JSON** and synced in real-time across all clients.
- When data changes on the server, all connected apps get updated instantly.
- Works even **offline** — syncs when connection is restored.
- Used for chat apps, live score updates, collaborative apps.

---

# PART – B (Long Answers)

---

## Q2a. Key Features of Kotlin (8 Marks)

Kotlin is a modern, statically-typed programming language developed by JetBrains. It runs on the JVM and is fully interoperable with Java.

**1. Concise Syntax**
Less boilerplate code compared to Java. You can write more in fewer lines.

**2. Null Safety**
Kotlin prevents NullPointerExceptions at compile time using nullable (`?`) and non-nullable types.
```kotlin
var name: String? = null  // nullable
var name2: String = "Kotlin"  // non-nullable
```

**3. Data Classes**
Automatically generates `equals()`, `hashCode()`, `toString()`, and `copy()`.

**4. Extension Functions**
Add new functions to existing classes without modifying them.
```kotlin
fun String.greet() = "Hello, $this"
println("Raj".greet())  // Hello, Raj
```

**5. Smart Casts**
Automatic type casting after type check.
```kotlin
if (obj is String) println(obj.length)  // No explicit cast needed
```

**6. Coroutines**
Simplified asynchronous programming — no need for callbacks or threads manually.

**7. Interoperability with Java**
Kotlin code can call Java code and vice versa easily.

**8. Functional Programming Support**
Supports lambda expressions, higher-order functions, and collection operations like `map`, `filter`, `reduce`.

---

## Q2b. Single Inheritance in Kotlin (7 Marks)

In Kotlin, a class can **inherit** from one parent class only (Single Inheritance). The parent class must be marked `open` to allow inheritance.

**Syntax:**
```kotlin
open class Animal {
    fun eat() {
        println("Animal is eating")
    }
}

class Dog : Animal() {
    fun bark() {
        println("Dog is barking")
    }
}

fun main() {
    val dog = Dog()
    dog.eat()   // inherited method
    dog.bark()  // own method
}
```

**Output:**
```
Animal is eating
Dog is barking
```

The `Dog` class inherits the `eat()` function from `Animal` class. This is single inheritance — `Dog` has only one parent.

---

## Q2c. Object-Oriented Concepts in Kotlin (8 Marks)

**1. Class and Object**
A class is a blueprint; an object is an instance of a class.
```kotlin
class Car(val brand: String) {
    fun drive() = println("$brand is driving")
}
val c = Car("Toyota")
c.drive()
```

**2. Inheritance**
Child class inherits properties and methods of parent class. Parent must be `open`.

**3. Encapsulation**
Hiding internal data using `private`, `protected`, `public` access modifiers.

**4. Polymorphism**
Same method name behaves differently. Done using `override`.
```kotlin
open class Shape { open fun area() = println("Shape area") }
class Circle : Shape() { override fun area() = println("Circle area") }
```

**5. Abstraction**
Hiding implementation using `abstract` classes or interfaces.
```kotlin
abstract class Vehicle {
    abstract fun fuelType()
}
```

**6. Interface**
Defines a contract. A class can implement multiple interfaces.
```kotlin
interface Flyable { fun fly() }
class Bird : Flyable { override fun fly() = println("Bird flies") }
```

---

## Q2d. Higher Order Functions in Kotlin (7 Marks)

A **Higher-Order Function** is a function that takes another function as a parameter or returns a function.

**Example 1 — Function as Parameter:**
```kotlin
fun operate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

fun main() {
    val sum = operate(5, 3) { x, y -> x + y }
    val product = operate(5, 3) { x, y -> x * y }
    println("Sum = $sum")        // Sum = 8
    println("Product = $product") // Product = 15
}
```

**Example 2 — Built-in Higher Order Functions:**
```kotlin
val numbers = listOf(1, 2, 3, 4, 5)
val evens = numbers.filter { it % 2 == 0 }
println(evens)  // [2, 4]
```

Higher-order functions make code clean, reusable, and functional in style.

---

## Q3a. Android Architecture (8 Marks)

Android architecture is arranged in **5 layers** from top to bottom:

```
┌───────────────────────────────────┐
│         APPLICATIONS              │  ← Phone, Camera, Maps, etc.
├───────────────────────────────────┤
│      APPLICATION FRAMEWORK        │  ← Activity Manager, Content Providers
├───────────────────────────────────┤
│    ANDROID RUNTIME + LIBRARIES    │  ← ART, SQLite, WebKit, OpenGL
├───────────────────────────────────┤
│         LINUX KERNEL              │  ← Drivers, Memory, Security
└───────────────────────────────────┘
```

**Layer Details:**

**1. Linux Kernel**
- Base of Android
- Manages hardware: Camera, WiFi, Bluetooth, Memory, Power

**2. Hardware Abstraction Layer (HAL)**
- Provides interface between hardware and higher layers

**3. Android Runtime (ART)**
- Executes app code
- Converts Kotlin/Java code to machine code using AOT (Ahead of Time) compilation

**4. Native Libraries**
- SQLite (database), WebKit (browser engine), OpenGL (graphics), SSL (security)

**5. Application Framework**
- Activity Manager, Content Providers, Location Manager, Notification Manager

**6. Applications Layer**
- Actual apps like Phone, Camera, Settings, and user-installed apps

---

## Q3b. Android App — Student Details Form (7 Marks)

**activity_main.xml (Layout):**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText android:id="@+id/etName"
        android:hint="Enter Name"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <RadioGroup android:id="@+id/rgGender"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">
        <RadioButton android:id="@+id/rbMale" android:text="Male"/>
        <RadioButton android:id="@+id/rbFemale" android:text="Female"/>
    </RadioGroup>

    <Button android:id="@+id/btnSubmit"
        android:text="Submit"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <TextView android:id="@+id/tvResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="16sp"/>
</LinearLayout>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etName = findViewById<EditText>(R.id.etName)
        val rgGender = findViewById<RadioGroup>(R.id.rgGender)
        val btnSubmit = findViewById<Button>(R.id.btnSubmit)
        val tvResult = findViewById<TextView>(R.id.tvResult)

        btnSubmit.setOnClickListener {
            val name = etName.text.toString()
            val selectedId = rgGender.checkedRadioButtonId
            val gender = findViewById<RadioButton>(selectedId).text.toString()
            tvResult.text = "Name: $name\nGender: $gender"
        }
    }
}
```

---

## Q3c. Activity Life Cycle (8 Marks)

The **Activity Lifecycle** defines the states an activity goes through from creation to destruction.

```
         onCreate()
             ↓
         onStart()
             ↓
         onResume()  ← Activity is RUNNING here
             ↓
         onPause()   ← Another activity comes in front
             ↓
         onStop()    ← Activity is no longer visible
             ↓
         onDestroy() ← Activity is destroyed
```

**Callback Functions:**

| Method | When Called |
|---|---|
| `onCreate()` | Activity is first created. Initialize UI here. |
| `onStart()` | Activity becomes visible to user. |
| `onResume()` | Activity starts interacting with user. |
| `onPause()` | Another activity is coming to front. Save data here. |
| `onStop()` | Activity is no longer visible. |
| `onRestart()` | Activity is coming back from stopped state. |
| `onDestroy()` | Activity is being destroyed completely. |

---

## Q3d. App to Select Favourite Programming Language (7 Marks)

**activity_main.xml:**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" android:padding="16dp">

    <Spinner android:id="@+id/spinnerLang"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <Button android:id="@+id/btnSelect"
        android:text="Select"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <TextView android:id="@+id/tvResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="18sp"/>
</LinearLayout>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val languages = listOf("Kotlin", "Java", "Python", "C++", "JavaScript")
        val spinner = findViewById<Spinner>(R.id.spinnerLang)
        val adapter = ArrayAdapter(this, android.R.layout.simple_spinner_item, languages)
        spinner.adapter = adapter

        val btn = findViewById<Button>(R.id.btnSelect)
        val tv = findViewById<TextView>(R.id.tvResult)

        btn.setOnClickListener {
            tv.text = "You selected: ${spinner.selectedItem}"
        }
    }
}
```

---

## Q4a. Android App — All Types of Menus with Submenus (15 Marks)

Android supports 3 types of menus: **Options Menu**, **Context Menu**, and **Popup Menu**.

**res/menu/main_menu.xml:**
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/file" android:title="File">
        <menu>
            <item android:id="@+id/new_file" android:title="New"/>
            <item android:id="@+id/open_file" android:title="Open"/>
        </menu>
    </item>
    <item android:id="@+id/edit" android:title="Edit"/>
    <item android:id="@+id/help" android:title="Help"/>
</menu>
```

**res/menu/context_menu.xml:**
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/copy" android:title="Copy"/>
    <item android:id="@+id/paste" android:title="Paste"/>
    <item android:id="@+id/delete" android:title="Delete"/>
</menu>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val btnPopup = findViewById<Button>(R.id.btnPopup)
        val tvContext = findViewById<TextView>(R.id.tvContext)
        registerForContextMenu(tvContext)

        // Popup Menu
        btnPopup.setOnClickListener {
            val popup = PopupMenu(this, btnPopup)
            popup.menuInflater.inflate(R.menu.context_menu, popup.menu)
            popup.setOnMenuItemClickListener {
                Toast.makeText(this, "Popup: ${it.title}", Toast.LENGTH_SHORT).show()
                true
            }
            popup.show()
        }
    }

    // Options Menu
    override fun onCreateOptionsMenu(menu: Menu): Boolean {
        menuInflater.inflate(R.menu.main_menu, menu)
        return true
    }

    override fun onOptionsItemSelected(item: MenuItem): Boolean {
        Toast.makeText(this, "Selected: ${item.title}", Toast.LENGTH_SHORT).show()
        return true
    }

    // Context Menu (Long Press)
    override fun onCreateContextMenu(menu: ContextMenu, v: View, menuInfo: ContextMenu.ContextMenuInfo?) {
        super.onCreateContextMenu(menu, v, menuInfo)
        menuInflater.inflate(R.menu.context_menu, menu)
        menu.setHeaderTitle("Context Menu")
    }

    override fun onContextItemSelected(item: MenuItem): Boolean {
        Toast.makeText(this, "Context: ${item.title}", Toast.LENGTH_SHORT).show()
        return true
    }
}
```

**Types Summary:**
- **Options Menu** — Appears in toolbar (top-right 3-dot menu)
- **Context Menu** — Appears on long press of a View
- **Popup Menu** — Appears anchored to a specific View on button click

---

## Q4b. Types of Intents in Android (15 Marks)

An **Intent** is a messaging object used to request actions from other components.

### Types of Intents:

**1. Explicit Intent**
Directly specifies the target Activity by class name.
```kotlin
val intent = Intent(this, SecondActivity::class.java)
intent.putExtra("message", "Hello from MainActivity")
startActivity(intent)
```

**2. Implicit Intent**
Does not specify target — Android finds the best app to handle it.
```kotlin
// Open a URL
val intent = Intent(Intent.ACTION_VIEW, Uri.parse("https://www.google.com"))
startActivity(intent)

// Make a call
val callIntent = Intent(Intent.ACTION_DIAL, Uri.parse("tel:9876543210"))
startActivity(callIntent)
```

**Complete App with All Intents:**

**activity_main.xml:**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:orientation="vertical" android:padding="16dp">
    <Button android:id="@+id/btnExplicit" android:text="Explicit Intent" .../>
    <Button android:id="@+id/btnBrowser" android:text="Open Browser" .../>
    <Button android:id="@+id/btnCall" android:text="Make Call" .../>
    <Button android:id="@+id/btnShare" android:text="Share Text" .../>
</LinearLayout>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Explicit Intent
        findViewById<Button>(R.id.btnExplicit).setOnClickListener {
            startActivity(Intent(this, SecondActivity::class.java))
        }

        // Implicit Intent - Open URL
        findViewById<Button>(R.id.btnBrowser).setOnClickListener {
            startActivity(Intent(Intent.ACTION_VIEW, Uri.parse("https://www.google.com")))
        }

        // Implicit Intent - Call
        findViewById<Button>(R.id.btnCall).setOnClickListener {
            startActivity(Intent(Intent.ACTION_DIAL, Uri.parse("tel:1234567890")))
        }

        // Implicit Intent - Share
        findViewById<Button>(R.id.btnShare).setOnClickListener {
            val shareIntent = Intent(Intent.ACTION_SEND)
            shareIntent.type = "text/plain"
            shareIntent.putExtra(Intent.EXTRA_TEXT, "Hello from my app!")
            startActivity(Intent.createChooser(shareIntent, "Share via"))
        }
    }
}
```

---

## Q5a. SQLite — Store Contact Information (8 Marks)

**DatabaseHelper.kt:**
```kotlin
class DatabaseHelper(context: Context) : SQLiteOpenHelper(context, "ContactDB", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        db.execSQL(
            "CREATE TABLE contacts (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, phone TEXT, email TEXT)"
        )
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        db.execSQL("DROP TABLE IF EXISTS contacts")
        onCreate(db)
    }

    fun insertContact(name: String, phone: String, email: String) {
        val db = writableDatabase
        val values = ContentValues()
        values.put("name", name)
        values.put("phone", phone)
        values.put("email", email)
        db.insert("contacts", null, values)
        db.close()
    }
}
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val dbHelper = DatabaseHelper(this)
        val etName = findViewById<EditText>(R.id.etName)
        val etPhone = findViewById<EditText>(R.id.etPhone)
        val etEmail = findViewById<EditText>(R.id.etEmail)
        val btnSave = findViewById<Button>(R.id.btnSave)

        btnSave.setOnClickListener {
            dbHelper.insertContact(
                etName.text.toString(),
                etPhone.text.toString(),
                etEmail.text.toString()
            )
            Toast.makeText(this, "Contact Saved!", Toast.LENGTH_SHORT).show()
        }
    }
}
```

---

## Q5b. SharedPreferences — Multiple User Preferences (7 Marks)

**SharedPreferences** stores small key-value data persistently on the device.

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    lateinit var sharedPref: SharedPreferences

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        sharedPref = getSharedPreferences("UserPrefs", Context.MODE_PRIVATE)

        val etUsername = findViewById<EditText>(R.id.etUsername)
        val spinnerLang = findViewById<Spinner>(R.id.spinnerLang)
        val switchNotif = findViewById<Switch>(R.id.switchNotif)
        val btnSave = findViewById<Button>(R.id.btnSave)
        val btnLoad = findViewById<Button>(R.id.btnLoad)
        val tvResult = findViewById<TextView>(R.id.tvResult)

        btnSave.setOnClickListener {
            val editor = sharedPref.edit()
            editor.putString("username", etUsername.text.toString())
            editor.putString("language", spinnerLang.selectedItem.toString())
            editor.putBoolean("notifications", switchNotif.isChecked)
            editor.apply()
            Toast.makeText(this, "Preferences Saved!", Toast.LENGTH_SHORT).show()
        }

        btnLoad.setOnClickListener {
            val username = sharedPref.getString("username", "N/A")
            val language = sharedPref.getString("language", "N/A")
            val notif = sharedPref.getBoolean("notifications", false)
            tvResult.text = "Username: $username\nLanguage: $language\nNotifications: $notif"
        }
    }
}
```

---

## Q5c. Firebase Realtime Database — Store User Feedback (8 Marks)

**Steps to Setup:**
1. Add Firebase to project via Firebase Console
2. Add dependency in `build.gradle`:
```
implementation 'com.google.firebase:firebase-database:20.3.0'
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    lateinit var database: DatabaseReference

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        database = FirebaseDatabase.getInstance().getReference("feedback")

        val etFeedback = findViewById<EditText>(R.id.etFeedback)
        val btnSubmit = findViewById<Button>(R.id.btnSubmit)

        btnSubmit.setOnClickListener {
            val feedback = etFeedback.text.toString()
            val id = database.push().key!!

            database.child(id).setValue(feedback)
                .addOnSuccessListener {
                    Toast.makeText(this, "Feedback Submitted!", Toast.LENGTH_SHORT).show()
                }
                .addOnFailureListener {
                    Toast.makeText(this, "Failed!", Toast.LENGTH_SHORT).show()
                }
        }
    }
}
```

**How it works:**
- `FirebaseDatabase.getInstance()` — connects to Firebase
- `.getReference("feedback")` — points to the "feedback" node
- `.push().key` — generates a unique key
- `.setValue()` — saves data to Firebase in real-time

---

## Q5d. Storing and Retrieving Data in SharedPreferences Across Activities (7 Marks)

**SharedPreferences** allows data to persist even after the app is closed and can be accessed from any Activity.

**Storing Data in Activity 1:**
```kotlin
// In FirstActivity.kt
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val editor = sharedPref.edit()
editor.putString("username", "Rahul")
editor.putInt("age", 22)
editor.apply()  // apply() is async and fast; commit() is synchronous
```

**Retrieving Data in Activity 2:**
```kotlin
// In SecondActivity.kt
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val username = sharedPref.getString("username", "Default")
val age = sharedPref.getInt("age", 0)

textView.text = "Name: $username, Age: $age"
```

**Key Points:**
- Use the **same file name** (`"MyPrefs"`) in both activities
- `MODE_PRIVATE` — only this app can access the file
- Use `editor.apply()` to save asynchronously
- Use `editor.remove("key")` to delete a specific preference
- Use `editor.clear()` to delete all preferences

---

*End of Answers — All questions covered for exam preparation*
*Subject: Android App Development using Kotlin | GIET University*
