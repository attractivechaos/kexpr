Kexpr is a lightweight two-file library for parsing math expressions. It
supports common math functions and works with variables. This library was
developed in 2015 as part of the klib library and is now separated into this
repo. Some of the design choices may be questionable and error checking is not
very robust, but the library is largely usable.

To use kexpr as a library, you may copy both `kexpr.h` and `kexpr.c` to your
own source code tree and call functions in the header file. Kexpr also comes
with a simple command-line interface. To compile:
```sh
gcc -O3 -Wall -std=c99 -DKE_MAIN kexpr.c -o kexpr
```
Here are some examples:
```sh
./kexpr "2+5*2"                  # output 12 (simple arithmetic)
./kexpr "2+5*exp(-1)"            # output 3.8394 (builtin functions)
./kexpr "2+5*exp(x+y)" x=-2 y=1  # output 3.8394 (variables)
./kexpr "2^1"                    # output 3 (bit operation)
```
The following examples cause parse errors:
```sh
./kexpr "5*"
./kexpr "5*exp("
./kexpr "5*exp)"
./kexpr "5*exp()"
./kexpr "5*exp(4,5)"
```
