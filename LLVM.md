#### Converting a C source code to LLVM assembly
- clang -emit-llvm -S source.c -o source.ll
- clang -cc1 -emit-llvm source.c -o source.ll

#### Converting IR to LLVM bitcode
- llvm-as test.ll -o test.bc

#### Converting a C source code to LLVM bitcode
- clang -emit-llvm -c main.c -o main.bc
- The -emit-llvm flag tell clang to generate either the LLVM bitcode or LLVM assembly files,depending on the presence of the -c or -S flag.
- -emit-llvm together with the -c flag tells clang to generate an object file int the LLVM bitcode format.
- -emit-llvm together with the -S flag tells clang to generate an LLVM assembly files.

#### Converting LLVM bitcode to target machine assembly
- llc test.bc -o test.s
- clang -S test.bc -o test.s -fomit-frame-pointer

#### Converting LLVM bitcode back to LLVM assembly
- llvm-dis test.bc -o test.ll

#### Linking LLVM bitcode
- llvm-link test1.bc test2.bc -o output.bc

#### Executing LLVM bitcode
- lli output.bc

#### Converting LLVM bitcode to executable program
- method one
	- llc -filetype=obj main.bc -o main.o
	- llc -filetype=obj sum.bc -o sum.o
	- clang main.o sum.o -o sum
- method two
	- llvm-link main.bc sum.bc -o sum.linked.bc
	- llc -filetype=obj sum.link.bc -o sum.linked.o
	- clang sum.link.o -o sum
- -filetype=obj: specifies an object file output instead of the target assembly file

#### opt
- This is a tool that is aimed at optimizing a program at the IR level.

#### llvm-mc
- This tool is able to assemble instructions and generate object files for several object formats such as ELF,MachO,and PE.

#### IR
- IR uses **Single-Static Assignments(SSA)**
- Code is organized as thress-address instructions
- It has an infinite number of register

#### LLVM structure
- Frontend: this includes a lexical analyzer, a syntax parser, a semantic analyzer, and the LLVM IR code generator
- IR: The LLVM IR has both human-readable(.ll) and binary-encoded representations(.bc).
- Backend: It converts LLVM IR to target-specific assembly code or object code binaries.
