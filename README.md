# VSDSquadron Mini Research Internship

Currently working on the VSDSquadron Mini RISC-V Development Kit as part of my internship. The powerful RISC-V architecture, enabling seamless integration into various development environments. Through this project, I am exploring the core functionalities and practical applications of RISC-V, gaining hands-on experience in cutting-edge embedded systems design.

# TASK - 1

## LAB - 1

-  We have to write a c program that will calculate from 1 to n.
-  Here we are using gEDIT as a Text Editor.
-  The command to open the text editor and type the C code is shown below.

          gedit sum1ton.c &

-  Here sum1ton.c is the c code saved by naming it sum1ton.c
-  `&`: This symbol is used to run the command in the background.
-  Below are the screenshots for your reference.

![tk1_1](https://github.com/user-attachments/assets/e9b7951f-6e97-4578-9aa3-2fc8eadc9bad)

-  Below is the C Program for your reference.

![tk1_6](https://github.com/user-attachments/assets/e9ceb147-a4a4-48ed-b666-27e471c7d4ea)

-  So now to Compile and Run we need to follow below commands

        gcc sum1ton.c
        ./a.out
-  gcc: This is the GNU Compiler Collection, a compiler for C (and other languages).
-  sum1ton.c: This is the C source file that you're compiling.
-  When you run gcc sum1ton.c, the compiler takes the sum1ton.c file and compiles it into an executable file. By default, this executable file is named a.out unless you specify a different name using the -o option.
-  ./a.out: This runs the executable that was created after compiling the program (a.out). The ./ tells the terminal to look for a.out in the current directory and execute it.
-  gcc sum1ton.c compiles the C program, producing an executable named a.out.
-  ./a.out runs that executable, executing your program.

![tk1_2](https://github.com/user-attachments/assets/45027b5b-c229-4a35-b8ae-859ce7e14f85)

-  So after running both the commands below is what we get as an output.

![tk1_3](https://github.com/user-attachments/assets/f12db4fc-926c-4034-a9d2-4c95973bbed5)

-  For better understanding, i have changed the value of n and followed the same steps.
-  Below is the modified program and its output.

![tk1_5](https://github.com/user-attachments/assets/f80dae91-037c-43b4-b083-d4263b2e05ed)
![tk1_4](https://github.com/user-attachments/assets/7aa0aa51-38b5-43db-b48e-a7acd6f14fc1)

## LAB-2

-  Now lets run our same c code using RISC-V Simulator. before that to check our actual c code in the terminal we need to type the below command.

        cat sum1ton.c
   
-  cat: This command stands for "concatenate" and is used to read the contents of a file and output it to the terminal.

![tk1_10](https://github.com/user-attachments/assets/7d2d2df7-c238-47d1-b0ba-4224f8480c0a)

-  Now lets execute our code using RISC-V Simulator using the following command

        riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
        ls -ltr sum1ton.o
        riscv64-unknown-elf-gcc -ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

![tk1_11](https://github.com/user-attachments/assets/3221b89f-c111-4e64-bf23-03fba3abf65a)

-  Now lets check the assembly code for our main C program.
-  Below is the command to check the assembly code

        riscv64-unknown-elf-objdump -d sum1ton.o

- After running that command we need to search for our main code assembly, to do that we need to first we need to run the below mentioned command

      riscv64-unknown-elf-objdump -d sum1ton.o | less  

-  Then type `/main` so that you will get the exact assembly for our main program as shown in the below image.

![tk1_12](https://github.com/user-attachments/assets/0446092f-729b-4514-8a38-16ce9213814d)

-  Then cross-verify how many instructions we have for our main. To do that we need to subtract our first assembly code value to the next main assembly code value which is shown in below images.
-  10210 - 10184 = 8C --> We need to divide the result by 4 because each instruction is incremented by 4. So the final result will be 35 in Decimal.
-  Below are the references

![tk1_13](https://github.com/user-attachments/assets/6f292296-b767-4f5f-b883-5e6ef4992a15)
![tk1_9](https://github.com/user-attachments/assets/bdcf063d-e4fa-4097-b766-9069fd724c41)

