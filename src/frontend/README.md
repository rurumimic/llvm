# Frontend

- [clang/tools/driver/cc1_main.cpp](https://github.com/llvm/llvm-project/blob/main/clang/tools/driver/cc1_main.cpp)
- [clang/lib/Frontend/FrontendAction.cpp](clang/lib/Frontend/FrontendAction.cpp)
- [clang/lib/Frontend/FrontendAction.cpp](https://github.com/llvm/llvm-project/blob/main/clang/lib/Frontend/FrontendAction.cpp)

```bash
clang -Xclang -ast-dump -fsyntax-only hello.c
clang -cc1 -ast-dump hello.c

|-VarDecl 0x806a79ba0 <line:486:1, col:12> col:12 __isthreaded 'int' extern
`-FunctionDecl 0x806a79e30 <hello.c:3:1, line:7:1> line:3:5 main 'int (int, char **)'
  |-ParmVarDecl 0x806a79c20 <col:10, col:14> col:14 argc 'int'
  |-ParmVarDecl 0x806a79d10 <col:20, col:31> col:26 argv 'char **':'char **'
  `-CompoundStmt 0x806a7c048 <line:4:1, line:7:1>
    |-CallExpr 0x806a79fc0 <line:5:3, col:27> 'int'
    | |-ImplicitCastExpr 0x806a79fa8 <col:3> 'int (*)(const char *, ...)' <FunctionToPointerDecay>
    | | `-DeclRefExpr 0x806a79ee0 <col:3> 'int (const char *, ...)' Function 0x806a685a8 'printf' 'int (const char *, ...)'
    | `-ImplicitCastExpr 0x806a7c000 <col:10> 'const char *' <NoOp>
    |   `-ImplicitCastExpr 0x806a79fe8 <col:10> 'char *' <ArrayToPointerDecay>
    |     `-StringLiteral 0x806a79f38 <col:10> 'char [15]' lvalue "Hello, World!\n"
    `-ReturnStmt 0x806a7c038 <line:6:3, col:10>
      `-IntegerLiteral 0x806a7c018 <col:10> 'int' 0
```

```bash
clang hello.c -###

FreeBSD clang version 13.0.0 (git@github.com:llvm/llvm-project.git llvmorg-13.0.0-0-gd7b669b3a303)
Target: x86_64-unknown-freebsd13.1
Thread model: posix
InstalledDir: /usr/bin
 "/usr/bin/clang" "-cc1" "-triple" "x86_64-unknown-freebsd13.1" "-emit-obj" "-mrelax-all" "--mrelax-relocations" "-disable-free" "-disable-llvm-verifier" "-discard-value-names" "-main-file-name" "hello.c" "-mrelocation-model" "static" "-mframe-pointer=all" "-fno-rounding-math" "-mconstructor-aliases" "-munwind-tables" "-target-cpu" "x86-64" "-tune-cpu" "generic" "-debugger-tuning=gdb" "-fcoverage-compilation-dir=/src/helloworld" "-resource-dir" "/usr/lib/clang/13.0.0" "-fdebug-compilation-dir=/src/helloworld" "-ferror-limit" "19" "-fgnuc-version=4.2.1" "-fcolor-diagnostics" "-faddrsig" "-D__GCC_HAVE_DWARF2_CFI_ASM=1" "-o" "/tmp/hello-8c3352.o" "-x" "c" "hello.c"
 "/usr/bin/ld" "--eh-frame-hdr" "-dynamic-linker" "/libexec/ld-elf.so.1" "--hash-style=both" "--enable-new-dtags" "-o" "a.out" "/usr/lib/crt1.o" "/usr/lib/crti.o" "/usr/lib/crtbegin.o" "-L/usr/lib" "/tmp/hello-8c3352.o" "-lgcc" "--as-needed" "-lgcc_s" "--no-as-needed" "-lc" "-lgcc" "--as-needed" "-lgcc_s" "--no-as-needed" "/usr/lib/crtend.o" "/usr/lib/crtn.o"
```

