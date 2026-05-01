# Android App Development using Kotlin – Complete Exam Answers

## PART A (Short Answers)

### 1. Elvis Operator
Elvis operator (?:) is used to handle null values.
Example:
val name = input ?: "Default"

### 2. Class vs Data Class
Class: General purpose
Data Class: Used to store data, auto generates equals(), hashCode()

### 3. Fragment
Fragment is a part of UI inside an Activity.

### 4. RecyclerView
Used to display large data efficiently.

### 5. Real-time Database
Firebase database that updates data instantly.

---

## PART B (Long Answers)

### Kotlin Features
- Simple and concise
- Null safety
- Interoperable with Java
- Smart casting

### Inheritance Example
open class Animal {
    fun sound() {
        println("Animal sound")
    }
}

class Dog: Animal()

### Higher Order Function
fun operate(a:Int, b:Int, op:(Int,Int)->Int):Int {
    return op(a,b)
}

### Android Architecture
Layers:
- Linux Kernel
- Libraries
- Application Framework
- Applications

### Activity Lifecycle
onCreate → onStart → onResume → onPause → onStop → onDestroy

### Intent Types
- Explicit Intent
- Implicit Intent

### SQLite Example
Store data using database tables.

### SharedPreferences
Used to store small data like settings.

---

## Conclusion
This file covers all important exam questions in simple format.
