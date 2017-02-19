Version 2.0.0:
- OCD got the best of me, fixed naming convention (isempty(...) -> is_empty(...)).
- Got rid of 'vec_newlen(...)' and 'vec_newsize(...)'. Replaced with 'vec_new_cap(...)' which does the same exact thing, but is now more explicit in its intentions.
- Since most functions in the API can't return an error code, error handling has been rather poor. To remedy this, rather than raising a SIGSEGV, the function will exit immediately, set errno to 'ENOMEM' (out of memory), and leave the parameters left unchanged.


Version 1.1.1:
- Merged pull request by 'Lakhdar Slaim': now using '_vec_hdr_size' instead of 'sizeof(size_t) * 3'.
- Minor bug fix regarding 'vec_insert(...)' interaction with an index equal to the vec's length.


Version 1.1.0:
- ‘VEC_CALLOC’ is now used instead of ‘VEC_MALLOC/memset(, 0, )’. Like usual, ‘VEC_CALLOC’ can be defined by the user.
- ‘vec_reserve’ and ‘vec_shrink’ simply do nothing (rather than raising a ‘SIGSEGV’) if they cannot undergo their respective 
  operations.
- Vector growth rate reduced from 2 to 1.5 to be on par with “the golden ratio.”
- There is no need to define ‘VEC_IMPLEMENTATION’ now for the implementation to be included in the respective file. 
  The implementation is automatically included. This was decided because every function is either a macro or inlined. 
  Note: you still can define the optional flags, and they must be defined everywhere you include the header if you want the 
  functionality across multiple translation units.
- Minor bug fixes regarding API interaction with ‘VEC_MAX_PREALLOC’.
