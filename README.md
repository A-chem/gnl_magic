<img width="1024" height="1024" alt="unnamed" src="https://github.com/user-attachments/assets/6406f37e-3f16-4ad8-9504-6cd7cf626e7c" />
# 📄 get_next_lin
e (42 Project)

`get_next_line` is a project from the [42](https://42.fr) curriculum.  
Its goal is to implement a function that reads from a file descriptor **one line at a time**, no matter the size of the file or buffer.  

---

## 🚀 Project Overview
The main objective is to code a function:
```c
char *get_next_line(int fd);
```

It must:
- Return the next line from a given file descriptor  
- Work with any `BUFFER_SIZE` value  
- Manage memory dynamically without leaks  
- Handle multiple file descriptors simultaneously  
- Return `NULL` when EOF is reached or an error occurs  

---

## 📖 Longer Description  

**get_next_line** is a project at [42](https://42.fr) that challenges students to implement a function capable of reading from a file descriptor and returning **one line at a time** until the end of the file (EOF). Unlike standard library functions such as `fgets`, this implementation must handle buffering, memory allocation, and edge cases manually, giving a deep understanding of how low-level input/output works in C.  

This project is not just about coding a function—it’s about learning how data flows between the operating system, files, and your program. Each call to `get_next_line` should deliver the **next full line**, even if the line spans multiple reads or if multiple file descriptors are used at the same time.  

### 🔑 The Project Focuses On
- **File descriptors and system calls (`read`)**  
  Understanding how data is read directly from files, standard input, or other data streams.  

- **Static variables and buffer management**  
  Keeping track of leftover data between function calls so the function can continue reading correctly.  

- **Dynamic memory allocation (`malloc`, `free`)**  
  Allocating just enough memory for each returned line while avoiding memory leaks or buffer overflows.  

- **Handling multiple file descriptors**  
  Ensuring that `get_next_line` works simultaneously with different open files or inputs without mixing data.  

- **Robust and efficient I/O**  
  Writing a function that behaves predictably across different environments, buffer sizes, and edge cases.  

### 📌 The Function Prototype
```c
char *get_next_line(int fd);
```

- **Parameters:**  
  - `fd`: the file descriptor to read from.  

- **Return value:**  
  - A string containing the next line read (including the newline `\n` if present).  
  - `NULL` if EOF is reached or an error occurs.  

### ⚙️ Key Requirements
- Must return the next line from a file descriptor, one call at a time.  
- Must work with different `BUFFER_SIZE` values, both small and large.  
- Must free all allocated memory properly (no leaks allowed).  
- Must handle edge cases: empty files, files without newlines, very long lines, and multiple open FDs.  
- Must stop reading and return `NULL` when there are no more lines.  

### 🎯 Learning Outcomes
By completing **get_next_line**, you will:  
- Understand how the **kernel provides data** to your program through system calls.  
- Learn how to **manage persistent state** across function calls using static variables.  
- Gain experience in **string manipulation and dynamic memory handling** in C.  
- Practice designing a function that is **robust, efficient, and flexible**.  
- Build a foundation for future 42 projects that depend heavily on reliable I/O handling, such as **pipex, minishell, and cub3D**.  

---

## 📂 Project Files
- **`get_next_line.c`** → core function logic  
- **`get_next_line_utils.c`** → helper functions (string handling, memory ops)  
- **`get_next_line.h`** → header file with prototypes and macros  
- **`main.c`** → test file (not required by the subject, for personal testing)  

---

## ⚙️ Installation
Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/get_next_line.git
cd get_next_line
```

Compile with:
```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 main.c get_next_line.c get_next_line_utils.c -o gnl
```

---

## ▶️ Usage
Run with a file:
```bash
./gnl text.txt
```

Or test with standard input:
```bash
./gnl
Hello world
Hello world
42 Network
42 Network
```

---

## 📝 Example
Input file (`file.txt`):
```
Hello 42
This is get_next_line
Reading one line at a time
```

Code:
```c
int fd = open("file.txt", O_RDONLY);
char *line;

while ((line = get_next_line(fd)))
{
    printf("%s", line);
    free(line);
}
close(fd);
```

Output:
```
Hello 42
This is get_next_line
Reading one line at a time
```

---

## 📚 Resources
- [man 2 read](https://man7.org/linux/man-pages/man2/read.2.html)  
- [42 Project Guidelines](https://github.com/42School)  

---

## ✅ Status
✔️ Project completed and validated at 42  
