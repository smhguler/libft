# libft

A custom C library implementation as part of the 42 curriculum.

## 📚 Description

**libft** is the first major C project in the 42 curriculum. The goal is to recreate many essential functions from the C standard library (libc) from scratch and build a personal static library (`libft.a`).

Through this project, I gained hands-on experience with:
- Memory management (`malloc`/`free`)
- Pointer arithmetic
- String operations
- Defensive programming
- Edge case handling (NULL, overflow, empty strings, allocation failures)
- 42 Norm compliance

This library serves as a personal toolkit for future 42 projects.

---

## 🛠️ Functions

### Part 1 — Libc Functions
Standard C functions reimplemented with `ft_` prefix:

**Character checks:**
- `ft_isalpha` — alphabetic character check
- `ft_isdigit` — digit check
- `ft_isalnum` — alphanumeric character check
- `ft_isascii` — ASCII character check
- `ft_isprint` — printable character check

**String operations:**
- `ft_strlen` — string length
- `ft_strchr` — locate first character occurrence
- `ft_strrchr` — locate last character occurrence
- `ft_strncmp` — compare strings
- `ft_strnstr` — locate substring
- `ft_atoi` — string to integer conversion

**Memory operations:**
- `ft_memset` — fill memory with a constant byte
- `ft_bzero` — zero a byte string
- `ft_memcpy` — copy memory area (no overlap)
- `ft_memmove` — copy memory area (overlap-safe)
- `ft_memchr` — scan memory for a byte
- `ft_memcmp` — compare memory areas

**String manipulation:**
- `ft_strlcpy` — safe string copy
- `ft_strlcat` — safe string concatenation
- `ft_toupper` — convert to uppercase
- `ft_tolower` — convert to lowercase
- `ft_calloc` — allocate and zero memory
- `ft_strdup` — duplicate string (dynamic)

### Part 2 — Additional Functions
Helper functions not in libc:

- `ft_substr` — extract substring
- `ft_strjoin` — concatenate two strings
- `ft_strtrim` — trim characters from string edges
- `ft_split` — split string by delimiter (most complex function)
- `ft_itoa` — integer to string conversion

**Functional programming:**
- `ft_strmapi` — apply function to string with index
- `ft_striteri` — iterate string with function

**File descriptor operations:**
- `ft_putchar_fd` — output char to fd
- `ft_putstr_fd` — output string to fd
- `ft_putendl_fd` — output string + newline to fd
- `ft_putnbr_fd` — output integer to fd

### Part 3 — Linked List (Bonus)
```c
typedef struct s_list
{
    void            *content;
    struct s_list   *next;
}   t_list;
```

**Functions:**
- `ft_lstnew` — create new node
- `ft_lstadd_front` — add node at beginning
- `ft_lstadd_back` — add node at end
- `ft_lstsize` — count list elements
- `ft_lstlast` — return last node
- `ft_lstdelone` — delete single node
- `ft_lstclear` — delete entire list
- `ft_lstiter` — apply function to each node
- `ft_lstmap` — apply function and create new list

---

## 🚀 Installation & Usage

### Compilation
```bash
# Compile the library
make

# Clean object files
make clean

# Remove all generated files
make fclean

# Recompile
make re
```

The Makefile compiles all `.c` files with `-Wall -Wextra -Werror` flags and creates the `libft.a` static library.

### Usage Example
```c
#include "libft.h"

int main(void)
{
    char *str = ft_strdup("Hello 42!");
    ft_putendl_fd(str, 1);
    free(str);
    return (0);
}
```

**Compile with libft:**
```bash
cc main.c -L. -lft -o program
```

---

## ✅ Testing

Developed on Windows, tested on Linux.

**Test tools used:**
- [Tripouille's libft tester](https://github.com/Tripouille/libftTester)
- [Francinette](https://github.com/xicodomingues/francinette)

**Testing focused on:**
- NULL pointer handling
- Malloc failure scenarios
- Edge cases (empty strings, `INT_MIN`, `INT_MAX`)
- Memory leak detection

---

## 📖 Resources

- **Man pages** — official documentation for each function
- **The C Programming Language (K&R)** — C fundamentals
- **GNU C Library Documentation** — libc reference
- Peer discussions and collaborative learning

---

## 🤖 AI Usage Note

Since the 42 subject is in English and I was new to C, I extensively used ChatGPT and Claude for:
- **Understanding requirements** in Turkish
- **Conceptual differences** (e.g., `memmove` vs `memcpy`, `calloc` vs `malloc`)
- **Edge case analysis** (NULL checks, overflow, allocation failures)
- **Debugging assistance** for complex functions like `ft_split` and `ft_lstmap`
- **Algorithm logic** clarification

**Important:** No function code was written by AI. All implementations were manually coded by me. AI was used only to understand concepts, get Turkish explanations, and accelerate my learning process.

---

## 📝 Technical Notes

- ✅ Fully compliant with **42 Norm v3**
- ✅ 25-line limit and function count restrictions respected
- ✅ No global variables — all variables are local/static
- ✅ No memory leaks — all `malloc`s checked and `free`d
- Platform notes:
  - `strlcpy` and `strlcat` are not in GNU libc by default (BSD functions)
  - `calloc`: returns safe-to-free pointer if `nmemb` or `size` = 0

---

## 👤 Author

**seguler** — 42 Student

---

## 📄 License

This project is part of the 42 school curriculum.
