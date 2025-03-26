---
title: "Midterm CS 1810"
description: "Learned Material in Computer Systems and Design"
pubDate: "Wednesday, March 26, 2025"
heroImage: "/blog-placeholder-4.jpg"
---

## Logic Gates 
NOT  
OR  
AND  
NOR  
NAND  
XOR  
## Three Ways of Illustrating Digital Circuit Behavior  
1. Logic Diagram  
2. Truth Table  
3. Boolean Alegbra  

## Constructing Gates from Transistors  

## Propagation Delay  

## Adders  

### Half Adders

____________

Half adders is a system that takes two binary inputs and adds them together producing a bit for the sum, and a bit indicating whether or not a carry occurred.

With two inputs in a half adder, you can have four possible patterns of ones and zeros

This gives us the following SOP (Sum of Product) expression:

### Syntax

```markdown
![Alt text]( )
```

### Output

![blog placeholder](/blog-placeholder-about.jpg)

The output Sum is equivalent to the 2-input XOR Gate!
For Carryout, the output equals 1 only when both A and B are equal to one, matching the AND gate!

The Half Adder works fine if we're trying to add two bits together - a situation that typically occurs in the rightmost column of a multi-bit addition.
But what if we wanted to add that third bit, the carry bit, from the previous column?

Adding the least significant bits of a multi-bit value uses the half-adder described above. Each input to the half-adder takes one of the least significant bits from each other. The outputs are the least significant digit of the sum and a possible carry to the next column.
What is needed for the remining columns is an adder similar to the half-adder that can add two bits along with a carry from the previous column to produce a sum and the carryout to the next column. This Circuit is called a Full Adder.

### Full Adders

With Three inputs, there are 2^3 = 8 possible patterns of ones and zeros that could be input to our full adder.

The table below lists all possible combinations  of addition Results Based on Inputs of a Full Adder.

The two-digit binary result in the last column of this table can be broken into its components, the sum and a carry to the next bit position.
This gives us two truth tables, one for the Sum and one for the Carry OUT:

With three inputs, a K

ripple carry 2-bit, 4-bit, and 8-bit adder


# The Stored-Program Concept
________

In the 1940s, it was realized that data and instructions are logically the same.

Both are comprised of bits and can be stored in the same way.

_von Neumann architecture_ — the design built on this principle

Units that process data are **separate** from units that process
instructions.


# Von Neuman Architecture - Primary Components of a Computer
________

### Memory

### ALU (Arithmetic Logic Unit)
The ALU is capable of performing basic arithmetic and logical operations limited to: 
1. addition
2. subtraction
3. bitwise **AND**
4. bitwise **NOR** 

A register is a special storage unit used to store data that is needed  again immediately (not memory).

There are very few registers in a computer, but the access time for a  register is much faster than for memory.

####  Example: x<sup>1</sup> * (x<sup>2</sup> + x<sup>3</sup>)

Rather than storing the addition result in  memory, leave it in the register for the multiplication

### Control Unit
This unit controls the actions of the other components.

The ALU and the control unit are often grouped together as one unit, called the central processing unit (CPU).

The bus is a set of wires through which data travels within computer.


### Input

### Output


# The Simple Computer
________

### RAM (Random Access Memory)

### General-Purpose Regisiters

### Bus

Clock

## Programming the SC via Direct Manipulation of the Control Path
________

### Address
### Write_RAM
### Write_R0
### Write_R1
### Operands
### Operator
### RAM_ALU_toBus

## The Fetch-Decode-Execute Cycle
____
### Program Counter
### Instruction Register
### Instruction Decoder

## SC's Machine Language
____

Recall that each type of computer has a specific set of operations that it can execute, called its machine language.  Machine language instructions are written in binary so that they may be stored in memory.  Furthermore, we often concisely express each binary instruction as hexadecimal.



| Instruction | Operation                   | Mnemonics |
|-------------|-----------------------------|-----------|
| `000abcde`  | `M[abcde] <- r0`            | `STORE`   |
| `001abcde`  | `M[abcde] <- r1`            | `STORE`   |
| `010abcde`  | `r0 <- M[abcde]`            | `LOAD`    |
| `011abcde`  | `r1 ,_ M[abcde]`            | `LOAD`    |
| `100abcde`  | ra <- rb op<sub>de</sub> rc | `ALU`     |

| Operator | code |
|----------|------|
| add      | 00   |
| subtract | 01   |
| and      | 10   |
| nor      | 11   |


## SC Assembly Language
____


Assembly language expresses instructions using a mix of English mnemonics and symbols. 

- Each mnemonic represents one or more operations of the computer.

- For the SC, an assembly language instruction can be translated into exactly one machine language instruction.

The program that does the translation is called an assembler.

```aiignore
store ra, L       // store the value in register ra to label L 
load L, ra        // load the value at label L into register ra
cmp ra, rb        // compare the values in registers ra and rb, setting condition codes 
add ra, rb, rc    // add the values in registers ra and rb, putting the result in register rc
sub ra, rb, rc    // subtract the value in register rb from the value in register ra, putting the result in register rc
and ra, rb, rc    // bitwise-and the values in registers ra and rb, putting the result in register rc 
nor ra, rb, rc    // bitwise-nor the values in registers ra and rb, putting the result in register rc not ra, rb
not ra, rb        // complement the value in register ra, putting the result in register rb
clear ra          // put the value zero into register ra
halt              // stop execution
jump L            // execute the instruction at label L next
bgt L             // if in the previous instruction the first operand is greater than the second operand, 
                  // execute the instruction at label L next
bne L             // if in the previous instruction the first and second operand are unequal, 
                  // execute the instruction at label L next
```

### Assembly Labels
The following program adds the values at labels A and B, putting the result at label C.
```aiignore
load A, r0       // r0 contains the value at A
    load B, r1       // r1 contains the value at B
    add r0, r1, r0   // r0 contains A + B
    store r0, C      // the value at C is A + B
    halt
A:  4 
B:  5 
C:  -1
```
Every line of an assembly language program must be either one of the instructions above or an integer (-128 to 127) prefaced by an alphanumeric label and colon.  Any instruction may be prefaced by an alphanumeric label and colon.  All labels used must be distinct.

Each <mark>label</mark> in an assembly language program represents a memory location.




## Programming Language Syntax/Semantics
____
Programming Language can be translated into instructions that a computer can execute. It is a set of grammar rules, symbols, and special words.

#### The two parts of programming language:

#### 1. Syntax  

Syntax defines the rules of how to write valid instructions

#### 2. Semantics

Semantics define the rules of what the instructions mean
   A program is a meaningful sequence of instructions for a computer to carry out.
   Programming or coding is the process of translating an algorithm into a program.

## Reduced C High-Level Programming Language
____
A Program in Reduced C consists of a single function declaration:

```java
int function_name(int var_name1, int var_name2, ...) 
    {
        function_body
    }
```

A function body consists of a list of local variable declarations:

``` java
int var_name1 = literal;
```

and statements, such as:

```javascript
var_name = exp;
while (exp) 
    {
        statements
    }
```

An Expression (`exp`) can be integer (`var`, `3`,`var+1`) or `Boolean` (`var<0`).



 
A program consists of a single function declaration.


A function declaration looks like the following:

### Common Mistakes

### Compiler (RCC)
A compiler is a program that translates high-level programming language instructions into assembly language instructions.

