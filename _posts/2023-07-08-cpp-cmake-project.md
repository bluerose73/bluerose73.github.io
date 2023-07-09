---
title: "A Very Gentle Introduction to C++ CMake Project"
published: true
---

🚧 This Post is under Construction 🚧

When I was new to C++, like many beginners, I coded [the entire program in a single source file](https://github.com/bluerose73/Amazon-chess). It took me 3 years to finally figure out how to make a "project" with multiple source files, a meaningful directory structure, and an automated build process. I found that beginner-level C++ "project structure" tutorials are surprisingly few on the internet, so I wrote this post in hope it would help C++ beginners like me in the past.

This post is intended for C++ beginners who are able to write small programs of 50~200 lines (like solving problems in LeetCode), and want to build something bigger.

After reading this post, you will be able to
- Split your code into multiple sources and headers
- Elegantly arrange the files into a tree structure
- Automate build process with CMake
- Power up your project with third-party libraries

## Sources and Headers

### The C++ Way

### The C Way

## Project Directory Structure

When you have many sources and headers, say, more than 20 files, you certainly don't want to put them all in the same folder, because the folder gets messy and it can be difficult to find the file you want. You want to arrange them in a meaningful tree structure, so that the code belonging to the same functional group stays in the same folder.

C++ project layout does not have a universal convention. I find myself comfortable with the project structrue below.

```shell
repo-name/
├── project-name/       # usually the same as repo-name
│   ├── my-package/
│   │   ├── source.cpp
│   │   ├── header.h
│   │   └── CMakeLists.txt
│   ├── app.cpp
│   └── CMakeLists.txt
├── thirdparty/
│   ├── library1/
│   ├── library2/
│   └── CMakeLists.txt
├── CMakeLists.txt
└── README.md
```

## Building with CMake

## Using Third-Party Libraries

### Include Source

A straightforward way to use a third-party library is adding its source code into your project. This approach is especially easy when the library is also a CMake project. All you need to do is copy the entire library code base to ``thirdparty`` directory, and add one line to your ``CMakeLists.txt``.

#### CMake Project


If the library is not a CMake project, you have to write the build files on your own. Typically it isn't worth your time, but there is an exception: single-header libraries.

#### Single-Header Library

### Include Built Libraries

Sometimes the build process becomes too long, or the source code is not available (like for closed-source libraries). In these cases, you can include headers and pre-built library files instead.

### Install Libraries System-Wide

Another approach is install the libraries to your computer, instead of putting it in a project. The advantage is nothing is added to your code repository, so the repo size stays small and the build is fast. Besides, if the library is installed as a dynamic linking library (with .so / .dll extensions), which is often the case, many programs can share one library at run time, so it consumes less storage and memory.

*TODO*

The last step is to make sure that your user's computer also has those libraries. One way is to declare them as dependencies in the README file and tell your users to install them. Even better, you can write a "install dependencies" script, which checks and installs missing libraries automatically.

Because it requires an extra step to install external libraries, we call this project not "self-contained". If one of the libraries are missing, your program won't run.

Here is a comparison of the three methods.

| Method | Self-Contained | Portability | Build Time | Repo Size |
| ------ | -------------- | ----------- | ---------- | --------- |
| Include source | ✅     | ✅         |            | Medium    |
| Include libraries | ✅  |            | ✅         | Large     |
| Install libraries |     | ✅         | ✅         | Small     |

## Further Readings

As a beginner's tutorial, some important (but less beginner-level) topics are skipped. For example, we didn't cover unit tests. Besides, a C++ project can be either an executable or a library, and this post only talks about executable projects. To learn more about C++ project structure and CMake, consider reading these pages below.

C++ project structure:
- [Canonical Project Structure](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1204r0.html)
- [C++ Project Structure and Cross-Platform Build With CMake](https://medium.com/swlh/c-project-structure-for-cmake-67d60135f6f5)

CMake tutorials:
- [The Official CMake Tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/index.html)
- [An Introduction to Modern CMake](https://cliutils.gitlab.io/modern-cmake/)