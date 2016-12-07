# Vec
The Vec library is meant to add generic and fast vectors to C (and is compatible with C++). A "vec" in a sense is a fat pointer to anything. The Vec API not only provides ways of creating, destroying, and manipulating generic fat pointers, but also functionality common to the traditional C++ vector type. Refer to the greatly commented vec.h for details.


## Usage
This library is self contained in one single header file and can be used either in header only mode or in implementation mode. The header only mode is used by default when included and allows including this header in other headers and does not contain the actual implementation. 

The implementation mode requires to define the preprocessor macro VEC_IMPLEMENTATION in *one* .c/.cpp file before #including this file, e.g.:
```C
#define VEC_IMPLEMENTATION
#include "vec.h"
```
Also optionally define the symbols listed under the "OPTIONAL DEFINES" section in the header *only* in implementation mode if you want to use additional functionality or need more control over the library. 


## API
The following is a list of available functions (all prefixed with "vec_"):
- new
- newlen, newsize
- dup
- free
- cap
- len, size
- isempty
- clear
- push
- pop
- insert
- remove
- reserve
- shrink


## Example
