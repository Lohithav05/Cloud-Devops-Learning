# Cloud DevOps Learning Journey: Day 32 

## Overview
On Day 32 of the Cloud DevOps Learning Journey, we dive into **Shell Scripting**, a powerful tool for automating tasks, managing systems, and streamlining DevOps workflows. Shell scripts allow you to write commands in a file to execute them sequentially, enabling efficient automation of repetitive tasks in Linux/Unix environments.

## What is Shell Scripting?
Shell scripting involves writing a series of commands in a plain text file (typically with a `.sh` extension) that can be executed by a shell interpreter like Bash (Bourne Again Shell). It is widely used in DevOps for tasks such as system monitoring, file manipulation, process automation, and deployment scripting.

## Key Concepts
- **Shebang**: The first line of a shell script (e.g., `#!/bin/bash`) specifies the shell interpreter.
- **Variables**: Store data for reuse (e.g., `name="DevOps"`).
- **Control Structures**: Use `if`, `for`, `while`, and `case` for logic and loops.
- **Command Substitution**: Capture command output (e.g., `date=$(date)`).
- **Functions**: Modularize code for reusability.
- **Exit Codes**: Indicate success (`0`) or failure (non-zero).

## Example Shell Script
Below is a simple shell script to check if a service is running and restart it if necessary.

```bash
#!/bin/bash

SERVICE="nginx"
if systemctl is-active --quiet $SERVICE; then
    echo "$SERVICE is running."
else
    echo "$SERVICE is not running. Restarting..."
    sudo systemctl restart $SERVICE
    if systemctl is-active --quiet $SERVICE; then
        echo "$SERVICE restarted successfully."
    else
        echo "Failed to restart $SERVICE."
        exit 1
    fi
fi
```

## Learning Objectives
1. **Write Basic Scripts**: Create scripts to automate simple tasks like file backups or log rotation.
2. **Use Conditionals and Loops**: Implement logic to handle dynamic scenarios.
3. **Handle Errors**: Use exit codes and error messages for robust scripts.
4. **Schedule Scripts**: Learn to use `cron` or `systemd` timers to run scripts periodically.
5. **Debugging**: Use `bash -x` to debug scripts and identify issues.

## Practice Tasks
- Write a script to monitor disk usage and send an alert if it exceeds 80%.
- Create a script to automate the installation of a package (e.g., `nginx` or `docker`).
- Use a `for` loop to process a list of files in a directory.

## Resources
- [Bash Scripting Tutorial](https://www.shellscript.sh/)
- [Linux Command Line Basics](https://linuxcommand.org/)
- [Cron Scheduling Guide](https://crontab.guru/)

