Common technical interview questions and answers, in my own words.

### Table of Contents

[Explain the difference between stack and heap memory allocation in C++. How do you decide which to use?](#sid_1)

[What are smart pointers in C++? Describe the differences between unique_ptr, shared_ptr, and weak_ptr](#sid_2)

[How would you detect and fix memory leaks in a large C++ application?](#sid_3)

<a id="sid_1"></a>
### Explain the difference between stack and heap memory allocation in C++. How do you decide which to use?
Auto variables, fix size buffers are allocated in stack. It is done during compiling time.
Heap is used for dynamically allocating memory. In c++, new/malloc. 

Extended: free memory, access speed, size limitation, etc.

<a id="sid_2"></a>
### What are smart pointers in C++? Describe the differences between unique_ptr, shared_ptr, and weak_ptr.
If you alloca memory but never free, it will cause memory leak. When using smart pointer, memory will be automatically freed after the variable is out of scope.
unique_ptr is used to replace c++ keynew new or malloc in c. shared_ptr use reference count. The reference number increases when is accquired, decreases when is released, memory is freed when the reference number becomes 0.
weak_ptr is a reference to the original smart pointer.

Extended: if not use.

<a id="sid_3"></a>
### How would you detect and fix memory leaks in a large C++ application?
If the memory leak in the legacy code, you can run the preformance monitor to detect the memory growing. You can disable some functions or comment out code to narrow down.
A good, test driven code should use reference count ( shared pointer) for dynamic memory allocation. It will prevent the memory leak and when it happenes, print the refernce number in the log for debugging.

Extended: what's overflow, what's the differences between these two.

<a id='sid_4'></a>
### How do move semantics work in C++11 and later? When would you use them in a streaming application?

