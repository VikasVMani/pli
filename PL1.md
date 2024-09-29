Example 1:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 入力ファイル、出力ファイル、システムプリントファイルをオープン
    # 出力ファイルにヘッダー部を出力
    # 出力件数に固定値Ｐ１を加算する

    /* 入力ファイル */
    DCL DTIN01   FILE RECORD INPUT;
    /* 出力ファイル */
    DCL DTOT01   FILE RECORD OUTPUT;
    /* システムプリントファイル */
    DCL SYSPRINT FILE OUTPUT PRINT;

    /* ヘッダー部 */
    DCL 1 OT01_HDR,
    /* 出力件数 */
    DCL U01_OT01CTR              FIXED DEC(9)  INIT(0),
    /* 固定値Ｐ１ */
    DCL K01_P1                   FIXED DEC(1)  INIT (1);
    """

    出力:
    """
        OPEN FILE(DTIN01),
            FILE(DTOT01),
            FILE(SYSPRINT);
        WRITE FILE(DTOT01) FROM(OT01_HDR);
        U01_OT01CTR = U01_OT01CTR + K01_P1;
    """
Example 2:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # [SUB2000]初期処理を呼び出す
    # [SUB3000]入力ファイルREAD処理を呼び出す
    # 入力ファイルEOF判断項目が固定値０であれば、繰り返して下記処理を行う
    ##  [SUB4000]出力処理を呼び出す
    ##  [SUB3000]入力ファイルREAD処理を呼び出す
    # [SUB9000]終了処理を呼び出す


    /* 入力ファイルEOF判断項目 */
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');
    /* 固定値０ */
    DCL K01_C0                   CHAR(01)      INIT ('0'),
    """

    出力:
    """
        CALL SUB2000;
        CALL SUB3000;
        DO WHILE(U01_IN01EOF = K01_C0);
        CALL SUB4000;
        CALL SUB3000;
        END;
        CALL SUB9000;
    """
Example 3:

    入力:
    """
    以下のコードをPL/Iで書いてください。

    1.住所変更ファイル(DTIN01)を読み込み、
    判断項目１が'1'又は判断項目２が'1'のデータは対象データとして取得する。
    2.投信住所変更ファイル(DTOT01)を編集して出力する。
        2.1 ヘッダー部は1行目で下記項目を出力する
            ・固定値「'SACCT'」
            ・固定値「'99999999'」
        2.2 明細部は1行目で繰り返して下記項目を出力する
            ①レコード区分＝'1'
            ②店コード＝住所変更ファイル.店コード
            ③口座＝住所変更ファイル.口座
            ④住所変更ファイル.判断項目３が'1'の場合、
            住所名前１＝住所変更ファイル.住所名前の1桁始まる長12桁
            住所名前２＝住所変更ファイル.住所名前の13桁始まる長18桁
            ⑤住所変更ファイル.判断項目３が'2'の場合、
            住所名前１＝住所変更ファイル.住所名前の1桁始まる長18桁
            ⑥カナ名前１＝住所変更ファイル.カナ名前の1桁始まる長30桁
            ⑦カナ名前２＝住所変更ファイル.カナ名前の31桁始まる長18桁
            ⑧電話＝住所変更ファイル.電話の1桁始まる長13桁
            ⑨郵便＝住所変更ファイル.郵便
            ⑩人口コード＝住所変更ファイル.判断項目３
            ⑪住所コード＝住所変更ファイル.住所コード
            ⑫住所変更ファイル.判断項目４が'4'又は'5'、又は'6'の場合、
                変更区分＝'1'
            上記以外の場合、
                変更区分＝'0'
        2.3 END部は1行目で下記項目を出力する
            ・固定値「'EACCT'」
            ・明細件数
    3.下記メッセージ情報をLOGへ表示する。
        ・1行目:固定値「'***TESTPG01***'」
        ・2行目:DTIN01 = 入力件数
        ・3行目:DTOT01 = 出力総件数
    4.Inputファイルにデータがなければ、ヘッダー部とEND部も印刷する。
    参考情報：
    住所変更ファイル(DTIN01)
    判断項目１ (CHK_ITEM1)
    判断項目２ (CHK_ITEM2)
    店コード (STORE_CODE)
    口座 (KOZA)
    判断項目３ (CHK_ITEM3)
    住所名前 (ADDR_KJNAME)
    カナ名前 (ADDR_KNNAME)
    電話 (TEL)
    郵便 (YUBIN)
    住所コード (KENCODE)
    判断項目４ (CHK_ITEM4)
    投信住所変更ファイル(DTOT01)
        レコード区分 (RECKBN)
        店コード (STORE_CODE)
        口座 (KOZA)
        住所名前１ (KJNAME1)
        住所名前２ (KJNAME2)
        カナ名前１ (KNNAME1)
        カナ名前２ (KNNAME2)
        電話 (TEL)
        郵便 (YUBIN)
        人口コード (JINKAKU_CODE)
        住所コード (KENCODE)
        変更区分 (HENKBN) 
    明細件数(U01_MEICTR)
    入力件数(U01_IN01CTR)
    出力総件数(U01_OT01CTR)
    """

    出力:
    """
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
    """

Example 4:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 入力ファイルの読み込みが終了する時、入力ファイルEOF判断項目に固定値Ｃ１をセット

    /* 入力ファイル */
    DCL DTIN01   FILE RECORD INPUT;

    /* 入力ファイルEOF判断項目 */
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');

    /* 固定値Ｃ１ */
    DCL K01_C1                   CHAR(01)      INIT ('1'),
    """

    出力:
    """
    ON ENDFILE(DTIN01)
        BEGIN;
            U01_IN01EOF = K01_C1;
        END;
    """
Example 5:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 判断項目３を場合分けする
    ## 固定値１の場合
    出力.漢字名前１に、入力.住所名前の1桁目から12桁目を抽出
    出力.漢字名前２に、入力.住所名前の13桁目から19桁目を抽出
    ## 固定値２の場合
    出力.漢字名前１に、入力.住所名前の1桁目から18桁目を抽出
    ## 上記以外の場合終了

    /* 判断項目３ */
    DCL 3 CHK_ITEM3            CHAR(01)      INIT(' '),

    /* 入力 */
    DCL 1 IN01,
    /* 住所名前 */
    DCL 3 ADDR_KJNAME          CHAR(30)      INIT(' '),

    /* 出力 */
    DCL 1 OT01_DAT,
    /* 漢字名前１ */
    DCL 3 KJNAME1              CHAR(30),
    /* 漢字名前２ */
    DCL 3 KJNAME2              CHAR(30),

    /* 固定値１ */
    DCL K01_C1                   CHAR(01)      INIT ('1'),
    /* 固定値２ */
    DCL K01_C2                   CHAR(01)      INIT ('2'),
    """

    出力:
    """
    /* 出力ファイル明細の一部を編集出力する */
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
    """

Example 6:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 対象データFLGに固定値Ｃ０をセット
    # 入力ファイルEOF判断項目が固定値Ｃ０かつ対象データFLGが固定値Ｃ０であれば、繰り返して下記処理を行う
    ## 入力ファイルを入力エリアに読み込む
    ## 入力ファイルEOF判断項目が固定値Ｃ１の場合
        継続
    ## 入力ファイルEOF判断項目が上記以外の場合
        入力件数に固定値Ｐ１を加算
    ### 入力.判断項目１又は入力.判断項目２が固定値Ｃ１の場合
        対象データFLGに固定値Ｃ１をセット

    /* 入力ファイル */
    DCL DTIN01   FILE RECORD INPUT;
    /* 入力ファイルEOF判断項目 */
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');
    /* 入力エリア */
    DCL 1 IN01,
    /* 判断項目１ */
    DCL 3 CHK_ITEM1              CHAR(01)      INIT(' '),
    /* 判断項目２ */
    DCL 3 CHK_ITEM2              CHAR(01)      INIT(' '),

    /* 対象データFLG */
    DCL U01TAISYO                CHAR(01)      INIT ('0');
    /* 入力件数 */
    DCL U01_IN01CTR              FIXED DEC(9)  INIT(0),

    /* 固定値Ｃ０ */
    DCL K01_C0                   CHAR(01)      INIT ('0'),
    /* 固定値Ｃ１ */
    DCL K01_C1                   CHAR(01)      INIT ('1'),
    /* 固定値Ｐ１ */
    DCL K01_P1                   FIXED DEC(1)  INIT (1);
    """

    出力:
    """
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
    """
Example 7:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 出力.カナ名前１に、入力.カナ名前の1桁から30桁を抽出
    # 出力.カナ名前２に、入力.カナ名前の31桁から18桁を抽出
    # 出力.電話に、入力.電話の1桁から13桁を抽出
    # 出力.人口コードに、入力.判断項目３をセット
    # 入力.判断項目４が'4'又は'5'、又は'6'の場合、
        出力.変更区分に、固定値Ｃ１をセット
    # 上記以外の場合、
        出力.変更区分に、固定値Ｃ０をセット

    /* 入力 */
    DCL 1 IN01,
    /* カナ名前 */
    DCL 3 ADDR_KNNAME          CHAR(48)      INIT(' '),
    /* 判断項目３ */
    DCL 3 CHK_ITEM3            CHAR(01)      INIT(' '),
    /* 電話 */
    DCL 3 TEL                  CHAR(15)      INIT(' '),
    /* 郵便 */
    DCL 3 YUBIN                CHAR(07)      INIT(' '),
    /* 住所コード */
    DCL 3 KENCODE              CHAR(02)      INIT(' '),

    /* 出力 */
    DCL 1 OT01_DAT,
    /* カナ名前１ */
    DCL 3 KNNAME1              CHAR(30),
    /* カナ名前２ */
    DCL 3 KNNAME2              CHAR(30),
    /* 電話 */
    DCL 3 TEL                  CHAR(13),
    /* 人口コード */
    DCL 3 JINKAKU_CODE         CHAR(01),
    /* 変更区分 */
    DCL 3 HENKBN               CHAR(01);

    /* 固定値Ｃ０ */
    DCL K01_C0                   CHAR(01)      INIT ('0'),
    /* 固定値Ｃ１ */
    DCL K01_C1                   CHAR(01)      INIT ('1'),
    """

    出力:
    """
    /* 出力ファイル明細の一部を編集出力する */
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
    """
Example 8:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 出力ファイルに明細部を出力
    # 明細件数に固定値Ｐ１を加算
    # 出力件数に固定値Ｐ１を加算

    /* 出力ファイル */
    DCL DTOT01   FILE RECORD OUTPUT;
    /* 明細部 */
    DCL 1 OT01_DAT,

    /* 明細件数 */
    DCL U01_MEICTR               FIXED DEC(9)  INIT(0);
    /* 出力件数 */
    DCL U01_OT01CTR              FIXED DEC(9)  INIT(0),
    /* 固定値Ｐ１ */
    DCL K01_P1                   FIXED DEC(1)  INIT(1);
    """

    出力:
    """
        WRITE FILE(DTOT01) FROM(OT01_DAT);
        U01_MEICTR  = U01_MEICTR  + K01_P1;
        U01_OT01CTR = U01_OT01CTR + K01_P1;
    """
Example 9:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 入力ファイル、出力ファイルをオープン

    /* 入力ファイル */
    DCL DTIN01   FILE  RECORD INPUT;
    /* 出力ファイル */
    DCL DTOT01   FILE  RECORD OUTPUT;
    """

    出力:
    """
    /* ファイルオープン */
    OPEN FILE(DTIN01),
            FILE(DTOT01);
    """
Example 10:

    入力:
    """
    以下の処理説明に従い、PLIを生成。


    # 入力ファイルを入力エリアに読み込む
    # 入力ファイルEOF判断項目が固定値Ｃ０であれば、繰り返して下記処理を行う
    ## 退避エリア.部門コードに、入力.部門コードをセット
    ## 退避エリア.部門名称に、入力.部門名称をセット
    ## 部門別人数に、0をセット
    ## 入力ファイルEOF判断項目が固定値Ｃ０かつ退避エリア.部門コードが入力.部門コードであれば、繰り返して下記処理を行う
    ### 入力件数に1を加算
    ### 部門別人数に1を加算
    ### 入力ファイルを入力エリアに読み込む
    ## 出力.部門コードに、退避エリア.部門コードをセット
    ## 出力.部門名称に、退避エリア.部門名称をセット
    ## 出力.部門別人数に、部門別人数をセット
    ## 出力ファイルに出力エリアを出力
    ## 出力件数に1を加算

    /* 入力ファイル */
    DCL DTIN01   FILE RECORD INPUT;
    /* 出力ファイル */
    DCL DTOT01   FILE  RECORD OUTPUT;

    /* 入力ファイルEOF判断項目 */
    DCL U01_IN01EOF              CHAR(01)      INIT ('0');

    /* 入力エリア */
    DCL 1 IN01_REC,

    /* 入力 */
    DCL 1 IN01_REC,
    /* 部門コード */
    DCL 3 DEPT_CODE         CHAR(08)      INIT(' '),
    /* 部門名称 */
    DCL 3 DEPT_NAME         CHAR(30)      INIT(' '),

    /* 出力エリア */
    DCL 1 OT01_REC,

    /* 出力 */
    DCL 1 OT01_REC,
    /* 部門コード */
    DCL 3 DEPT_CODE         CHAR(08)      INIT(' '),
    /* 部門名称 */
    DCL 3 DEPT_NAME         CHAR(30)      INIT(' '),
    /* 部門別人数 */
    DCL 3 DEPT_COUNT        FIXED DEC(5)  INIT(0);

    /* 固定値Ｃ０ */
    DCL K01_C0                CHAR(01)      INIT('0'),

    /* 部門別人数 */
    DCL WK_COUNT              FIXED DEC(5)  INIT(0);
    /* 入力件数 */
    DCL U01_IN01CTR           FIXED DEC(9)  INIT(0);
    /* 出力件数 */
    DCL U01_OT01CTR           FIXED DEC(9)  INIT(0);

    /* 退避エリア */
    DCL 1 SAVE_KEY,
    /* 部門コード */
    DCL 3 DEPT_CODE         CHAR(08)      INIT(' '),
    /* 部門名称 */
    DCL 3 DEPT_NAME         CHAR(30)      INIT(' ');
    """

    出力:
    """
    /* 先頭レコード読み込み */
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
    """
Example 11:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 入力ファイルの読み込みが終了する時、入力ファイルEOF判断項目に固定値Ｃ１をセット

    /* 入力ファイル */
    DCL DTIN01   FILE RECORD INPUT;

    /* 入力ファイルEOF判断項目 */
    DCL EOF_DTIN01               CHAR(01)      INIT ('0');
    /* 固定値Ｃ１ */
    DCL K01_C1                   CHAR(01)      INIT ('1'),
    """

    出力:
    """
    ON ENDFILE(DTIN01)        EOF_DTIN01 = K01_C1;
    """

Example 12:

    入力:
    """
    以下のコードをPL/Iで書いてください。

    1.入力の部門情報詳細ファイルを読み込む。
    2.部門コードがキーとしてブレークする時、部門人数を合計して部門情報統計ファイルに出力する。
    3.INPUT、OUTPUTの件数をLOGへ表示する。
        ・1行目:'*** INPUT  DTIN01  =' + 部門情報詳細ファイルの件数 + ' KEN ***'
        ・2行目:'*** OUTPUT  DTOT01 =' + 部門情報統計ファイルの件数 + ' KEN ***'
    参考情報：
    部門情報詳細ファイル<DTIN01> のレイアウト：
    部門コード (DEPT_CODE)
    部門名称 (DEPT_NAME)
    社員番号 (EMP_CODE)
    社員名前 (EMP_NAME)
    電話番号 (EMP_TEL)
    部門情報統計ファイル<DTOT01> のレイアウト：
    部門コード (DEPT_CODE)
    部門名称 (DEPT_NAME)
    部門人数 (DEPT_COUNT)
    """

    出力:
    """
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
    DCL K01_C0                CHAR(01)      INIT('0'),
        K01_C1                CHAR(01)      INIT('1');
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
    """
Example 13:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # '*** INPUT  DTIN01  ='入力件数' KEN ***'をLOGに出力
    # '*** OUTPUT DTOT01  ='出力件数' KEN ***'をLOGに出力
    # 入力ファイル、出力ファイルをクローズ

    /* 入力ファイル */
    DCL DTIN01   FILE  RECORD INPUT;
    /* 出力ファイル */
    DCL DTOT01   FILE  RECORD OUTPUT;

    /* 入力件数 */
    DCL U01_IN01CTR           FIXED DEC(9)  INIT(0);
    /* 出力件数 */
    DCL U01_OT01CTR           FIXED DEC(9)  INIT(0);
    """

    出力:
    """
    PUT SKIP LIST ('*** INPUT  DTIN01  ='|| U01_IN01CTR ||' KEN ***');
    PUT SKIP LIST ('*** OUTPUT DTOT01  ='|| U01_OT01CTR ||' KEN ***');
    CLOSE FILE(DTIN01),
            FILE(DTOT01);
    """

example 14:

    入力:
    """
    以下の処理説明に従い、PLIを生成。

    # 出力ファイルにトレーラー部を出力
    # 出力件数に固定値Ｐ１を加算
    # '***TESTPG01***'をLOGに出力
    # 'DTIN01ｹﾝｽｳ ='入力件数をLOGに出力
    # 'DTOT01ｹﾝｽｳ ='出力総件数をLOGに出力
    # 入力ファイル、出力ファイル、システムプリントファイルをクローズ

    /* 入力ファイル */
    DCL DTIN01   FILE RECORD INPUT;
    /* 出力ファイル */
    DCL DTOT01   FILE RECORD OUTPUT;
    /* システムプリントファイル *
    DCL SYSPRINT FILE OUTPUT PRINT;

    /* トレーラー部 */
    DCL 1 OT01_END,
    /* 入力件数 */
    DCL U01_IN01CTR              FIXED DEC(9)  INIT(0),
    /* 出力件数 */
    DCL U01_OT01CTR              FIXED DEC(9)  INIT(0),

    /* 固定値Ｐ１ */
    DCL K01_P1                   FIXED DEC(1)  INIT (1);
    """

    出力:
    """
        WRITE FILE(DTOT01) FROM(OT01_END);
        U01_OT01CTR = U01_OT01CTR + K01_P1;
        PUT SKIP LIST ( '***TESTPG01***' );
        PUT SKIP LIST ( 'DTIN01ｹﾝｽｳ = '|| U01_IN01CTR );
        PUT SKIP LIST ( 'DTOT01ｹﾝｽｳ = '|| U01_OT01CTR );
        CLOSE FILE(DTIN01),
            FILE(DTOT01),
            FILE(SYSPRINT);
    """