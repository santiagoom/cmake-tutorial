
# operation

## target_include_directories
```
Add include directories to a target.
target_include_directories(<target> [SYSTEM] [BEFORE]
  <INTERFACE|PUBLIC|PRIVATE> [items1...]
  [<INTERFACE|PUBLIC|PRIVATE> [items2...] ...])
Specifies include directories to use when compiling a given target. The named <target> must have been created by a command such as add_executable() or add_library() and must not be an ALIAS target.
```

## set
```
Set a normal, cache, or environment variable to a given value. See the cmake-language(7) variables documentation for the scopes and interaction of normal variables and cache entries.
Signatures of this command that specify a <value>... placeholder expect zero or more arguments. Multiple arguments will be joined as a semicolon-separated list to form the actual variable value to be set. Zero arguments will cause normal variables to be unset. See the unset() command to unset variables explicitly.

Set Normal Variable
set(<variable> <value>... [PARENT_SCOPE])
Sets the given <variable> in the current function or directory scope.

If the PARENT_SCOPE option is given the variable will be set in the scope above the current scope. Each new directory or function creates a new scope. This command will set the value of a variable into the parent directory or calling function (whichever is applicable to the case at hand). The previous state of the variable’s value stays the same in the current scope (e.g., if it was undefined before, it is still undefined and if it had a value, it is still that value).
```

## add_executable
```
Contents
add_executable
Normal Executables
Imported Executables
Alias Executables
Add an executable to the project using the specified source files.
Normal Executables
add_executable(<name> [WIN32] [MACOSX_BUNDLE]
               [EXCLUDE_FROM_ALL]
               [source1] [source2 ...])
Adds an executable target called <name> to be built from the source files listed in the command invocation. (The source files can be omitted here if they are added later using target_sources().) The <name> corresponds to the logical target name and must be globally unique within a project. The actual file name of the executable built is constructed based on conventions of the native platform (such as <name>.exe or just <name>).

By default the executable

```

## add_library
```
Contents
add_library
Normal Libraries
Object Libraries
Interface Libraries
Imported Libraries
Alias Libraries
Add a library to the project using the specified source files.
Normal Libraries
add_library(<name> [STATIC | SHARED | MODULE]
            [EXCLUDE_FROM_ALL]
            [<source>...])
Adds a library target called <name> to be built from the source files listed in the command invocation. (The source files can be omitted here if they are added later using target_sources().) The <name> corresponds to the logical target na
```


## find_library
```
A short-hand signature is:

find_library (<VAR> name1 [path1 path2 ...])
The general signature is:

find_library (
          <VAR>
          name | NAMES name1 [name2 ...] [NAMES_PER_DIR]
          [HINTS path1 [path2 ... ENV var]]
          [PATHS path1 [path2 ... ENV var]]
          [PATH_SUFFIXES suffix1 [suffix2 ...]]
          [DOC "cache documentation string"]
          [REQUIRED]
          [NO_DEFAULT_PATH]
          [NO_PACKAGE_ROOT_PATH]
          [NO_CMAKE_PATH]
          [NO_CMAKE_ENVIRONMENT_PATH]
          [NO_SYSTEM_ENVIRONMENT_PATH]
          [NO_CMAKE_SYSTEM_PATH]
          [CMAKE_FIND_ROOT_PATH_BOTH |
           ONLY_CMAKE_FIND_ROOT_PATH |
           NO_CMAKE_FIND_ROOT_PATH]
         )
This command is used to find a library. A cache entry named by <VAR> is created to store the result of this command. If the library is found the result is stored in the variable and the search will not be repeated unless the variable is cleared. If nothing is found, the result will be <VAR>-NOTFOUND. The REQUIRED option stops processing with an error message if nothing is found, otherwise the search will be attempted again the next time find_library is invoked with the same variable.

```

## find_package
```
Contents
find_package
Basic Signature and Module Mode
Full Signature and Config Mode
Version Selection
Search Procedure
Package File Interface Variables
Find an external project, and load its settings.

Basic Signature and Module Mode
find_package(<PackageName> [version] [EXACT] [QUIET] [MODULE]
             [REQUIRED] [[COMPONENTS] [components...]]
             [OPTIONAL_COMPONENTS components...]
             [NO_POLICY_SCOPE])
Finds and loads settings from an external project. <PackageName>_FOUND will be set to indicate whether the package was found. When the package is found package-specific information is provided through variables and Imported Targets documented by the package itself. The QUIET option disables informational messages, including those indicating that the package cannot be found if it is not REQUIRED. The REQUIRED option stops processing with an error message if the package cannot be found.

A package-specific list of required components may be listed after the COMPONENTS option (or after the REQUIRED option if present). Additional optional components may be listed after OPTIONAL_COMPONENTS. Available components and their influence on whether a package is considered to be found are defined by the target package.
```

## get_cmake_property
```

Get a global property of the CMake instance.

get_cmake_property(<var> <property>)
Gets a global property from the CMake instance. The value of the <property> is stored in the variable <var>. If the property is not found, <var> will be set to NOTFOUND. See the cmake-properties(7) manual for available properties.
```

## option
```

Provide an option that the user can optionally select.

option(<variable> "<help_text>" [value])
Provides an option for the user to select as ON or OFF. If no initial <value> is provided, OFF is used. If <variable> is already set as a normal or cache variable, then the command does nothing (see policy CMP0077).

If you have options that depend on the values of other options, see the module help for CMakeDependentOption.
```

## list
```
List operations.

Synopsis
Reading
  list(LENGTH <list> <out-var>)
  list(GET <list> <element index> [<index> ...] <out-var>)
  list(JOIN <list> <glue> <out-var>)
  list(SUBLIST <list> <begin> <length> <out-var>)

Search
  list(FIND <list> <value> <out-var>)

Modification
  list(APPEND <list> [<element>...])
  list(FILTER <list> {INCLUDE | EXCLUDE} REGEX <regex>)
  list(INSERT <list> <index> [<element>...])
  list(POP_BACK <list> [<out-var>...])
  list(POP_FRONT <list> [<out-var>...])
  list(PREPEND <list> [<element>...])
  list(REMOVE_ITEM <list> <value>...)
  list(REMOVE_AT <list> <index>...)
  list(REMOVE_DUPLICATES <list>)
  list(TRANSFORM <list> <ACTION> [...])

Ordering
  list(REVERSE <list>)
  list(SORT <list> [...])
```

## install
```
Specify rules to run at install time.

Synopsis
install(TARGETS <target>... [...])
install({FILES | PROGRAMS} <file>... [...])
install(DIRECTORY <dir>... [...])
install(SCRIPT <file> [...])
install(CODE <code> [...])
install(EXPORT <export-name> [...])
```

## CheckSymbolExists
```
Provides a macro to check if a symbol exists as a function, variable, or macro in C.

check_symbol_exists
check_symbol_exists(<symbol> <files> <variable>)
Check that the <symbol> is available after including given header <files> and store the result in a <variable>. Specify the list of files in one argument as a semicolon-separated list. <variable> will be created as an internal cache variable.

For example:

include(CheckSymbolExists)

# Check for macro SEEK_SET
check_symbol_exists(SEEK_SET "stdio.h" HAVE_SEEK_SET)
# Check for function fopen
check_symbol_exists(fopen "stdio.h" HAVE_FOPEN)

```

## target_compile_definitions¶
```
Add compile definitions to a target.

target_compile_definitions(<target>
  <INTERFACE|PUBLIC|PRIVATE> [items1...]
  [<INTERFACE|PUBLIC|PRIVATE> [items2...] ...])
Specifies compile definitions to use when compiling a given <target>. The named <target> must have been created by a command such as add_executable() or add_library() and must not be an ALIAS target.

```
## add_custom_command

```
Add a custom build rule to the generated build system.

There are two main signatures for add_custom_command.

Generating Files
The first signature is for adding a custom command to produce an output:

add_custom_command(OUTPUT output1 [output2 ...]
                   COMMAND command1 [ARGS] [args1...]
                   [COMMAND command2 [ARGS] [args2...] ...]
                   [MAIN_DEPENDENCY depend]
                   [DEPENDS [depends...]]
                   [BYPRODUCTS [files...]]
                   [IMPLICIT_DEPENDS <lang1> depend1
                                    [<lang2> depend2] ...]
                   [WORKING_DIRECTORY dir]
                   [COMMENT comment]
                   [DEPFILE depfile]
                   [JOB_POOL job_pool]
                   [VERBATIM] [APPEND] [USES_TERMINAL]
                   [COMMAND_EXPAND_LISTS])
This defines a command to generate specified OUTPUT file(s). A target created in the same directory (CMak
```

## target_link_libraries
```
Contents
target_link_libraries
Overview
Libraries for a Target and/or its Dependents
Libraries for both a Target and its Dependents
Libraries for a Target and/or its Dependents (Legacy)
Libraries for Dependents Only (Legacy)
Linking Object Libraries
Cyclic Dependencies of Static Libraries
Creating Relocatable Packages
Specify libraries or flags to use when linking a given target and/or its dependents. Usage requirements from linked library targets will be propagated. Usage requirements of a target’s dependencies affect compilation of its own sources.
```

##  Package Layout
```

A config-file package consists of a Package Configuration File and optionally a Package Version File provided with the project distribution.

```
# parameter
## PROJECT_SOURCE_DIR
```
This is the source directory of the last call to the project() command made in the current directory scope or one of its parents. Note, it is not affected by calls to project() made within a child directory scope (i.e. from within a call to add_subdirectory() from the current scope).
```


## PROJECT_BINARY_DIR
```
Full path to build directory for project.
This is the binary directory of the most recent project() command.
```


## cmake-variables(7)
```
https://cmake.org/cmake/help/latest/manual/cmake-variables.7.html?highlight=project_binary_dir
```
## CMAKE_PREFIX_PATH
```
CMAKE_PREFIX_PATH¶
Semicolon-separated list of directories specifying installation prefixes to be searched by the find_package(), find_program(), find_library(), find_file(), and find_path() commands. Each command will add appropriate subdirectories (like bin, lib, or include) as specified in its own documentation.

By default this is empty. It is intended to be set by the project.

See also CMAKE_SYSTEM_PREFIX_PATH, CMAKE_INCLUDE_PATH, CMAKE_LIBRARY_PATH, CMAKE_PROGRAM_PATH, and CMAKE_IGNORE_PATH.





The environment variable CMAKE_PREFIX_PATH may also be populated with prefixes to search for packages. Like the PATH environment variable, this is a list and needs to use the platform-specific environment variable list item separator (: on Unix and ; on Windows).
```


Libraries not Providing Config-file Packages
```
Third-party libraries which do not provide config-file packages can still be found with the find_package() command, if a FindSomePackage.cmake file is available.

These module-file packages are different to config-file packages in that:

They should not be provided by the third party, except perhaps in the form of documentation

The availability of a Find<PackageName>.cmake file does not indicate the availability of the binaries themselves.

CMake does not search the CMAKE_PREFIX_PATH for Find<PackageName>.cmake files. Instead CMake searches for such files in the CMAKE_MODULE_PATH variable. It is common for users to set the CMAKE_MODULE_PATH when running CMake, and it is common for CMake projects to append to CMAKE_MODULE_PATH to allow use of local module-file packages.

CMake ships Find<PackageName>.cmake files for some third party packages for convenience in cases where the third party does not provide config-file packages directly. These files are a maintenance burden for CMake, so new Find modules are generally not added to CMake anymore. Third-parties should provide config file packages instead of relying on a Find module to be provided by CMake.

Module-file packages may also provide Imported Targets. A complete example which finds such a package might look like

Module-file packages may also provide Imported Targets. A complete example which finds such a package might look like:

cmake_minimum_required(VERSION 3.10)
project(MyExeProject VERSION 1.0.0)

find_package(PNG REQUIRED)

# Add path to a FindSomePackage.cmake file
list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake")
find_package(SomePackage REQUIRED)

add_executable(MyExe main.cpp)
target_link_libraries(MyExe PRIVATE
    PNG::PNG
    SomePrefix::LibName
)
The <PackageName>_ROOT variable is also searched as a prefix for find_package() calls using module-file packages such as FindSomePackage.

```




