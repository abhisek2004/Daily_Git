# Android App Development using Kotlin — Complete Exam Answers (SET 2)
### GIET University | Sub Code: BOECS6040 | May 2024

---

# PART – A (Short Answers)

---

## Q.1(a) What is a Toast? Write its Syntax.

- **Toast** is a small popup message that appears on the screen for a short time and disappears automatically.
- It is used to show quick notifications or messages to the user.
- It does **not** require any user interaction.

**Syntax:**
```kotlin
Toast.makeText(context, "Your Message", Toast.LENGTH_SHORT).show()
```

**Example:**
```kotlin
Toast.makeText(this, "Login Successful!", Toast.LENGTH_SHORT).show()
```

- `Toast.LENGTH_SHORT` — message shows for 2 seconds
- `Toast.LENGTH_LONG` — message shows for 3.5 seconds

---

## Q.1(b) What is an Adapter?

- An **Adapter** acts as a **bridge between data and UI components** like ListView or RecyclerView.
- It takes data from a data source (like a List or Array) and converts each item into a View to display on screen.
- Without an adapter, we cannot display lists of data in Android.

**Common Adapters:**
- `ArrayAdapter` — for simple ListView
- `BaseAdapter` — custom adapter
- `RecyclerView.Adapter` — for RecyclerView

**Example:**
```kotlin
val names = arrayOf("Ram", "Sita", "Laxman")
val adapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, names)
listView.adapter = adapter
```

---

## Q.1(c) Differences Between Activity and Fragment

| Feature | Activity | Fragment |
|--------|---------|---------|
| Definition | A single screen with UI | A part/portion of an Activity's UI |
| Independent | Yes, can work alone | No, needs an Activity to run |
| Reusability | Less reusable | Highly reusable |
| Lifecycle | Has its own lifecycle | Has its own lifecycle but depends on Activity |
| Back Stack | Managed by Android | Managed by FragmentManager |
| Use Case | Full screen | Tabs, multi-panel UI |

---

## Q.1(d) Intent and Types of Intent

- An **Intent** is a messaging object used to **communicate between components** (Activity, Service, etc.) in Android.
- It is used to start another Activity, pass data, or call a service.

### Types of Intent:

**1. Explicit Intent**
- Used to start a **specific Activity** within the same app.
```kotlin
val intent = Intent(this, ProfileActivity::class.java)
startActivity(intent)
```

**2. Implicit Intent**
- Used to request an **action** from any app that can handle it (e.g., open browser, make call).
```kotlin
val intent = Intent(Intent.ACTION_VIEW)
intent.data = Uri.parse("https://www.google.com")
startActivity(intent)
```

---

## Q.1(e) Companion Object in Kotlin

- A **companion object** is an object declared inside a class using `companion object`.
- It is used to define **static** members (like Java's `static` keyword).
- Members of companion object can be accessed directly using the class name.

**Example:**
```kotlin
class MathUtils {
    companion object {
        val PI = 3.14

        fun square(n: Int): Int {
            return n * n
        }
    }
}

fun main() {
    println(MathUtils.PI)         // 3.14
    println(MathUtils.square(5))  // 25
}
```

---

---

# PART – B (Long Answers)

---

## Q.2(a) Function Overloading — Area of Circle, Rectangle, Triangle

- **Function Overloading** = same function name but different parameters.
- Kotlin decides which function to call based on the arguments passed.

```kotlin
fun area(radius: Double): Double {
    return 3.14 * radius * radius
}

fun area(length: Double, breadth: Double): Double {
    return length * breadth
}

fun area(base: Double, height: Double, isTriangle: Boolean): Double {
    return 0.5 * base * height
}

fun main() {
    println("Area of Circle    : ${area(7.0)}")
    println("Area of Rectangle : ${area(5.0, 4.0)}")
    println("Area of Triangle  : ${area(6.0, 8.0, true)}")
}
```

**Output:**
```
Area of Circle    : 153.86
Area of Rectangle : 20.0
Area of Triangle  : 24.0
```

- Each `area()` function has different parameters — this is function overloading.

---

## Q.2(b) Features of Kotlin

1. **Concise** — Less code compared to Java. No need to write getter/setter manually.

2. **Null Safety** — Kotlin prevents NullPointerException using `?` operator.
   ```kotlin
   var name: String? = null  // nullable
   ```

3. **Interoperable with Java** — Kotlin can use Java code and vice versa. Works on JVM.

4. **Statically Typed** — Types are checked at compile time. Less runtime errors.

5. **Smart Cast** — Kotlin automatically casts types after type checking.
   ```kotlin
   if (obj is String) println(obj.length)  // auto cast
   ```

6. **Extension Functions** — Add functions to existing classes without modifying them.
   ```kotlin
   fun String.greet() = "Hello, $this"
   println("Ram".greet())  // Hello, Ram
   ```

7. **Data Classes** — Auto-generates equals, hashCode, toString.
   ```kotlin
   data class Student(val name: String, val age: Int)
   ```

8. **Coroutines** — Supports asynchronous programming easily (like background tasks).

9. **Higher Order Functions & Lambda** — Functions can be passed as arguments.

10. **Open Source** — Developed by JetBrains, freely available.

---

## Q.2(c) Armstrong Numbers Between 100 to 500

- An **Armstrong number** is a number where the sum of cubes of its digits equals the number itself.
- Example: 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153 ✅

```kotlin
fun main() {
    println("Armstrong numbers between 100 and 500:")

    for (num in 100..500) {
        val digits = num.toString()
        var sum = 0

        for (ch in digits) {
            val digit = ch - '0'
            sum += digit * digit * digit
        }

        if (sum == num) {
            println(num)
        }
    }
}
```

**Output:**
```
Armstrong numbers between 100 and 500:
153
370
371
407
```

---

## Q.2(d) Inheritance in Kotlin

- **Inheritance** allows a class to use the properties and functions of another class.
- The class that is inherited from is called **Parent (Base) class**.
- The class that inherits is called **Child (Derived) class**.
- In Kotlin, classes are `final` by default. Use `open` keyword to allow inheritance.

**Syntax:**
```kotlin
open class ParentClass {
    // parent code
}

class ChildClass : ParentClass() {
    // child code
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
    val d = Dog("Tommy")
    d.eat()    // Tommy is eating
    d.sound()  // Tommy says: Woof!

    val c = Cat("Kitty")
    c.eat()    // Kitty is eating
    c.sound()  // Kitty says: Meow!
}
```

**Key Points:**
- `open` — marks class/function as inheritable/overridable
- `override` — used in child class to override parent function
- Child class gets all properties and functions of parent class

---

## Q.3(a) Layered Architecture of Android

Android is built in **5 layers** from bottom to top:

```
┌──────────────────────────────────────────┐
│         5. Applications Layer            │
│   (Contacts, Camera, Browser, Your App)  │
├──────────────────────────────────────────┤
│      4. Application Framework Layer      │
│  (Activity Manager, Content Providers,   │
│   Location Manager, Notification Mgr)    │
├──────────────────────────────────────────┤
│     3. Libraries + Android Runtime       │
│  (SQLite, WebKit, Media, SSL)            │
│  (Dalvik VM / ART Runtime)               │
├──────────────────────────────────────────┤
│        2. Hardware Abstraction Layer     │
│    (HAL — connects hardware to software) │
├──────────────────────────────────────────┤
│          1. Linux Kernel Layer           │
│  (Drivers: WiFi, Camera, Power Mgmt)    │
└──────────────────────────────────────────┘
```

### Layer Descriptions:

**1. Linux Kernel**
- Foundation of Android OS.
- Manages hardware drivers (camera, WiFi, Bluetooth, display).
- Handles memory management, power management, security.

**2. Hardware Abstraction Layer (HAL)**
- Acts as bridge between hardware and higher-level software.
- Defines standard interfaces for hardware components.

**3. Android Runtime + Libraries**
- **ART (Android Runtime):** Runs Android apps (converts .dex bytecode).
- **Libraries:** SQLite (database), WebKit (browser engine), SSL (security), Media libraries.

**4. Application Framework**
- Provides APIs for app development.
- Includes: Activity Manager, Window Manager, Content Providers, Resource Manager, Location Manager, Notification Manager.

**5. Applications Layer**
- Top-most layer.
- All installed apps (system apps + user apps) run here.
- Example: Phone, Camera, Gmail, your custom app.

---

## Q.3(b) Android App — Enter 2 Numbers and Display Result on Button Click

### activity_main.xml
```xml
<LinearLayout
    android:orientation="vertical"
    android:padding="20dp"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <EditText
        android:id="@+id/etNum1"
        android:hint="Enter First Number"
        android:inputType="number"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <EditText
        android:id="@+id/etNum2"
        android:hint="Enter Second Number"
        android:inputType="number"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <Button
        android:id="@+id/btnAdd"
        android:text="Add"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <TextView
        android:id="@+id/tvResult"
        android:text="Result will appear here"
        android:textSize="18sp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

</LinearLayout>
```

### MainActivity.kt
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
            val n1 = etNum1.text.toString().toIntOrNull()
            val n2 = etNum2.text.toString().toIntOrNull()

            if (n1 == null || n2 == null) {
                tvResult.text = "Please enter valid numbers"
            } else {
                val result = n1 + n2
                tvResult.text = "Result: $result"
            }
        }
    }
}
```

---

## Q.3(c) Android App File Structure in Android Studio

When you create a new Android project, Android Studio creates the following structure:

```
MyApp/
├── app/
│   ├── manifests/
│   │   └── AndroidManifest.xml       ← App entry point, permissions, activities
│   ├── java/
│   │   └── com.example.myapp/
│   │       └── MainActivity.kt       ← Kotlin source code files
│   ├── res/
│   │   ├── layout/
│   │   │   └── activity_main.xml     ← UI layout files
│   │   ├── drawable/
│   │   │   └── ic_launcher.png       ← Images, icons
│   │   ├── values/
│   │   │   ├── strings.xml           ← String constants
│   │   │   ├── colors.xml            ← Color definitions
│   │   │   └── themes.xml            ← App theme/style
│   │   └── mipmap/
│   │       └── ic_launcher.png       ← App launcher icon
│   └── Gradle Scripts/
│       ├── build.gradle (Project)    ← Project-level build config
│       └── build.gradle (Module)     ← App-level build config, dependencies
```

### Key Files:

| File | Purpose |
|------|---------|
| `AndroidManifest.xml` | Declares all activities, permissions, app name |
| `MainActivity.kt` | Main Kotlin code file |
| `activity_main.xml` | UI layout using XML |
| `strings.xml` | All text strings in one place |
| `colors.xml` | Define colors used in app |
| `build.gradle` | Dependencies (like libraries) added here |

---

## Q.3(d) Android App — Change Background Color Using Radio Buttons

### activity_main.xml
```xml
<LinearLayout
    android:id="@+id/mainLayout"
    android:orientation="vertical"
    android:padding="30dp"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <RadioGroup android:id="@+id/radioGroup"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">

        <RadioButton android:id="@+id/rbRed"   android:text="Red"/>
        <RadioButton android:id="@+id/rbGreen" android:text="Green"/>
        <RadioButton android:id="@+id/rbBlue"  android:text="Blue"/>

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

## Q.4(a) MVC, MVP and MVVM Architecture

### 1. MVC — Model View Controller

```
User → Controller → Model
                  ↓
              View (UI)
```

- **Model** — Data and business logic
- **View** — UI (what user sees)
- **Controller** — Handles input, updates Model and View
- **Problem:** Controller becomes large and difficult to maintain.

---

### 2. MVP — Model View Presenter

```
View ↔ Presenter ↔ Model
```

- **Model** — Data layer
- **View** — Activity/Fragment (only shows data, no logic)
- **Presenter** — All logic is here; connects View and Model
- View and Model do NOT talk to each other directly.
- **Advantage:** Easy to test, better separation of concerns.

---

### 3. MVVM — Model View ViewModel (Recommended for Android)

```
View ↔ ViewModel ↔ Model
(observes LiveData)
```

- **Model** — Data (Room DB, API)
- **View** — Activity/Fragment (observes data)
- **ViewModel** — Holds and manages UI data; survives screen rotation
- Uses **LiveData** — View automatically updates when data changes.
- **Advantage:** No memory leaks, easy to test, best practice for Android.

### Comparison Table:

| Feature | MVC | MVP | MVVM |
|---------|-----|-----|------|
| Complexity | Low | Medium | Medium |
| Testability | Low | High | High |
| Data Binding | No | No | Yes (LiveData) |
| Android Recommended | No | No | Yes |

---

## Q.4(b) Android App with 3 Fragments — Login, Register, Home

### Step 1: Create activity_main.xml
```xml
<FrameLayout
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```

### Step 2: MainActivity.kt
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

### Step 3: LoginFragment.kt
```kotlin
class LoginFragment : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        val view = inflater.inflate(R.layout.fragment_login, container, false)

        view.findViewById<Button>(R.id.btnLogin).setOnClickListener {
            requireActivity().supportFragmentManager.beginTransaction()
                .replace(R.id.container, HomeFragment())
                .commit()
        }

        view.findViewById<Button>(R.id.btnRegister).setOnClickListener {
            requireActivity().supportFragmentManager.beginTransaction()
                .replace(R.id.container, RegisterFragment())
                .commit()
        }

        return view
    }
}
```

### Step 4: fragment_login.xml
```xml
<LinearLayout android:orientation="vertical" ...>
    <TextView android:text="Login" android:textSize="24sp"/>
    <Button android:id="@+id/btnLogin" android:text="Login"/>
    <Button android:id="@+id/btnRegister" android:text="Register"/>
</LinearLayout>
```

### Step 5: HomeFragment.kt
```kotlin
class HomeFragment : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        return inflater.inflate(R.layout.fragment_home, container, false)
    }
}
```

### Step 6: RegisterFragment.kt
```kotlin
class RegisterFragment : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        return inflater.inflate(R.layout.fragment_register, container, false)
    }
}
```

### fragment_home.xml
```xml
<LinearLayout ...>
    <TextView android:text="Welcome to Home!" android:textSize="22sp"/>
</LinearLayout>
```

### fragment_register.xml
```xml
<LinearLayout ...>
    <TextView android:text="Register Page" android:textSize="22sp"/>
</LinearLayout>
```

---

## Q.4(c) Fragment in Android + Fragment Lifecycle

### What is a Fragment?
- A **Fragment** is a **reusable portion of UI** inside an Activity.
- An Activity can have multiple fragments at the same time (e.g., in a tablet layout).
- Fragment has its own layout, lifecycle, and back stack.
- Fragment cannot exist without an Activity.

**Example use cases:** Tab layouts, Navigation Drawer, Split-screen UI.

---

### Fragment Lifecycle:

```
onAttach()       → Fragment is attached to Activity
     ↓
onCreate()       → Fragment is created
     ↓
onCreateView()   → Fragment's layout is inflated (UI created here)
     ↓
onViewCreated()  → View is ready, set up UI components here
     ↓
onStart()        → Fragment becomes visible
     ↓
onResume()       → Fragment is active and interactive
     ↓
onPause()        → Fragment is partially hidden
     ↓
onStop()         → Fragment is no longer visible
     ↓
onDestroyView()  → Fragment's view is destroyed
     ↓
onDestroy()      → Fragment is destroyed
     ↓
onDetach()       → Fragment is detached from Activity
```

### Key Callback Descriptions:

| Callback | Purpose |
|---------|---------|
| `onAttach()` | Fragment connects to Activity |
| `onCreate()` | Initialize data/variables |
| `onCreateView()` | Inflate and return the fragment layout |
| `onViewCreated()` | Set up buttons, listeners |
| `onResume()` | Fragment is active |
| `onDestroyView()` | Clean up view references |
| `onDetach()` | Fragment disconnects from Activity |

---

## Q.4(d) Registration Activity with Validation

### activity_register.xml
```xml
<LinearLayout android:orientation="vertical" android:padding="20dp" ...>

    <EditText android:id="@+id/etName"
        android:hint="Enter Name"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <EditText android:id="@+id/etEmail"
        android:hint="Enter Email"
        android:inputType="textEmailAddress"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <EditText android:id="@+id/etMobile"
        android:hint="Enter Mobile Number"
        android:inputType="phone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <Button android:id="@+id/btnRegister"
        android:text="Register"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <TextView android:id="@+id/tvMessage"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

</LinearLayout>
```

### RegisterActivity.kt
```kotlin
class RegisterActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_register)

        val etName   = findViewById<EditText>(R.id.etName)
        val etEmail  = findViewById<EditText>(R.id.etEmail)
        val etMobile = findViewById<EditText>(R.id.etMobile)
        val btnRegister = findViewById<Button>(R.id.btnRegister)
        val tvMessage   = findViewById<TextView>(R.id.tvMessage)

        btnRegister.setOnClickListener {
            val name   = etName.text.toString().trim()
            val email  = etEmail.text.toString().trim()
            val mobile = etMobile.text.toString().trim()

            when {
                name.isEmpty() -> {
                    tvMessage.text = "Name cannot be empty"
                }
                email.isEmpty() || !android.util.Patterns.EMAIL_ADDRESS.matcher(email).matches() -> {
                    tvMessage.text = "Enter a valid email address"
                }
                mobile.isEmpty() || mobile.length != 10 -> {
                    tvMessage.text = "Enter a valid 10-digit mobile number"
                }
                else -> {
                    tvMessage.text = "Registration Successful!\nName: $name\nEmail: $email\nMobile: $mobile"
                }
            }
        }
    }
}
```

**Validations Done:**
1. Name must not be empty.
2. Email must be a valid email format.
3. Mobile must be exactly 10 digits.

---

## Q.5(a) Steps to Connect Android App with SQLite Database

**Step 1: Create a class extending SQLiteOpenHelper**
```kotlin
class DatabaseHelper(context: Context) :
    SQLiteOpenHelper(context, "MyDatabase.db", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        val query = "CREATE TABLE users (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, age INTEGER)"
        db.execSQL(query)
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        db.execSQL("DROP TABLE IF EXISTS users")
        onCreate(db)
    }
}
```

**Step 2: Insert Data**
```kotlin
fun insertData(name: String, age: Int) {
    val db = writableDatabase
    val values = ContentValues()
    values.put("name", name)
    values.put("age", age)
    db.insert("users", null, values)
    db.close()
}
```

**Step 3: Read Data**
```kotlin
fun getAllData(): List<String> {
    val list = mutableListOf<String>()
    val db = readableDatabase
    val cursor = db.rawQuery("SELECT * FROM users", null)
    while (cursor.moveToNext()) {
        val name = cursor.getString(1)
        list.add(name)
    }
    cursor.close()
    return list
}
```

**Step 4: Use in Activity**
```kotlin
val dbHelper = DatabaseHelper(this)
dbHelper.insertData("Ram", 22)
val data = dbHelper.getAllData()
```

---

## Q.5(b) Shared Preferences in Android

- **SharedPreferences** stores small data as **key-value pairs** on the device permanently.
- Data is saved even when app is closed or phone is restarted.
- Used for: saving login status, user settings, theme preferences.

### Storing Data:
```kotlin
val sharedPref = getSharedPreferences("AppPrefs", Context.MODE_PRIVATE)
val editor = sharedPref.edit()
editor.putString("username", "giet@gmail.com")
editor.putInt("age", 21)
editor.putBoolean("isLoggedIn", true)
editor.apply()   // Always call apply() to save
```

### Reading Data:
```kotlin
val sharedPref = getSharedPreferences("AppPrefs", Context.MODE_PRIVATE)
val username   = sharedPref.getString("username", "Not Found")
val age        = sharedPref.getInt("age", 0)
val isLoggedIn = sharedPref.getBoolean("isLoggedIn", false)

println("Username: $username")    // giet@gmail.com
println("Age: $age")              // 21
println("Logged In: $isLoggedIn") // true
```

### Deleting Data:
```kotlin
editor.remove("username")  // Remove a specific key
editor.clear()             // Remove all saved data
editor.apply()
```

### Practical Use Case — Auto Login:
```kotlin
// On Login Button Click — save login status
editor.putBoolean("isLoggedIn", true)
editor.apply()

// On App Start — check if already logged in
val isLoggedIn = sharedPref.getBoolean("isLoggedIn", false)
if (isLoggedIn) {
    startActivity(Intent(this, HomeActivity::class.java))
}
```

---

## Q.5(c) Types of Menus in Android + Steps to Create Option Menu

### Types of Menus:

**1. Options Menu**
- Appears in the **top Action Bar / Toolbar**.
- Most commonly used menu.
- Accessed by tapping the 3-dot (⋮) icon.

**2. Context Menu**
- Appears when user **long-presses** on a view (like a list item).
- Shows options related to that specific item.

**3. Popup Menu**
- Appears as a **dropdown list** attached near a button.
- Used for quick options.

---

### Steps to Create Option Menu:

**Step 1: Create menu XML file**

Create `res/menu/menu_main.xml`:
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/action_home"     android:title="Home"/>
    <item android:id="@+id/action_settings" android:title="Settings"/>
    <item android:id="@+id/action_logout"   android:title="Logout"/>
</menu>
```

**Step 2: Override onCreateOptionsMenu in Activity**
```kotlin
override fun onCreateOptionsMenu(menu: Menu?): Boolean {
    menuInflater.inflate(R.menu.menu_main, menu)
    return true
}
```

**Step 3: Handle Item Clicks with onOptionsItemSelected**
```kotlin
override fun onOptionsItemSelected(item: MenuItem): Boolean {
    return when (item.itemId) {
        R.id.action_home -> {
            Toast.makeText(this, "Home clicked", Toast.LENGTH_SHORT).show()
            true
        }
        R.id.action_settings -> {
            Toast.makeText(this, "Settings clicked", Toast.LENGTH_SHORT).show()
            true
        }
        R.id.action_logout -> {
            Toast.makeText(this, "Logged out", Toast.LENGTH_SHORT).show()
            true
        }
        else -> super.onOptionsItemSelected(item)
    }
}
```

---

## Q.5(d) Android App — Store Employee Data in SQLite

### DatabaseHelper.kt
```kotlin
class DatabaseHelper(context: Context) :
    SQLiteOpenHelper(context, "EmployeeDB.db", null, 1) {

    override fun onCreate(db: SQLiteDatabase) {
        val createTable = """
            CREATE TABLE employee (
                empno       INTEGER PRIMARY KEY,
                name        TEXT,
                department  TEXT,
                designation TEXT
            )
        """.trimIndent()
        db.execSQL(createTable)
    }

    override fun onUpgrade(db: SQLiteDatabase, oldV: Int, newV: Int) {
        db.execSQL("DROP TABLE IF EXISTS employee")
        onCreate(db)
    }

    // Insert Employee
    fun insertEmployee(empno: Int, name: String, dept: String, desig: String): Boolean {
        val db = writableDatabase
        val values = ContentValues()
        values.put("empno", empno)
        values.put("name", name)
        values.put("department", dept)
        values.put("designation", desig)
        val result = db.insert("employee", null, values)
        db.close()
        return result != -1L
    }

    // Read All Employees
    fun getAllEmployees(): List<String> {
        val list = mutableListOf<String>()
        val db = readableDatabase
        val cursor = db.rawQuery("SELECT * FROM employee", null)
        while (cursor.moveToNext()) {
            val empno = cursor.getInt(0)
            val name  = cursor.getString(1)
            val dept  = cursor.getString(2)
            val desig = cursor.getString(3)
            list.add("EmpNo: $empno | Name: $name | Dept: $dept | Desig: $desig")
        }
        cursor.close()
        return list
    }
}
```

### MainActivity.kt
```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val db = DatabaseHelper(this)

        // Insert sample employees
        db.insertEmployee(101, "Ram Kumar",  "IT",  "Developer")
        db.insertEmployee(102, "Sita Devi",  "HR",  "Manager")
        db.insertEmployee(103, "Laxman Rao", "CSE", "Analyst")

        // Fetch and display all employees
        val employees = db.getAllEmployees()
        val tvResult = findViewById<TextView>(R.id.tvResult)
        tvResult.text = employees.joinToString("\n\n")
    }
}
```

### activity_main.xml
```xml
<ScrollView ...>
    <LinearLayout android:orientation="vertical" android:padding="20dp" ...>
        <TextView
            android:id="@+id/tvResult"
            android:textSize="16sp"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>
    </LinearLayout>
</ScrollView>
```

**Output displayed:**
```
EmpNo: 101 | Name: Ram Kumar  | Dept: IT  | Desig: Developer
EmpNo: 102 | Name: Sita Devi  | Dept: HR  | Desig: Manager
EmpNo: 103 | Name: Laxman Rao | Dept: CSE | Desig: Analyst
```

---

*End of Answer Sheet — SET 2*
