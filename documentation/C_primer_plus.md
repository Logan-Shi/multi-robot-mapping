## Chap. 4: Charater Strings and Formatted Input/Output

### Input

* stdio.h:  
> scanf();  
> getchar();  
> gets();  
>>  It reads an entire line up through the newline character, discards the newline character, stores the remaining characters, adding a null character to create a C string. __Dangerous__, can cause *buffer overflow*.   
>> ``` 
>>  char words[STR_LEN];   
>>  gets(words);
>> ```  
> fgets();  
>> It takes a second argument indicating the maximum number of characters to read.  
>> If fgets() reads the newline, it stores it in the string, unlike gets(), which discards it.     
>> It takes a third argument indicating which file to read.    
>> ```  
>>  char words[STR_LEN];
>>  fgets(words, STR_LEN,stdin); //stdin for standard input to read from keyboard.
>> ```
> gets_s();  
>> ```
>>  gets_s(words, STR_LEN);//need to implement handler
>> ```


### Output

* stdio.h:  
> printf();  
> putchar();  
> puts();  
>> paired with gets(), displays a string, adding a newline.  
>> ```
>>  puts(words);//print until NULL('\0')
>> ```  
> fputs();  
>> paired with fgets(), displays a string to desired output without adding a newline.  
>> ```
>>  fputs(words,stdout);
>> ```

### Other Functions

* string.h:  
> strlen(words);  
> strcat();  
>> append add_on to original string, can cause *buffer overflow*,returns string    
>> ```
>>  strcat(string, add_on); 
>> ```
> strncat();  
>> append add_on to original string, discard content exceeding SIZE, returns string    
>> ```
>>  strncat(string, add_on, SIZE); 
>> ```
> strcmp();  
>> returns a nagative number if the first string comes before the second alphabetically    
>> returns 0 if they are the same      
>> returns a positive number if the first string comes after the second alphabetically  
>> ```
>>  while(!strcmp(string_A, string_b))
>>    puts("Same!");  
>> ```
> strncmp();  
>> ```
>>  strncmp("astronomy", "astrology", 5) == 0;
>> ```
> strcpy();  
>> can be used as string assignment, returns target  
>> ```
>>  strcpy(target, source);
>> ```
> strncpy();  
>> 
>> ```
>>  strncpy(target, source, SIZE - 1);
>>  target[SIZE - 1] = '\0';  //strnpy() might discard NULL
>> ```
> strchr();  
> ...  

* stdio.h:  
> sprintf();  
>> "print" into target  
>> ```
>>  sprintf(target, "%s, %-19s: $%6.2f\n", string_A, string_B, float_A);
>> ```

* ctype.h:  
> toupper();  
> ...  

## Chap. 7: C Control Statements: Branching and Jumps

* ?: (ternary)  
> *expression_1* ? *expression_2* : *expression_3*  
> The value of the whole expression equals the value of *expression_2* if *expression_1* is true. Otherwise, it equals the value of 
*expression_3* .  

## Chap. 10: Arrays and Pointers

* concept to remember:  
> \*(\*(zippo+2)+1) == zippo[2][1]

* compound literals:   
> int (\*pt)\[4\]; // declare a pointer to an array of 4-int arrays  
> pt = (int \[2\]\[4\]) { {1, 2, 3, -9}, {4, 5, 6, -8} };

* variable-lenth array:   
> void use_a_VLA(int n, int m, ar[n][m]);    

## Chap. 11: Character Strings and String Functions 

### About Strings

* string literals:  
> *const* char \* pClub = "Chelsea";   
> //so that "Chelsea" won't be changed accidentally with `pClub[0] = 'P';`.     
> char title[] = "16-17 Premier League Champion";  
> //copy to string 'title' to alter contents.  

* An array of pointers to strings(`const char *pStrings[LIST_NUM]`) takes up less space, but an array of `char` arrays(`char strings[LIST_NUM][STRING_LENGTH]`) can alter contents.  

* wild pointer: 
> char \* pWild;      //unintialized pointer  
> scanf("%s", pWild); //ended up screwing up something else  

### Command-Line Argumants

```
int main(int argc, char **argv)
{
  statements;
  return 0;
}
```

* argc for *argument count*  
* argv for *argument value*  
* example:  C> demo.exe --help  
> argc == 2  
> argv[0] == "demo.exe"  (for most systems)  
> argv[1] == "--help"  

### String-to-Number Conversions

* stdlib.h:  
> int atoi(char \* );  
> double atof(char \*);  
> long atol(char \*);  
> strtol();  
> strtoul();  
> strtod();   
>> long strtol(const char * restrict nptr, char ** restrict endptr, int base);  

## Chap. 12 Storage Classed, Linkage, and Memory Management

* scope: the region or regions of a program that can access an identifier  
  - block scope: local variables' region  
  - function scope: something about `goto`    
  - function prototype scope: in declaration of functions  
  - file scope: global variables' region  
  
* linkage:   
  - external linkage: can be used anywhere in a multiple program    
  - internal linkage: can be used anywhere in a single translation unit (a source file plus its included header files)  
  - no linkage: other than file scope variables   

* storage duration: persistence of the objects accessed by identifiers   
  - static duration: exists throughout program execution   
  - thread duration: exists in the thread      
  - automatic duration: usually in a block  
  - allocated duration: allocated deliberately    
  
* storage class:  

|  __Storage Class__   | __Duration__  | __Scope__ |__Linkage__|__How Declared__                                  |
|  :----------------:  | :----------:  | :-------: | :-------: | :----------------------------------------------- |
| automatic            | Automatic     |Block      |None       |In a block                                        |
| register             | Automatic     |Block      |None       |In a block with keyword *register*                |
| static with external linkage|Static  |File       |External   |Outside of all functions                          |
| static with internal linkage|Static  |File       |Internal   |Outside of all functions with the keyword *static*|
| static with no linkage|Static        |Block      |None       |In a block with the keyword *static*              |

* storage classed and functions:    
  - double gamma(double); // external by default     
  - static double beta(int, int);   
  - extern double delta(double, int);
  - beta() is restricted to one file
  
* random-number:    
  - stdlib.h & time.h:  
  > rand();  
  >> returns int from 0 to RAND_MAX   
  >> ```
  >>  rand() % base + 1; // generate random number from 1 to base  
  >> ```
  > srand((unsigned int) time(0));  
  >> setup seed  
  
* allocated memory:  
  - stdlib.h:  
  > malloc();  
  >> it's possible that malloc() fails to allocate available memory and return NULL  
  >> ```
  >>  double * pDouble;
  >>  pDouble = (double * ) malloc (30 * sizeof(double));  
  >> ``` 
  > free();  
  >> must use to prevent *memory leak*  
  >> ```
  >>  free(pDouble);
  >> ```
  > calloc();  
  >> sets all the bits in the block to zero
  >> ```
  >>  long * pLong;
  >>  pLong = (long * ) calloc (100, sizeof (long));
  >> ```
  > exit();  
  >> exit(EXIT_FAILURE);  
  
* type qualifiers:  
  - const:  
   ```
    const float * pf; // or
    float const * pf; // * pf = 1.0 is invalid
    float * const pf; // pf = & other_address is invalid
   ```
   usage:  
   + to protect array data:  
   ```
   char *strcat(char * restrict s1, const char * restrict s2);
   ```
   + to protect global data;  
   ```
   /* constant.h -- defines some global constants */
   static const double PI = 3.14159;
   
   /* file1.c -- use global constants defined elsewhere */  
   #include "constant.h"    
   
   /* file2.c -- use global constants defined elsewhere */  
   #include "constant.h"
   ```
  
  - volatile:  
   identifier with keyword volatile tells the compiler that a variable can have its value altered by agencies other than the program. It is typically used for hardware addresses and for data shared with other programs or threads running simultaneously. it helps the compiler to cache unchanged data to register therefore speed up execution.
   
  - restrict:  
   It can be applied only to pointers, and it indicates that a pointer is the sole initial means of accessing a data object.  
   
  - \_Atomic:  
  used in concurrent programming.  defined in `stdatomic.h` and  `threads.h`
  
## Chap. 13 File Input/Output
  
  - stdio.h:  
  > fopen();  
  >> returns a FILE pointer if successful, ohterwise returns NULL   
  >> ```
  >>  FILE * fp;
  >>  if((fp = fopen(file_name,"r")) == NULL)
  >>    printf("Can't open %s\n",argv[1]);
  >> ```
  > fclose();  
  >> returns 0 if successful, and EOF if not  
  >> ```
  >>  if(fcloce(fp) != 0)
  >>    printf("Error in closing file &s\n",argv[1]);
  >> ```
  > getc();  
  >> get from fp
  >> ```
  >>  ch = getc(fp);
  >> ```
  > putc();  
  >> print to fpout  
  >> ```
  >>  putc(ch, fpout);
  >> ```
  > fprintf();  
  >> ```
  >>  fprintf(stderr,"Can't create output file.\n");
  >> ```
  > fscanf();  
  >> ```
  >>  fscanf(stdin, "%40s", words)
  >> ```
  > fgets();  
  > fputs();  discussed in Chap. 4  
  > fseek();  
  >> offset: how far to move from the starting point  
  >> mode: SEEK_SET, SEEK_CUR, SEEL_END  
  >> returns 0 if no error occured, -1 if not  
  >> ```
  >>  fseek(fp, 0L, SEEK_SET);   // go to the beginning of the file  
  >>  fseek(fp, 10L, SEEK_SET);  // go 10 bytes into the file  
  >>  fseek(fp, 2L, SEEK_CUR);   // advance 2 bytes from the current position  
  >>  fseek(fp, 0L, SEEK_END);   // go to the end of the file  
  >>  fseek(fp, -10L, SEEK_END); // back up 10 bytes from the end of the fil
  >> ```
  > ftell();  
  >> return (long) current file location  
  >> ```
  >>  cursor = ftell(fp);
  >> ```
  > fgetpos();  
  >> ```
  >>  int fgetpos(FILE * restrict stream, fpos_t * restrict pos);
  >> ```
  > fsetpos();   
  >> ```
  >>  int fsetpos(FILE * stream, const fpos_t * pos);  
  >> ```
  > ...  
  
## Chap. 14 Strutures and Other Data Forms  

* flexible array member  
> - rules  
>>  1. The flexible array member must be the last member of the structure. 
>>  2. There must be at least one other member  
> - example  
>> ```
>> struct flex
>> {
>>   size_t count;
>>   double average;
>>   double scores[]; // flexible array member
>> };
>> 
>> struct flex * pf;
>> pf = malloc(sizeof(struct flex) + 5 * sizeof(double));
>>
>> pf->count = 5;
>> pf->scores[2] = 18.5;
>> ```

* Unions  
> ```
> union hold
> {
> int digit;
> double bigfl;
> char letter;
> };
>
> union hold valA;
> valA.letter = 'R';
> union hold valB = valA; // initialize one union to another
> union hold valC = {88}; // initialize digit member of union
> union hold valD = {.bigfl = 118.2}; // designated initializer
> ```

* enumerated types
> ```
> enum spectrum {red, orange, yellow, green, blue, violet};
> enum spectrum color;
>
> color = blue;
> if (color == yellow)
>   ...;
> ```

* typedef  
> ```
> typedef struct complex
> {
>   float real;
>   float imag;
> } COMPLEX;
> ```

* functions and pointers    
> ```
> void ToUpper(char *);
> void (*pf)(char *)； // pf is a pointer-to-function
> pf = ToUpper;
> (*pf)(mis); // same as ToUpper(mis)
> pf(mis); // also the same
> ```

## Chap. 15 Bit Fiddling  
### bit logical operators  
* bitwise nagation: ~  
> ~(10011010) // expression  
>  (01100101) // result  

* bitwise AND: &  
> (10010011) & (00111101) // expression    
> (00010001) // result  

* bitwise OR: |  
> (10010011) | (00111101)  // expression  
> (10111111) // result  

* bitwise XOR: ^  
> (10010011) ^ (00111101) // expression  
> (10101110) // result if different then 1  

#### usage  
* mask: 
> ```
> flag &= MASK;
> ch &= 0xff;
> ch &= 0377;
> ```

* setting bits:  
> ```
> flags |= MASK;
> ```

* clearing bits:  
> ```
> flags &= ~MASK;
> ```

* toggling bits:  
> ```
> flags ^= MASK;
> ```

* checking the value of bit:  
> ```
> if ((flags & MASK) == MASK)
>   puts("flags are set correctly with MASK's ones")
> ```

### bit shift operators  
* left shift: <<  
> ```
> (10001010) << 2 // expression
> (00101000) // result 
> ```

* right shift: >>  
> ```
> (10001010) >> 2 // expression
> (00100010) // result could be (11100010) because some systems fill the vacated with the leftmost bit for unsigned value
> ```

### bit fields
* examples:  
> ```
> struct box_props {
>   bool opaque               : 1; // or unsigned int (pre C99)
>   unsigned int fill_color   : 3;
>   unsigned int              : 4; // use unamed field to place fill-related information in one byte and border-related information in the other one
>   bool show_border          : 1;
>   unsigned int border_color : 3;
>   unsigned int border_style : 2;
>   unsigned int              : 2;
> };
> ```

## Chap. 16 The C Preprocessor and the C Library  


