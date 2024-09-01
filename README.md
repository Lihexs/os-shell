# OS Shell Project

This project implements a custom shell as part of an Operating Systems course assignment. The shell provides basic command execution capabilities along with several advanced features commonly found in shell environments.

## Features

- **Command Execution**: Execute standard system commands.
- **Background Processes**: Run commands in the background using the `&` operator.
- **Piping**: Support for single piping between two commands using the `|` operator.
- **Input Redirection**: Redirect input from a file using the `<` operator.
- **Output Redirection (Append)**: Append output to a file using the `>>` operator.
- **Signal Handling**: Custom handling of SIGINT (Ctrl+C) for both the shell and child processes.
- **Zombie Process Prevention**: Automatically reaps terminated child processes to prevent zombies.

## Project Structure

- `src/shell.c`: Main shell loop and command parsing logic.
- `src/myshell.c`: Implementation of shell functionality including command execution, piping, and I/O redirection.


## Usage Examples

1. Regular command execution:
   ```
   ls -l
   ```

2. Background execution:
   ```
   sleep 10 &
   ```

3. Piping:
   ```
   ls | grep .txt
   ```

4. Input redirection:
   ```
   sort < input.txt
   ```

5. Output redirection (append):
   ```
   echo "Hello, World!" >> output.txt
   ```

## Implementation Details

- The shell uses `fork()` and `execvp()` for command execution.
- Piping is implemented using the `pipe()` system call and two child processes.
- I/O redirection utilizes the `open()` and `dup2()` system calls.
- Signal handling is set up using `sigaction()` to ignore SIGINT in the parent shell process.
- Child processes are reaped using `waitpid()` with the `WNOHANG` option to prevent zombie processes.

## Limitations

- Only single piping is supported (one `|` per command).
- Background execution, piping, and I/O redirection are mutually exclusive and cannot be combined in a single command.



This project is an academic assignment designed to demonstrate understanding of process management, inter-process communication, and system calls in a Unix-like environment. It is not intended for production use.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
