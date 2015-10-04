#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>



int main(int argc, char *argv[])
{
  FILE *parent, *child;
   
  printf ("I am: %n\n", (int) getpid());

  parent = fopen("pr", "w");
  fprintf(parent,"%d\n", getpid())

  pid_t pid = fork();
  printf("fork returned:%d\n", (int) pid );

  if (pid == -1)
  {
    perror("Fork failed");
  }
   
  if (pid == 0)
  {
    printf("I am the child process %d\n", (int) getpid());
    child = fopen("ch", "w");
    fprintf(child,"%d\n", getppid());

    parent = fopen("pr", "a");
    fprintf("parent,"\n%d\n",getpid());

    sleep(5);
    print ("Ending child process...");
  }

  printf("Parent process waiting for a child.\n")
  wait(NULL);

  ch = fopen("ch", "r");
  
  if (NULL = ch)
  {  
    printf("Error! Could not open the file!\n");
  } 
  printf ("Parent ending.\n");

  return 0;
}
