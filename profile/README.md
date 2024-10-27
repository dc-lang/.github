# DC
```cpp
extern i32 getchar;

context main i32 argc str* argv -> i32;
  "This is a programming language, written in C++ using llvm, for small scripts/programs"
  "You can use standard C library"
  declare i32 c;
  getchar() -> c;
  "Or DC Standard library"
  declare i32 num;
  parse_int("69") -> num;
  "Use memory allocations when needed"
  declare str my_str;
  alloc(64) -> my_str; "Allocate 64 bytes for my_str"
  "Code with my_str here"
  delete(my_str); "Delete when needed"
  "DC Also supports expressions"
  declare i32 expr_res;
  assign expr_res = 5 * (2 + 2); "tho you can't use functions in expressions, I could implement that but that's too hard for me"
  printf("%d\n", expr_res);
  "If statements, it's not a programming language without them!"
  if argc == 3;
    printf("argc == 3\n");
  elif argc == 4;
    printf("argc == 4\n");
  else;
    printf("argc != 3, argc != 4\n");
  fi;
  "DC Provides a crash system, kinda like panics in rust, or exceptions in c++, in DC they are called collapses"
  parse_int("69something") -> num; "This will cause a collapse"
  collapse("Manual collapse"); "Or you can manually cause a collapse"
  return 0;
context;

"Define some contexts!"
context some_context -> void;
  "Because of DC name mangling this function in llvm IR would be called _Z11somecontext4aout_void"
  printf("I'm in some_context now!");
  return; "Contexts in DC need to return, every time"
context;

"Disable name mangling with #nomangle"
context #nomangle some_nomangled_context -> void;
  printf("I'm in some_nomangled_context!");
  return;
context;
```
### Tools without which this project wouldn't be possible
- [LLVM](https://llvm.org/): Basically for the compiler, absolutely love using it
- [IDA](https://hex-rays.com/): Really helpful for finding errors in the dc compiler
- [Ghidra](https://github.com/NationalSecurityAgency/ghidra): Alternative for IDA, been a second option when IDA didn't properly understood the generated assembly from IR
- [VSCode](https://code.visualstudio.com/): You know it, you love it, best code editor
