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
>> can be used as string initialization, returns target  
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




