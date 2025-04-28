#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid, ppid;

    // Get the PID of the parent process
    ppid = getpid();

    // Create a new process using fork()
    pid = fork();

    if (pid == -1) {
        // If fork() fails
        perror("fork failed");
        return 1;
    } else if (pid == 0) {
        // Child process
        printf("Child process:\n");
        printf("PID: %d\n", getpid());    // Get the PID of the child
        printf("PPID: %d\n", getppid()); // Get the PPID of the child
    } else {
        // Parent process
        printf("Parent process:\n");
        printf("PID: %d\n", getpid());    // Get the PID of the parent
        printf("PPID: %d\n", getppid()); // Get the PPID of the parent
    }

    return 0;
}
