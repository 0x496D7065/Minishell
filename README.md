*This project has been created as part of the 42 curriculum*

# Minishell

This project was developed with https://github.com/Zerrino.

## Description

Minishell is a minimal Unix shell written in C, inspired by Bash. It displays a prompt, reads commands, parses them, and executes them, handling quoting, environment variables, redirections, pipes, and signals the way Bash does for the supported features.

## Features

- Interactive prompt with command history
- Execution of binaries found through `PATH`, or via a relative or absolute path
- Single quotes `'` (no interpretation) and double quotes `"` (only `$` is interpreted)
- Environment variable expansion (`$VAR`) and the last exit status (`$?`)
- Redirections:
  - `<` redirects input
  - `>` redirects output
  - `>>` redirects output in append mode
  - `<<` heredoc, reading input until a delimiter
- Pipes `|`, chaining the output of one command into the next
- Signal handling in interactive mode:
  - `Ctrl-C` shows a new prompt on a new line
  - `Ctrl-D` exits the shell
  - `Ctrl-\` does nothing

### Built-in commands

| Command | Behavior |
|---|---|
| `echo` | Print arguments (with `-n` option) |
| `cd` | Change directory (relative or absolute path) |
| `pwd` | Print the current directory |
| `export` | Set environment variables |
| `unset` | Remove environment variables |
| `env` | Print the environment |
| `exit` | Exit the shell |

## Instructions

### Requirements

- A C compiler (`cc`) and `make`
- The `readline` library (for example `libreadline-dev` on Debian and Ubuntu)

### Build

```bash
make          # builds the minishell executable
make clean    # removes object files
make fclean   # removes object files and the executable
make re       # rebuilds everything
```

### Run

```bash
./minishell
```

### Example

```
minishell$ echo "Hello" | cat -e
Hello$
minishell$ export NAME=42
minishell$ echo $NAME
42
minishell$ ls -l > out.txt
minishell$ cat < out.txt
```

## Project structure

```
.
├── Makefile
├── includes/   # header files
├── srcs/       # shell source code
├── libft/      # personal C library
└── ft_printf/  # personal printf implementation
```

## Resources

- `man bash`, `man 3 readline`, `man 2 fork`, `man 2 execve`, `man 2 pipe`, `man 2 dup2`, `man 2 sigaction`
- [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)
- The 42 Minishell subject PDF
