ilint
=====

`ilint` is a small POSIX shell script that brute-force searches for
redudant C/C++ includes by deleting include lines one at a time and testing
if it breaks the build.

To run, `cd` to the directory where your makefile or build script is and run
`ilint PATH` where `PATH` is the path to the source directory or source file
that you want to check.
If `PATH` is not specified it will default to the current directory.
All C/C++ files and header files in `PATH` will be checked.
If your build command is non-standard, you can set the `BUILD` environment
variable to your build command.

Typically there will be some cases where an include is flagged as redundant,
but it is appropriate to keep it according to the "include what you use"
paradigm. This can happen when a header file includes other header files, which
occurs in the standard library. This issue can be minimized by using
[Pike style](https://www.lysator.liu.se/c/pikestyle.html) which says
"include files should never include include files".
