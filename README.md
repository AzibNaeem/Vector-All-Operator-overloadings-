Vector Class Implementation In C++

This repository contains a simple implementation of a dynamic array-like structure called `Vector` in C++. The `Vector` class mimics some of the functionalities of the `std::vector` from the C++ Standard Library, providing dynamic resizing, element access, and modification.

## Overview

The `Vector` class is designed to manage a collection of integers, allowing for dynamic resizing as elements are added or removed. The class includes various methods for interacting with the vector, such as adding elements, removing elements, and accessing elements by index.

### Key Features

- **Dynamic Resizing:** The vector automatically resizes itself when more capacity is needed, doubling its capacity when full and halving it when less than half full.
- **Element Access:** Provides methods to access elements at the front, back, and by index.
- **Comparison Operator:** Allows for comparison between two `Vector` instances.
- **Memory Management:** Manages its own memory using raw pointers, with appropriate allocation and deallocation.

### Class Members

- **Private Members:**
  - `int *elements;` - Pointer to the dynamic array holding the elements.
  - `int size_;` - Current number of elements in the vector.
  - `int capacity_;` - Current capacity of the vector.

### Public Methods

- **Constructors & Destructor:**
  - `Vector()` - Initializes an empty vector with a default capacity of 5.
  - `~Vector()` - Destructor that cleans up the allocated memory.
  
- **Element Access:**
  - `int& operator[](int index)` - Overloaded subscript operator for accessing elements by index.
  - `int& front()` - Returns a reference to the first element.
  - `int& back()` - Returns a reference to the last element.
  
- **Size and Capacity:**
  - `int size() const` - Returns the current size of the vector.
  - `int capacity() const` - Returns the current capacity of the vector.
  - `bool empty() const` - Checks if the vector is empty.
  
- **Modifiers:**
  - `void push_back(int value)` - Adds an element to the end of the vector, resizing if necessary.
  - `void pop_back()` - Removes the last element, resizing if the size drops below half of the capacity.
  - `void insert(int index, int value)` - Inserts an element at the specified index, shifting elements as needed.
  
- **Operators:**
  - `bool operator==(const Vector& other) const` - Compares two vectors for equality.
  - `Vector& operator=(const Vector& other)` - Assignment operator to copy another vector.
  
- **Iterators:**
  - `int* begin() const` - Returns a pointer to the first element.
  - `int* end() const` - Returns a pointer to the element following the last element.

### Memory Management Methods

- **Private Methods:**
  - `void increase_cap()` - Doubles the capacity of the vector when the size exceeds capacity.
  - `void decrease_cap()` - Halves the capacity of the vector when the size falls below half of the capacity.

### Example Usage

```cpp
int main() {
    Vector v;
    v.push_back(10);

    v.insert(1, 15); // Insert 15 at index 1
    v.insert(2, 20);
    v.insert(3, 30);

    for (int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";
    }
    // Output: 10 15 20 30

    return 0;
}
```

### Notes

- **Memory Management:** The class manages its own memory and ensures that resources are properly cleaned up in the destructor. However, it does not use smart pointers, which might be a consideration for more complex implementations.
- **Error Handling:** The subscript operator does not throw an exception or handle out-of-bounds
