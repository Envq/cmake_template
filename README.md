# A simple cmake template


## GCC Static Library linking
Fixing the path of files (e.g. "../include/mylib.hpp" for mylib.cpp)
~~~
g++ -o foo main.cpp src/mylib.cpp
./foo
~~~

## GCC Shared Library linking
Fixing the path of files (e.g. "../include/mylib.hpp" for mylib.cpp)
~~~
g++ -fpic -shared -o libfoo.so src/mylib.cpp
g++ -o foo main.cpp -L. -lfoo
./foo
~~~