Instruction:

    Generate PLI according to the following process description.

    # Open input file, output file, and system print file
    # Output header section to output file
    # Add fixed value P1 to the number of output cases

    /* Input file */
    DDCL DTIN01   FILE RECORD INPUT;
    /* Output file */
    DCL DTOT01   FILE RECORD OUTPUT;
    /* system print file */
    DCL SYSPRINT FILE OUTPUT PRINT;

    /* header section */
    DCL 1 OT01_HDR,
    /* number of outputs */
    DCL U01_OT01CTR              FIXED DEC(9)  INIT(0),
    /* Fixed value P1 */
    DCL K01_P1                   FIXED DEC(1)  INIT (1);

Input:  

Output:

     OPEN FILE(DTIN01),
          FILE(DTOT01),
          FILE(SYSPRINT);
     WRITE FILE(DTOT01) FROM(OT01_HDR);
     U01_OT01CTR = U01_OT01CTR + K01_P1;


instructions:

    Generate PLI according to the following process description.

    # Call [SUB2000] initial processing
    # Call [SUB3000] input file READ processing
    # If the input file EOF decision item is a fixed value of 0, repeat the following process.
    ## [SUB4000] call output process.
    ## [SUB3000] Call input file READ process.
    ## [SUB9000] call end processing


    /* Input file EOF decision item */
    DCL K01_C0                   CHAR(01)      INIT ('0'),
    /* Fixed value 0 */
    DCL K01_C0                   CHAR(01)      INIT ('0'),


Input:  

Output:

     CALL SUB2000;
     CALL SUB3000;
     DO WHILE(U01_IN01EOF = K01_C0);
       CALL SUB4000;
       CALL SUB3000;
     END;
     CALL SUB9000;


instructions:

    Please write the following code in PL/I

    1. Read the address change file (DTIN01),
    1. Read the change of address file (DTIN01) and acquire the data for which the decision item 1 is '1' or the decision item 2 is '1' as the target data.
    2. Edit and output the DTOT01 file.
        2.1 Output the following items in the first line of the header section.
            Fixed value ‘SACCT’.
            Fixed value ‘9999999999’.
        2.2 The detail section outputs the following items repeated on the first line
            (1) Record classification = '1'
            (2) Store code = Address change file. (2) Store code = '1' (3) Account = '1' in the change of address file.
            (3) Account = Change of address file. Account = Address change file.
            Account ④ Address Change File. If decision item 3 is '1',
            Address Name 1 = Address Change File. The length of the address name is 12 digits starting from the first digit of the name of the address.
            Address Name 2 = Address Change File. Address name 2 = Address change file.
            (5) Address Change File. When the judgment item 3 is '2',
            Address Name 1 = Address Change File. (5) Address Name 1 = Address Change File. 18 digits beginning with 1 digit of the address name.
            Kana Name 1 = Address Change File. (6) Kana Name 1 = Address Change File. 30 digits long starting with 1 digit of Kana Name.
            (7) Kana Name 2 = Address Change File. (7) Kana Name 2 = Address Change File. 31 digits beginning with Kana Name, 18 digits long.
            Phone = Change of Address File. Telephone=Long 13 digits beginning with 1 digit of Telephone
            Postal = Change Address file. Postal code = Postal code file.
            ⑩Population code = Change of address file. Determination item 3
            (11) Address code = Address change file. Address Code = Address Code
            (12) Change of Address File. If the judgment item 4 is '4', '5', or '6',
                Change Category = '1'.
            Other than the above,
                Change classification = '0'.
        2.3 The END section outputs the following items on the first line
            Fixed value ‘EACCT’.
            Number of details
    3. The following message information is displayed in LOG.
        Fixed value ‘***TESTPG01***’ in the first line.
        Line 2: DTIN01 = number of entries
        Third line: DTOT01 = Total number of outputs
    4. If there is no data in the Input file, the header and END sections are also printed.
    Reference information:
    Change of address file (DTIN01)
    Judgment item 1 (CHK_ITEM1)
    Judgment item 2 (CHK_ITEM2)
    Store code (STORE_CODE)
    Account (KOZA)
    Judgment item 3 (CHK_ITEM3)
    Address Name (ADDR_KJNAME)
    Kana Name (ADDR_KNNAME)
    Telephone (TEL)
    Postal Code (YUBIN)
    Address code (KENCODE)
    Decision Item 4 (CHK_ITEM4)
    Investment Trust Address Change File (DTOT01)
        Record Category (RECKBN)
        Store Code (STORE_CODE)
        Account (KOZA)
        Address Name1 (KJNAME1)
        Address Name2 (KJNAME2)
        KANA_NAME1 (KNNAME1)
        KANA_NAME2 (KNNAME2)
        Telephone (TEL)
        Postal code (YUBIN)
        Population Code (JINKAKU_CODE)
        Address Code (KENCODE)
        Change classification (HENKBN) 
    Number of statements (U01_MEICTR)
    Number of inputs (U01_IN01CTR)
    Total number of outputs (U01_OT01CTR)


Input:  

Output:

    /*-------------------------------------------------------------------*/
    /* PROGRAM DESCRIPTION:                                              */
    /*  PROCESS ADDRESS CHANGE FILE.                                     */
    /*  EXTRACT DESTINATIONS WITH INVESTMENT TRUST TRANSACTIONS AND      */
    /*  CREATE AN INVESTMENT TRUST ADDRESS CHANGE FILE.                  */
    /*-------------------------------------------------------------------*/
    PGM01:PROC OPTIONS(MAIN);
    /*--- FUNCTION DECLARATION ------------------------------------------*/
    DCL SUBSTR    BUILTIN;
    /* FILE DECLARATION */
    DCL DTIN01   FILE RECORD INPUT;
    DCL DTOT01   FILE RECORD OUTPUT;
    DCL SYSPRINT FILE OUTPUT PRINT;
    /*--- DTIN01 INPUT AREA ---------------------------------------------*/
    DCL 1 IN01,
        3 CHK_ITEM1            CHAR(01)      INIT(' '),
        3 CHK_ITEM2            CHAR(01)      INIT(' '),
        3 STORE_CODE           CHAR(03)      INIT(' '),
        3 KOZA                 PIC'9999999999',
        3 CHK_ITEM3            CHAR(01)      INIT(' '),
        3 ADDR_KJNAME          CHAR(30)      INIT(' '),
        3 ADDR_KNNAME          CHAR(48)      INIT(' '),
        3 TEL                  CHAR(15)      INIT(' '),
        3 YUBIN                CHAR(07)      INIT(' '),
        3 KENCODE              CHAR(02)      INIT(' '),
        3 CHK_ITEM4            CHAR(01)      INIT(' ');
    /*--- DTOT01 OUTPUT AREA--------------------------------------------*/
    DCL 1 OT01_HDR,
        3 DUMMY1               CHAR(01)      INIT('S'),
        3 DUMMY2               CHAR(04)      INIT('ACCT'),
        3 DUMMY3               CHAR(08)      INIT('99999999'),
        3 DUMMY4               CHAR(145)     INIT(' ');
    DCL 1 OT01_DAT,
        3 RECKBN               CHAR(01),
        3 STORE_CODE           PIC'999',
        3 KOZA                 PIC'9999999999',
        3 KJNAME1              CHAR(30),
        3 KJNAME2              CHAR(30),
        3 KNNAME1              CHAR(30),
        3 KNNAME2              CHAR(30),
        3 TEL                  CHAR(13),
        3 YUBIN                CHAR(07),
        3 JINKAKU_CODE         CHAR(01),
        3 KENCODE              CHAR(02),
        3 HENKBN               CHAR(01);
    DCL 1 OT01_END,
            2 DUMMY1               CHAR(01)      INIT('E'),
            2 DUMMY2               CHAR(04)      INIT('ACCT'),
            2 OT01_HDR_CNT         PIC'99999999',
            2 DUMMY3               CHAR(145)     INIT(' ');
    /*--- WORK AREA ----------------------------------------------------*/
    DCL U01_IN01CTR              FIXED DEC(9)  INIT(0),
        U01_OT01CTR              FIXED DEC(9)  INIT(0),
        U01_MEICTR               FIXED DEC(9)  INIT(0);
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');
    DCL U01TAISYO                CHAR(01)      INIT ('0');
    /*--- CONSTANT DECLARATION  ----------------------------------------*/
    DCL K01_C0                   CHAR(01)      INIT ('0'),
        K01_C1                   CHAR(01)      INIT ('1'),
        K01_C2                   CHAR(01)      INIT ('2'),
        K01_P1                   FIXED DEC(1)  INIT (1);
    /*--- ON CONDITION BLOCK --------------------------------------------*/
    ON ENDFILE(DTIN01)
        BEGIN;
            U01_IN01EOF = K01_C1;
        END;
    /*--- INIT ROUTINE --------------------------------------------------*/
        CALL SUB2000;
    /*--- MAIN ROUTINE --------------------------------------------------*/
        CALL SUB3000;
        DO WHILE(U01_IN01EOF = K01_C0);
        CALL SUB4000;
        CALL SUB3000;
        END;
    /*--- END ROUTINE  -------------------------------------------------*/
        CALL SUB9000;
    /*--- INIT PROCESS -------------------------------------------------*/
    SUB2000:PROC;
        OPEN FILE(DTIN01),
            FILE(DTOT01),
            FILE(SYSPRINT);
        WRITE FILE(DTOT01) FROM(OT01_HDR);
        U01_OT01CTR = U01_OT01CTR + K01_P1;
    END SUB2000;
    /*---  DTIN01 READ --------------------------------------------------*/
    SUB3000:PROC;
        U01TAISYO = K01_C0;
        DO WHILE(U01_IN01EOF = K01_C0 & U01TAISYO = K01_C0);
        READ FILE(DTIN01) INTO(IN01);
        IF U01_IN01EOF = K01_C1
        THEN;
        ELSE DO;
            U01_IN01CTR = U01_IN01CTR + K01_P1;
            IF IN01.CHK_ITEM1 = K01_C1 | IN01.CHK_ITEM2 = K01_C1
            THEN DO;
            U01TAISYO = K01_C1;
            END;
            ELSE;
        END;
        END;
    END SUB3000;
    /*---  DTOT01 EDIT & WRITE   ---------------------------------------*/
    SUB4000:PROC;
        OT01_DAT = '';
        OT01_DAT.RECKBN     = K01_C1;
        OT01_DAT.STORE_CODE = IN01.STORE_CODE;
        OT01_DAT.KOZA       = IN01.KOZA;
        SELECT(IN01.CHK_ITEM3);
        WHEN(K01_C1) 
            DO;      /* LEGAL PERSON */
            OT01_DAT.KJNAME1 = SUBSTR(IN01.ADDR_KJNAME,1,12);
            OT01_DAT.KJNAME2 = SUBSTR(IN01.ADDR_KJNAME,13,18);
            END;
        WHEN(K01_C2) 
            DO;      /* INDIVIDUAL PERSON  */
            OT01_DAT.KJNAME1 = SUBSTR(IN01.ADDR_KJNAME,1,18);
            END;
        OTHER;
        END;
        OT01_DAT.KNNAME1   = SUBSTR(IN01.ADDR_KNNAME,1,30);
        OT01_DAT.KNNAME2   = SUBSTR(IN01.ADDR_KNNAME,31,18);
        OT01_DAT.TEL       = SUBSTR(IN01.TEL,1,13);
        OT01_DAT.JINKAKU_CODE = IN01.CHK_ITEM3;
        IF IN01.CHK_ITEM4 = '4'
        | IN01.CHK_ITEM4 = '5'
        | IN01.CHK_ITEM4 = '6'
        THEN DO;
        OT01_DAT.HENKBN = K01_C1;
        END;
        ELSE DO;
        OT01_DAT.HENKBN = K01_C0;
        END;
        OT01_DAT.YUBIN    = IN01.YUBIN;
        OT01_DAT.KENCODE = IN01.KENCODE;
        WRITE FILE(DTOT01) FROM(OT01_DAT);
        U01_MEICTR  = U01_MEICTR  + K01_P1;
        U01_OT01CTR = U01_OT01CTR + K01_P1;
    END SUB4000;
    /*---  END PROCESSING  ---------------------------------------------*/
    SUB9000:PROC;
        OT01_HDR_CNT = U01_MEICTR;
        WRITE FILE(DTOT01) FROM(OT01_END);
        U01_OT01CTR = U01_OT01CTR + K01_P1;
        PUT SKIP LIST ( '***TESTPG01***' );
        PUT SKIP LIST ( 'DTIN01ｹﾝｽｳ = '|| U01_IN01CTR );
        PUT SKIP LIST ( 'DTOT01ｹﾝｽｳ = '|| U01_OT01CTR );
        CLOSE FILE(DTIN01),
            FILE(DTOT01),
            FILE(SYSPRINT);
    END SUB9000;
    END PGM01;
    


instructions:

    Generate PLI according to the following process description.

    # Set fixed value C1 to the input file EOF decision item when the input file is finished being read.

    /* input file */
    DCL DTIN01   FILE RECORD INPUT;

    /* Input file EOF judgment item */
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');

    /* Fixed value C1 */
    DCL K01_C1                   CHAR(01)      INIT ('1'),


Input:  

Output: 

   ON ENDFILE(DTIN01)
      BEGIN;
        U01_IN01EOF = K01_C1;
      END;


instructions:

    Generate PLI according to the following process description.

    ## Separate decision item 3 into cases.
    ## For fixed value 1
    Output . Kanji name 1, input . Extract the first to twelfth digits of the address name
    Output. Extract the 13th to 19th digit of the address name from Kanji name 2. Extract the 13th to 19th digit of the address name.
    ## For fixed value 2
    Output. Kanji name 1, input. Extract the 1st to 18th digit of the address name.
    ## In case of other than the above, exit

    /* Decision item 3 */
    DCL 3 CHK_ITEM3            CHAR(01)      INIT(' '),

    /* Input */
    DCL 1 IN01,
    /* Address name */
    DCL 3 ADDR_KJNAME          CHAR(30)      INIT(' '),

    /* Output */
    DCL 1 OT01_DAT,
    /* KJNAME1 */
    DCL 3 KJNAME1              CHAR(30),
    /* KJNAME2 */
    DCL 3 KJNAME2              CHAR(30),

    /* Fixed value 1 */
    DCL K01_C1                   CHAR(01)      INIT ('1'),
    /* Fixed value 2 */
    DCL K01_C2                   CHAR(01)      INIT ('2'),

Input:  

Output: 

    /* Edit output file details for some of the output file details */
    SELECT(IN01.CHK_ITEM3);
    WHEN(K01_C1) 
        DO;      /* LEGAL PERSON */
        OT01_DAT.KJNAME1 = SUBSTR(IN01.ADDR_KJNAME,1,12);
        OT01_DAT.KJNAME2 = SUBSTR(IN01.ADDR_KJNAME,13,18);
        END;
    WHEN(K01_C2) 
        DO;      /* INDIVIDUAL PERSON  */
        OT01_DAT.KJNAME1 = SUBSTR(IN01.ADDR_KJNAME,1,18);
        END;
    OTHER;
    END;


instructions:

    Generate PLI according to the following process description.

    # Set the target data FLG to the fixed value C0.
    # If the input file EOF judgment item is fixed value C0 and the target data FLG is fixed value C0, repeat the following process
    ## Read the input file into the input area
    ## If input file EOF judgment item is fixed value C1
        Continue
    ## If the input file EOF judgment item is other than the above
        Add fixed value P1 to the number of input cases.
    ### Input. If judgment item 1 or judgment item 2 is fixed value C1, add fixed value P1 to the number of entries. When judgment item 2 is fixed value C1
        Fixed value C1 is set to the target data FLG.

    /* input file */
    DCL DTIN01   FILE RECORD INPUT;
    /* Input file EOF judgment item */
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');
    /* Input area */
    DCL 1 IN01,
    /* Decision item 1 */
    DCL 3 CHK_ITEM1              CHAR(01)      INIT(' '),
    /* Decision item 2 */
    DCL 3 CHK_ITEM2              CHAR(01)      INIT(' '),

    /* Target data FLG */
    DCL U01TAISYO                CHAR(01)      INIT ('0');
    /* Number of inputs */
    DCL U01_IN01CTR              FIXED DEC(9)  INIT(0),

    /* Fixed value C0 */
    DCL K01_C0                   CHAR(01)      INIT ('0'),
    /* Fixed value C1 */
    DCL K01_C1                   CHAR(01)      INIT ('1'),
    /* Fixed value P1 */
    DCL K01_P1                   FIXED DEC(1)  INIT (1);



Input:  

Output: 

    U01TAISYO = K01_C0;
    DO WHILE(U01_IN01EOF = K01_C0 & U01TAISYO = K01_C0);
    READ FILE(DTIN01) INTO(IN01);
    IF U01_IN01EOF = K01_C1
    THEN;
    ELSE DO;
        U01_IN01CTR = U01_IN01CTR + K01_P1;
        IF IN01.CHK_ITEM1 = K01_C1 | IN01.CHK_ITEM2 = K01_C1
        THEN DO;
        U01TAISYO = K01_C1;
        END;
        ELSE;
    END;
    END;


instructions:

    Generate PLI according to the following process description.

    # Output . KanaName1, Input. Extract 1 to 30 digits of Kana name.
    # Output. Extract 18 digits from 31 digits of input . Extract 18 digits from 31 digits of Kana name.
    # Output. Phone, input. Extract 13 digits from 1 digits of phone.
    # Output. To population code, input . Set the decision item 3.
    # Input. If judgment item 4 is '4' or '5' or '6',
        Output. Change classification is set to the fixed value C1.
    # If other than above,
        Output. Change classification is set to the fixed value C0.

    /* Input */
    DCL 1 IN01,
    /* Kana name */
    DCL 3 ADDR_KNNAME          CHAR(48)      INIT(' '),
    /* Decision item 3 */
    DCL 3 CHK_ITEM3            CHAR(01)      INIT(' '),
    /* Telephone */
    DCL 3 TEL                  CHAR(15)      INIT(' '),
    /* Postal */
    DCL 3 YUBIN                CHAR(07)      INIT(' '),
    /* Address code */
    DCL 3 KENCODE              CHAR(02)      INIT(' '),

    /* Output */
    DCL 1 OT01_DAT,
    /* Kana name 1 */
    DCL 3 KNNAME1              CHAR(30),
    /* Kana name 2 */
    DCL 3 KNNAME2              CHAR(30),
    /* Phone */
    DCL 3 TEL                  CHAR(13),
    /* Population code */
    DCL 3 JINKAKU_CODE         CHAR(01),
    /* Change classification */
    CL 3 HENKBN               CHAR(01);

    /* Fixed value C0 */
    DCL K01_C0                   CHAR(01)      INIT ('0'),
    /* Fixed value C1 */
    DCL K01_C1                   CHAR(01)      INIT ('1'),


Input:  

Output: 

    /* Edit output to output a portion of the output file details */
    OT01_DAT.KNNAME1   = SUBSTR(IN01.ADDR_KNNAME,1,30);
    OT01_DAT.KNNAME2   = SUBSTR(IN01.ADDR_KNNAME,31,18);
    OT01_DAT.TEL       = SUBSTR(IN01.TEL,1,13);
    OT01_DAT.JINKAKU_CODE = IN01.CHK_ITEM3;
    IF IN01.CHK_ITEM4 = '4'
    | IN01.CHK_ITEM4 = '5'
    | IN01.CHK_ITEM4 = '6'
    THEN DO;
    OT01_DAT.HENKBN = K01_C1;
    END;
    ELSE DO;
    OT01_DAT.HENKBN = K01_C0;
    END;


instructions:

    Generate PLI according to the following process description.

    # Output detail section to output file
    # Add fixed value P1 to the number of statements
    # Add fixed value P1 to the number of output items

    /* Output file */
    DCL DTOT01   FILE RECORD OUTPUT;
    /* statement section */
    DCL 1 OT01_DAT,

    /* number of statements */
    DCL U01_MEICTR               FIXED DEC(9)  INIT(0);
    /* Number of outputs */
    DCL U01_OT01CTR              FIXED DEC(9)  INIT(0),
    /* Fixed value P1 */
    DCL K01_P1                   FIXED DEC(1)  INIT(1);


Input:  

Output: 

    WRITE FILE(DTOT01) FROM(OT01_DAT);
    U01_MEICTR  = U01_MEICTR  + K01_P1;
    U01_OT01CTR = U01_OT01CTR + K01_P1;


instructions:

    Generate PLI according to the following process description.

    # Open input and output files.

    /* Input file */
    DCL DTIN01   FILE  RECORD INPUT;
    /* Output file */
    DCL DTOT01   FILE  RECORD OUTPUT;


Input:  

Output: 

    /* open file */
    OPEN FILE(DTIN01),
        FILE(DTOT01);


instructions:

    Generate PLI according to the following process description.


    # Read the input file into the input area
    # If the input file EOF decision item is fixed value C0, repeat the following process.
    ## Retreat area . Set the department code to the input . Set the department code to the input.
    ## Set the department code in the evasion area. Set department name to input. Set department name.
    ## Set the number of persons by department to 0.
    ## If the input file EOF judgment item has the fixed value C0 and the save area. If the department code is Input. If it is a department code, repeat the following process.
    ### Add 1 to the number of entries.
    ### Add 1 to the number of persons in the department.
    ### Load the input file into the input area.
    ## Output. Set the department code to the save area. Set the department code in the save area to the department code.
    ## Output. Set department name to saved area. Department name is set to the department name.
    ## Output. Set department headcount to department headcount.
    ## Output area to output file.
    ## Add 1 to the number of outputs

    /* input file */
    DCL DTIN01   FILE RECORD INPUT;
    /* Output file */
    DCL DTOT01   FILE  RECORD OUTPUT;

    /* Input file EOF decision item */
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');

    /* Input area */
    DCL 1 IN01_REC,

    /* Input */
    DCL 1 IN01_REC,
    /* Department code */
    DCL 3 DEPT_CODE         CHAR(08)      INIT(' '),,
    /* Department name */
    DCL 3 DEPT_NAME         CHAR(30)      INIT(' '),

    /* Output area */
    DCL 1 OT01_REC,

    /* Output */
    DCL 1 OT01_REC,
    /* Department code */
    DCL 3 DEPT_CODE         CHAR(08)      INIT(' '),
    /* Department name */
    DCL 3 DEPT_NAME         CHAR(30)      INIT(' '),
    /* Number of persons by department */
    DCL 3 DEPT_COUNT        FIXED DEC(5)  INIT(0);

    /* Fixed value C0 */
    DCL K01_C0                CHAR(01)      INIT('0'),

    /* Number of persons by department */
    DCL WK_COUNT              FIXED DEC(5)  INIT(0);
    /* Number of inputs */
    DCL U01_IN01CTR           FIXED DEC(9)  INIT(0);
    /* Number of outputs */
    DCL U01_OT01CTR           FIXED DEC(9)  INIT(0);

    /* Save area */
    DCL 1 SAVE_KEY,
    /* Department code */
    DCL 3 DEPT_CODE         CHAR(08)      INIT(' '),
    /* Department name */
    DCL 3 DEPT_NAME         CHAR(30)      INIT(' ');


Input:  

Output:

    /* read first record */
    READ FILE(DTIN01) INTO(IN01_REC);
        DO WHILE(EOF_DTIN01 = K01_C0);
        SAVE_KEY.DEPT_CODE  = IN01_REC.DEPT_CODE;
        SAVE_KEY.DEPT_NAME  = IN01_REC.DEPT_NAME;
        WK_COUNT            = 0;
        DO WHILE(EOF_DTIN01 = K01_C0 &
            SAVE_KEY.DEPT_CODE = IN01_REC.DEPT_CODE);
            U01_IN01CTR        = U01_IN01CTR + 1;
            WK_COUNT           = WK_COUNT + 1;
            /* 次レコード読み込み */
            READ FILE(DTIN01)   INTO(IN01_REC);
        END;
        OT01_REC.DEPT_CODE  = SAVE_KEY.DEPT_CODE;
        OT01_REC.DEPT_NAME  = SAVE_KEY.DEPT_NAME;
        OT01_REC.DEPT_COUNT = WK_COUNT;
        WRITE FILE(DTOT01)  FROM(OT01_REC);
        U01_OT01CTR         = U01_OT01CTR + 1;
        END;


instructions:

    Generate PLI according to the following process description.

    # Set fixed value C1 to the input file EOF decision item when the input file is finished being read.

    /* input file */
    DCL DTIN01   FILE RECORD INPUT;

    /* Input file EOF judgment item */
    DCL EOF_DTIN01               CHAR(01)      INIT ('0');
    /* Fixed value C1 */
    DCL K01_C1                   CHAR(01)      INIT ('1'),


Input:  

Output: 

   ON ENDFILE(DTIN01)        EOF_DTIN01 = K01_C1;

instructions:

    Write the following code in PL/I.

    1. Read the department information detail file of the input.
    2. When the department code breaks as a key, total the number of people in the department and output to the department information statistics file.
    3. Display the number of INPUT and OUTPUT to LOG.
        Line 1:'*** INPUT DTIN01 =' + number of items in the department information detail file + 'KEN ***'.
        2nd line: '*** OUTPUT DTOT01 =' + number of items in the department information statistics file + ' KEN ***'
    Reference information:
    Layout of the department information detail file <DTIN01>:
    Department code (DEPT_CODE)
    Department name (DEPT_NAME)
    Employee number (EMP_CODE)
    Employee name (EMP_NAME)
    Phone number (EMP_TEL)
    Layout of the department information statistics file <DTOT01>:
    Department code (DEPT_CODE)
    Department name (DEPT_NAME)
    Department headcount (DEPT_COUNT)


Input:  

Output:

    PGM03: PROC    OPTIONS (MAIN);
    /*-------------------------------------------------------------------*/
    /* PROGRAM DESCRIPTION:                                              */
    /*  COUNT THE NUMBER OF EMPLOYEES IN THE SAME DEPARTMENT.            */
    /*  (BREAK PROCESS)                                                  */
    /*-------------------------------------------------------------------*/
    /* FILE DECLARATION */
    DCL DTIN01   FILE  RECORD INPUT;
    DCL DTOT01   FILE  RECORD OUTPUT;
    /* LAYOUT  DECLARATION */
    DCL 1 IN01_REC,
            3 DEPT_CODE         CHAR(08)      INIT(' '),
            3 DEPT_NAME         CHAR(30)      INIT(' '),
            3 EMP_CODE          CHAR(06)      INIT(' '),
            3 EMP_NAME          CHAR(20)      INIT(' '),
            3 EMP_TEL           CHAR(13)      INIT(' ');
    DCL 1 OT01_REC,
            3 DEPT_CODE         CHAR(08)      INIT(' '),
            3 DEPT_NAME         CHAR(30)      INIT(' '),
            3 DEPT_COUNT        PIC'(5)9'     INIT(0);
    /* USER DECLARATION */
    DCL K01_C0                CHAR(01)      INIT('0'),
        K01_C1                CHAR(01)      INIT('1');
    DCL WK_COUNT              FIXED DEC(5)  INIT(0);
    DCL U01_IN01CTR           FIXED DEC(9)  INIT(0);
    DCL U01_OT01CTR           FIXED DEC(9)  INIT(0);
    DCL 1 SAVE_KEY,
            3 DEPT_CODE         CHAR(08)      INIT(' '),
            3 DEPT_NAME         CHAR(30)      INIT(' ');
    /* ON CONDITION BLOCK */
    ON ENDFILE(DTIN01)        EOF_DTIN01 = K01_C1;
    /* OPEN */
    OPEN FILE(DTIN01),
        FILE(DTOT01);
    /* READ FIRST REOCRD */
    READ FILE(DTIN01) INTO(IN01_REC);
        DO WHILE(EOF_DTIN01 = K01_C0);
        SAVE_KEY.DEPT_CODE  = IN01_REC.DEPT_CODE;
        SAVE_KEY.DEPT_NAME  = IN01_REC.DEPT_NAME;
        WK_COUNT            = 0;
        DO WHILE(EOF_DTIN01 = K01_C0 &
            SAVE_KEY.DEPT_CODE = IN01_REC.DEPT_CODE);
            U01_IN01CTR        = U01_IN01CTR + 1;
            WK_COUNT           = WK_COUNT + 1;
            /* READ NEXT REOCRD */
            READ FILE(DTIN01)   INTO(IN01_REC);
        END;
        OT01_REC.DEPT_CODE  = SAVE_KEY.DEPT_CODE;
        OT01_REC.DEPT_NAME  = SAVE_KEY.DEPT_NAME;
        OT01_REC.DEPT_COUNT = WK_COUNT;
        WRITE FILE(DTOT01)  FROM(OT01_REC);
        U01_OT01CTR         = U01_OT01CTR + 1;
        END;
    /* CLOSE */
    PUT SKIP LIST ('*** INPUT  DTIN01  ='|| U01_IN01CTR ||' KEN ***');
    PUT SKIP LIST ('*** OUTPUT DTOT01  ='|| U01_OT01CTR ||' KEN ***');
    CLOSE FILE(DTIN01),
            FILE(DTOT01);
    END PGM03;



instructions:

    Generate PLI according to the following process description.

    # '*** INPUT DTIN01 ='Number of inputs' KEN ***' to LOG
    # Output '*** OUTPUT DTOT01 ='Number of outputs' KEN ***' to LOG
    # Close input and output files.

    /* input file */
    DCL DTIN01   FILE  RECORD INPUT;
    /* Output file */
    DCL DTOT01   FILE  RECORD OUTPUT;

    /* Input count */
    DCL U01_IN01CTR           FIXED DEC(9)  INIT(0);
    /* Number of outputs */
    DCL U01_OT01CTR           FIXED DEC(9)  INIT(0);


Input:  

Output: 

    PUT SKIP LIST ('*** INPUT  DTIN01  ='|| U01_IN01CTR ||' KEN ***');
    PUT SKIP LIST ('*** OUTPUT DTOT01  ='|| U01_OT01CTR ||' KEN ***');
    CLOSE FILE(DTIN01),
            FILE(DTOT01);


instructions:

    Generate PLI according to the following process description.

    # Output trailer section to output file
    # Add fixed value P1 to the number of output cases
    # Output '***TESTPG01***' to LOG
    # Output 'DTIN01Kensou =' number of input cases to LOG
    # Output 'DTOT01Kensou =' Total number of outputs to LOG
    # Close input file, output file and system print file

    /* Input file */
    DCL DTIN01   FILE RECORD INPUT;
    /* Output file */
    DCL DTOT01   FILE RECORD OUTPUT;
    /* system print file */
    DCL SYSPRINT FILE OUTPUT PRINT;

    /* Trailer section */
    DCL 1 OT01_END,
    /* number of inputs */
    DDCL U01_IN01CTR              FIXED DEC(9)  INIT(0),
    /* Number of outputs */
    DCL U01_OT01CTR              FIXED DEC(9)  INIT(0),

    /* Fixed value P1 */
    DCL K01_P1                   FIXED DEC(1)  INIT (1);


Input:  

Output:

    WRITE FILE(DTOT01) FROM(OT01_END);
    U01_OT01CTR = U01_OT01CTR + K01_P1;
    PUT SKIP LIST ( '***TESTPG01***' );
    PUT SKIP LIST ( 'DTIN01ｹﾝｽｳ = '|| U01_IN01CTR );
    PUT SKIP LIST ( 'DTOT01ｹﾝｽｳ = '|| U01_OT01CTR );
    CLOSE FILE(DTIN01),
        FILE(DTOT01),
        FILE(SYSPRINT);
