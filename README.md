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
---
## CMAKE build
create the build directory and move into it
~~~
mkdir -p build
cd build/
~~~
Build library and install in /lib
~~~
cmake .. -DMODE=1
make
make install
~~~
Build executable and install in /bin
~~~
cd build/
cmake .. -DMODE=2
make
make install
~~~
Execute executable:
~~~
../bin/foo.x
~~~
Note: use "make rm" to clean project