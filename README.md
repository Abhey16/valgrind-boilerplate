# Valgrind Exercise

## Standard install via command-line
```bash
# Configure the project and generate a native build system:
  # Must re-run this command whenever any CMakeLists.txt file has been changed.
  cmake -S ./ -B build/
# To build with debugging information, do:
  cmake -S ./ -B build/ -D CMAKE_BUILD_TYPE=Debug
# Compile and build the project:
  # rebuild only files that are modified since the last build
  cmake --build build/
  # or rebuild everything from scracth
  cmake --build build/ --clean-first
  # to see verbose output, do:
  cmake --build build/ --verbose
# Run program:
  ./build/app/shell-app
# Clean
  cmake --build build/ --target clean
# Clean and start over:
  rm -rf build/
```

---

## Q What happens when the executable is linked statically?  Does Valgrind still detect those same bugs? Why or why not.

Static linking means that all external library code used by shell-app (like standard libraries or any other linked libraries) will be included directly in the final executable.

When an executable is linked statically, Valgrind still detects the same memory-related bugs as in dynamically linked executable. This is because Valgrind analyzes runtime memory usage and access patterns, which are independent of the linking method. The detection of bugs depends on the executable's code and its memory interactions, not on how it's linked. 

However, if a statically linked library contains bugs that aren't triggered by the executable, Valgrind won't detect them.
