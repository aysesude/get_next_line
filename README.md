# get_next_line

## 📌 Project Description
The `get_next_line` project is designed to implement a function that reads a file line by line. The function should work with any file descriptor and must return each line, including the newline character (`\n`).

The function should:
- Read from a file descriptor (`fd`) one line at a time.
- Return `NULL` when there is nothing left to read or if an error occurs.
- Work with different `BUFFER_SIZE` values set at compile time.
- Handle both file input and standard input (`stdin`).
- Be implemented without using global variables or the `lseek()` function.

## 📁 Files

### Mandatory Files
- `get_next_line.c` – Main function to read a line from a file descriptor.
- `get_next_line_utils.c` – Helper functions used in `get_next_line.c`.
- `get_next_line.h` – Header file containing function prototypes and necessary includes.

### Bonus Files (Supports Multiple File Descriptors)
- `get_next_line_bonus.c` – Modified `get_next_line` to handle multiple file descriptors.
- `get_next_line_utils_bonus.c` – Helper functions for the bonus part.
- `get_next_line_bonus.h` – Header file for the bonus implementation.

## 🚀 Compilation
You can compile the project with different `BUFFER_SIZE` values using:
```sh
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c -o gnl
```

For the bonus part:
```sh
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_bonus.c get_next_line_utils_bonus.c -o gnl_bonus
```

## ⚙️ Usage
To use the function in a test program:
```c
#include <fcntl.h>
#include <stdio.h>
#include "get_next_line.h"

int main(void)
{
    int fd = open("test.txt", O_RDONLY);
    char *line;
    while ((line = get_next_line(fd)))
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## 🔍 Features
- Reads and returns one line at a time.
- Handles any `BUFFER_SIZE` value.
- Works with both files and standard input.
- The bonus version supports multiple file descriptors simultaneously.

## 📜 License
This project follows the [42 School](https://42.fr/) project requirements and is meant for educational purposes.

