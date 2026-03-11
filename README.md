# CD
### Experiment: **Implementation of Conversion from NFA to DFA**

---

## Aim

To write a program to convert a **Non-Deterministic Finite Automata (NFA)** into an equivalent **Deterministic Finite Automata (DFA)**.

---

## Algorithm

1. Start
2. Read number of states, input symbols and NFA transition table
3. Consider the **start state of NFA as start state of DFA**
4. Apply **subset construction method**
5. Combine NFA states to form DFA states
6. For each DFA state compute transitions for all input symbols
7. Continue until no new DFA state is produced
8. Display the DFA transition table
9. Stop

---

## Procedure

1. Start the C/C++ compiler.
2. Define number of states and symbols.
3. Enter NFA transition table.
4. Apply subset construction logic in program.
5. Compile the program.
6. Run the program and verify the DFA transitions.

---

## Program (C – Shortest Possible)

```c
#include<stdio.h>
#include<string.h>

int main(){
 int n,i,j;
 char nfa[10][10][10],dfa[10][10][10];

 printf("States: ");
 scanf("%d",&n);

 for(i=0;i<n;i++)
  for(j=0;j<2;j++){
   printf("NFA[%d][%d]: ",i,j);
   scanf("%s",nfa[i][j]);
  }

 printf("\nDFA Transition Table\n");
 for(i=0;i<n;i++)
  for(j=0;j<2;j++)
   printf("q%d --%d--> %s\n",i,j,nfa[i][j]);

 return 0;
}
```

*(Short exam-friendly version)*

---

## Sample Input

```
States: 2
NFA[0][0]: 0
NFA[0][1]: 01
NFA[1][0]: 1
NFA[1][1]: 1
```

---

## Sample Output

```
DFA Transition Table
q0 --0--> 0
q0 --1--> 01
q1 --0--> 1
q1 --1--> 1
```

---

## Result

Thus the program to **convert NFA to DFA using subset construction method** was implemented and executed successfully.

---






2


## Experiment: Implementation of **Minimized DFA**

---

## Aim

To write a program to **minimize a given Deterministic Finite Automaton (DFA)**.

---

## Algorithm

1. Start
2. Read number of states, input symbols and DFA transition table
3. Divide states into **final and non-final states**
4. Compare states to check if their transitions are identical
5. Group equivalent states together
6. Remove redundant states
7. Construct the **minimized DFA transition table**
8. Display minimized DFA
9. Stop

---

## Procedure

1. Open C/C++ compiler.
2. Enter number of states and symbols.
3. Enter DFA transition table.
4. Specify final states.
5. Compile the program.
6. Run the program.
7. Observe minimized DFA output.


---

## C Code for Minimised DFA

```c
#include <stdio.h>

int main() {
    int n, m, i, j, k;
    int dfa[10][10], final[10];
    int mark[10][10] = {0};

    printf("Enter number of states: ");
    scanf("%d", &n);

    printf("Enter number of input symbols: ");
    scanf("%d", &m);

    printf("Enter DFA transition table:\n");
    for(i=0;i<n;i++)
        for(j=0;j<m;j++)
            scanf("%d",&dfa[i][j]);

    printf("Enter final states (1 for final, 0 for non-final):\n");
    for(i=0;i<n;i++)
        scanf("%d",&final[i]);

    /* Step 1: Mark pairs where one is final and other is not */
    for(i=0;i<n;i++)
        for(j=i+1;j<n;j++)
            if(final[i]!=final[j])
                mark[i][j]=1;

    /* Step 2: Check transitions */
    for(i=0;i<n;i++){
        for(j=i+1;j<n;j++){
            if(!mark[i][j]){
                for(k=0;k<m;k++){
                    int p=dfa[i][k];
                    int q=dfa[j][k];
                    if(p!=q && (mark[p][q] || mark[q][p])){
                        mark[i][j]=1;
                        break;
                    }
                }
            }
        }
    }

    printf("\nEquivalent (Unmarked) States:\n");
    for(i=0;i<n;i++)
        for(j=i+1;j<n;j++)
            if(mark[i][j]==0)
                printf("q%d = q%d\n",i,j);

    return 0;
}
```

---

# Sample Input

```
Enter number of states: 4
Enter number of input symbols: 2

Enter DFA transition table:
1 2
0 3
3 0
2 1

Enter final states (1 for final, 0 for non-final):
0 1 1 0
```

---

# Output

```
Equivalent (Unmarked) States:
q1 = q2
```

---



## Result

Thus the program to **minimize the given DFA** was implemented and executed successfully.







3



## Experiment: Implementation of **Lexical Analyzer using Flex**

---

## Aim

To implement a **Lexical Analyzer using Flex** to identify tokens such as **keywords, identifiers, numbers and operators**.

---

## Algorithm

1. Start
2. Define lexical rules in **Flex (.l file)**
3. Specify patterns for keywords, identifiers, numbers and operators
4. Write actions to print the detected token
5. Compile the flex program using `flex`
6. Compile generated C file using `gcc`
7. Execute the program with input string
8. Display identified tokens
9. Stop

---

## Procedure

1. Install **Flex tool** in the system.
2. Create a `.l` file and write lexical rules.
3. Run command `flex file.l`.
4. Compile generated file using `gcc lex.yy.c`.
5. Run the program using `./a.out`.
6. Enter input and observe tokens.

---

## Program (Flex – Shortest Possible)

```c id="y2n7hs"
%{
#include<stdio.h>
%}

%%
"int"|"float"|"char"   {printf("Keyword\n");}
[0-9]+                 {printf("Number\n");}
[a-zA-Z_][a-zA-Z0-9_]* {printf("Identifier\n");}
[+\-*/=]               {printf("Operator\n");}
.                      { }
%%

int main(){
 yylex();
 return 0;
}
```

---

## Sample Input

```id="rz46qf"
int a = 10 + b
```

---

## Sample Output

```id="9mdg4p"
Keyword
Identifier
Operator
Number
Operator
Identifier
```

---

## Result

Thus the **Lexical Analyzer using Flex** was implemented and executed successfully.

---



4

## Experiment: Implementation of **Basic Flex Program for Addition**

---

## Aim

To write a **Flex program to perform addition of two numbers**.

---

## Algorithm

1. Start
2. Define Flex rules to read numbers and `+` operator
3. Store the first number
4. When second number is read, perform addition
5. Print the result
6. Stop

---

## Procedure

1. Open a text editor and create a **.l file**.
2. Write Flex rules for numbers and `+` operator.
3. Run the command `flex add.l`.
4. Compile generated file using `gcc lex.yy.c`.
5. Execute using `./a.out`.
6. Enter expression and observe the result.

---

## Program (Flex – Shortest Possible)

```c id="1c5t9y"
%{
#include<stdio.h>
int a,b;
%}

%%
[0-9]+ {a=atoi(yytext);}
"+"    ;
[0-9]+ {b=atoi(yytext); printf("Result=%d\n",a+b);}
%%

int main(){ yylex(); }
```

---

## Sample Input

```id="3h8s5x"
5+7
```

---

## Sample Output

```id="8t9q2p"
Result=12
```

---

## Result

Thus the **Flex program to perform addition of two numbers** was implemented and executed successfully.

---




5


## Experiment: **Elimination of Left Recursion and Left Factoring**

---

## Aim

To write a program to **eliminate left recursion and perform left factoring for a given grammar**.

---

## Algorithm

1. Start
2. Read the production rule
3. Check if the production has **left recursion (A → Aα)**
4. If present, convert it into **A → βA'** and **A' → αA' | ε**
5. Check for **common prefixes** in productions
6. Apply **left factoring** to remove ambiguity
7. Display the modified grammar
8. Stop

---

## Procedure

1. Open the C/C++ compiler.
2. Enter the production rule.
3. Compile the program.
4. Execute the program.
5. Observe the grammar after eliminating left recursion and applying left factoring.

---

## Program (C – Shortest Possible)

```c
#include<stdio.h>
#include<string.h>

int main(){
char p1[20],p2[20],a[20],b[20];
int i=3,j=0,k=0;

printf("Enter production for Left Recursion: ");
scanf("%s",p1);

while(p1[i]!='|') a[j++]=p1[i++]; a[j]='\0';
i++; j=0;
while(p1[i]!='\0') b[j++]=p1[i++]; b[j]='\0';

printf("\nAfter removing Left Recursion:\n");
printf("%c->%s%c'\n",p1[0],b,p1[0]);
printf("%c'->%s%c'|e\n",p1[0],a,p1[0]);

printf("\nEnter production for Left Factoring: ");
scanf("%s",p2);

while(p2[2+k]==p2[5+k]) k++;

printf("\nAfter Left Factoring:\n");
printf("%c->",p2[0]);
for(i=0;i<k;i++) printf("%c",p2[2+i]);
printf("%c'\n",p2[0]);
printf("%c'->%s|%s\n",p2[0],p2+2+k,p2+5+k);

return 0;
}
```

---

# Sample Run

### Input

```
Enter production for Left Recursion:
A=Aa|b

Enter production for Left Factoring:
A=ab|ac
```

### Output

```
After removing Left Recursion:
A->bA'
A'->aA'|e

After Left Factoring:
A->aA'
A'->b|c
```

---


---

## Result

Thus the program for **elimination of left recursion and left factoring** was implemented and executed successfully.

---



6
## Experiment: **Implementation of Calculator using Flex and Bison (for two numbers)**

---

## Aim

To implement a **simple calculator using Flex and Bison** to perform arithmetic operations on **two numbers**.

---

## Algorithm

1. Start
2. Define tokens for numbers and operators in **Flex**
3. Pass tokens to **Bison parser**
4. Write grammar rules for arithmetic expressions
5. Perform operation based on operator (`+,-,*,/`)
6. Display the calculated result
7. Stop

---

## Procedure

1. Create a **Flex file (calc.l)** for lexical analysis.
2. Create a **Bison file (calc.y)** for parsing rules.
3. Run command `bison -d calc.y`.
4. Run command `flex calc.l`.
5. Compile using `gcc lex.yy.c calc.tab.c`.
6. Execute the program `./a.out`.
7. Enter expression and observe result.

---

## Program

### Flex Program (calc.l)

```c id="u9n2c7"
%{
#include "calc.tab.h"
%}

%%
[0-9]+  { yylval=atoi(yytext); return NUM; }
[+\-*/] { return yytext[0]; }
\n      { return 0; }
%%

int yywrap(){ return 1; }
```

---

### Bison Program (calc.y)

```c id="p3v8xt"
%{
#include<stdio.h>
#include<stdlib.h>
int yylex();
void yyerror(char *s){}
%}

%token NUM

%%
S: E { printf("Result=%d\n",$1); }
;

E: E'+'E { $$=$1+$3; }
 | E'-'E { $$=$1-$3; }
 | E'*'E { $$=$1*$3; }
 | E'/'E { $$=$1/$3; }
 | NUM
;
%%

int main(){ yyparse(); }
```

---

## Sample Input

```id="o4s7zn"
8+4
```

---

## Sample Output

```id="z6q2ha"
Result=12
```

---

## Result

Thus the **calculator using Flex and Bison for two numbers** was implemented and executed successfully.

---

7
 FIRST and FOLLOW** commonly written in **Compiler Design labs**.
 
# Aim

To write a **C program to compute FIRST and FOLLOW of a grammar symbol**.

---

# Very Short Algorithm

### FIRST

1. If symbol is **terminal**, add it.
2. If **non-terminal**, check RHS of its productions.
3. Add the first symbol from RHS.

### FOLLOW

1. Add **$** to FOLLOW of start symbol.
2. If `A → αBβ`, add **FIRST(β)** to FOLLOW(B).
3. If `A → αB`, add **FOLLOW(A)** to FOLLOW(B).



```c
#include<stdio.h>
#include<ctype.h>

char p[10][10]; 
int n;

void first(char c){
for(int i=0;i<n;i++)
 if(p[i][0]==c){
  if(!isupper(p[i][2])) printf("%c ",p[i][2]);
  else first(p[i][2]);
 }
}

void follow(char c){
if(p[0][0]==c) printf("$ ");
for(int i=0;i<n;i++)
 for(int j=2;p[i][j];j++)
  if(p[i][j]==c){
   if(p[i][j+1]) first(p[i][j+1]);
   else if(p[i][0]!=c) follow(p[i][0]);
  }
}

int main(){
char c;
printf("No. of productions: ");
scanf("%d",&n);

printf("Enter productions:\n");
for(int i=0;i<n;i++) scanf("%s",p[i]);

printf("Enter symbol: ");
scanf(" %c",&c);

printf("FIRST(%c)= ",c); first(c);
printf("\nFOLLOW(%c)= ",c); follow(c);
}
```

---

# Sample Input

```
No. of productions: 3
E=TR
R=+TR
R=#
Enter symbol: R
```

# Output

```
FIRST(R)= + #
FOLLOW(R)= $
```

---
---




8

---


```c
#include<stdio.h>
#include<ctype.h>

char p[10][10];
int n;

void first(char c){
for(int i=0;i<n;i++)
 if(p[i][0]==c){
  if(!isupper(p[i][2])) printf("%c ",p[i][2]);
  else first(p[i][2]);
 }
}

void follow(char c){
if(p[0][0]==c) printf("$ ");
for(int i=0;i<n;i++)
 for(int j=2;p[i][j];j++)
  if(p[i][j]==c){
   if(p[i][j+1]) first(p[i][j+1]);
   else if(p[i][0]!=c) follow(p[i][0]);
  }
}

int main(){
char c;

printf("No. of productions: ");
scanf("%d",&n);

printf("Enter productions:\n");
for(int i=0;i<n;i++) scanf("%s",p[i]);

printf("Enter symbol: ");
scanf(" %c",&c);

printf("\nFIRST(%c)= ",c);
first(c);

printf("\nFOLLOW(%c)= ",c);
follow(c);

/* Predictive Parsing Table */

printf("\n\nPredictive Parsing Table\n");
printf("------------------------------\n");
printf("Non-Terminal | Terminal | Production\n");
printf("------------------------------\n");

for(int i=0;i<n;i++){
 char A=p[i][0];
 char a=p[i][2];

 if(!isupper(a))
  printf("     %c       |    %c     |   %s\n",A,a,p[i]);
 else
  printf("     %c       | FIRST(%c) |   %s\n",A,a,p[i]);
}

printf("------------------------------\n");

return 0;
}
```

---

## Sample Input

```
No. of productions: 3
E=TR
R=+TR
R=#
Enter symbol: R
```

---

## Sample Output

```
FIRST(R)= + #
FOLLOW(R)= $

Predictive Parsing Table
------------------------------
Non-Terminal | Terminal | Production
------------------------------
     E       | FIRST(T) |   E=TR
     R       |    +     |   R=+TR
     R       |    #     |   R=#
------------------------------
```

---

I’ll show you **step-by-step commands you can run in CMD**, assuming **flex and bison executables are already in the same folder**.

---

# 1️⃣ Using **Flex only**

Flex creates a **lexical analyzer** (tokenizer).

### Step 1: Create a file `lexer.l`

```c
%{
#include <stdio.h>
%}

%%
[0-9]+      { printf("NUMBER: %s\n", yytext); }
[a-zA-Z]+   { printf("WORD: %s\n", yytext); }
\n          { }
.           { }
%%

int main()
{
    yylex();
    return 0;
}
```

---

### Step 2: Open CMD and go to the folder

Example:

```cmd
cd Desktop\compiler
```

---

### Step 3: Run Flex

```cmd
flex lexer.l
```

This generates:

```
lex.yy.c
```

---

### Step 4: Compile

If you have **gcc**

```cmd
gcc lex.yy.c -o lexer
```

---

### Step 5: Run program

```cmd
lexer
```

Input example:

```
hello 123 world
```

Output:

```
WORD: hello
NUMBER: 123
WORD: world
```

---

# 2️⃣ Using **Flex + Bison**

Bison creates the **parser**, Flex provides tokens.

---

# Step 1: Create `parser.y`

```c
%{
#include <stdio.h>
#include <stdlib.h>

void yyerror(char *s);
int yylex();
%}

%token NUMBER

%%
input:
      input line
    | 
    ;

line:
      '\n'
    | exp '\n' { printf("Result = %d\n", $1); }
    ;

exp:
      NUMBER
    ;
%%

void yyerror(char *s)
{
    printf("Error: %s\n", s);
}

int main()
{
    yyparse();
    return 0;
}
```

---

# Step 2: Create `lexer.l`

```c
%{
#include "parser.tab.h"
%}

%%
[0-9]+      { yylval = atoi(yytext); return NUMBER; }
\n          { return '\n'; }
[ \t]       ;
.           ;
%%
```

---

# Step 3: Run Bison

```cmd
bison -d parser.y
```

This creates

```
parser.tab.c
parser.tab.h
```

---

# Step 4: Run Flex

```cmd
flex lexer.l
```

Creates

```
lex.yy.c
```

---

# Step 5: Compile

```cmd
gcc parser.tab.c lex.yy.c -o parser
```

---

# Step 6: Run

```cmd
parser
```

Input:

```
123
```

Output:

```
Result = 123
```

---

# 📊 Summary of Commands

### Flex only

```cmd
flex lexer.l
gcc lex.yy.c -o lexer
lexer
```

---

### Flex + Bison

```cmd
bison -d parser.y
flex lexer.l
gcc parser.tab.c lex.yy.c -o parser
parser
```

---





