# 📄 Get Next Line Project

## 📝 Project Overview

The **Get Next Line** project focuses on creating a function in **C** that reads and returns a line from a file descriptor. This function will be a helpful utility for many file-handling tasks in C programming, while also introducing key concepts such as **static variables**.

## 🎯 Goals

- Implement a function that reads and returns a line from a specified file descriptor.
- Handle repeated calls to read a file or standard input line by line.
- Understand and apply the use of **static variables** to manage state across function calls.
- Comply with best coding practices, including proper memory management and preventing unexpected terminations (e.g., segmentation faults).

## 💡 Key Concepts

- **Static Variables**: Use static variables to maintain state between function calls, allowing for efficient reading of the next line without losing data.
- **Memory Management**: Ensure that all allocated memory is freed properly to avoid memory leaks.

## 🛠️ Project Requirements

### Function Specification

- **Function Name**: `get_next_line`
- **Prototype**: `char *get_next_line(int fd);`
- **Parameters**: 
  - `fd`: The file descriptor from which the function reads.
- **Return Values**:
  - Returns the next line read from the file descriptor, including the terminating newline character (`\n`), if one is present.
  - Returns `NULL` if there are no more lines to read or if an error occurs.
  
### Additional Notes

- The function should handle repeated calls, reading and returning one line at a time from the specified file descriptor.
- The function must work for both **file reading** and **standard input**.
- Ensure compliance with all coding norms, avoiding segmentation faults or other unexpected terminations.
- Handle any errors related to file reading and memory allocation.

## 🛠️ Implementation Details

- **Static Variables**: Used to retain information across multiple function calls, enabling the function to remember the portion of the file that hasn't been read yet.
- **Memory Management**: Careful memory allocation for each line and freeing allocated memory after each call.
- **Edge Cases**: The function should handle files with no newline characters, empty files, and large files efficiently.

## 🔗 References

- **File Descriptors**: The function reads from file descriptors, allowing it to handle files, standard input (stdin), and other data sources.
- **Static Variables in C**: Understanding static variables is crucial to managing state between function calls in C.

## 📦 Memory Management

- Ensure that:
  - All dynamically allocated memory is properly freed after use to avoid memory leaks.
  - Handle memory reallocation as needed for reading variable-length lines.

## 🏗️ Makefile

The project must include a **Makefile** with the following rules:
- `all`: Compile the program.
- `clean`: Remove all object files.
- `fclean`: Remove all compiled files and binaries.
- `re`: Recompile the project from scratch.

Any **bonus** functionality should be handled separately in the Makefile.

## 💻 Usage Example

```c
#include "get_next_line.h"

int main(void)
{
    int fd = open("testfile.txt", O_RDONLY);
    char *line;

    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
