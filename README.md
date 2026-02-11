# How to create and ship your own third-party static library in C language?

## Source Code Structure
```
xyz/
├── include/
│   └── xyz.h
├── lib/
└── src/
    └── xyz.c
```

### Explanation
`xyz.h` resides under the `include` directory and it is nothing but kind of an interface, it contains singature of functions and other include stuff, it also contains some boilerplate code like this:
```
#ifndef XYZ_H
#define XYZ_H
.
.
bla bla bla
.
.
#endif
```

`xyz.c` resides under the `src` directory and it is the actual implementation of the functions defined in `xyz.h`

`lib` folder remains empty for now and will be used later


## Converting code into a library

Step 1: Create an object file from your source code.
```
gcc -I./path/to/xyz/include -c path/to/xyz/src/xyz.c -o path/to/xyz/src/xyz.o
```

Step 2: Archive the object
```
ar rcs path/to/xyz/lib/libxyz.a path/to/xyz/src/xyz.o
```

## Shipping the library
```
xyz-lib-vx.y.z/
├── include/
│   └── xyz.h       <-- The Interface (Header)
├── lib/
│   └── libxyz.a    <-- The Binary (Static Library)
├── README.md        <-- Documentation
└── LICENSE          <-- Legal stuff
```
