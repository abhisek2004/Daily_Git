# Android App Development using Kotlin — Complete Exam Answers
### GIET University | Sub Code: BOECS6040 | May 2024

---

# PART – A (Short Answers)

---

## Q.1(a) Uses of Data Class and Interface

**Data Class:**
- Used to hold/store data (like a model or container).
- Automatically generates `equals()`, `hashCode()`, `toString()`, and `copy()` functions.
- Reduces boilerplate code.
- Example: `data class Student(val name: String, val age: Int)`

**Interface:**
- Used to define a contract (set of functions) that a class must follow.
- Supports multiple inheritance.
- Functions in interface have no body by default (but can have default body in Kotlin).
- Example: `interface Animal { fun sound() }`

---

## Q.1(b) Loop in Kotlin — For Loop

A **for loop** is used to iterate over a range or collection.

**Syntax:**
```kotlin
for (i in 1..5) {
    println(i)
}
```

**Output:**
```
1
2
3
4
5
```

- `1..5` means from 1 to 5 (inclusive).
- You can also loop over a list: `for (item in listOf("A","B","C")) { println(item) }`

---

## Q.1(c) Different Ways to Define a Variable in Kotlin

1. **val** — Immutable (read-only), value cannot be changed.
   ```kotlin
   val name: String = "Kotlin"
   ```

2. **var** — Mutable, value can be changed.
   ```kotlin
   var age: Int = 20
   age = 21  // allowed
   ```

3. **Type Inference** — Kotlin automatically detects the type.
   ```kotlin
   val city = "Delhi"   // String inferred
   var marks = 95       // Int inferred
   ```

4. **Nullable Variable** — Can hold null value using `?`
   ```kotlin
   var phone: String? = null
   ```

---

## Q.1(d) Define Android Virtual Devices (AVD)

- AVD stands for **Android Virtual Device**.
- It is an **emulator** (virtual phone/tablet) that runs on your computer.
- It allows developers to **test Android apps without a real device**.
- Created using **AVD Manager** in Android Studio.
- You can set screen size, Android version, RAM, etc.

---

## Q.1(e) Two Features of Android Operating System

1. **Open Source** — Android is free and open-source (based on Linux kernel). Anyone can use or modify it.
2. **Multi-tasking** — Android supports running multiple apps at the same time in the background.

---

---

# PART – B (Long Answers)

---

## Q.2(a) Types of Constructors in Kotlin

A **constructor** is a special function called when an object is created.

### 1. Primary Constructor
- Defined in the class header.
```kotlin
class Person(val name: String, val age: Int)

fun main() {
    val p = Person("Ram", 25)
    println(p.name)  // Ram
}
```

### 2. Secondary Constructor
- Defined inside the class body using `constructor` keyword.
```kotlin
class Student {
    var name: String
    var marks: Int

    constructor(name: String, marks: Int) {
        this.name = name
        this.marks = marks
    }
}

fun main() {
    val s = Student("Sita", 90)
    println(s.name)   // Sita
    println(s.marks)  // 90
}
```

### 3. Init Block
- Runs after the primary constructor.
```kotlin
class Car(val model: String) {
    init {
        println("Car created: $model")
    }
}

fun main() {
    val c = Car("Swift")  // prints: Car created: Swift
}
```

**Summary:**
- Primary constructor = in class header
- Secondary constructor = using `constructor` keyword inside body
- `init` block = runs automatically during object creation

---

## Q.2(b) When Statement in Kotlin

`when` is like a **switch statement** in Java. It checks a value against multiple conditions.

**Syntax:**
```kotlin
when (variable) {
    value1 -> { // code }
    value2 -> { // code }
    else   -> { // default code }
}
```

**Example:**
```kotlin
fun main() {
    val day = 3

    when (day) {
        1 -> println("Monday")
        2 -> println("Tuesday")
        3 -> println("Wednesday")
        4 -> println("Thursday")
        5 -> println("Friday")
        else -> println("Weekend")
    }
}
```
**Output:** `Wednesday`

**Features of when:**
- Can check ranges: `in 1..5 ->`
- Can check type: `is String ->`
- Can be used as expression (return a value)

```kotlin
val result = when (day) {
    1, 2, 3, 4, 5 -> "Weekday"
    else -> "Weekend"
}
println(result)
```

---

## Q.2(c) Lambda Function and Higher Order Function

### Lambda Function
- A **lambda** is an anonymous function (function without a name).
- Written inside `{ }`.

```kotlin
val add = { a: Int, b: Int -> a + b }

fun main() {
    println(add(3, 5))  // Output: 8
}
```

### Higher Order Function
- A function that **takes another function as parameter** OR **returns a function**.

```kotlin
fun operate(a: Int, b: Int, action: (Int, Int) -> Int): Int {
    return action(a, b)
}

fun main() {
    val result = operate(10, 5, { x, y -> x + y })
    println(result)  // Output: 15

    val result2 = operate(10, 5, { x, y -> x * y })
    println(result2)  // Output: 50
}
```

- `action: (Int, Int) -> Int` means "a function that takes 2 Ints and returns an Int"
- Lambda is passed directly as argument.

---

## Q.2(d) Sealed Classes in Kotlin

- A **sealed class** is a restricted class hierarchy — all subclasses must be defined in the same file.
- Used to represent a **fixed set of types** (like states or results).
- Useful with `when` statement because compiler knows all cases.

**Example:**
```kotlin
sealed class Result
class Success(val data: String) : Result()
class Failure(val error: String) : Result()
class Loading : Result()

fun handleResult(result: Result) {
    when (result) {
        is Success -> println("Data: ${result.data}")
        is Failure -> println("Error: ${result.error}")
        is Loading -> println("Please wait...")
    }
}

fun main() {
    handleResult(Success("User loaded"))  // Data: User loaded
    handleResult(Failure("Network error"))  // Error: Network error
}
```

**Key Points:**
- All subclasses must be in same file.
- `when` does not need `else` if all cases are covered.
- Better than enums because subclasses can have their own properties.

---

## Q.3(a) Activity Lifecycle and Callbacks

The **Activity Lifecycle** is the series of states an Activity goes through from creation to destruction.

### Lifecycle Diagram (Text Format):

```
App Launches
     ↓
  onCreate()      → Activity is created
     ↓
  onStart()       → Activity becomes visible
     ↓
  onResume()      → Activity is in foreground (user can interact)
     ↓
  onPause()       → Another activity comes to foreground
     ↓
  onStop()        → Activity is no longer visible
     ↓
  onRestart()     → Activity is coming back from stopped state
     ↓
  onDestroy()     → Activity is destroyed
```

### Callback Descriptions:

| Method | Called When |
|--------|------------|
| `onCreate()` | Activity is first created. Initialize UI here. |
| `onStart()` | Activity becomes visible to user. |
| `onResume()` | Activity starts interacting with user. |
| `onPause()` | User is leaving, but activity still visible. |
| `onStop()` | Activity no longer visible. |
| `onRestart()` | Activity re-starting after being stopped. |
| `onDestroy()` | Activity is being destroyed. |

**Example:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        println("onCreate called")
    }

    override fun onStart() {
        super.onStart()
        println("onStart called")
    }

    override fun onResume() {
        super.onResume()
        println("onResume called")
    }

    override fun onPause() {
        super.onPause()
        println("onPause called")
    }

    override fun onStop() {
        super.onStop()
        println("onStop called")
    }

    override fun onDestroy() {
        super.onDestroy()
        println("onDestroy called")
    }
}
```

---

## Q.3(b) Android Program — Display Text in TextView from Button (Dynamic)

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // Create LinearLayout dynamically
        val layout = LinearLayout(this)
        layout.orientation = LinearLayout.VERTICAL
        layout.setPadding(50, 50, 50, 50)

        // Create TextView dynamically
        val textView = TextView(this)
        textView.text = "Press the button"
        textView.textSize = 18f

        // Create Button dynamically
        val button = Button(this)
        button.text = "Click Me"

        // Button click action
        button.setOnClickListener {
            textView.text = "Hello! Button was clicked!"
        }

        // Add views to layout
        layout.addView(textView)
        layout.addView(button)

        // Set layout as content view
        setContentView(layout)
    }
}
```

- Both `TextView` and `Button` are created in code (not XML).
- On button click, the text of TextView changes.

---

## Q.3(c) Difference Between LinearLayout and RelativeLayout

| Feature | LinearLayout | RelativeLayout |
|---------|-------------|----------------|
| Arrangement | Views arranged in a **single row or column** | Views arranged **relative to each other** |
| Direction | Horizontal or Vertical | No fixed direction |
| Complexity | Simple | More flexible |
| Performance | Slightly slower for nested layouts | Better for complex layouts |

**LinearLayout Example:**
```xml
<LinearLayout
    android:orientation="vertical">
    <TextView android:text="Name"/>
    <EditText android:hint="Enter name"/>
</LinearLayout>
```
(Views appear one below the other)

**RelativeLayout Example:**
```xml
<RelativeLayout>
    <TextView
        android:id="@+id/label"
        android:text="Name"/>
    <EditText
        android:layout_below="@id/label"
        android:hint="Enter name"/>
</RelativeLayout>
```
(EditText placed below TextView using `layout_below`)

---

## Q.3(d) Login Activity + Profile Activity with Validation

### MainActivity.kt (Login Activity)
```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etUsername = findViewById<EditText>(R.id.etUsername)
        val etPassword = findViewById<EditText>(R.id.etPassword)
        val btnLogin = findViewById<Button>(R.id.btnLogin)

        btnLogin.setOnClickListener {
            val username = etUsername.text.toString()
            val password = etPassword.text.toString()

            if (username.isEmpty() || password.isEmpty()) {
                Toast.makeText(this, "Fields cannot be blank", Toast.LENGTH_SHORT).show()
            } else if (username == "giet@gmail.com" && password == "giet@123") {
                val intent = Intent(this, ProfileActivity::class.java)
                startActivity(intent)
            } else {
                Toast.makeText(this, "Invalid credentials", Toast.LENGTH_SHORT).show()
            }
        }
    }
}
```

### ProfileActivity.kt
```kotlin
class ProfileActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_profile)

        val tvMessage = findViewById<TextView>(R.id.tvMessage)
        tvMessage.text = "Welcome : GIET"
    }
}
```

### activity_main.xml (Layout)
```xml
<LinearLayout android:orientation="vertical" ...>
    <EditText android:id="@+id/etUsername" android:hint="Username"/>
    <EditText android:id="@+id/etPassword" android:hint="Password" android:inputType="textPassword"/>
    <Button android:id="@+id/btnLogin" android:text="Login"/>
</LinearLayout>
```

### activity_profile.xml
```xml
<LinearLayout ...>
    <TextView android:id="@+id/tvMessage" android:textSize="24sp"/>
</LinearLayout>
```

---

## Q.4(a) Types of Application Architecture

### 1. MVC — Model View Controller
- **Model**: Data and business logic
- **View**: UI (what user sees)
- **Controller**: Handles user input and updates model/view
- Problem: Controller becomes very large.

### 2. MVP — Model View Presenter
- **Model**: Data layer
- **View**: UI (Activity/Fragment)
- **Presenter**: Middle layer between View and Model
- View and Model do not talk directly.
- Easier to test.

### 3. MVVM — Model View ViewModel (Most used in Android)
- **Model**: Data (Room DB, API)
- **View**: UI (Activity/Fragment)
- **ViewModel**: Holds UI data and survives screen rotation
- Uses **LiveData** to observe data changes automatically.
- Best practice for Android development.

### 4. Clean Architecture
- Separates code into multiple layers: UI, Domain, Data
- Each layer has a specific responsibility
- Easy to maintain and scale large apps

**Summary Table:**

| Architecture | Advantage |
|---|---|
| MVC | Simple, small apps |
| MVP | Testable, separates concerns |
| MVVM | Best for Android, uses LiveData |
| Clean Architecture | Large scale, highly maintainable |

---

## Q.4(b) Android App — 3 Radio Buttons to Change Background Color

### activity_main.xml
```xml
<LinearLayout
    android:id="@+id/mainLayout"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <RadioGroup android:id="@+id/radioGroup">
        <RadioButton android:id="@+id/rbRed" android:text="Red"/>
        <RadioButton android:id="@+id/rbGreen" android:text="Green"/>
        <RadioButton android:id="@+id/rbBlue" android:text="Blue"/>
    </RadioGroup>

</LinearLayout>
```

### MainActivity.kt
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

## Q.4(c) RecyclerView vs ListView

### RecyclerView
- Advanced and flexible version of ListView.
- Uses **ViewHolder pattern** (mandatory) — better performance.
- Supports **horizontal, vertical, and grid** layouts.
- Uses `RecyclerView.Adapter` and `LayoutManager`.

### ListView
- Older and simpler.
- ViewHolder pattern is optional — leads to poor performance.
- Only vertical scrolling.
- Harder to customize.

**Difference Table:**

| Feature | ListView | RecyclerView |
|---------|----------|--------------|
| ViewHolder | Optional | Mandatory |
| Layout | Only Vertical | Vertical, Horizontal, Grid |
| Animation | Not supported | Supported |
| Performance | Less efficient | High performance |
| Customization | Limited | Highly customizable |

---

## Q.4(d) Android App — 3 Buttons to Change Background Color

### activity_main.xml
```xml
<LinearLayout
    android:id="@+id/mainLayout"
    android:orientation="vertical" ...>

    <Button android:id="@+id/btnRed" android:text="Red"/>
    <Button android:id="@+id/btnGreen" android:text="Green"/>
    <Button android:id="@+id/btnBlue" android:text="Blue"/>

</LinearLayout>
```

### MainActivity.kt
```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val layout = findViewById<LinearLayout>(R.id.mainLayout)

        findViewById<Button>(R.id.btnRed).setOnClickListener {
            layout.setBackgroundColor(Color.RED)
        }
        findViewById<Button>(R.id.btnGreen).setOnClickListener {
            layout.setBackgroundColor(Color.GREEN)
        }
        findViewById<Button>(R.id.btnBlue).setOnClickListener {
            layout.setBackgroundColor(Color.BLUE)
        }
    }
}
```

---

## Q.5(a) SQLite and Firebase — Steps to Connect SQLite

### SQLite
- SQLite is a **lightweight local database** stored on the device itself.
- No internet required.
- Used for offline data storage.
- Android provides built-in support through `SQLiteOpenHelper` class.

### Firebase
- Firebase is a **cloud-based database** by Google.
- Data stored on Google's server.
- Supports real-time updates across multiple devices.
- Requires internet connection.

### Steps to Connect Android App with SQLite:

**Step 1:** Create a class that extends `SQLiteOpenHelper`

```kotlin
class DatabaseHelper(context: Context) :
    SQLiteOpenHelper(context, "MyDB", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        db.execSQL("CREATE TABLE users (id INTEGER PRIMARY KEY, name TEXT, age INTEGER)")
    }

    override fun onUpgrade(db: SQLiteDatabase, oldV: Int, newV: Int) {
        db.execSQL("DROP TABLE IF EXISTS users")
        onCreate(db)
    }
}
```

**Step 2:** Insert Data
```kotlin
val db = DatabaseHelper(this).writableDatabase
val values = ContentValues()
values.put("name", "Ram")
values.put("age", 22)
db.insert("users", null, values)
```

**Step 3:** Read Data
```kotlin
val db = DatabaseHelper(this).readableDatabase
val cursor = db.rawQuery("SELECT * FROM users", null)
while (cursor.moveToNext()) {
    val name = cursor.getString(1)
    println(name)
}
cursor.close()
```

---

## Q.5(b) Types of Menus in Android + Steps to Create Option Menu

### Types of Menus:

1. **Options Menu** — Appears in the top action bar (toolbar). Most common.
2. **Context Menu** — Appears when user long-presses on a view.
3. **Popup Menu** — Appears as a dropdown near a button.

### Steps to Create Option Menu:

**Step 1:** Create `res/menu/menu_main.xml`
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/action_settings" android:title="Settings"/>
    <item android:id="@+id/action_about" android:title="About"/>
</menu>
```

**Step 2:** Override `onCreateOptionsMenu` in Activity
```kotlin
override fun onCreateOptionsMenu(menu: Menu?): Boolean {
    menuInflater.inflate(R.menu.menu_main, menu)
    return true
}
```

**Step 3:** Handle menu item click with `onOptionsItemSelected`
```kotlin
override fun onOptionsItemSelected(item: MenuItem): Boolean {
    return when (item.itemId) {
        R.id.action_settings -> {
            Toast.makeText(this, "Settings clicked", Toast.LENGTH_SHORT).show()
            true
        }
        R.id.action_about -> {
            Toast.makeText(this, "About clicked", Toast.LENGTH_SHORT).show()
            true
        }
        else -> super.onOptionsItemSelected(item)
    }
}
```

---

## Q.5(c) Shared Preferences in Android

- **SharedPreferences** is used to store **small key-value data** permanently on the device.
- Data is saved even after the app is closed.
- Used for: saving settings, login status, user preferences, etc.

### Storing Data:
```kotlin
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val editor = sharedPref.edit()
editor.putString("username", "giet@gmail.com")
editor.putBoolean("isLoggedIn", true)
editor.apply()  // Save changes
```

### Reading Data:
```kotlin
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val username = sharedPref.getString("username", "default")
val isLoggedIn = sharedPref.getBoolean("isLoggedIn", false)
println(username)    // giet@gmail.com
println(isLoggedIn)  // true
```

### Deleting Data:
```kotlin
editor.remove("username")  // Remove one key
editor.clear()             // Remove all data
editor.apply()
```

**Use Case:** After login, save `isLoggedIn = true`. On next app open, check this value to skip login screen.

---

## Q.5(d) Classes and Functions for SQLite Connection

### 1. SQLiteOpenHelper
- Base class for managing database creation and version management.
- Important Methods:
  - `onCreate(db)` — Called when database is created for the first time.
  - `onUpgrade(db, oldV, newV)` — Called when database version changes.

### 2. SQLiteDatabase
- Used to perform CRUD operations.
- Important Functions:

| Function | Purpose |
|----------|---------|
| `execSQL(sql)` | Run any SQL command (CREATE, DROP) |
| `insert(table, null, values)` | Insert a row |
| `update(table, values, where, args)` | Update rows |
| `delete(table, where, args)` | Delete rows |
| `rawQuery(sql, args)` | Run SELECT query, returns Cursor |
| `query(...)` | Run SELECT with parameters |

### 3. ContentValues
- Used to hold column-value pairs for insert/update.
```kotlin
val values = ContentValues()
values.put("name", "Ravi")
values.put("age", 20)
```

### 4. Cursor
- Used to read query results row by row.
- Important Functions:

| Function | Purpose |
|----------|---------|
| `moveToFirst()` | Move to first row |
| `moveToNext()` | Move to next row |
| `getString(index)` | Get String value |
| `getInt(index)` | Get Int value |
| `close()` | Close cursor after use |

**Complete Example:**
```kotlin
class DBHelper(context: Context) : SQLiteOpenHelper(context, "School.db", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        db.execSQL("CREATE TABLE student (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT)")
    }

    override fun onUpgrade(db: SQLiteDatabase, old: Int, new: Int) {}

    fun insertStudent(name: String) {
        val db = writableDatabase
        val cv = ContentValues()
        cv.put("name", name)
        db.insert("student", null, cv)
    }

    fun getAllStudents(): List<String> {
        val list = mutableListOf<String>()
        val db = readableDatabase
        val cursor = db.rawQuery("SELECT * FROM student", null)
        while (cursor.moveToNext()) {
            list.add(cursor.getString(1))
        }
        cursor.close()
        return list
    }
}
```

---

*End of Answer Sheet*
