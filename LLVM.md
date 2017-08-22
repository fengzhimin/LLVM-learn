#### Converting a C source code to LLVM assembly
- clang -emit-llvm -S source.c -o source.ll
- clang -cc1 -emit-llvm source.c -o source.ll

#### Converting IR to LLVM bitcode
- llvm-as test.ll -o test.bc

#### Converting LLVM bitcode to target machine assembly
- llc test.bc -o test.s
- clang -S test.bc -o test.s -fomit-frame-pointer

#### Converting LLVM bitcode back to LLVM assembly
- llvm-dis test.bc -o test.ll

#### IR
- IR uses **Single-Static Assignments(SSA)**
- Code is organized as thress-address instructions
- It has an infinite number of register

#### LLVM structure
- Frontend: this includes a lexical analyzer, a syntax parser, a semantic analyzer, and the LLVM IR code generator
- IR: The LLVM IR has both human-readable(.ll) and binary-encoded representations(.bc).
- Backend: It converts LLVM IR to target-specific assembly code or object code binaries.
