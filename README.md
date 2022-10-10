# cardiac-advance
A CARDIAC paper computer interpreter. On the GBA. This is probably a crime against computing itself.

# Why?
because i felt like it and im weird and strange.  

# CARDIAC Info
1. the CARDIAC computer consists of 100 memory cells that contain a three-digit decimal number up to 999.
2. the CPU itself is a single instruction, single accumulator machine. Each command runs on the accumulator  
and a single memory cell.
3. The accumulator itself has 4 bits exclusively to handle overflows and underflows. It seems to be undefined  
whether or not the carry bit is kept moving forward.
4. Assume numbers are signed by default, it doesn't seem to matter too much, since it isn't clear when it is or isn't  
unsigned.
5. This simulator will throw away the 4th bit of the accumulator. If this breaks your workflow, I don't care.  
5a. And yes, I do know about https://xkcd.com/1172/ don't @ me.
## I/O
The CARDIAC has one input and one output device. The first person to connect a mouse somehow wins spontanious combustion as a prize. For input you get a card reader. for ouput, a punched card. Each card equals essentially one memory cell (so, one three-digit signed decimal integer). When INP is executed, the specified card is read into memory and removed from the input stack. On OUT, A new card is punched with the same sort of data and placed into the output stack.
## Opcodes
INP is opcode 0, and loads a card into memory from the stack.  
CLA is opcode 1, and clears the accumulator and adds from memory (load).  
ADD is opcode 2, and adds the memory cell content to the accumulator.
TAC is opcode 3, and checks the accumulator value and jumps if negative.  
SFT is opcode 4, and shifts the accumulator.  
OUT is opcode 5, and outputs a freshly punched card to the output stack.  
STO is opcode 6, and stores the accumulator to memory.  
SUB is opcode 7, and subtracts the current memory value from the accumulator
JMP is opcode 8, and jumps to another address and saves PC
HRS is opcode 9, and halts the cardiac cpu and resets it
