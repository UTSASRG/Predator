Predator - Predictive False Sharing Detection
=============================================

Usage Manual:

Step 1: entering into the "runtime" directory, and execute "make" command. 
This will generate the "./libdefault64.so" there. 

Step 2: compiling the compiler. We should download the source code of llvm. Currently, Predator 
is only supported the llvm-3.2 version. 
After that, we could patch the original llvm file. After the compilation, we will generate a new 
version of llvm, which will be used to compile applicatations we would like to detect false sharing issues. 

Step 3: compiling the applications. 
For instance, we could use the following command:
clang -Wl,$PATH/libdefault64.so -finstrumenter -g -O0 -o test mytest.c

That is, the "test" binary will be the one with the intrumentation. 

Step 4: running the applications. 
You need to make sure that libdefault64.so is on the default path. If not, please use 
LD_LIBRARY_PATH to set up it. 
Then you can run it and the false sharing will print on the screen. 

 
