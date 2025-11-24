# minishell

A tiny Unix shell written in C, inspired by `bash` and built as part of the 42 cursus.  
The goal: travel back in time and talk to your computer through a simple, interactive command line.

---

## ✨ Features

- Prompt that waits for a new command
- Command history (powered by `readline`)
- PATH resolution for executables, plus support for:
  - Absolute paths (`/bin/ls`)
  - Relative paths (`./my_script.sh`)
- Single global variable used only for signal handling
- Proper handling of quotes:
  - Single quotes `'...'` keep everything literal
  - Double quotes `"..."` expand `$VAR` but keep other meta-characters
- Redirections:
  - `<`  — redirect input
  - `>`  — redirect output (truncate)
  - `>>` — redirect output (append)
  - `<<` — heredoc until a given delimiter (no history update)
- Pipes: `cmd1 | cmd2 | cmd3`
- Environment variables:
  - `$VAR` expansion
  - `$?` for the last exit status
- Logical operators and precedence:
  - `&&` and `||`
  - Parentheses for priority: `(cmd1 && cmd2) || cmd3`
- Signal handling (interactive mode):
  - `Ctrl-C` prints a new prompt on a new line
  - `Ctrl-D` exits the shell
  - `Ctrl-\` is ignored, like in `bash`
- No unrequired special characters: no interpretation of unclosed quotes, `\`, `;`, etc.

---

## 🔧 Built-in commands

Implemented built-ins (without extra options/flags unless specified):

- `echo [-n]` – print text with optional no-newline
- `cd [path]` – change directory (relative or absolute)
- `pwd` – print current working directory
- `export` – print environment (and manage exported variables internally)
- `unset` – remove environment variables
- `env` – print current environment
- `exit` – exit minishell

---

## 🏗️ Tech & Constraints

- Language: **C**
- Build system: **Makefile**
  - Targets: `all`, `clean`, `fclean`, `re`
- Allowed external functions (as per subject):
  - `readline`, `add_history`, `rl_clear_history`, `rl_on_new_line`, `rl_replace_line`, `rl_redisplay`
  - `printf`, `malloc`, `free`, `write`
  - `access`, `open`, `read`, `close`
  - `fork`, `wait`, `waitpid`, `wait3`, `wait4`
  - `signal`, `sigaction`, `sigemptyset`, `sigaddset`, `kill`
  - `exit`
  - `getcwd`, `chdir`
  - `stat`, `lstat`, `fstat`, `unlink`
  - `execve`, `dup`, `dup2`, `pipe`
  - `opendir`, `readdir`, `closedir`
  - `strerror`, `perror`
  - `isatty`, `ttyname`, `ttyslot`, `ioctl`
  - `getenv`
  - `tcsetattr`, `tcgetattr`
  - `tgetent`, `tgetflag`, `tgetnum`, `tgetstr`, `tgoto`, `tputs`
- Libft: **allowed** and used
- Memory: no leaks allowed in **my** code (the known `readline` leaks are tolerated by the subject)

---

## 🚀 Getting Started

### Prerequisites

- `gcc` or `clang`
- `make`
- `readline` development headers installed  
  (e.g. on macOS: `brew install readline`, on Linux: `sudo apt install libreadline-dev`)

### Build

```bash
make
