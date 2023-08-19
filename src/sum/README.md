# Sum

## Build

### One Command

```bash
clang main.c sum.c -o sum
```

### Breakdown

#### Bitcode

```bash
clang -emit-llvm -c main.c -o main.bc
clang -emit-llvm -c sum.c -o sum.bc
```

```bash
clang -flto -c main.c -o main.bc
clang -flto -c sum.c -o sum.bc
```

to asm:

```bash
clang -emit-llvm -S -c main.c -o main.ll
clang -emit-llvm -S -c sum.c -o sum.ll
```

#### Object file

##### obj → system linker

1. llc: bc → obj
2. clang (system linker): obj → exec

```bash
llc -filetype=obj main.bc -o main.o
llc -filetype=obj sum.bc -o sum.o
clang main.o sum.o -o sum
```

##### linker → obj → system linker

1. llvm-link: 2 bc → 1 bc 
2. llc: bc → obj
3. clang (system linker): obj → exec

```bash
llvm-link main.bc sum.bc -o sum.linked.bc
llc -filetype=obj sum.linked.bc -o sum.linked.o
clang sum.linked.o -o sum
```

