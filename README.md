# cmake template
A simple cmake template for build project with shared library


## GCC Static Library linking
Fixing the path of files (e.g. "../include/mylib.hpp" for mylib.cpp)
~~~
g++ -o foo examples/main.cpp mylib/src/mylib.cpp
./foo
~~~

## GCC Shared Library linking
Fixing the path of files (e.g. "../include/mylib.hpp" for mylib.cpp)
~~~
g++ -fpic -shared -o libfoo.so mylib/src/mylib.cpp
g++ -o foo examples/main.cpp -L. -lfoo
./foo
~~~
---
## CMAKE build
create the build directory and move into it
~~~
mkdir -p build
cd build/
cmake ..
../bin/example.x
~~~
Note: use "make rm" to clean project