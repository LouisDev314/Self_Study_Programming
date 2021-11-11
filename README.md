# Self_Study_Programming
My self-study journey on programming

---------------------------------

**<ins>Language: C++</ins>**

**<ins>Intro</ins>**

- Direct control over hardware
- Source code -> Compiler -> Machine code (for CPU to execute)
  - Compile -> Run
- Fast code & performs well
  - Faster than languages use VM (C#, Java, etc.) because it compiles code directly to machine code based on compiler for specific platform
  - Source code -> Intermediate code -> (Runtime) VM -> convert to machine code base on platform
  - Compile -> Translate (Runtime) -> Run
- Can run on multiple platforms based on the compiler (x64/ x86 windows or MacOS) that output machine code for platforms

**<ins>HelloWorld in C++</ins>**

- ```#include <iostream>``` is a preprocessor statement (w/ hash)
  - Compiler preprocess all preprocessors before compilation of other source code
  - [include] will find a file and copy & paste everything in the file to the place

- Main Function: the entry point of C++ program (execution start with the first line of code in main function and go line by line)
  - Doesn't need return statement despite the return type [int] (assume return 0)

- [<<] left shift (overloaded) operator in ```std::cout <<```
  - Overloaded: parameters XOR Override: contents
  - Push statements one by one to the cout function

- ```std::cin.get()``` is to wait for pressing Enter to continue (use as a pause)

**<ins>Workflow of C++</ins>**

- File is just a way to feed compiler with source code
- Solution Configuration: rules when build projects
- Solution platform: platform compiler is targeting

****** Header files do not get compiled in compile time (compilation priority), just cpp files (translation unit)

- CPP files compiled individually -> Object files -> Linker to link obj files -> exe file (common binary)
- Declaration: state the function name
- Definition: what the function is
- Function Signature: input and output type
- As long as a declaration is made in a cpp file, when it comes to linker, even without definition in the same cpp file, the linker will still find the definition of the function
  - Unresolved External Symbol: linking error occurs when linker cannot find the definition of the function
- ```#define INTEGER int``` do a search for INTEGER and replace with int
- Constant Folding: simple math calculation can be done in compile time
  - eax: return register
  - imul: multiplication
  - a mov can be saved by return constant calculation

**!!!** When the same function definition appears in single cpp file -> compile error

**!!!** When the same definition appears in different cpp file -> linking error

**<ins>Variables</ins>**

- *char* - 1 byte
- *short* - 2 bytes
- *int* - 4 bytes
- *long* - 4 bytes
- *float* - 4 bytes
- *double* - 8 bytes
- *long long* - 8 bytes
- *unsigned* - double bytes in non-negative
- *bool* - 0 = false; any other number = true (1 for bool)
  - cost 1 bit but only bytes can be accessed, so 1 byte

**<ins>Header Files</ins>**

- To declare certain type of functions to be used throughout the program (just declaration stored to tell the program what functions exist & prevent overlap definition)
  - When there are functions that are defined somewhere and need to be used in many places, header file can save some time from keep copy & paste a bunch of code
- *#include* absolute/standard library header files use <>; *#include* relative header files use ""
- ```#pragma once``` means only include this file once: incase a header file included another header file but the other header file is also being included in the same translation unit

**<ins>Pointers</ins>**

- <ins>Heap</ins> is the memory space for C++
- Pointer is an int variable that holds specific memory address (can point to new address)
- Double pointer means a pointer pointing to the address of another pointer that is pointing to a variable's address
- ```&var``` to retrieve the memory address of that var
  - Can be (double*) &var
- ```ptr*``` is dereferencing the pointer -> accessing the data it points to
- This is the pointer that points to the beginning of the block of memory
  ```char* ptr = new char[8]```
- Function ```memset``` takes in a pointer to the beginning of a block of memory, a value, bytes it should fill
- ```delete[] ptr``` after using to free up memory space

**<ins>References</ins>**

- Reference is the reference of an existing variable (share the same address)
  ```c++
  int& ref = a
  ```

- Does not occupy new memory space
  - change ref -> change the original variable's data

- After reference is declared, cannot change what it references
- Pass it as parameter to modify the data directly & save memory from copying the data

**<ins>Classes</ins>**

- Functions inside classes are called *Methods*
- Variables are private initially
- *class* normally used for inheritances
- *struct* is the same as class except the variables are public initially

**<ins>Static & Extern</ins>**

- ```inline```similar to static but return the same address in different cpp files when *static* returns different address
- ```static``` functions are only declared to be used in that specific cpp file, invisible for linker
  - can avoid conflict if there are different definitions of a function/variable

- ```static``` method can be called without class initialization & do not have access to a class instance
- Global ```static``` variable:
  - scope: only visible to that transition unit 
  - will look for definition only in the transition unit when linking

- Class ```static``` variable:
  - scope: become global scope
  - only one instance of the variable will be created across all class instances
  - only visible to that class (need to be accessed by ```Class::Var```)
- ```extern``` looks for the definition in an external translation unit
- Lifetime: until the program terminates
- Non-static method automatically take in a class instance as a parameter while ```static``` method does not (so it can't access non-static variables because that belong to the class and there is no class instance passed in as parameter)

**<ins>Singleton</ins>**

- A class that should only has 1 instance exists

- ```c++
  class Singleton {
  public:
  	static Singleton& get() {
  		static Singleton instance;
  		return instance;
  	}
  }
  ```

**<ins>Enums</ins>**

- A set/type to give a name to an int (semantic use), and the enum type of variable can only be modified with the same enum variable

- Start at 0 since the 1st variable/The next few variables are the increment of the previous one

- Can be fixed to a certain variable type

  ```c++
  enum Example : unsigned char
  ```

- Allows duplicated variable name for different type

  ```c++
  enum Example {
  	INIT, END
  };
  int main() {
  	Example e1 = INIT; // e1 = 0
      float INIT = 1.0;  // valid
  }
  ```

**<ins>Constructor</ins>**

- C++ has a default constructor for a class/struct
- 
- *Destructor*
  - C++ has a default destructor for a class/struct -> auto activate when out of scope

**<ins>Inheritance</ins>**

- 
