# Vec
The Vec library is meant to add generic and fast vectors to C (and is compatible with C++). A "vec" in a sense is a fat pointer to anything. The Vec API not only provides ways of creating, destroying, and manipulating generic fat pointers, but also functionality common to the traditional C++ vector type. Refer to the greatly commented header file for details.


## Usage
This library is self contained in one single header file and can be used by simply #including the 'vec.h' file, e.g.:
```C
#include "vec.h"
```
Also optionally define the symbols listed in the header's subtitled section "OPTIONAL DEFINES" before the #include if you want to use additional functionality or need more control over the library. 


## API
The following is a list of available functions (all prefixed with "vec_"):
- new
- new_cap
- dup
- free
- cap
- len, size
- is_empty
- clear
- push
- pop
- insert
- remove
- swap
- reserve
- shrink


## Example
```C
#include <stdlib.h>
#include <stdio.h>


#define VEC_PRIVATE
#include "vec.h"


struct matrix {
	size_t row;
	size_t col;
	double value;
};


void do_something(struct matrix *ptr) {
	for (size_t c = 0; c < vec_len(ptr); ++c) {
		printf(
			"Index: %zd, Row: %zd, Col: %zd, VecCap: %zd, VecLen: %zd, Value: %.3f\n",
			c, ptr[c].row, ptr[c].col, vec_cap(ptr), vec_len(ptr), ptr[c].value
		);
	}
}


int main(void) {
	struct matrix *foo = vec_new(sizeof(struct matrix));
	
	{
		struct matrix bar = { 1, 1, 1.125 };
		for (int c = 0; c < 10; ++c) {
			vec_push(foo, bar);
			
			if (bar.col == 5) {
				++bar.row;
				bar.col = 1;
			} else {
				++bar.col;
			}

			bar.value *= bar.value;
		}
	}

	do_something(foo);
	vec_free(foo);

    return 0;
}
```
