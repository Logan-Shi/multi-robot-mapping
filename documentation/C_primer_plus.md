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
  
  
