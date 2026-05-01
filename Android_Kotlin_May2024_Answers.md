# Android App Development using Kotlin — Complete Exam Answers
### 21BCMOE36001 / 21BCSOE36001 / 21BCDOE36001
### B.Tech 6th Semester | GIET University | May 2024

---

# PART – A (Short Answers – 2 Marks Each)

---

## Q1a. What is a Toast? Write its Syntax.

A **Toast** is a small popup message that appears on the screen for a short time and then disappears automatically. It is used to show quick information to the user.

**Syntax:**
```kotlin
Toast.makeText(context, "Your Message", Toast.LENGTH_SHORT).show()
```

**Example:**
```kotlin
Toast.makeText(this, "Button Clicked!", Toast.LENGTH_SHORT).show()
```

- `Toast.LENGTH_SHORT` — shows for 2 seconds
- `Toast.LENGTH_LONG` — shows for 3.5 seconds

---

## Q1b. What is an Adapter?

An **Adapter** acts as a bridge between a data source (like a list or array) and a UI component (like ListView, RecyclerView, Spinner).

- It takes data from the source and fills it into the UI element.
- Common adapters: `ArrayAdapter`, `BaseAdapter`, `RecyclerView.Adapter`

**Example:**
```kotlin
val languages = listOf("Kotlin", "Java", "Python")
val adapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, languages)
listView.adapter = adapter
```

---

## Q1c. Difference Between Activity and Fragment

| Feature | Activity | Fragment |
|---|---|---|
| Definition | A single screen with UI | A part/portion of a screen |
| Dependency | Independent | Depends on an Activity |
| Lifecycle | Has own lifecycle | Has own lifecycle but tied to Activity |
| Reusability | Cannot be reused easily | Can be reused in multiple Activities |
| Back Stack | Managed by system | Managed by FragmentManager |

---

## Q1d. Intent — Types of Intent

An **Intent** is a messaging object used to communicate between components (Activity to Activity, Activity to Service, etc.).

**Types:**

**1. Explicit Intent** — Target component is specified directly.
```kotlin
val intent = Intent(this, SecondActivity::class.java)
startActivity(intent)
```

**2. Implicit Intent** — Target is not specified; Android finds the best app.
```kotlin
val intent = Intent(Intent.ACTION_VIEW, Uri.parse("https://www.google.com"))
startActivity(intent)
```

---

## Q1e. Companion Object in Kotlin

A **companion object** is used to define members that belong to the class itself, not to instances (similar to `static` in Java).

**Example:**
```kotlin
class MathHelper {
    companion object {
        val PI = 3.14
        fun square(n: Int) = n * n
    }
}

fun main() {
    println(MathHelper.PI)         // 3.14
    println(MathHelper.square(5))  // 25
}
```

No object creation is needed — called directly using the class name.

---

# PART – B (Long Answers)

---

## Q2a. Function Overloading — Area of Circle, Rectangle, Triangle (8 Marks)

**Function Overloading** means having multiple functions with the same name but different parameters.

```kotlin
// Area of Circle
fun area(radius: Double): Double {
    return 3.14 * radius * radius
}

// Area of Rectangle
fun area(length: Double, breadth: Double): Double {
    return length * breadth
}

// Area of Triangle
fun area(base: Double, height: Double, isTriangle: Boolean): Double {
    return 0.5 * base * height
}

fun main() {
    println("Area of Circle = ${area(7.0)}")
    println("Area of Rectangle = ${area(5.0, 4.0)}")
    println("Area of Triangle = ${area(6.0, 8.0, true)}")
}
```

**Output:**
```
Area of Circle = 153.86
Area of Rectangle = 20.0
Area of Triangle = 24.0
```

Each `area()` function has a different number or type of parameters. Kotlin picks the correct one based on what arguments you pass.

---

## Q2b. All Features of Kotlin (7 Marks)

**1. Concise Syntax**
Write less code. No need for semicolons or getter/setter methods.

**2. Null Safety**
Prevents NullPointerException at compile time.
```kotlin
var name: String? = null  // nullable type
val len = name?.length ?: 0  // safe call with elvis
```

**3. Data Classes**
Auto-generates `toString()`, `equals()`, `copy()`, `hashCode()`.
```kotlin
data class Student(val name: String, val marks: Int)
```

**4. Extension Functions**
Add functions to existing classes without modifying them.
```kotlin
fun String.hello() = "Hello, $this!"
println("Raj".hello())  // Hello, Raj!
```

**5. Smart Cast**
No need for manual casting after type check.
```kotlin
if (obj is String) println(obj.length)  // auto cast
```

**6. Coroutines**
Easy way to write async/background code.

**7. Interoperability**
Kotlin works perfectly with existing Java code.

**8. Higher-Order Functions & Lambdas**
Functions can take other functions as parameters.
```kotlin
val nums = listOf(1, 2, 3, 4)
val even = nums.filter { it % 2 == 0 }
```

---

## Q2c. Armstrong Numbers Between 100 to 500 (8 Marks)

An **Armstrong number** is a number where the sum of each digit raised to the power of number of digits equals the number itself.

**Example:** 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153 ✓

```kotlin
fun main() {
    println("Armstrong numbers between 100 and 500:")
    for (num in 100..500) {
        val digits = num.toString()
        val n = digits.length
        var sum = 0
        for (ch in digits) {
            val d = ch.toString().toInt()
            var power = 1
            repeat(n) { power *= d }
            sum += power
        }
        if (sum == num) {
            print("$num  ")
        }
    }
}
```

**Output:**
```
Armstrong numbers between 100 and 500:
153  370  371  407
```

---

## Q2d. Inheritance in Kotlin (7 Marks)

**Inheritance** allows a child class to use properties and methods of a parent class. In Kotlin, the parent class must be declared with `open` keyword.

**Syntax:**
```kotlin
open class ParentClass {
    // properties and methods
}

class ChildClass : ParentClass() {
    // can use parent's methods
}
```

**Example:**
```kotlin
open class Animal(val name: String) {
    fun eat() {
        println("$name is eating")
    }

    open fun sound() {
        println("Some sound")
    }
}

class Dog(name: String) : Animal(name) {
    override fun sound() {
        println("$name says: Woof!")
    }
}

class Cat(name: String) : Animal(name) {
    override fun sound() {
        println("$name says: Meow!")
    }
}

fun main() {
    val dog = Dog("Bruno")
    dog.eat()    // inherited
    dog.sound()  // overridden

    val cat = Cat("Kitty")
    cat.eat()
    cat.sound()
}
```

**Output:**
```
Bruno is eating
Bruno says: Woof!
Kitty is eating
Kitty says: Meow!
```

---

## Q3a. Layered Architecture of Android (8 Marks)

Android is built in **5 layers** (from bottom to top):

```
┌──────────────────────────────────────┐
│           APPLICATIONS               │
│   (Contacts, Camera, Maps, Browser)  │
├──────────────────────────────────────┤
│       APPLICATION FRAMEWORK          │
│  (Activity Mgr, Content Providers,   │
│   Notification Mgr, Location Mgr)    │
├──────────────────────────────────────┤
│  ANDROID RUNTIME  │  CORE LIBRARIES  │
│  (ART / Dalvik)   │  (SQLite, WebKit)│
├──────────────────────────────────────┤
│         HARDWARE ABSTRACTION         │
│              LAYER (HAL)             │
├──────────────────────────────────────┤
│            LINUX KERNEL              │
│  (Drivers: Camera, WiFi, Bluetooth,  │
│   Memory Management, Security)       │
└──────────────────────────────────────┘
```

**Layer Explanation:**

**1. Linux Kernel (Bottom Layer)**
- Core of Android OS
- Manages hardware drivers (Camera, Audio, WiFi, USB)
- Handles memory, power, and security

**2. Hardware Abstraction Layer (HAL)**
- Interface between hardware and software layers
- Allows Android to work on different hardware brands

**3. Android Runtime (ART)**
- Runs Android apps
- Converts app code (DEX files) into machine code
- Uses AOT (Ahead-Of-Time) compilation for faster execution

**4. Native C/C++ Libraries**
- SQLite — database
- WebKit — web browser engine
- OpenGL — graphics
- SSL — secure connections

**5. Application Framework**
- Provides APIs to developers
- Activity Manager, Window Manager, Content Providers, Notification Manager

**6. Applications (Top Layer)**
- Apps that users install and use (Phone, WhatsApp, etc.)

---

## Q3b. App to Enter 2 Numbers and Display Result (7 Marks)

**activity_main.xml:**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText android:id="@+id/etNum1"
        android:hint="Enter First Number"
        android:inputType="number"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <EditText android:id="@+id/etNum2"
        android:hint="Enter Second Number"
        android:inputType="number"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <Button android:id="@+id/btnAdd"
        android:text="Add"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <TextView android:id="@+id/tvResult"
        android:textSize="20sp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
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
            val sum = num1 + num2
            tvResult.text = "Result = $sum"
        }
    }
}
```

---

## Q3c. Android App File Structure in Android Studio (8 Marks)

When you create a new Android project, Android Studio generates the following folder structure:

```
MyApp/
├── app/
│   ├── manifests/
│   │   └── AndroidManifest.xml        ← App info, permissions, activities
│   ├── java/
│   │   └── com.example.myapp/
│   │       └── MainActivity.kt        ← Kotlin source code
│   ├── res/
│   │   ├── layout/
│   │   │   └── activity_main.xml      ← UI Layout files
│   │   ├── drawable/                  ← Images and icons
│   │   ├── values/
│   │   │   ├── strings.xml            ← String resources
│   │   │   ├── colors.xml             ← Color definitions
│   │   │   └── themes.xml             ← App theme/style
│   │   └── mipmap/                    ← App launcher icons
│   └── build.gradle (app)             ← App level dependencies
├── Gradle Scripts/
│   └── build.gradle (project)         ← Project level config
```

**Key Files Explained:**

- **AndroidManifest.xml** — Declares all activities, permissions, app name, launch activity
- **MainActivity.kt** — Main Kotlin file with app logic
- **activity_main.xml** — Defines the UI layout of main screen
- **strings.xml** — Stores all text strings (good for localization)
- **colors.xml** — Stores color codes used in the app
- **build.gradle** — Adds libraries/dependencies (like Firebase, Retrofit)
- **drawable/** — Stores images, icons, shapes
- **mipmap/** — Stores the launcher icon in different resolutions

---

## Q3d. Change Background Color Using RadioButton (7 Marks)

**activity_main.xml:**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/mainLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <RadioGroup android:id="@+id/rgColors"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <RadioButton android:id="@+id/rbRed"
            android:text="Red"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>

        <RadioButton android:id="@+id/rbGreen"
            android:text="Green"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>

        <RadioButton android:id="@+id/rbBlue"
            android:text="Blue"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>
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
        val rgColors = findViewById<RadioGroup>(R.id.rgColors)

        rgColors.setOnCheckedChangeListener { _, checkedId ->
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

## Q4a. MVC, MVP and MVVM Architecture (7 Marks)

### 1. MVC — Model View Controller

- **Model** — handles data and business logic
- **View** — shows UI to user
- **Controller** — handles user input and updates Model/View

**Flow:** User → Controller → Model → View

**Drawback:** Controller becomes too large and hard to test.

---

### 2. MVP — Model View Presenter

- **Model** — data and business logic
- **View** — only displays UI (Activity/Fragment)
- **Presenter** — middle layer between View and Model

**Flow:** View → Presenter → Model → Presenter → View

**Advantage:** View and Presenter are separate, so easy to unit test.

---

### 3. MVVM — Model View ViewModel ⭐ (Most Popular)

- **Model** — data layer (database, API)
- **View** — Activity/Fragment (observes ViewModel)
- **ViewModel** — holds and manages UI data, survives screen rotation

**Flow:** View observes ViewModel → ViewModel gets data from Model

**Advantage:** View and business logic are fully separated. Best for Android with LiveData.

| | MVC | MVP | MVVM |
|---|---|---|---|
| Testability | Low | Medium | High |
| Complexity | Simple | Medium | Medium |
| Used in Android | Old apps | Medium apps | Modern apps |

---

## Q4b. Android App with 3 Fragments (8 Marks)

**LoginFragment.kt:**
```kotlin
class LoginFragment : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        val view = inflater.inflate(R.layout.fragment_login, container, false)

        view.findViewById<Button>(R.id.btnLogin).setOnClickListener {
            // Navigate to HomeFragment
            parentFragmentManager.beginTransaction()
                .replace(R.id.container, HomeFragment())
                .commit()
        }

        view.findViewById<Button>(R.id.btnRegister).setOnClickListener {
            // Navigate to RegisterFragment
            parentFragmentManager.beginTransaction()
                .replace(R.id.container, RegisterFragment())
                .addToBackStack(null)
                .commit()
        }
        return view
    }
}
```

**HomeFragment.kt:**
```kotlin
class HomeFragment : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        return inflater.inflate(R.layout.fragment_home, container, false)
    }
}
```

**RegisterFragment.kt:**
```kotlin
class RegisterFragment : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        return inflater.inflate(R.layout.fragment_register, container, false)
    }
}
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Load LoginFragment first
        supportFragmentManager.beginTransaction()
            .replace(R.id.container, LoginFragment())
            .commit()
    }
}
```

**activity_main.xml:**
```xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```

---

## Q4c. Fragment in Android — Fragment Lifecycle (8 Marks)

### What is a Fragment?
A **Fragment** is a reusable, modular section of an Activity that has its own layout and lifecycle. Multiple fragments can be shown in a single Activity.

### Fragment Lifecycle Methods:

```
onAttach()        ← Fragment is attached to Activity
     ↓
onCreate()        ← Fragment is created (initialize data)
     ↓
onCreateView()    ← Fragment's UI is created (return layout here)
     ↓
onViewCreated()   ← After view is ready (set click listeners here)
     ↓
onStart()         ← Fragment becomes visible
     ↓
onResume()        ← Fragment is active and interactive
     ↓
onPause()         ← Fragment loses focus
     ↓
onStop()          ← Fragment is no longer visible
     ↓
onDestroyView()   ← Fragment's view is destroyed
     ↓
onDestroy()       ← Fragment is destroyed
     ↓
onDetach()        ← Fragment is detached from Activity
```

**Most Important Methods:**
- `onCreateView()` — inflate and return the layout
- `onViewCreated()` — setup button clicks, LiveData observers
- `onDestroyView()` — clean up references to views

---

## Q4d. Registration Activity with Validation (7 Marks)

**activity_main.xml:**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:orientation="vertical" android:padding="16dp">

    <EditText android:id="@+id/etName" android:hint="Enter Name"
        android:layout_width="match_parent" android:layout_height="wrap_content"/>

    <EditText android:id="@+id/etEmail" android:hint="Enter Email"
        android:inputType="textEmailAddress"
        android:layout_width="match_parent" android:layout_height="wrap_content"/>

    <EditText android:id="@+id/etMobile" android:hint="Enter Mobile Number"
        android:inputType="phone"
        android:layout_width="match_parent" android:layout_height="wrap_content"/>

    <Button android:id="@+id/btnRegister" android:text="Register"
        android:layout_width="match_parent" android:layout_height="wrap_content"/>

    <TextView android:id="@+id/tvResult"
        android:layout_width="match_parent" android:layout_height="wrap_content"/>
</LinearLayout>
```

**MainActivity.kt:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etName = findViewById<EditText>(R.id.etName)
        val etEmail = findViewById<EditText>(R.id.etEmail)
        val etMobile = findViewById<EditText>(R.id.etMobile)
        val btnRegister = findViewById<Button>(R.id.btnRegister)
        val tvResult = findViewById<TextView>(R.id.tvResult)

        btnRegister.setOnClickListener {
            val name = etName.text.toString().trim()
            val email = etEmail.text.toString().trim()
            val mobile = etMobile.text.toString().trim()

            // Validation
            if (name.isEmpty()) {
                etName.error = "Name is required"
                return@setOnClickListener
            }
            if (email.isEmpty() || !android.util.Patterns.EMAIL_ADDRESS.matcher(email).matches()) {
                etEmail.error = "Enter valid email"
                return@setOnClickListener
            }
            if (mobile.isEmpty() || mobile.length != 10) {
                etMobile.error = "Enter valid 10-digit mobile number"
                return@setOnClickListener
            }

            tvResult.text = "Registered!\nName: $name\nEmail: $email\nMobile: $mobile"
        }
    }
}
```

---

## Q5a. Steps to Connect Android App with SQLite Database (7 Marks)

**SQLite** is a lightweight built-in database in Android. No external setup is needed.

**Step-by-Step Process:**

**Step 1:** Create a class that extends `SQLiteOpenHelper`

**Step 2:** Override `onCreate()` to create tables

**Step 3:** Override `onUpgrade()` to handle database upgrades

**Step 4:** Write insert, update, delete, query methods

**Step 5:** Create an object of this helper class in your Activity

**Step 6:** Call the methods to perform database operations

**Basic Template:**
```kotlin
class DBHelper(context: Context) : SQLiteOpenHelper(context, "MyDB", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        db.execSQL("CREATE TABLE users (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT)")
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        db.execSQL("DROP TABLE IF EXISTS users")
        onCreate(db)
    }

    fun insertData(name: String) {
        val db = writableDatabase
        val values = ContentValues()
        values.put("name", name)
        db.insert("users", null, values)
    }

    fun getAllData(): Cursor {
        return readableDatabase.rawQuery("SELECT * FROM users", null)
    }
}
```

---

## Q5b. SharedPreferences in Android — With Example (8 Marks)

**SharedPreferences** is used to store small amounts of data as key-value pairs. The data is saved permanently even after the app is closed.

**Storing Data:**
```kotlin
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val editor = sharedPref.edit()
editor.putString("username", "Rahul")
editor.putInt("age", 22)
editor.putBoolean("isLoggedIn", true)
editor.apply()  // saves data
```

**Retrieving Data:**
```kotlin
val sharedPref = getSharedPreferences("MyPrefs", Context.MODE_PRIVATE)
val username = sharedPref.getString("username", "Guest") // "Guest" is default
val age = sharedPref.getInt("age", 0)
val isLoggedIn = sharedPref.getBoolean("isLoggedIn", false)
```

**Complete Example:**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val pref = getSharedPreferences("UserData", Context.MODE_PRIVATE)
        val etName = findViewById<EditText>(R.id.etName)
        val btnSave = findViewById<Button>(R.id.btnSave)
        val btnLoad = findViewById<Button>(R.id.btnLoad)
        val tvShow = findViewById<TextView>(R.id.tvShow)

        btnSave.setOnClickListener {
            pref.edit().putString("name", etName.text.toString()).apply()
            Toast.makeText(this, "Saved!", Toast.LENGTH_SHORT).show()
        }

        btnLoad.setOnClickListener {
            val name = pref.getString("name", "Not Found")
            tvShow.text = "Saved Name: $name"
        }
    }
}
```

**Key Methods:**
- `putString()`, `putInt()`, `putBoolean()` — save data
- `getString()`, `getInt()`, `getBoolean()` — load data
- `editor.remove("key")` — delete one key
- `editor.clear()` — delete all data

---

## Q5c. Types of Menus in Android + Steps for Options Menu (8 Marks)

### Types of Menus in Android:

**1. Options Menu**
- Appears in the top app bar (Action Bar) when user taps the 3-dot icon
- Used for global app actions like Settings, Logout, Search

**2. Context Menu**
- Appears when user **long-presses** on a View
- Used for actions specific to that item (Copy, Delete, Share)

**3. Popup Menu**
- Appears anchored to a specific View on button click
- Dismisses when user taps outside

---

### Steps to Create Options Menu:

**Step 1:** Create menu XML file in `res/menu/main_menu.xml`
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/menuSettings" android:title="Settings"/>
    <item android:id="@+id/menuLogout" android:title="Logout"/>
    <item android:id="@+id/menuAbout" android:title="About"/>
</menu>
```

**Step 2:** Override `onCreateOptionsMenu()` in Activity
```kotlin
override fun onCreateOptionsMenu(menu: Menu): Boolean {
    menuInflater.inflate(R.menu.main_menu, menu)
    return true
}
```

**Step 3:** Handle menu item clicks in `onOptionsItemSelected()`
```kotlin
override fun onOptionsItemSelected(item: MenuItem): Boolean {
    when (item.itemId) {
        R.id.menuSettings -> Toast.makeText(this, "Settings", Toast.LENGTH_SHORT).show()
        R.id.menuLogout   -> Toast.makeText(this, "Logged Out", Toast.LENGTH_SHORT).show()
        R.id.menuAbout    -> Toast.makeText(this, "About App", Toast.LENGTH_SHORT).show()
    }
    return true
}
```

---

## Q5d. SQLite — Store Employee Data (7 Marks)

**DatabaseHelper.kt:**
```kotlin
class DatabaseHelper(context: Context) : SQLiteOpenHelper(context, "EmployeeDB", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        db.execSQL("""
            CREATE TABLE employee (
                empno INTEGER PRIMARY KEY,
                name TEXT,
                department TEXT,
                designation TEXT
            )
        """)
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        db.execSQL("DROP TABLE IF EXISTS employee")
        onCreate(db)
    }

    fun insertEmployee(empno: Int, name: String, dept: String, designation: String) {
        val db = writableDatabase
        val values = ContentValues()
        values.put("empno", empno)
        values.put("name", name)
        values.put("department", dept)
        values.put("designation", designation)
        db.insert("employee", null, values)
        db.close()
    }

    fun getAllEmployees(): String {
        val db = readableDatabase
        val cursor = db.rawQuery("SELECT * FROM employee", null)
        val result = StringBuilder()
        while (cursor.moveToNext()) {
            result.append("EmpNo: ${cursor.getInt(0)}\n")
            result.append("Name: ${cursor.getString(1)}\n")
            result.append("Dept: ${cursor.getString(2)}\n")
            result.append("Designation: ${cursor.getString(3)}\n\n")
        }
        cursor.close()
        return result.toString()
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
        val etEmpNo = findViewById<EditText>(R.id.etEmpNo)
        val etName = findViewById<EditText>(R.id.etName)
        val etDept = findViewById<EditText>(R.id.etDept)
        val etDesig = findViewById<EditText>(R.id.etDesig)
        val btnSave = findViewById<Button>(R.id.btnSave)
        val btnView = findViewById<Button>(R.id.btnView)
        val tvResult = findViewById<TextView>(R.id.tvResult)

        btnSave.setOnClickListener {
            db.insertEmployee(
                etEmpNo.text.toString().toInt(),
                etName.text.toString(),
                etDept.text.toString(),
                etDesig.text.toString()
            )
            Toast.makeText(this, "Employee Saved!", Toast.LENGTH_SHORT).show()
        }

        btnView.setOnClickListener {
            tvResult.text = db.getAllEmployees()
        }
    }
}
```

---

*End of Answers — All questions covered completely*
*Subject: Android App Development using Kotlin | GIET University | May 2024*
