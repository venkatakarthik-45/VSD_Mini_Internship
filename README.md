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

-  Now let's Breakdown our command mentioned above,
-  riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

          - riscv64-unknown-elf-gcc: This is the RISC-V cross-compiler (GNU Compiler Collection for RISC-V). It's designed to compile code for a RISC-V 64-bit architecture. riscv64-unknown-elf refers to the target platform where riscv64 specifies the 64-bit RISC-V architecture.
          - unknown is a placeholder for the vendor.
          - elf indicates the compiler produces an ELF (Executable and Linkable Format) output.
          - -mabi=lp64: This specifies the ABI (Application Binary Interface) to use.
          - lp64 means that the program will use 64-bit long integers and pointers, which is typical for a 64-bit system.
          - -march=rv64i: This specifies the target architecture for the compiled code.
          - rv64i stands for the 64-bit RISC-V base integer instruction set, which is the core instruction set for 64-bit RISC-V processors.
          - -o sum1ton.o: The -o option tells the compiler to produce an output file named sum1ton.o.
          - In this case, it’s generating an object file (.o), which is a compiled version of sum1ton.c, but not yet linked into a final executable.
          - sum1ton.c: This is the source C file that is being compiled.
          
- Now let's check the assembly code for our main C program.
- Below is the command to check the assembly code

        riscv64-unknown-elf-objdump -d sum1ton.o

- Now let's breakdown the above command,

          - riscv64-unknown-elf-objdump: This is a tool used to inspect object files, executables, and libraries for RISC-V architecture. It provides detailed information about the binary, such as disassembly, symbol tables, and more.
          - -d: This flag tells objdump to disassemble the object file. It converts the machine code inside sum1ton.o into human-readable assembly instructions. The output shows each instruction, along with the memory address and the binary representation of the instruction.
          - sum1ton.o: This is the input object file generated by a compiler (riscv64-unknown-elf-gcc) from your sum1ton.c source code.  

- Running `riscv64-unknown-elf-objdump -d sum1ton.o` disassembles the compiled object file sum1ton.o and displays the RISC-V assembly code corresponding to the machine code inside. This is useful for debugging, understanding how high-level C code translates to assembly, and verifying that optimizations are applied correctly.
  
- After running that command we need to search for our main code assembly, to do that we need first we need to run the below-mentioned command

      riscv64-unknown-elf-objdump -d sum1ton.o | less  

-  Then type `/main` so that you will get the exact assembly for our main program as shown in the below image.

![tk1_12](https://github.com/user-attachments/assets/0446092f-729b-4514-8a38-16ce9213814d)

-  Then cross-verify how many instructions we have for our main. To do that we need to subtract our first assembly code value to the next main assembly code value which is shown in below images.
-  10210 - 10184 = 8C --> We need to divide the result by 4 because each instruction is incremented by 4. So the final result will be 35 in Decimal.
-  Below are the references

![tk1_13](https://github.com/user-attachments/assets/6f292296-b767-4f5f-b883-5e6ef4992a15)
![tk1_9](https://github.com/user-attachments/assets/bdcf063d-e4fa-4097-b766-9069fd724c41)

# TASK - 2                    

## LAB - 1 SPIKE SIMULATION AND DEBUGGING OUR SUM1TON.C CODE USING SPIKE

- Executable File: Typically, we would use a complete executable file rather than an object file. If you want to run the program, you might need to link it first, producing an executable file.

          riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

- The command that we need to simulate using spike is shown below,

          spike pk sum1ton.o
  
- The command spike pk sum1ton.o is used to run a RISC-V program on the Spike simulator, which is an architecture simulator for RISC-V. Here’s a breakdown of what each part of the command does:

Breakdown of the command:
- spike:
Spike is a RISC-V ISA (Instruction Set Architecture) simulator that simulates RISC-V programs on the architecture. It allows you to run RISC-V binaries in a controlled environment.

- pk:
This stands for Proxy Kernel, which is a minimal operating system that provides basic system calls and an environment for running RISC-V binaries.
It acts as a bridge between the simulator and the program being run, handling system calls and providing the necessary infrastructure for executing the binary.

- sum1ton.o:
This is the RISC-V object file (the compiled version of your C program) that you want to run in the Spike simulator. Note that it should ideally be a runnable binary, so if you've only compiled it to an object file, you might need to link it first to produce an executable.
What it does:
Running spike pk sum1ton.o executes the sum1ton.o program in the Spike simulator, utilizing the Proxy Kernel for necessary system services.

![tk2_1](https://github.com/user-attachments/assets/ca56a40f-0834-4ebb-9983-65fd5f84925d)


## LAB - 2 DIGITAL DESIGN APPLICATION - RISC-V SEVEN SEGMENT DISPLAY DECODER.

### 7-Segment Display Decoder

- Introduction : 
The 7-Segment Display Decoder project is a fundamental exercise in digital logic design, where the goal is to simulate the functioning of a 7-segment display using a C program. A 7-segment display consists of seven LED segments arranged in a figure-eight pattern that can represent decimal digits and some alphabetic characters by illuminating specific segments. This project involves taking a hexadecimal input (ranging from 0 to 15) and decoding it to determine which segments to light up on the display. Understanding this concept is crucial for anyone interested in digital electronics and embedded systems, as it forms the basis for displaying numerical data in many electronic devices.

Project Overview
- Functionality
1) Input: The user enters a hexadecimal digit (0-9 or A-F).
2) Processing: The program maps the input to a binary representation that determines which segments of the display will be illuminated.
3) Output: The program displays the corresponding segments that should be lit up, both in binary format and as an ASCII representation for visual confirmation.

- How It Works
1) Binary Encoding: Each of the 7 segments of the display (labeled a to g) corresponds to a binary bit. The segments light up in specific combinations to represent hexadecimal digits.
2) Lookup Table: A predefined array holds the binary codes for each hexadecimal digit, making it easy to reference which segments to light up for a given input.
3) User Interaction: The program prompts the user for input, checks the validity of the input, and then retrieves the appropriate segment pattern from the lookup table.

- Example of Segment Encoding

Hex	Segment Code	Segments Lit
0	0b1111110	          a, b, c, d, e, f
1	0b0110000	          b, c
2	0b1101101	          a, b, d, e, g
3	0b1111001	          a, b, c, d, g
4	0b0110011	          b, c, f, g
5	0b1011011	          a, c, d, f, g
6	0b1011111	          a, c, d, e, f, g
7	0b1110000	          a, b, c
8	0b1111111	          a, b, c, d, e, f, g
9	0b1111011	          a, b, c, d, f, g
A	0b1110111	          a, b, c, e, f, g
B	0b0011111	          c, d, e, f, g
C	0b1001110	          a, d, e, f
D	0b0111101	          b, c, d, e, g
E	0b1001111	          a, d, e, f, g
F	0b1000111	          a, e, f, g

- Implementation

- C CODE

          #include <stdio.h>

          void displaySegment(int num) {
              // 7-segment display binary codes for hexadecimal 0-F
              const char *segmentCodes[] = {
        "0b1111110", // 0
        "0b0110000", // 1
        "0b1101101", // 2
        "0b1111001", // 3
        "0b0110011", // 4
        "0b1011011", // 5
        "0b1011111", // 6
        "0b1110000", // 7
        "0b1111111", // 8
        "0b1111011", // 9
        "0b1110111", // A
        "0b0011111", // B
        "0b1001110", // C
        "0b0111101", // D
        "0b1001111", // E
        "0b1000111"  // F
              };

              // Print the corresponding segment code
              printf("7-Segment Display for %X: %s\n", num, segmentCodes[num]);
            }

          int main() {
              int input;

              printf("Enter a number (0-15) to display on a 7-segment: ");
              scanf("%d", &input);

              // Check if the input is in the valid range
              if (input < 0 || input > 15) {
                  printf("Invalid input. Please enter a number between 0 and 15.\n");
              } else {
        displaySegment(input);
              }

              return 0;
          }

![tk2_2](https://github.com/user-attachments/assets/d5ddca28-f496-4ef2-a390-9800a7a4c062)
![tk2_3](https://github.com/user-attachments/assets/8a38f8eb-6d83-485a-9798-7669bc402450)


- Compilation steps are same as the previous one, Below are the steps we need to follow for our application as we did previously

1) gcc
2) RISC-V gcc
3) Spike

1) first we need to create a file and save the code which we wrote.

          gedit seven_segment_display.c &

2) Let's compile it and check the output with GCC

          gcc seven_segment_display.c
          ./a.out


3) Let's link our compiled file to an executable file, as we typically use a complete executable file rather than an object file. If you want to run the program, you'll need to link it first to produce an executable file.

          riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o seven_segment_display.o seven_segment_display.c
          riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o seven_segment_display.o seven_segment_display.c


![tk2_5](https://github.com/user-attachments/assets/21f728a1-03a8-499d-b867-2a126a2f062c)
![tk2_6](https://github.com/user-attachments/assets/9054fed4-3e0b-4666-a4da-96ac92827dec)


4) Let's look into the object file if we need to but it's optional,

          riscv64-unknown-elf-objdump -d seven_segment_display.o

![tk2_4_7segmentobjfile](https://github.com/user-attachments/assets/de2c9271-3340-424e-bdab-49ba7c031801)

 
5) Let's simulate using spike

          spike pk seven_segment_display.o

- Let's breakdown the above command,
 
- spike:
Spike is the RISC-V instruction set simulator. It simulates RISC-V processors and allows you to run binaries compiled for RISC-V architecture. It's useful for testing and debugging RISC-V programs without needing actual hardware.

- pk:
This stands for "Proxy Kernel." The proxy kernel is a lightweight operating system that runs alongside Spike, providing a minimal execution environment for the program. It allows the execution of bare-metal applications (those that run without an operating system).

- seven_segment_display.o:
This is the object file that you want to execute. It contains the compiled code (usually resulting from a C source file) for your specific application related to the seven-segment display.

- What It Does: When you run spike pk seven_segment_display.o, the following occurs:
1) Spike initializes the simulation environment.
2) The proxy kernel (pk) is started, which sets up the necessary runtime environment for the program.
3) The seven_segment_display.o binary is loaded and executed.
- This command is typically used to test embedded applications or simulations for RISC-V processors, especially for systems where you want to run low-level code directly without a full operating system.

- Now let's debug the seven_segment_display file by using the following command

          spike -d pk seven_segment_display.o 

- Everything is similar to the above explanation but only one change which is "-d".
- -d:
This flag enables debugging mode. When used, Spike provides additional information during the execution of the program, which can help in diagnosing issues or understanding the program's behavior step-by-step.
In debugging mode, you might see information about instruction execution, register values, memory accesses, and other details that can be crucial for debugging your application.

- Below is the final output of our application and finally we proved O0 = O1.

![tk2_7_final_output](https://github.com/user-attachments/assets/983027eb-61da-458b-b7c5-8c2df3f5ce0d)





