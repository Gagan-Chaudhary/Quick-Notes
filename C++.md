# 🚀 C++ Learning Roadmap

## 📌 Topic 1: Basics of C++

### ✅ Introduction to C++

C++ is a powerful general-purpose programming language that supports procedural, object-oriented, and generic programming. It is widely used in system programming, game development, embedded systems, and competitive programming due to its efficiency and flexibility.

**Why use C++?**

- Performance and efficiency
- Object-oriented programming (OOP) support
- Rich standard library (STL)
- Low-level memory management capabilities

### ✅ Setting up the Environment

To start coding in C++, install an IDE and a compiler. Some common setups include:

**IDE Choices:**

- **VS Code** (lightweight, requires extensions like C/C++ from Microsoft)
- **CodeBlocks** (user-friendly, includes a compiler by default)
- **CLion** (best for large projects, paid, supports advanced refactoring)
- **Dev-C++** (simple, lightweight alternative)

**Compiler Choices:**

- GCC (GNU Compiler Collection)
- Clang (LLVM-based compiler)
- MSVC (Microsoft C++ Compiler)

### ✅ Input/Output Operations

**Basic I/O using cin and cout:**

```cpp
#include <iostream>
using namespace std;
int main() {
    int num;
    cout << "Enter a number: ";
    cin >> num;
    cout << "You entered: " << num << endl;
    return 0;
}
```

**Formatted Output using printf:**

```cpp
#include <cstdio>
int main() {
    printf("Hello, %s! Your score is %d.\n", "Alice", 90);
    return 0;
}
```

**Using scanf for Input:**

```cpp
#include <cstdio>
int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    printf("You entered: %d\n", num);
    return 0;
}
```

### ✅ Data Types and Ranges

| Data Type   | Size         | Range                                                   | Example                         |
| ----------- | ------------ | ------------------------------------------------------- | ------------------------------- |
| `int`       | 4 bytes      | -2,147,483,648 to 2,147,483,647                         | `int x = 10000;`                |
| `long int`  | 4 or 8 bytes | Depends on the system                                   | `long int y = 1000000;`         |
| `long long` | 8 bytes      | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | `long long z = 10000000000;`    |
| `float`     | 4 bytes      | ~3.4e±38                                                | `float f = 3.14f;`              |
| `double`    | 8 bytes      | ~1.7e±308                                               | `double d = 3.141592653589793;` |
| `char`      | 1 byte       | -128 to 127                                             | `char c = 'A';`                 |
| `bool`      | 1 byte       | `true (1)`, `false (0)`                                 | `bool isTrue = true;`           |

### ✅ Function Overloading

Function overloading allows multiple functions to have the same name but different parameters.

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }
string add(string a, string b) { return a + " " + b; }

int main() {
    cout << add(5, 10) << endl;
    cout << add(5.5, 2.2) << endl;
    cout << add("Hello", "World") << endl;
    return 0;
}
```

## 📌 Topic 3: Object-Oriented Programming (OOPs)

### ✅ Classes and Objects

```cpp
class Car {
public:
    string brand;
    Car(string b) { brand = b; }
    void show() { cout << "Brand: " << brand << endl; }
};
int main() { Car car1("Toyota"); car1.show(); }
```

### ✅ Inheritance

```cpp
class Parent { public: void show() { cout << "Parent"; } };
class Child : public Parent {};
```

### ✅ Polymorphism (Function Overriding)

```cpp
class Base {
public:
    virtual void show() { cout << "Base Class"; }
};
class Derived : public Base {
public:
    void show() override { cout << "Derived Class"; }
};
```

## 📌 Topic 4: Exception Handling

```cpp
#include <iostream>
using namespace std;

void divide(int a, int b) {
    if (b == 0) throw runtime_error("Division by zero not allowed");
    cout << "Result: " << a / b << endl;
}

int main() {
    try {
        divide(10, 0);
    } catch (exception &e) {
        cout << "Caught exception: " << e.what() << endl;
    }
    return 0;
}
```

## 📌 Topic 5: Standard Template Library (STL)

### ✅ Vectors

```cpp
vector<int> v = {10, 20, 30};
v.push_back(40);
cout << *min_element(v.begin(), v.end()) << endl;
```

### ✅ Maps

```cpp
map<string, int> scores;
scores["Alice"] = 90;
```

### ✅ STL Algorithms

```cpp
sort(v.begin(), v.end());
binary_search(v.begin(), v.end(), 30);
reverse(v.begin(), v.end());
accumulate(v.begin(), v.end(), 0);
```

## 📌 Topic 6: Competitive Programming & DSA

### ✅ Sliding Window Technique

```cpp
int maxSumSubarray(vector<int>& arr, int k) {
    int sum = 0, maxSum = 0;
    for (int i = 0; i < k; i++) sum += arr[i];
    maxSum = sum;
    for (int i = k; i < arr.size(); i++) {
        sum += arr[i] - arr[i - k];
        maxSum = max(maxSum, sum);
    }
    return maxSum;
}
```

This version includes additional details, examples, and deep dives into STL and OOPs concepts. Let me know if you need further refinements!
