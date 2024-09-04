instruction:  How Declare a fixed binary variable in PL/1.

input:   

output:

    DECLARE x FIXED BINARY(31); 

instruction:  Declare a character string variable in PL/1.

input:   

output:

    DECLARE name CHAR(20); 

instruction:  Declare a decimal floating-point variable in PL/1.

input:   

output:

    DECLARE price DECIMAL(7,2); 

instruction:  Declare an array of integers in PL/1.

input:   

output:

    DECLARE arr(10) FIXED BINARY(31); 

instruction:  Declare a structure with integer and character fields in PL/1.

input:   

output:

    DECLARE 1 person,
        2 id FIXED BINARY(31),
        2 name CHAR(20); 

instruction:  Declare a pointer variable in PL/1.

input:   

output:

    DECLARE p POINTER; 

instruction:  Declare a variable as input in PL/1.

input:   

output:

    DECLARE x INPUT; 

instruction:  Declare a string with varying length in PL/1.

input:   

output:

    DECLARE description CHAR VARYING(100); 

instruction:  Declare a procedure in PL/1.

input:   

output:

    PROCEDURE main;
        DECLARE x FIXED BINARY(31);
        DECLARE y CHAR(20);
        /* procedure body */
    END main; 

instruction:  Declare a floating-point variable in PL/1.

input:   

output:

    DECLARE rate FLOAT; 

instruction:  Declare a constant variable in PL/1.

input:   

output:

    DECLARE Pi FIXED DEC(5,2) INIT(3.14); 

instruction:  Declare an array of character strings in PL/1.

input:   

output:

    DECLARE names(5) CHAR(20); 

instruction:  Declare a nested structure in PL/1.

input:   

output:

    DECLARE 1 address,
        2 street CHAR(50),
        2 city CHAR(30),
        2 zipcode FIXED BINARY(5); 

instruction:  Declare a union in PL/1.

input:   

output:

    DECLARE 1 data UNION,
        2 int FIXED BINARY(31),
        2 float FLOAT; 

instruction:  Declare a static variable in PL/1.

input:   

output:

    DECLARE count STATIC FIXED BINARY(31); 

instruction:  Declare an external procedure in PL/1.

input:   

output:

    DECLARE EXTERNAL ENTRY 'externalProc'; 

instruction:  Declare an input-output file in PL/1.

input:   

output:

    DECLARE file1 FILE RECORD INPUT OUTPUT; 

instruction:  Declare an internal file in PL/1.

input:   

output:

    DECLARE file2 FILE RECORD; 

instruction:  Declare a controlled variable in PL/1.

input:   

output:

    DECLARE i CONTROLLED FIXED BINARY(31); 

instruction:  Declare a variable with initial value in PL/1.

input:   

output:

    DECLARE counter FIXED BINARY(31) INIT(0); 

instruction:  Declare a string variable with an initial value in PL/1.

input:   

output:

    DECLARE message CHAR(50) INIT('Hello, World!'); 

instruction:  Declare a fixed decimal variable in PL/1.

input:   

output:

    DECLARE amount FIXED DECIMAL(10,2); 

instruction:  Declare a variable with a picture clause in PL/1.

input:   

output:

    DECLARE phone CHAR(10) PICTURE '999-999-9999'; 

instruction:  Declare a label variable in PL/1.

input:   

output:

    DECLARE start LABEL; 

instruction:  Declare a based variable in PL/1.

input:   

output:

    DECLARE p BASED; p = ADDR(x); 

instruction:  Declare an automatic variable in PL/1.

input:   

output:

    DECLARE total AUTOMATIC FIXED BINARY(31); 

instruction:  Declare an aligned variable in PL/1.

input:   

output:

    DECLARE alignedVar ALIGNED FIXED BINARY(31); 

instruction:  Declare a structure with varying length string in PL/1.

input:   

output:

    DECLARE 1 employee,
        2 id FIXED BINARY(31),
        2 name CHAR VARYING(50); 

instruction:  Declare a character variable initialized with null in PL/1.

input:   

output:

    DECLARE nullChar CHAR(1) INIT('00'x); 

instruction:  Declare a binary floating-point variable in PL/1.

input:   

output:

    DECLARE value FLOAT BINARY; 

instruction:  Declare a variable with dimension and bounds in PL/1.

input:   

output:

    DECLARE matrix(1:10, 1:10) FIXED BINARY(31); 

instruction:  Declare a variable as external in PL/1.

input:   

output:

    DECLARE counter EXTERNAL FIXED BINARY(31); 

instruction:  Declare a static constant in PL/1.

input:   

output:

    DECLARE Pi STATIC FIXED DEC(5,2) INIT(3.14); 

instruction:  Declare a procedure with parameters in PL/1.

input:   

output:

    PROCEDURE add(a FIXED BINARY(31), b FIXED BINARY(31)) RETURNS(FIXED BINARY(31));
        RETURN a + b;
    END add; 

instruction:  Declare a table with index in PL/1.

input:   

output:

    DECLARE table(100) FIXED BINARY(31);
    DECLARE idx FIXED BINARY(31);
    DO idx = 1 TO 100;
        table(idx) = idx * 2;
    END; 

instruction:  Declare a structure with nested arrays in PL/1.

input:   

output:

    DECLARE 1 school,
        2 classes(10),
        3 students(30) CHAR(50); 

instruction:  Declare a variable with alignment and initial value in PL/1.

input:   

output:

    DECLARE value ALIGNED FIXED DECIMAL(10,2) INIT(100.00); 

instruction:  Declare a based variable with initial address in PL/1.

input:   

output:

    DECLARE p BASED INIT(ADDR(x)); 

instruction:  Declare a structure with varying array size in PL/1.

input:   

output:

    DECLARE 1 department,
        2 deptName CHAR(50),
        2 employee(*) CHAR(50); 

instruction:  Declare a variable with an initial value using hexadecimal in PL/1.

input:   

output:

    DECLARE flag FIXED BINARY(31) INIT('0A'x); 

instruction:  Declare an input-only file in PL/1.

input:   

output:

    DECLARE fileIn FILE RECORD INPUT; 

instruction:  Declare a structure with union in PL/1.

input:   

output:

    DECLARE 1 record,
        2 id FIXED BINARY(31),
        2 info UNION,
        3 name CHAR(20),
        3 age FIXED BINARY(31); 

instruction:  Declare a label and a goto statement in PL/1.

input:   

output:

    DECLARE start LABEL;

    start:
        /* code */
        GOTO start; 

instruction:  Declare a parameter as varying length in PL/1.

input:   

output:

    PROCEDURE processData(data CHAR VARYING(100));
        /* procedure body */
    END processData; 

instruction:  Declare a controlled variable with initial value in PL/1.

input:   

output:

    DECLARE i CONTROLLED FIXED BINARY(31) INIT(1); 

instruction:  Declare a file with organization and access mode in PL/1.

input:   

output:

    DECLARE dataFile FILE RECORD ORGANIZATION SEQUENTIAL ACCESS MODE SEQUENTIAL; 

instruction:  Declare a constant character string in PL/1.

input:   

output:

    DECLARE greeting CHAR(20) INIT('Hello'); 

instruction:  Declare an external variable in PL/1.

input:   

output:

    DECLARE total EXTERNAL FIXED BINARY(31); 

instruction:  Declare a parameterized structure in PL/1.

input:   

output:

    DECLARE 1 person(n),
        2 name CHAR(n),
        2 age FIXED BINARY(31); 

instruction:  Declare a file with keyed access in PL/1.

input:   

output:

    DECLARE keyedFile FILE RECORD ORGANIZATION INDEXED ACCESS MODE DYNAMIC; 

instruction:  Declare a static variable with initial value in PL/1.

input:   

output:

    DECLARE counter STATIC FIXED BINARY(31) INIT(100); 

instruction:  Declare a decimal variable with picture clause in PL/1.

input:   

output:

    DECLARE salary DECIMAL(9,2) PICTURE '9999999.99'; 

instruction:  Declare a structure with static array in PL/1.

input:   

output:

    DECLARE 1 company,
        2 dept(5) CHAR(20); 

instruction:  Declare a simple procedure to add two numbers in PL/1.

input:   

output:

    PROCEDURE addTwoNumbers(a FIXED BINARY(31), b FIXED BINARY(31)) RETURNS(FIXED BINARY(31));
        DECLARE sum FIXED BINARY(31);
        sum = a + b;
        RETURN sum;
    END addTwoNumbers; 

instruction:  Declare a procedure to calculate the factorial of a number in PL/1.

input:   

output:

    PROCEDURE factorial(n FIXED BINARY(31)) RETURNS(FIXED BINARY(31));
        DECLARE result FIXED BINARY(31) INIT(1);
        DECLARE i FIXED BINARY(31);
        DO i = 1 TO n;
            result = result * i;
        END;
        RETURN result;
    END factorial; 

instruction:  Declare a structure with nested records in PL/1.

input:   

output:

    DECLARE 1 student,
        2 id FIXED BINARY(31),
        2 name CHAR(50),
        2 address,
            3 street CHAR(50),
            3 city CHAR(30),
            3 zipcode FIXED BINARY(10); 

instruction:  Declare a procedure to find the maximum of an array in PL/1.

input:   

output:

    PROCEDURE findMax(arr() FIXED BINARY(31)) RETURNS(FIXED BINARY(31));
        DECLARE max FIXED BINARY(31) INIT(arr(1));
        DECLARE i FIXED BINARY(31);
        DO i = 2 TO EXTENT(arr);
            IF arr(i) > max THEN max = arr(i);
        END;
        RETURN max;
    END findMax; 

instruction:  Declare a file with sequential access mode in PL/1.

input:   

output:

    DECLARE inputFile FILE RECORD INPUT;
    DECLARE line CHAR(100);
    OPEN FILE(inputFile);
    DO WHILE (NOT ENDFILE(inputFile));
        READ FILE(inputFile) INTO(line);
        PUT SKIP LIST(line);
    END;
    CLOSE FILE(inputFile); 

instruction:  Declare a structure with varying length arrays in PL/1.

input:   

output:

    DECLARE 1 company,
        2 name CHAR(50),
        2 employees(*),
            3 id FIXED BINARY(31),
            3 name CHAR(50),
            3 position CHAR(30); 

instruction:  Declare a procedure to reverse a string in PL/1.

input:   

output:

    PROCEDURE reverseString(input CHAR(100)) RETURNS(CHAR(100));
        DECLARE output CHAR(100);
        DECLARE i FIXED BINARY(31);
        DO i = 1 TO LENGTH(input);
            SUBSTR(output, i, 1) = SUBSTR(input, LENGTH(input) - i + 1, 1);
        END;
        RETURN output;
    END reverseString; 

instruction:  Declare a procedure to sort an array using bubble sort in PL/1.

input:   

output:

    PROCEDURE bubbleSort(arr() FIXED BINARY(31));
        DECLARE i, j FIXED BINARY(31);
        DECLARE temp FIXED BINARY(31);
        DO i = 1 TO EXTENT(arr) - 1;
            DO j = 1 TO EXTENT(arr) - i;
                IF arr(j) > arr(j+1) THEN DO;
                    temp = arr(j);
                    arr(j) = arr(j+1);
                    arr(j+1) = temp;
                END;
            END;
        END;
    END bubbleSort; 

instruction:  Declare a nested structure with varying length strings in PL/1.

input:   

output:

    DECLARE 1 department,
        2 deptName CHAR(50),
        2 employees(*),
            3 empName CHAR VARYING(100),
            3 empID FIXED BINARY(31); 

instruction:  Declare a procedure to count vowels in a string in PL/1.

input:   

output:

    PROCEDURE countVowels(input CHAR(100)) RETURNS(FIXED BINARY(31));
        DECLARE count FIXED BINARY(31) INIT(0);
        DECLARE i FIXED BINARY(31);
        DO i = 1 TO LENGTH(input);
            IF SUBSTR(input, i, 1) IN ('A', 'E', 'I', 'O', 'U', 'a', 'e', 'i', 'o', 'u') THEN
                count = count + 1;
        END;
        RETURN count;
    END countVowels; 

instruction:  Declare a file with indexed access mode in PL/1.

input:   

output:

    DECLARE dataFile FILE RECORD ORGANIZATION INDEXED ACCESS MODE DYNAMIC;
    DECLARE record CHAR(100);
    OPEN FILE(dataFile);
    LOCATE FILE(dataFile) KEY IS record;
    READ FILE(dataFile) INTO(record);
    CLOSE FILE(dataFile); 

instruction:  Declare a procedure to merge two sorted arrays in PL/1.

input:   

output:

    PROCEDURE mergeArrays(arr1() FIXED BINARY(31), arr2() FIXED BINARY(31)) RETURNS(FIXED BINARY(31)(*));
        DECLARE result(EXTENT(arr1) + EXTENT(arr2)) FIXED BINARY(31);
        DECLARE i, j, k FIXED BINARY(31) INIT(1);
        DO WHILE (i <= EXTENT(arr1) AND j <= EXTENT(arr2));
            IF arr1(i) <= arr2(j) THEN
                result(k) = arr1(i);
                i = i + 1;
            ELSE
                result(k) = arr2(j);
                j = j + 1;
            k = k + 1;
        END;
        DO WHILE (i <= EXTENT(arr1));
            result(k) = arr1(i);
            i = i + 1;
            k = k + 1;
        END;
        DO WHILE (j <= EXTENT(arr2));
            result(k) = arr2(j);
            j = j + 1;
            k = k + 1;
        END;
        RETURN result;
    END mergeArrays; 

instruction:  Declare a procedure to convert a string to uppercase in PL/1.

input:   

output:

    PROCEDURE toUpperCase(input CHAR(100)) RETURNS(CHAR(100));
        DECLARE output CHAR(100);
        DECLARE i FIXED BINARY(31);
        DO i = 1 TO LENGTH(input);
            IF SUBSTR(input, i, 1) IN ('a', 'z') THEN
                SUBSTR(output, i, 1) = SUBSTR(input, i, 1) - 'a' + 'A';
            ELSE
                SUBSTR(output, i, 1) = SUBSTR(input, i, 1);
        END;
        RETURN output;
    END toUpperCase; 

instruction:  Declare a nested structure with varying length arrays and strings in PL/1.

input:   

output:

    DECLARE 1 organization,
        2 name CHAR(50),
        2 departments(*),
            3 deptName CHAR VARYING(100),
            3 employees(*),
                4 empName CHAR VARYING(100),
                4 empID FIXED BINARY(31); 

instruction:  Declare a procedure to perform matrix multiplication in PL/1.

input:   

output:

    PROCEDURE matrixMultiply(a(,) FIXED BINARY(31), b(,) FIXED BINARY(31)) RETURNS(FIXED BINARY(31)(,));
        DECLARE i, j, k FIXED BINARY(31);
        DECLARE c(DIM(a,1), DIM(b,2)) FIXED BINARY(31) INIT(0);
        DO i = 1 TO DIM(a,1);
            DO j = 1 TO DIM(b,2);
                DO k = 1 TO DIM(a,2);
                    c(i,j) = c(i,j) + a(i,k) * b(k,j);
                END;
            END;
        END;
        RETURN c;
    END matrixMultiply; 

instruction:  Declare a structure to represent a library system in PL/1.

input:   

output:

    DECLARE 1 library,
        2 books(*),
            3 title CHAR(100),
            3 author CHAR(50),
            3 ISBN CHAR(13),
        2 members(*),
            3 name CHAR(50),
            3 memberID FIXED BINARY(31);
            3 borrowedBooks(*) CHAR(13); 

instruction: write a code to compute the largest of 3 float binary numbers x,y and z in PL/1.

input:  

output:

    /***************************************/
    /* This program computes the largest of three */
    /* FLOAT BINARY numbers x, y, and z*/
    /******************************************
    test:
        procedure options (main);
        declare
            (a,b,c) float binary;
        put list ('Type Three Numbers: ');
        get list (a,b,c);
        put list ('The Largest Value is',max3(a,b,c));
        /* this procedure computes the largest of x,y, and z*/
        max3:
            procedure (x,y,z)
            returns(float binary);
            declare
                (x,y,z,max) float binary;
            if x>y then
                if x >z then
                    max=x;
                else
                    max = z;
            else
                if y>z then
                    max = y;
                else
                    max=z;
            return(max);
        end max3;
    end test; 



instruction: write a code for compilation of demo using $N switch in PL/1.

input:  

output:

 
    demo:
        procedure options(main);
        declare
            name character(20) varying;
        put skip(2) list('PLEASE ENTER YOUR FIRST NAME: ');
        get list(name);
        put skip(2) list('HELLO '::name::', WELCOME TO PL/1'):
    demo;
 

instruction: write a polynomial evalution program in PL/1.

input:  

output:

 
    /**************************************************/
    /* This program evaluates a polynomial expression */
    /* using FLOAT BINARY data. */
    /**************************************************/
    fltpoly:
        procedure options(main);
        
        %replace 
            true by '1'b;
        declare
            (x,y,z) float binary(24);
        do while(true);
            put skip(2) list('Type x,y,z: ');
            get list(x,y,z);
            
            if x=0 & y=0 & z=0 then
                stop;
            put skip list('    2');
            put skip list('    x+2y+z=',P(x,y,z));
            end;
            P:
                procedure (x,y,z) returns (float binary(24));
                declare
                    (x,y,z) float binary;
                return(x*x+2*y+z);
            end P;
    end fltpoly;

 

instruction: write a polynomial evalution program using fixed decimal in PL/1.

input:  

output:

 
    /**********************************************/
    /* This program evaluates a polynomial expression using FIXED DECIMAL data.*/
    /**********************************************/

    decpoly:
        procedure options (main);
        %replace
            true by '1'b;
        declare
            (x,y,z) fixed decimal (15,4);
        do while (true);
            put skip(2) list('Type x,y,z: '); 
            get list(x,y,z);
            if x=0 & y=0 & z=0 then
                stop;
            put skip list('    2');
            put skip list('    x+2y+z=',P(x,y,z));
            end;
            P:
                procedure (x,y,z) returns (fixed decimal (15,4));
                declare
                    (x,y,z) fixed decimal(15,4);
                return(x*x+2*y+z);
            end P;
    end decpoly
 

instruction: can you write a sample code for the optimist programin PL/1? 

input:  

output:

    /**************************************************/
    /* This program demonstrates PL/1 character string*/
    /* processing by turning a negative sentence into a */
    /* positive one. 								*/
    /***********************************************************/
    optimist:
        procedure options (main);
        %replace
            true by '1'b, 
            false by '0'b, 
            nwords by 5;
        declare
            negative (1:nwords) character (8) varying static initial 
                (' never',' none', ' nothing',' not', ' no'),
            Positive (1:nwords) character(10) varying static initial
                (' always', ' all',' something',' ''' some'), 
            upper character (28) static initial
                ('ABCDEFGHIJKLMNOPORSTUVWXYZ, ') ,
            lower character (28) static initial
                ('abodefghijklmnoparstuvwxyz. '),
            sent character (254) varying,
            word character (32) varying, 
            (I,j) fixed;

        do while(true);
            put skip list('What’s up? ');
            sent = '	';
            do while
                (substr(sent,length(sent)) ^= ‘.’);
                get list (word) ;
                sent = sent !! ‘ ’ !! word;
            end;
            sent = translate(sent, lower,upper) i
            if verify(sent, lower) ^= 0 then
                sent = ‘ that’ is an interesting idea,';
            do i = 1 to nwords;
                j= indextsent negative (il);
                if j^= 0 then
                    sent = substr(sent,1,j-1) !!
                positive (i) !! 
                substr(sent,j+length (negative (i)));
            end;
            put list('Actually,'!!sent);
            put skip;
        end;
    end optimist;
 

instruction: What is FSCAN program in PL/1? 

input:  

output:

    FSCAN demonstrates the embedded subroutine called GNT, Get Next Token, which parses an input line into separate items called tokens. Once you test GNT, you can extract it from this program and put it into a production program where required. 

instruction: Write the FSCAN program in PL/1. 

input:  

output:

    /**************************************************/
    /* This program tests the procedure called GNT, a */
    /* free-field scanner (parser) that reads a line  */
    /* of input and breaks it into individual parts.  */
    /**************************************************/
    fscan:
    procedure options(Main);
        %replace
            true by '1'b;
        declare 
            token character(80) varying static initial('');

        GNT:
            procedure;
            declare
            i fixed;
            line character(80) varying static initial('');

            line = substr(line,length(token)+1);
            do while(true);
            if line = '' then
                get edit(line) (a);

            i = verify(line, ' ');
            if i = 0 then
                line = '';
            else
            do;
                line = substr(line, i);
                i = verify(line, '0123456789.');
                if i = 0 then
                token = line;
                else
                if i = 1 then
                token = substr(line, 1, 1);
                else
                token = substr(line, 1, i-1);
                return;
            end;
            end;
        end GNT;

        do while(true);
            call GNT;
            put edit('''' !! token !! '''') (x(1), a);
        end;
    end fscan;
    
instruction: Write a PL/1 program to read a sentence and reverse it. 

input:  

output:

    /**************************************************/
    /* This program reads a sentence and reverses it. */
    /**************************************************/
    reverse:
    procedure options(Main);
    declare
        sentence pointer,
        1 wordnode based (sentence),
        2 word character(35) varying,
        2 next pointer;

    do while('1'b);
        call read_it();
        if sentence = null then
        stop;
        call write_it();
    end;

    read_it:
        procedure;
        declare
        newword character(35) varying,
        newnode pointer;

        sentence = null;
        put skip list('What''s up?');
        do while('1'b);
        get list(newword);
        if newword = '.' then
            return;
        allocate wordnode set(newnode);
        newnode->next = sentence;
        sentence = newword;
        word = newnode;
        end;
    end read_it;

    write_it:
        procedure;
        declare
        p pointer;

        put skip list('Actually, ');
        do while (sentence ^= null);
        put list(word);
        p = sentence;
        sentence = next;
        free p->wordnode;
        end;
        put list('.');
        put skip;
    end write_it;

    end reverse; 

instruction: Write a NETWORK program in PL/1 which consist of all the procedures like setup, connect, find, print_all, print_paths, print_route, shortest_distance and free all. 

input:  

output:

 
    /***************************************************/
    /* This program finds the shortest path between nodes */
    /* in a networK. It has 8 internal procedures: */
    /* SETUP, CONNECT, FIND, PRINT_ALL, PRINT_PATHS, */
    /* SHORTEST_DISTANCE, PRINT_ROUTE, and FREE_ALL. */
    /******************************************************/

    network:
    procedure options(Main);
    %replace
        true by '1'b,
        false by '0'b,
        citysize by 20,
        infinite by 32767;

    declare
        sysin file;

    declare 
        1 city_node based,
            2 city_name character(citysize) varying,
            2 total_distance fixed,
            2 investigate bit,
            2 city_list pointer,
            2 route_head pointer;

    declare 
        1 route_node based,
            2 next_city pointer,
            2 route_distance fixed,
            2 route_list pointer;

    declare
        city_head pointer;

    do while (true);
        call setup();
        if city_head = null then stop;
        call print_all();
        call print_paths();
        call free_all();
    end;
    /******************************************************/
    /* This procedure reads two cities and then calls the */
    /* procedure CONNECT to establish the connection (in */
    /* both directions) between the cities. */
    /******************************************************/
    setup:
        procedure;
        declare 
        distance fixed,
        (city1, city2) character(citysize) varying;

        on endfile(sysin) goto eof;
        city_head = null;
        put skip list('Type `City1, Dist, City2;` ');
        put skip;
        do while (true);
            get list(city1, distance, city2);
            call connect(city1, distance, city2);
            call connect(city2, distance, city1);
        end;
        eof:
    end setup;
    /******************************************************/
    /* This procedure establishes a single route_node to */
    /* connect the first city to the second city by */
    /* calling the FIND procedure twice; once for the */
    /* first city and once for the second city. */
    /******************************************************/
    connect:
        procedure (source_city, distance, destination_city);
        declare 
            source_city character(citysize) varying,
            destination_city character(citysize) varying,
            distance fixed,
            (r, s, d) pointer;

        s = find(source_city);
        d = find(destination_city);
        allocate route_node set (r);
        r -> route_distance = distance;
        r -> next_city = d;
        r -> route_list = s -> route_head;
        s -> route_head = r;
    end connect;
    /**************************************************/
    /* This procedure searches the list of cities and */
    /* returns a pointer to the re9uested city_node. */
    /**************************************************/
    find:
        procedure (city) returns (pointer);
        declare
            city character(citysize) varying,
            (p,q) pointer;

        do p = city_head;
            repeat (p -> city_list) while (p ^= null);
            if city = p -> city_name then
            return (p);
        end;
        allocate city_node set (p);
        p -> city_name = city;
        p -> city_list = city_head;
        city_head = p;
        p -> total_distance = infinite;
        p -> route_head = null;
        return (p);
    end find;

    /**********************************************/
    /* This procedure starts at the city head and */
    /* displays all the cities in the city list. */
    /**********************************************/
    print_all:
        procedure;
        declare
            (p, q) pointer;

        do p = city_head
            repeat (p -> city_list) while (p ^= null);
            put skip list(p -> city_name,':');
            do q = p -> route_head
                repeat (q -> route_list) while (q ^= null);
            put skip list(q -> route_distance, ' Miles to ', q -> next_city -> city_name);
            end;
        end;
    end print_all;
    /******************************************************/
    /* This procedure reads a destination city, calls the */
    /* SHORTEST_DISTANCE procedure, and sets the */
    /* total_distance field in each city_node to the */
    /* total distance froM the destination city, */
    /*************~****************************************/
    print_paths:
        procedure;
        declare
            city character(citysize) varying;

        on endfile(sysin) goto eof;
        do while (true);
            put skip list('Type Destination ');
            get list(city);
            call shortest_distance(city);
            on endfile(sysin) goto eol;
            do while (true);
                put skip list('Type Start ');
                get list(city);
                call print_route(city);
            end;
            eof: end print_paths;
            eol: revert endfile(sysin);
        end;
    end print_paths
    /******************************************************/
    /* This procedure is the heart of the pro!:lraM. It */
    /* taKes an input city, the destination, and COMPutes */
    /* the MiniMuM total distance froM every city in the */
    /* networK to the destination. It then records this */
    /* MiniMuM value in the total_distance field of every */
    /* city_node                                          */
    /******************************************************/
    shortest_distance:
        procedure (city);
        declare
            city character(citysize) varying;
        declare
            bestp pointer,
            (d, bestd) fixed,
            (p, q, r) pointer;

        do p = city_head
            repeat (p -> city_list) while (p ^= null);
            p -> total_distance = infinite;
            p -> investigate = false;
        end;
        p = find(city);
        p -> total_distance = 0;
        p -> investigate = true;
        do while (true);
            bestp = null;
            bestd = infinite;
            do p = city_head
                repeat (p -> city_list) while (p ^= null);
                if p -> investigate then
                    do;
                        if p -> total_distance < bestd then
                            do;
                                bestd = p -> total_distance;
                                bestp = p;
                            end;
                    end;
            end;
            if bestp = null then return;
            bestp -> investigate = false;
            do q = bestp -> route_head
                repeat (q -> route_list) while (q ^= null);
                r = q -> next_city;
                d = bestd + q -> route_distance;
                if d < r -> total_distance then
                    r -> total_distance = d;
                    r -> investigate = true;
                end;
            end;
        end;
    end shortest_distance;
    /***********************************************/
    /* This procedure displays the best route frOM */
    /* the input city to the destination. */
    /***********************************************/

    print_route:
        procedure (city);
        declare
            city character(citysize) varying;
        declare
            (p, q) pointer,
            (t, d) fixed;

        p = find(city);
        do while (true);
            t = p -> total_distance;
            if t = infinite then
                do;
                    put skip list('(No Connection)');
                    return;
                end
            if t = 0 then
                return;
            put skip list(t,' Miles remain');
            q = p -> route_head;
            do while (q ^= null);
                p = q -> next_city;
                d = q -> route_distance;
                if t = d + p -> total_distance then
                    do;
                        put list(d || ' Miles to ' || p -> city_name);
                        q = null;
                    end
                else
                    q = q -> route_list;
            end;
        end;
        end print_route;
    /**************************************************/ 
    /* This procedure frees all the storage allocated */
    /* by the prOgraM while processing the networK. */
    /**************************************************/
    free_all:
        procedure;
        declare
            (p, q) pointer;
        do p = city_head
            repeat (p -> city_list) while (p ^= null);
            do q = p -> route_head
                repeat (q -> route_list) while (q ^= null);
                free q -> route_node;
            end;
            free p -> city_node;
        end;
    end free_all;

    end network;
    

instruction: Write a PL/1 program to fin the factorial of a number using iteration. 

input:  

output:

    /********************************************/
    /* This program evaluates the Factorial */
    /* function (n!) using iteration,		*/
    /****************************************/ 
    ifact:
    procedure options (main);
    declare
        (i, n, F) fixed;
    do i = 0 by 1;
        F = 1;
    Do n= i to 1 by -1;
        F=n* F;
    end;
    put edit('factorial(',i, ')=',F)
        (skip, a,f(2), a, f(7));
    end;
    end ifact;
 

instruction: Write a PL/1 program to fin the factorial of a number using recusrion. 

input:  

output:

 
    /********************************************/
    /* This program evaluates the Factorial */
    /* function (n!) using iteration,		*/
    /****************************************/ 
    rfact:
        procedure options (main);
        declare
            i fixed;
        do i = 0 repeat(i+1);
            put skip list ('factorial(',i,')' = ',factorial(i));
        end;
        stop;
        factorial:
            procedure(i) returns(fixed) recursive;
            declare
                i fixed;
            if i=0 then return (1);
            return (i*factorial(i-1));
        end factorial;
    end rfact;
 

instruction: Write a PL/1 program to fin the factorial of a number using recusrion and FIXED DECIMAL. 

input:  

output:

    /********************************************/
    /* This program evaluates the Factorial */
    /* function (n!) using iteration and FIXED DECIMAL.*/
    /****************************************/ 
    dfact:
        procedure options (main);
        declare
            i fixed;
        do i = 0 repeat(i+1);
            put skip list ('factorial(',i,')' = ',factorial(i));
        end;
        stop;
        factorial:
            procedure(i) returns(fixed decimal(15,0)) recursive;
            declare
                i fixed;
            if i=0 then return (1);
            return (decimal(i,15)*factorial(i-1));
        end factorial;
    end dfact;
 

instruction: Write a PL/1 program to fin the factorial of a number using recusrion and FLOAT BINARY. 

input:  

output:

    /********************************************/
    /* This program evaluates the Factorial function*/
    /*  (n!) using iteration and FLOAT BINARY.*/
    /****************************************/ 
    dfact:
        procedure options (main);
        declare
            i fixed;
        do i = 0 repeat(i+1);
            put skip list ('factorial(',i,')' = ',factorial(i));
        end;
        stop;
        factorial:
            procedure(i) returns(float) recursive;
            declare
                i fixed;
            if i=0 then return (1);
            return (i*factorial(i-1));
        end factorial;
    end dfact;
 

instruction: Write a PL/1 program for the Ackermann function. 

input:  

output:

    /***************************************************/
    /* This program evaluates the Ackermann function */
    /* A(m,n), and increases the size of the stack */
    /* because of the large number of recursive calls. */
    /***************************************************
    ack:
        procedure options(main,stacK(2000));
        declare
            (m,maxm,n,maxn) fixed;

        put sKip list('Type max m,n: ');
        get list(maxm,maxn);
        put sKip
            lis t ('    ',(decimal(n,4) do n=O to maxn))
        do m = 0 to maxm;
            put sKip list(decimal(m,4),': ');
            do n = 0 to maxn;
                put list (decimal (ackermann(m,n),4)); 
            end;
        end;
        stop;

        ackermann:
                procedure(m,n) returns(fixed) recursive
                declare (m,n) fixed;
                if m = 0 then
                    return(n+1);
                if n = 0 then
                    return(ackermann(m-1,1);
                return(ackermann(m-1,ackermann(m,n-1)));
        end ackermann;
    end ack;
 

instruction: Write an expression evaluation program in PL/1. 

input:  

output:

    /***************************************************/
    /* This program evaluates an arithmetic expression */
    /* using recursion. It contains two procedures. GNT */
    /* obtains the input expression consisting of separate */
    /* tokens, and EXP that performs the recursive */
    /* evaluation of the tokens in the input line. */
    /*****************************************************/
    expression:
        procedure options (main);
        declare
            sysin file,
            value float,
            token character (10) varying;
        
        on endfile (sysin)
        stop;

        on error(1) /* conversion or signal */
        begin;
            put skip list('Invalid Input at ',token);
            get skip;
            goto restart;
        end;

        restart:
            do while('1'b);
                put skip(3) list('Type expression: ');
                value = exp();
                put skip list('Value is:',value);
            end;
        gnt:
            procedure;
                get list(token);
        end gnt;

        exp:
            procedure returns(float binary) recursive;
            declare x float binary;
            call gnt();
            if token = '(' then
                do;
                    x = exp();
                    call gnt();
                    if token ='+' then 
                        x= x + exp();
                    else
                    if token = '-' then
                        x=x - exp() ;
                    else
                    if token = '*' then
                        x = x * exp();
                    else
                    if token = '/' then
                    x= x / exp();
                    else
                    signal error (1);
                    call gnt ();
                    if token ^= ')' then
                        signal error (1);
                end;
            else
                x = token;
            return (x);
        end exp
    end expression;
 

instruction: Write an expression program in PL/1 which consist of seperate tokens. 

input:  

output:

 
    /*****************************************************/
    /* This program evaluates an arithmetic expression */
    /* usin~ recursion. It contains an expanded version */
    /* of the GNT procedure that obtains an expression */
    /* containing separate toKens, EXP then recursively */
    /* evaluates the toKens in the input line. /
    /*****************************************************/
    expression:
        procedure options(Main);

        %replace
            true by '1'b;

        declare
            sysin file,
            value float,
            (token character(10), line character(80)) varying static initial(' ');

        on endfile(sysin)
            stop;

        on error(1)  /* conversion or signal */
            put skip list('Invalid input at', token);
            token = ' '; line = ' ';
            goto restart;
        end;

        restart:
            do while (true);
                put skip(3) list('Type expression: ');
                value = exp();
                put edit('Value is: ', value) (skip, a, f(10, 4));
            end;

        gnt:
            procedure;
            declare
                i fixed;

            line = substr(line, length(token) + 1);
            do while (true);
                if line = ' ' then
                    get edit(line) (a);
                    i = verify(line, ' ');
                if i = 0 then
                    line = ' ';
                else
                    do;
                        line = substr(line, i);
                        i = verify(line, '0123456789. ');
                        if i = 0 then
                            token = line;
                        else if i = 1 then
                            token = substr(line, 1, 1);
                        else
                            token = substr(line, 1, i - 1);
                        return;
                    end;
            end;
        end gnt;

        exp:
            procedure returns (float binary) recursive;
            declare x float binary;
            call gnt();
            if token = '(' then
                do;
                    x = exp();
                    call gnt();
                    if token = '+' then
                        x = x + exp();
                    else
                    if token = '-' then
                        x = x - exp();
                    else
                    if token = '*' then
                        x = x * exp();
                    else
                    if token = '/' then
                        x = x / exp();
                    else
                        signal error(1);
                    call gnt();
                    if token ^= ')' then
                        signal error(1);
                end;
            else
                x = token;
            return (x);
        end exp;
    end expression;
 

instruction: Write a PL/1 program that illustrates ENTRY variables and constants. 

input:  

output:

 
    /************************************************/
    /* This program illustrates ENTRY variables and */
    /* constants.                                   * /
    /*************************************************/
    call:
        procedure options (main);
        declare
            f (3) entry(float) returns(float) variable,
            a entry(float) returns(float),
            i fixed, x float;
        
        f(1) = a;
        f(2) = b;
        f(3) = c;
        do i = 1 to 3;
            put skip list('Type x ');
            get list(x);
            put listl'f(',i,')=',f(i)(x));
        end;
        stop;

        b:
            procedure(x) returns(float); /* internal procedure */ 
            declare x float;
            return(2*x + 1);
        end b;
        c:
            procedure(x) returns(float); /* internal procedure */ 
            declare x float;
            return(sin(x));
        end c;
    end call;
 

instruction: Write a PL/1 program tha performs matrix conversion. 

input:  

output:

    /*****************************************************/
    /* This program is the main module in a program that */
    /* performs matrix inversion. It calls the entry */
    /* constant INVERT which does the actual inversion. */
    /*****************************************************/
    maininvt:
        procedure options(main);
        %replace
            true by '1'b,
            false by '0'b;
            %replace
            maxrow by 26,
            maxcol by 40;

        declare
            mat(maxrow, maxcol) float binary(24),
            (i, j, n, m) fixed(6),
            var character(26) static initial('abcdefghijklmnopqrstuvwxyz'),
            invert entry
            ((maxrow, maxcol) float(21), fixed(6), fixed(6));

        put list('Solution of Simultaneous Equations');
            do while (true);
                put skip(2) list('Type rows, columns: ');
                get list(n);

                if n = 0 then
                    stop;

                get list(m);

                if n > maxrow ! m > maxcol then
                    put skip list('Matrix is too large');
                else
                    do;
                        put skip list('Type Matrix of Coefficients');
                        put skip;
                        do i = 1 to n;
                            put list('Row', i,':');
                            get list((mat(i, j) do j = 1 to n));
                        end;

                        put skip list('Type Solution Vectors');
                        put skip;

                        do j = n + 1 to m;
                            put list('Variable',substr(var, j - n, 1), ': ');
                            get list((mat(i, j) do i = 1 to n));
                        end;

                        call invert(mat, n, m);
                        put skip(2) list('Solutions: ');

                        do i = 1 to n;
                            put skip list(substr(var, i, 1),'= ');
                            put edit((mat(i, j) do j = n + 1 to m))
                                (f(8, 2));
                        end;

                        put skip(2) list('Inverse Matrix is');

                        do i = 1 to n;
                            put skip edit((mat(i, j) do j = 1 to n))
                            (x(3), 6f(8, 2)),skip);
                        end;
                    end;
            end;

        end maininvt;

        invert:
            procedure(a, r, c);
                %replace
                maxrow by 26,
                maxcol by 40;

            declare
                (d, a(maxrow, maxcol)) float binary(24),
                (i, j, k, r, c) fixed binary(6);

            do i = 1 to r;
                d = a(i, i);

                do j = 1 to c - 1;
                    a(i, j) = a(i, j + 1) / d;
                end;
                a(i, c) = 1 / d;

                do k = 1 to r;
                    if k ^= i then
                    do;
                        d = a(k, i);
                        do l = 1 to c - 1;
                            a(k, j) = a(k, l + 1) - a(i, l) * d;
                        end;
                    end;
                end;
            end;

        end invert; 

instruction: Can you write a sapmle program for a customer who has taken a loan of $500 on an interest rate of 14%. He wants to find out how many time will it take for him ti repay the loan? 

input:  

output:

    /*******************************************************/
    /* This program produces a schedule of loan payments*/
    /* using the following algorithm: if P= loan payment, */
    /* i = interest, and PMT is the monthly payment then */
    /* P= (P + (i*p) - РМТ).						* /
    /*********************************************************/
    loan1:
    procedure options (main);
        declare
        m	fixed binary, 
        y	fixed binary,
        P 	fixed decimal (11,2), 
        PMT fixed decimal (6,2),
        i 	fixed decimal (4,2);

        do while ( ‘1’ b);
            put skip list('Principal ');
            get list (P)I;
            put list(‘Interest '); 
            get list(i);
            put list (‘Payment	’) 
            get list (PMT);
            m = 0;
            y = 0;
            do while (P > 0);
                if mod(m,12) = 0 then
                    do;
                        y=y + 1;
                        put skip list('Year',y);
                    end;
                M =M + 1;
                put skip list(m,P);
                P= P + round(i*P / 1200, 2);
                if P < PMT
                    then PMT = P;
                put list (PMT) ;
                P = P - PMT;
            end;
        end;
    end loan1
 

instruction: Write a PL/1 program for ANNUITY problem. 

input:  

output:

 
    /*******************************************************/
    /* This prograM COMPutes either the present valueIPV), */
    /* the payment(PMT), or the nUMber of periods in an */
    /* ordinary annuity,                                    */
    /*******************************************************/
    annuity:
        procedure options(Main);
        %replace
            clear by '^z',
            true by '1'b;

        declare
            PMT fixed decimal(7, 2),
            PV fixed decimal(9, 2),
            IP fixed decimal(6, 6),
            i float binary,
            yi float binary,
            n float binary,
            n fixed;

        declare
            ftc entry(float binary(24)) returns(character(17) varying);

        put list(clear, '^i^iORDINARY ANNUITY');
        put skip(2) list(^i'Enter Known Values; or 0, on Each Iteration');

        on error
            begin;
                put skip list('^iInvalid Data, Re-enter');
                goto retry;
            end;

        retry:
        do while (true);
            put skip(3) list('^iPresent Value ');
            get list(PV);
            put list('^iPayment ');
            get list(PMT);
            put list('^iInterest Rate ');
            get list(yi);
            i = yi / 1200;
            put list('^iPay Periods ');
            get list(n);

            if PV = 0 | PMT = 0 then
                x = 1 - 1 / (1 + i)*/n;

            if PV = 0 then
                do;
                    PV = PMT * dec(ftc(x / i) 15, 6);
                    put edit('^iPresent Value is ', PV) (a, p'$$$,$$$,$$$V.99');
                end;
            
            /***********************/
            /* Compute the payment */
            /***********************/

            if PMT = 0 then
                do;
                    PMT = PV * dec(ftc(i / x) 15, 8);
                    put edit('^iPayment is ', PMT) (a, p'$$,$$$,$$$V.99');
                end;
            /***********************/
            /* Compute number of periods */
            /***********************/
            if n = 0 then
                do;
                    IP = ftc(i);
                    x = char(PV * IP / PMT);
                    n = ceil(-log(1 - x) / log(1 + i));
                    put edit(n, '^iPay Periods') (a, p'ZZZ9', a);
                end;
        end;
    end annuity;

 

instruction: Write a PL/1 program to compute a schedule of loan payments using elaborate analysis and display formats. 

input:  

output:

 
    /*******************************************************/
    /* This program computes a schedule of loan payments, */
    /* using an elaborate analysis and display format, */
    /* It contains five internal procedures: DISPLAY */
    /*SUMMARY, CURRENT_YEAR, HEADER, and LINE         */
    /*******************************************************/
    loan2:
        procedure options(Main);

        %replace
            true by '1'b,
            false by '0'b,
            clear by '^Z';

        declare
            end bit(1),
            m fixed binary,
            sm fixed binary,
            sy fixed binary,
            fm fixed binary,
            dl fixed binary,
            P fixed decimal(10,2),
            PV fixed decimal(10,2),
            PP fixed decimal(10,2),
            PL fixed decimal(10,2),
            PMT fixed decimal(10,2),
            PMV fixed decimal(10,2),
            INT fixed decimal(10,2),
            YIN fixed decimal(10,2),
            IP fixed decimal(10,2),
            yi fixed decimal(4,2),
            i  fixed decimal(4,2),
            INF fixed decimal(4,3),
            ci fixed decimal(15,14),
            fi fixed decimal(7,5),
            ir fixed decimal(4,2);

        declare
            name character(14) varying static initial('$con'),
            output file;

        put list(clear '^i^ iUMMARY OF PAYMENTS');

        on undefinedfile(output)
            begin;
                put skip list('^i^icannot write to ', name);
                goto open_output;
            end;

        open_output:
        put skip(2) list('^i^iOutput File Name ');
        get list(name);
        if name = '$con' then
            open file(output) title('$con') print pagesize(0);
        else
            open file(output) title(name) print;

        on error
            begin;
                put skip list('^i^iBad Input Data, Retry');
                goto retry;
            end;

        retry:
        do while (true);
            put skip(2) list('^i^iPrincipal ');
            get list(PV);
            P = PV;
            put list('^i^iInterest ');
            get list(yi);
            i = yi;
            put list('^i^iPayment ');
            get list(PMV);
            PMT = PMV;
            put list('^i^i%Inflation ');
            get list(ir);
            fi = 1 + ir / 1200;
            ci = 1.00;

            put list('^i^iStarting Month ');
            get list(sm);
            put list('^i^iStarting Year ');
            get list(sy);
            put list('^i^iFiscal Month ');
            get list(fm);
            put edit('^i^iDisplay Level',
                    '^i^iYr Results: 0,
                    '^i^iYr Interest: 1,
                    '^i^iAll Values: 2')
                (skip, a);
            get list(dl);
            if dl < 0 | dl > 2 then 
                signal error;

            m = sm;
            y = sy;
            IP = 0;
            PP = 0;
            YIN = 0;

            if name ^= '' then
                put file(output) page;
            call header();

            do while (P > 0);
                INT = round(i * P / 1200, 2);
                IP = IP + INT;
                PL '= P;
                P = P + INT;
                if P < PMT then
                    PMT = P;
                P = P - PMT;
                PP = PP + (PL - P);
                INF = ci;
                ci = ci / fi;
                if (P = 0 | dl > 1 | M = fM) then
                    do;
                        put file(output) skip edit(':' , 100 * m + y) (a, p'99/99');
                        call display(PL * INF, INT * INF, PMT * INF, PP * INF, IP * INF);
                    end;
                if m = fm & dl > 0 then
                    call summary();

                m = m + 1;
                if m > 12 then
                    do;
                        M = 1;
                        y = y + 1;
                        if y > 99 then
                            y = 0;
                    end;
            end;

            if dl = 0 then
                call line();
            else 
            if ^end then
                call summary();
        end retry;
        /****************************************************/
        /* This procedure performs the output of the actual */
        /* parameters passed to it by the Main part of the */
        /* program.                                          */
        /****************************************************/
        display:
            procedure(a, b, c, d, e);
            declare
                (a, b, c, d, e) fixed decimal(10,2);

            put file(output) edit
                ('|' , a , '|' , b , '|' , c , '|' , d , '|' , e , '|')
                (a, 2(2(p'$zz,zzz,zz9v.99', a), p'$zzz,zz9.v99', a));
        end display;
        /*************************************************/
        /* This procedure computes the summary of yearly */
        /* interest.                                       */
        /*************************************************/
        summary:
            procedure;
            end = true;
            call current_year(IP - YIN);
            YIN = IP;
        end summary;

        /****************************************************/
        /* This procedure computes the interest paid during' */
        /* current Year.                                      */
        /****************************************************/
        current_year:
            procedure(l);
            declare
                yp fixed binary,
                l fixed decimal(10,2);

            yp = y;

            if fm < 12 then yp = yp - 1;
            call line();
            put skip file(output) edit
                (':',`Interest Paid During``',yp,'_``',y,' is ,I,':')
                (a,x(15) ,2(a,p'99') ,a,p'$$$,$$$,$$9V.99' ,x(16) ,a);
        end current_year;
        /***************************************************** */
        /* This procedure defines and prints out an elaborate */
        /* header format.                                    */
        /****************************************************/
        header:
            procedure;
            put file(output) list(clear);
            call line();
            put file(ouput) skip edit
                ('|','LOAN PAYMENT SUMMARY','|')
                (a,x(19));
            call line();
            put file(output) skip edit
                ('|','Interest Rate',yi,'%','Inflation Rate',ir,'%','|')
                (a,x(15),2(a,p'b99v.99' ,a ,x(6)) ,x(9) ,a);
            call line();
            put file(output) skip edit
            ('|Date |',' Principal |','Plus Interest|',' Payment |',
                'Principal Paid|','Interest Paid |') (a);
            call line();
        end header;
        /***************************************************** **/
        /* This procedure prints out a series of dashed lines. */
        /***************************************************** **/
        line:
            procedure;
            declare
                i fixed bin;
            put file(output) skip edit
                ('____________','____________',
                ('_______________' do i = 1 to 4)) (a);
        end line;
    end loan2;


instruction: Write a PL/1 program for depreciaition schedule including three different depreciation shcedules. 

input:  

output:

    /*******************************************************/
    /* This program calculates three kinds of depreciation */
    /* schedules: straight_line, sum_of_the_years, and     */
    /*double_declining.                                    */
    /*******************************************************/
    depreciate:
    procedure options(main);
        %replace
            clear_screen by '^z',
            indent by 15,
            ITC_rate by .1,
            bonus_rate by .1,
            bonus_max by 2000;
        
        declare
            selling_price decima1(8,2),
            adjusted_price decimal(8,2),
            residual_value decima1(8 ,2),
            year _alue decimal(8,2),
            depreciation_value decimal(8 ,2),
            total_depreciation decimal(8,2),
            book_value decimal(8,2),
            tax_rate decimal(3,2),
            sales_tax decimal (8 ,2) ,
            tax_bracket decimal(2),
            FYD decimal(8,2),
            ITC decimal (8 ,2) ,
            bonus_dep decimal (8 ,2) ,
            months_remaining decimal (2),
            new character(4),
            factor decimal(2,1),
            years decimal(2),
            year_sum decimal(3),
            current_year decimal(2),
            select_sched character(!);
        declare
            copy_to_list character(4),
            output file variable,
            (sysprint, list) file;

        schedule (0) = error;
        schedule (1) = straight_line;
        schedule (2) = sum_of_years;
        schedule (3) = double_declining;

        open file(sysprint) stream print pagesize(0) title('$con');

        do while ('1'b);
            put list(clear_screen,'^i^i^iDepreciation Schedule');
            put skip(3) list('^i^iSelling Price? ');
            get list(selling_price);
            put list('^i^iResidual Value? ');
            get list(residual_value);
            put list('^i^iSales Tax (%)? ');
            get list(tax_rate);
            put list('^i^iTax Bracket (%)? ');
            get list(tax_bracket);
            put list('^i^iProRate Months? ');
            get list(months_remaining);
            put list('^i^iHow Many Years? ');
            get list(years);
            put list('^i^iNew? (yes/no) ');
            get list(new);
            put edit('^i^iSchedule:', 
                    '^i^iStraight Line (s)', 
                    '^i^iSum-of-Years (y)', 
                    '^i^iDouble Declining (d)? ') (a,skip);
            get list(select_sched);
            put list('^i^iList? (yes/no) ');
            get list(copy_to_list);
            if copy_to_list = 'yes' then
                open file(list) stream print title('$lst');
            factor = 1.5;
            if new = 'yes' then
                factor = 2.0;
            sales_tax = decimal(selling_price * tax_rate,12,2)/ 100 + .005;
            if new = 'yes' | selling_price <= 100000.00 then
                ITC = selling_price * ITC_rate;
            else
                ITC = 100000 * ITC_rate;
            bonus_dep = selling_price * bonus_rate;
            if bonus_dep > bonus_max then
                bonus_dep = bonus_max;
            put list(clear_screen);
            call display(sysprint);
            if copy_to_list = 'yes' then
                call display(list);
            put skip list('^i^iType RETURN to Continue');
            put skip(2);
        end;

        /***********************************************/
        /* This procedure displays the various          */
        /* depreciation schedules. It calls the         */
        /* appropriate schedule with an index into an   */
        /* array of entry constants.                    */
        /***********************************************/
        display:
            procedure(f);
            declare
                f file;
            output = f;
            call schedule(index(schedules,select_sched));
        end display;

        /***********************************************/
        /* This is a global error recovery routine.     */
        /***********************************************/
        error:
            procedure;
            put file(output) edit('Invalid Schedule - Enter s, y, or d')
                            (page,column(indent),x(8),a);
            call line();
        end error;

        /***********************************************/
        /* This procedure computes straight_line        */
        /* depreciation.                                */
        /***********************************************/
        straight_line:
            procedure;
            adjusted_price = selling_price - bonus_dep;
            put file(output) edit('S T R A I G H T  L I N E')
                            (page,column(indent),x(11),a);
            call header();
            depreciation_value = adjusted_price - residual_value;
            book_value = adjusted_price;
            total_depreciation = 0;
            do current_year = 1 to years;
                year_value = decimal(depreciation_value/years,8,2) + .005;
                if current_year = 1 then
                do;
                    year_value = year_value * months_remaining / 12;
                    FYD = year_value;
                end;
                depreciation_value = depreciation_value - year_value;
                total_depreciation = total_depreciation + year_value;
                book_value = adjusted_price - total_depreciation;
                call print_line();
            end;
            call summary();
        end straight_line;

        /***********************************************/
        /* This procedure computes depreciation based   */
        /* on the sum_of_the_years.                     */
        /***********************************************/
        sum_of_years:
            procedure;
            adjusted_price = selling_price - bonus_dep;
            put file(output) edit('S U M  O F  T H E  Y E A R S')
                            (page,column(indent),x(11),a);
            call header();
            depreciation_value = adjusted_price - residual_value;
            book_value = adjusted_price;
            total_depreciation = 0;
            year_sum = 0;
            do current_year = 1 to years;
                year_sum = year_sum + current_year;
            end;
            do current_year = 1 to years;
                year_value = decimal(depreciation_value *
                            (years - current_year + 1) / year_sum,12,2) + .005;
                if current_year = 1 then
                    do;
                    year_value = year_value * months_remaining / 12;
                    FYD = year_value;
                    end;
                depreciation_value = depreciation_value - year_value;
                total_depreciation = total_depreciation + year_value;
                book_value = adjusted_price - total_depreciation;
                call print_line();
            end;
            call summary();
        end sum_of_years;

        /***********************************************/
        /* This procedure computes double_declining     */
        /* depreciation.                                */
        /***********************************************/
        double_declining:
            procedure;
            adjusted_price = selling_price - bonus_dep;
            put file(output) edit('D O U B L E  D E C L I N I N G')
                            (page,column(indent),x(10),a);
            call header();
            depreciation_value = adjusted_price - residual_value;
            book_value = adjusted_price;
            total_depreciation = 0;
            do current_year = 1 to years 
                while (depreciation_value > 0);
                year_value = decimal(book_value / years,8,2) * factor + .005;
                if current_year = 1 then
                    do;
                    year_value = year_value * months_remaining / 12;
                    FYD = year_value;
                    end;
                if year_value > depreciation_value then
                    year_value = depreciation_value;
                depreciation_value = depreciation_value - year_value;
                total_depreciation = total_depreciation + year_value;
                book_value = adjusted_price - total_depreciation;
                call print_line();
            end;
            call summary();
        end double_declining;

        /***********************************************/
        /* This procedure prints an output header       */
        /* record.                                      */
        /***********************************************/
        header:
            procedure;
            declare
                new_or_used character(5);
            if new = 'yes' then
                new_or_used = 'New';
            else
                new_or_used = 'Used';
            put file(output) edit('--------------------------------------------------',
                                '|',selling_price+sales_tax,new_or_used,
                                residual_Value,'Residual Value|',
                                '|',months_remaining,'Months Left',
                                tax_rate, '% Tax',tax_bracket,'% Tax Bracket|')
                            (2(skip,column(indent),a),
                            2(p'$$$,$$$,$$9.V99',a),
                            skip,column(indent),a,x(5),f(2),a,
                            2(x(2),p'999',a));
            put file(output) edit('--------------------------------------------------',
                                ' | Y | Depreciation | Depreciation | Book Value |',
                                ' | r | For Year     | Remaining    |            |')
                            (skip,column(indent),a);
            
        end header;

        /***********************************************/
        /* This procedure prints the current line.      */
        /***********************************************/
        print_line:
            procedure;
            put file(output) edit(
                '|',current_year,
                ' |',year_value,
                ' | ',depreciation_value,
                ' | ',book_value,' |')
                (skip,column(indent),a,f(2),4(a,p'$z,zzz,zz9v.99'));
        end print_line;

        /***********************************************/
        /* This procedure prints the summary of values  */
        /* for each type of depreciation schedule.      */
        /***********************************************/
        summary:
            procedure;
            declare 
                adj_ITC decimal(8,2),
                total decimal(8,2),
                direct decimal(8,2);
            call line();
            adj_ITC = ITC * 100 / tax_bracket;
            total = FYD + sales_tax + adj_ITC + bonus_dep;
            direct = total * tax_bracket / 100;
            put file(output) edit(
            '|       First Year Reduction in Taxable Income        |',
            '-------------------------------------------------------',
            '|       Depreciation            ',FYD,               '|',
            '|       Sales Tax               ', sales_tax,        '|',
            '|       ITC (Adjusted)          ', adj_ITC,          '|',
            '|       Bonus Depreciation      ', bonus_dep,        '|',
            '|       Total for First Year    ', total,            '|',
            '|       Direct Reduction in Tax ', direct,           '|')
            (2(skip,column(indent),a), 2(4(skip,column(indent),a,p'$z,zzz,zz9v.99',x(3),a),
            skip,column(indent),a));
            call line();
        end summary;
        /**********************************************/
        /* This procedure prints a  ine of dashes.   */
        /**********************************************/
        line:
            procedure;
            put file (output) edit(
            '-------------------------------------------------')
            (skip,column(indent),a);
        end line;
    end depreciate;
    

instruction: Write a PL/1 program to test an assembly routine to do floating-point division. 

input:  

output:

    /*****************************************************/
    /* This program tests an assembly language routine to */
    /* do floating-point division.                        * /
    /******************************************************/
    dtest:
    procedure options (main);
    declare
        div2 entry(fixed (7) ,float),
        i fixed(7),
        f float;
    do i = 0 by 1;
        f = 100;
        call div2(i,f);
        put skip list('100 / 2 **',i, '=',f);
    end;
    end dtest;
 

instruction: Write a PL/1 program to test an assembly routine called FDIV2 which returns a FLOAT BINARY value. 

input:  

output:

    /*****************************************************/
    /* This program tests the assembly language routine     */
    /* called FDIV2 ahich returns a FLOAT BINARY value.    * /
    /******************************************************/
    fdtest:
    procedure options (main);
    declare
        div2 entry(fixed (7) ,float) returns(float),
        i fixed(7),
        f float;
    
    do i = 0 by 1;
        put skip list('100 / 2 **',i, '=',fdiv2(i,100));
    end;
    end fdtest;
 

instruction: Write a PL/1 program to test TOTWDS, MAXWDS and ALLWDS functions from the run-time subroutine library. 

input:  

output:

    /*****************************************************/
    /* This program tests the TOTWDS, MAXWDS, and ALLWDS  */
    /* functions from the Run-time Subroutine Library.    */
    /******************************************************/

    alltst:
    procedure options (main);
    declare
        totwds entry returns(fixed (15)),
        maxwds entry returns(fixed (15)),
        allwds entry(fixed (15)) returns (pointer);
    declare
        allreq fixed(15),
        memptr ptr;
        meminx fixed (15),
        memory (0:0) bit(16) based(memptr);
    do while ('1 'b);
        put edit (totwds(), ' Total Words Available',
                maxwas(), ' Maximum Segment Size',
                'Allocation Size? ') (2(skip,f(6),a),skip,a);
        get list(allreq);
        memptr = allwds (allreq);
        put edit('Allocated', allreq,' Words at ',unspec (memper))
                (sKip,a,f(6),a,b4) ;
        /* clear memory as example */
        do meminx = 0 to allreq-1;
            memory(meminx) = '0000'b4;
        end;
    endi
    end alltst;
    

instruction: Write a program in PL/1 to test the STKSIZ function while evaluating a RECURSIVE procedure. 

input:  

output:

    /*******************************************#**********/
    /* This program tests the STKSIZ Punction while */
    /* evaluating a RECURSIVE procedure.            */
    /******************************************************/
    ack:
    procedure options(main,stack (2000));
    declare
        (mon) fixed,
        (maxm,maxn) fixed,
        ncalls decimal(6),
        (curstack, stacksize) fixed,
        stksiz entry returns (fixed);
    put skip list('Type max m,n: ');
    get list (maxm,maxn);
    do m = O to maxm;
        do n = 0 to maxn;
            ncalls      = 0;
            curstack    = 0;
            stacksize   = 0;
            put edit('Ack(',m,',',n,')=',ackermann(m,n),
                ncalls,' Calls,',stacksize,' Stack Bytes')
                (skip,a,2(f(2) ,a),f(6),f(7),a,f(4),a);
        end;
    end;
    stop;

    ackermann:
        procedure (m,n) returns(fixed) recursive;
        declare
            (m,n) fixedi
        ncalls = ncalls + 11
        curstack = stksiz ();
        if curstack > stacksize then
            stacksize = curstack;
        if m= 0 then
            return(n+1);
        if n= 0 then
            return (ackermann (m-1,1));
        return(ackermann(m-1, rackermann (m,n-1)));
    end ackermann;
    end ack;
 

instruction: Write a PL/1 code which showcase the skeleton for parameter passing in PL/1. 

input:  

output:

    /*Below is a sample PL/1 code which represents the skeleton of */
    /*parameter passing in PL/1*/
    main:
        proceudre options(main);
        declare
            a float binary;
                |
                |
        call low_sub(a); /* pass by reference */
            |
        call middle_sub((a)); /* pass by value */
            |
        call high_sub(a); /* pass by reference */
            |
            |
        low_sub:
            procedure;
            declare
                x float binary;
            |
            |
        end low_sub;
        
        middle_sub:
            procedure;
            declare
                x float binary;
            |
            |
        end middle_sub;
        
        high_sub:
            procedure(x);
            declare
                (x,my_x) float binary;
            my_x = x; /* reassign using local variable */
            |
            |
        end high_sub;
    end main; 

instruction: Write an simple example of assignment statements in PL/1. 

input:  

output:

    assign:
        procedure options(main);
        declare
            p pointer,
            i fixed binary(7),
            r bit(16),
            s bit(16) based,
            (u, v) float binary(24),
            A(5,2) character(2),
            B(5,2) character(2),
            C character(2),
            1 w,
                2 x fixed binary,
                2 y bit(16),
            1 z,
                2 x fixed binary,
                2 y bit(16);
            

        u = u + v; /* simple assignment */
        A = B; /* array aggregate assignment */
        A(3) = B(4); /* cross-sectional reference */
        w = z; /* structure aggregate assignment */
        p -> s = (r=w,y); /* pointer-qualified reference */
        w,x = w,x + z,x; /* partially qualified aggregate reference */
        unspec(w,y) = unspec(A(5,1)); /* pseudo-variable reference */ 
        substr(C,i+l,3) = substr(C,10,3); /* pseudo-variable reference */ 
        A(2*i+l) = B(4); /* variable is expression */
            |
            |
            |

    end assign; 

instruction: Show me and example of structures in PL/1. 

input:  

output:

    declare
        1 employee,
            2 name_address,
                3 name,
                    4 first character(10),
                    4 middle-initial character(1),
                    4 last character(20),
                3 address,
                    4 street character(40),
                    4 city character(10),
                    4 state character(2),
                    4 zip_code character(5),
            2 position
                3 department_no character(3),
                3 job_title character(20),
            2 salary fixed decimal(8,2),
            2 number_of_dependents fixed,
            2 health_plan bit(1),
            2 date_hired character(8); 

instruction: Can you show a sample code which have an external procedure and internal procedure? 

input:  

output:

    /************External procedure*****************************/
    a : 
    procedure(x) returns(float); /* external procedure */
    declare x float;
    return (x/2);
    end a;


    /**********************the CALL program******************/
    call:
        procedure options (main);
        declare
            f(3) entry(float) returns(float) variable,
            a entry(float) returns(float); /* entry constant /*
        declare
            I fixed, x float;
        f(1) = a;
        f(2) = b;
        f(3) = c;
        do i = 1 to 3;
        put skip list (‘Type x ’);
        get list(x);
        put list(‘f(‘,i,’) = ’,f(i)(x));
        end;
        stop;

        b :
        procedure(x) returns(float); /* internal procedure */ 
        declare x float;
        return (2*x + 1);
        end b;

        с :
        procedure(x) returns(float); /* internal procedure */
        declare x float;
        return(sin(x));
        end c;
    end call; 

instruction: Can you show an example for label variables. 

input:  

output:

    chase_your_tail:
        procedure options (main);
        declare
            wherever label;
        there:
            wherever = here;
        here:
            wherever = there;
        goto wherever;
    end chase your tail; 

instruction: Show me a program that illustrates statements from each category. 

input:  

output:

    sample:
        procedure options(main);
        declare
            c character(10) varying;

        do;
            put skip list(‘Input: ‘);
            get list(c);
            c = upper(c); /* function reference*/
            put skip list(‘Output: ’,c);
        end;
        
        begin;
        declare
            c float binary(24);
            put skip list(‘Input: ‘);
            get list(c);
            call output(c); /* subroutine invocation */
        end;
        upper:
                procedure(c) returns(character(10) varying;
                declare
            c character(10) varying;
                return(translate(c,’ABCDEFGHIJKLMNOPQRSTUVWXYZ’,’abcdefghijklmnopqrstuvwxyz’));
        end upper;
        output:
            procedure(c);
            declare
                c float binary(24);
            put skip edit(c) (column(20),e(10.2));
        end output;
    end sample; 

instruction: Write a program to copy one file into another file in PL/1 language. 

input:  

output:

    /*******************************************#**********/
    /* This program copies one file to another using */ 
    /* buffered I/O.                                */
    /******************************************************/
    copy:
    procedure options (main);
    declare
        (input_ file, output file) file;
    open file (input_file) stream
        environment(b(8192)) title('$1,$1');
    open file loutput_file) stream output
        environment(b(8192)) title ('$2.$2');
    declare
        buff character (254) varying;
    do while ('1'b);
        read file (input_file) into (buff);
        write file (output_ file) from (buff);
    end;
    end copy; 

instruction: Write a PL/1  program to create a name and address file. 

input:  

output:

    /*****************************************************/
    /* This program creates a name and address file. The */
    /* data structure for each record is in the %INCLUDE */
    /* file RECORD.DCL.                                  */
    /*****************************************************/
    create:
        procedure options(Main);
        declare
            1 record,
                2 name  character(30) varying,
                2 addr  character(30) varying,
                2 city  character(20) varying,
                2 state character(10) varying,
                2 zip   fixed decimal(6),
                2 phone character(12) varying;

        %replace
        true  by '1'b,
        false by '0'b;

        declare
            output file,
            filename character(14) varying,
            eofile bit(1) static initial(false);

        put list('Name and Address Creation Program, File Name: ');
        get list(filename);

        open file(output) stream output title(filename);

        do while (^eofile);
            put skip(3) list('Name: ');
            get list(name);
            eofile = (name = 'EOF');
            if ^eofile then
                do;
            /* write prompt strings to console */
                    put list('Address: ');
                    get list(addr);
                    put list('City, State, Zip: ');
                    get list(city, state, zip);
                    put list('Phone: ');
                    get list(phone);

            /* data in memory, write to output file */
                    put file(output) list(name, addr, city, state, zip, phone);
                    put file(output) skip;
                end;
        end;
        put file(output) skip list('EOF');
        put file(output) skip;
    end create; 

instruction: Write a PL/1 program to read a name and addredd data file nad display the information on request. 

input:  

output:

    /***************************************************/
    /* This program reads a name and address data file */
    /* and displays the information on request.        */
    /***************************************************/
    retrieve:
    procedure options(main);

    declare
        1 record,
            2 name  character(30) varying,
            2 addr  character(30) varying,
            2 city  character(20) varying,
            2 state character(10) varying,
            2 zip   fixed decimal(6),
            2 phone character(12) varying;

    declare
        true  by '1'b,
        false by '0'b;

    declare
        (sysprint, input) file,
        filename character(14) varying,
        (lower, upper) character(30) varying,
        eofile bit(1);

    open file(sysprint) print title('$con');
    put list('Name and Address Retrieval, File Name: ');
    get list(filename);

    do while (true);
        lower = 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA';
        upper = 'zzzzzzzzzzzzzzzzzzzzzzzzZZZZZZ';
        put skip(2) list('Type Lower, Upper Bounds: ');
        get list(lower, upper);
        if lower = 'EOF' then
            stop;

        open file(input) stream input environment(b(1024)) title(filename);
        eofile = false;
        do while (^eofile);
            get file(input) list(name);
            eofile = (name = 'EOF');
            if ^eofile then
                do;
                get file(input) list(addr, city, state, zip, phone);
                if name >= lower & name <= upper then
                    do;
                        put page skip(3) list(name);
                        put skip list(addr);
                        put skip list(city, state);
                        put skip list(zip);
                        put skip list(phone);
                    end;
                end;
        end;
        close file(input);
    end;
    end retrieve; 

instruction: Write a PL/1 program to construct a database of employee record using a structure declaration. 

input:  

output:

    /***************************************************/
    /* This program constructs a database of employee  */
    /* records using a structure declaration.          */
    /***************************************************/
    enter:
    procedure options(Main);

    5replace
        true  by '1'b,
        false by '0'b;

    declare
        1 employee static,
            2 name      character(30) varying,
            2 address,
                3 street character(30) varying,
                3 city   character(10) varying,
                3 state  character(12) varying,
                3 zip    fixed decimal(5),
            2 age       fixed decimal(3),
            2 wage      fixed decimal(5,2),
            2 hours     fixed decimal(5,2);

    declare
        1 default static,
            2 street character(30) varying initial('(no street)'),
            2 city character(10) varying initial('(no city)'),
            2 state character(12) varying initial('(no state)'),
            2 zip fixed decimal(5) initial(00000);

    declare
        emp file;

    open file(emp) keyed output environment(f(128),b(8000)) title ('$1.EMP');

    do while(true);
        put list('Employee: ');
        get list(name);

        if name = 'EOF' then
            do;
                call write_it();
                stop;
            end;

        address = default;
        put list('Age, Wage: ');
        get list(age, wage);
        hours = 0;
        call write_it();
    end;

    write_it:
        procedure;
        write file(emp) from(employee);
    end write_it;
    end enter;
 

instruction: Write a program to read an employee record file and create another file of keys to access the records. 

input:  

output:

    /***************************************************/
    /* This program reads an employee record file and */
    /* creates another file of keys to access the records. */
    /***************************************************/
    keyfile:
    procedure option(main);
    declare
        1 employee static,
            2 name character(30) varying;
    declare
        (input, keys) file,
        k fixed;
    open file(input) keyed environment(f(128),b(10000))
        title('$1.emp');
    open file(keys) stream output
        linesize(60) title('$1.key');
    do while('1');
        read file(input) into(employee) keyto(k);
        put skip list(k,name);
        put file(keys) list(name,k);
        if name = 'EOF' then
            stop;
    end;
    end keyfile; 

instruction: Write a program to retrieve and update records in an employee database in PL/1. 

input:  

output:

    /*****************************************************/
    /* This program allows you to retrieve and update    */
    /* individual records in an employee database using  */
    /* a keyed file.                                     */
    /*****************************************************/
    update:
    procedure options(Main);
    declare 
        1 employee static,
            2 name      character(30) varying,
            2 address,
                3 street character(30) varying,
                3 city   character(10) varying,
                3 state  character(12) varying,
                3 zip    fixed decimal(5),
            2 age       fixed decimal(3),
            2 wage      fixed decimal(5,2),
            2 hours     fixed decimal(5,1);

    declare 
        1 keylist(100),
            2 keyname character(30) varying,
            2 keyval fixed binary;

    declare 
        (i, endlist) fixed,
        eolist bit(1) static initial('0'b),
        matchname character(30) varying,
        (emp, keys) file;

    /* Open the employee file for update with direct access */
    open file(emp) update direct environment(f(128))
        title('$1.EMP');

    /* Open the keys file as a stream */
    open file(keys) stream environment(b(4000))
        title('$1.KEY');

    /* Read keys into keylist */
    do i = 1 to 100 while (^eolist);
        get file(keys) list(keyname(i), keyval(i));
        eolist = keyname(i) = 'EOF';
    end;

    do while('1'b);
        put skip list('Employee: ');
        get list(matchname);
        if matchname = 'EOF' then
        stop;
        do i = 1 to 100;
            if matchname = keyname(i) then
                do;
                /* Read employee record with matching key */
                read file(emp) into(employee)
                    key(keyval(i));
                put skip list('Address: ', street, city, state, zip);
                put skip list(' ');
                get list(street, city, state, zip);
                put list('Hours: ', hours);
                get list(hours);
                /* Update employee record with new values */
                write file(emp) from(employee)
                    keyfrom(keyval(i));
                end;
        end;
    end;
    end update; 

instruction: Write a PL/1 program to read an employee's database and print a list of paychecks. 

input:  

output:

    /*****************************************************/
    /* This program reads an employee data base and    */
    /* prints a list of paychecks                        */
    /*****************************************************/

    report:
    procedure options (main);
    declare
        1 employee static,
            2 name      character (30) varying,
            2 address,
                3 street character (30) varying,
                3 city   character(10) varying,
                3 state  character (12) varying,
                3 zip    fixed decimal(5),

            2 age       fixed decimal(3),
            2 wage      fixed decimal(5,2),
            2 hours     fixed decimal(5,1);
    
    declare
        i fixed,
        dashes character (15) static initial
        ('$-------------');
        buff character 20) varying, 
        (grosspay, withhold) fixed decimal(7,2),
        (repfile, emptile) filei

    open file(empfile) Keyed environment (f(128),b(4000))
        title ('$1,EMP');
    open file(repfile) stream print environment(b(2000))
        title ('$2.$2');
    put listl'Set Top of Forms, Press Return');
    get skip;
    do while('1'b);
        read file(empfile) into(employee);
        if name = 'EOF' then
            stop;
        put file(repfile) skip(2);
        buff = '[' !! name !! ']^m^j';
        write file(repfile) from (buff);
        grosspy = wage * hours;
        withhold = grosspay * .15;
        buff = grosspay - withhold;
        do i=1 to 15
            while (substr(buff,i,1) = ' ');
        end;
        substr(buff,1,i) = substr(dashes,1,i);
        write file (repfile) from(buff);
    end;
    end report; 

instruction: write a PL/1 program to shocase the concept of label constant and variables. 

input:  

output:

    /*****************************************************/
    /* This is a nonfunctional pro~raM. Its purpose is */
    /* to illustrate the connept of label constants and */
    /* variables.                                         */
    /*****************************************************/
    labels:
        procedure option(main);
        declare
            i fixed,
            (x,y,z(3)) label;
        x = lab1;
        y = x;

        goto lab1;
        goto x;
        goto y;

        call P(lab2);
        do i=1 to 3;
            z(i) = c(i);
        end;

        i=2;
        goto z(i);
        goto c(i);

        c(1);
        c(2);
        c(3);

        lab2:;
        lab2:;

        P:
            procedure (g);
            declare
                g label;
            goto g;
        end P;
    end labels; 

instruction: Write a PL/1 program to shocase how PL/1 executes ON and REVERT statements. 

input:  

output:

    /*****************************************************/
    /* This program is nonfunctional, Its purpose is to */
    /* illustrate how PL/1 executes the ON and REVERT statements */
    /*****************************************************/
    auto_revert:
    procedure options (main);
    declare
        i fixed,
        sysin file;
    do i = 1 to 10000;
        call P(i,exit);
        exit:
    end;

    P:
        procedure (index,lab) ;
        declare
            (t, index) fixed,
            lab label;
        on endfile(sysin)
            goto lab;
        put skip list(index,':');
        get list(t);
        if t = index then
            goto lab;
    end P; /* implicit REVERT supplied here */
    end auto_revert; 

instruction: How can I copy my file to another file? Can you write a PL/1 program for the same? 

input:  

output:

    You can do the copying of files using buffer I/O. Below is the sample code for that.
    /********************************************************
    * This program copies one file to another using */
    /* buffered I/O							*/
    /******************************************************/
    copy:
        procedure options (main);
        declare
            (input_file, output_file) file;
        open file (input_file) stream
            environment (b (8192)) title ('$1,$1');
        open file (output_file) stream output
            environment (b (8192)) title ('$2,$2');
        declare
            buff character (254) varying;
        do while ('1'b);
            read file (input_file) into (buff);
            write file (output_file) from (buff);
        end;
    end copy; 

instruction: Write a PL/1 program to evaluat apolynomial expression considering end-of-file condition. 

input:  

output:

    /*****************************************************/
    /* This program evaluates a polynomial expression */
    /* using FLOAT BINARY data.It also traps the end-of- */
    /* file condition for the file SYSIN.                 */
    /*******************************************************/
    Pltpoly2:
    procedure options (main);
    %replace
        false by '0'b,
        true by '1'b;
    declare
        (x,y,z) float binary (24),
        eofile bit(1) static initial(false),
        sysin file;

    on endfile(sysin)
        eofile = true;
    do while(truel;
        put skip(2) lists'Type x,y,z: ');
        get list(x,y,z);

        if eofile then
            stop;
        put skip list('      2'); 
        put skip list('       x + 2y + z=',P(x,y,z));
    end;
    P:
        procedure (x,y,z) returns (float binary (24));
        declare
            (x,y,z) float binary (24);
        return (x*x+2*y+z);
    end P;
    end fitpoly2; 

instruction: Write a PL/1 program tocopy a STREAM file on disk to a print file. 

input:  

output:

 
    /*****************************************************/
    /* This program copies a STREAM file on disk to a */
    /* PRINT file, and formats the output with a page */
    /* header, and line numbers.                      */
    /****************************************************/
    copy: 
      procedure options(Main);
      declare 
          (sysin, sourcefile, printfile) file,
          (pagesize, pagewidth, spaces, linenumber) fixed,
          (line character(14), buff character(254)) varying;

      /* Error handler for end-of-file on console input */
      put list('^z   File to Print Copy Program');
      on endfile(sysin) 
          go to typeover;

      typeover:
          /* Get number of lines per page */
          put skip list('How Many Lines Per Page? ');
          get list(pagesize);

          /* Get number of column positions */
          put skip list('How Many Column Positions? ');
          get list(pagewidth);

      /* Error handler for invalid input */
      on error(1)
          begin;
              put list('Invalid Number, Type Integer');
              go to getnumber;
          end;

      /* Get line spacing */
      getnumber:
          put skip list('Line Spacing (1=Single)? ');
          get skip list(spaces);
          revert error(1);

      /* Get destination device/file */
      put skip list('Destination Device/File: ');
      get skip list(line);

      /* Open print file */
      open file(printfile) print pagesize(pagesize)
          linesize(pagewidth) title(line);

      /* Error handler for undefined source file */
      on undefinedfile(sourcefile)
          begin;
              put skip list('''',line,''' isn''t a Valid Name');
              go to retry;
          end;

      /* Retry getting source file */
      retry:
          put skip list('Source File to Print? ');
          get list(line);

          /* Open source file */
          open file(sourcefile) stream environment(b(8000))
              title(line);

      /* Error handler for end-of-file on source file */
      on endfile(sourcefile)
          begin;
              put file(printfile) page;
              stop;
          end;

      /* Error handler for end-of-file on print file */
      on endfile(printfile)
          begin;
              put skip list('^g^g^g^g Disk is Full');
              stop;
          end;

      /* Error handler for end-of-page on print file */
      on endpage(printfile)
          begin;
              put file(printfile) page skip(2)
                  list('PAGE', pageno(printfile));
              put file(printfile) skip(2);
          end;

      /* Trigger end-of-page signal */
      signal endpage(printfile);

      /* Main loop to copy lines from source to print file */
      do linenumber = 1 repeat(linenumber + 1);
          get file(sourcefile) edit(buff) (a);
          put file(printfile)
              edit(linenumber, ':', buff) (f(5), x(1), a(2), a);
          put file(printfile) skip(spaces);
      end;
    end copy; 

