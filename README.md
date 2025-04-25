# utl-adding-a-comprehensive-list-of-additional-functions-to-python-l-using-sqlean-dll
Adding a comprehensive list of additional functions to python pandaql using sqlean dll
    %let pgm=utl-adding-a-comprehensive-list-of-additional-functions-to-python-l-using-sqlean-dll;

    %stop_submission;

    Adding a comprehensive list of additional functions to python pandaql using sqlean dll

    Final example

       Example of perl regex in python using sqlean.dll extension refex_like function
       Problem Identifly company names that contain any of these words

    gitbub
    https://tinyurl.com/2um5wnvj
    https://github.com/rogerjdeangelis/utl-adding-a-comprehensive-list-of-additional-functions-to-python-l-using-sqlean-dll

    gthub
    https://tinyurl.com/4a2z4c3f
    https://github.com/rogerjdeangelis/utl-adding-a-superset-of-windows-functions-to-r-sqldf-using-precompiled-sqlean-dll

    /*
     _ __  _ __ ___ _ __
    | `_ \| `__/ _ \ `_ \
    | |_) | | |  __/ |_) |
    | .__/|_|  \___| .__/
    |_|            |_|
    */

     1 LOAD PRECOMPILED FUNCTIONS
     ============================

      I always create a restore point before downloading anything.

      download
      https://github.com/nalgeon/sqlean/releases/tag/0.27.1
      https://github.com/nalgeon/sqlean/releases/download/0.27.1/sqlean-win-x86.zip
      or
      https://tinyurl.com/3vet24f5
      https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories/blob/master/sqlean.dll
      or
      macros
      https://tinyurl.com/y9nfugth
      https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories

     2 UNZIP INTO
     ============
      d:/dll/sqlean.dll

     3 STATTRANSFER FUNCTION THAT CONVERTS PANDA DATAFRAME TO SAS DATASET
     ====================================================================

       You need to buy /StatTransfer
       https://stattransfer.com/ordering/store/

       filename ft15f001 "c:/oto/fn_tosas9x.py";
       parmcards4;
       def fn_tosas9x(df,outlib="d:/sd1/",outdsn="txm",timeest=3):
        pthsd1  = outlib + outdsn + ".sas7bdat"
        fthout  = outlib + outdsn + ".feather"
        statcmd = outlib + "statcmd.stcmd"
        if os.path.exists(pthsd1):
           os.remove(pthsd1)
        if os.path.exists(fthout):
           os.remove(fthout)
        if os.path.exists(statcmd):
           os.remove(statcmd)
        feather.write_feather(df,fthout,version=1)
        f = open(statcmd, "a")
        f.writelines([
         "set numeric-names        n                "
        ,"\nset log-level          e                "
        ,"\nset in-encoding        system           "
        ,"\nset out-encoding       system           "
        ,"\nset enc-errors         sub              "
        ,"\nset enc-sub-char       _                "
        ,"\nset enc-error-limit    100              "
        ,"\nset var-case-ci        preserve-always  "
        ,"\nset preserve-label-sets y               "
        ,"\nset preserve-str-widths n               "
        ,"\nset preserve-num-widths n               "
        ,"\nset recs-to-optimize   all              "
        ,"\nset map-miss-with-labs n                "
        ,"\nset user-miss          all              "
        ,"\nset map-user-miss      n                "
        ,"\nset sas-date-fmt       mmddyy           "
        ,"\nset sas-time-fmt       time             "
        ,"\nset sas-datetime-fmt   datetime         "
        ,"\nset write-file-label   none             "
        ,"\nset write-sas-fmts     n                "
        ,"\nset sas-outrep         windows_64       "
        ,"\nset write-old-ver      1                "
        ,"\ncopy " + fthout + " sas9 " + pthsd1 ])
        f.close()
        cmds="c:/PROGRA~1/StatTransfer17-64/st.exe " + outlib + "statcmd.stcmd"
        devnull = open('NUL', 'w');
        ;;;;
        run;quit;

      4 INTERFACE TO PANDASQL WITH EXTENSIONS AND EXPORT TO SAS DATASET
        SAVE THIS PYTON CODE in c:/oto/fn_pythonx.py

        NOTE YOU NEED sqlite3conn.load_extension('d:/dll/sqlean.dll') statement to add extensions

        filename ft15f001 "c:/oto/fn_pythonx.py";
        parmcards4;
        import pyarrow.feather as feather;
        import tempfile;
        import pyperclip;
        import os;
        import sys;
        import subprocess;
        import time;
        import pandas as pd;
        import pyreadstat as ps;
        import numpy as np;
        from pandasql import sqldf;
        mysql = lambda q: sqldf(q, globals());
        from pandasql import PandaSQL;
        pdsql = PandaSQL(persist=True);
        sqlite3conn = next(pdsql.conn.gen).connection.connection;
        sqlite3conn.enable_load_extension(True);
        sqlite3conn.load_extension('d:/dll/sqlean.dll');
        mysql = lambda q: sqldf(q, globals());
        exec(open('c:/oto/fn_tosas9x.py').read());
        ;;;;
        run;quit;

     You add these functions to both r sqldf and pandasql

     CATEGORIES OF ADDED FUNCTIONS FROM SQLEAN.DLL
    =============================================

    rypto       Hashing, encoding, and decoding data (e.g., MD5, SHA, Base64)
    define      User-defined functions and dynamic SQL
    fileio      File input/output (read/write files from SQL)
    fuzzy       Fuzzy string matching and phonetics (e.g., soundex, metaphone)
    ipaddr      IP address manipulation (IPv4/IPv6 parsing, conversion)
    math        Mathematical functions (trigonometry, rounding, etc.)
    regexp      Regular expressions (pattern matching)
    stats       Statistical functions (median, percentiles, etc.)
    text        Advanced string and Unicode functions
    time        High-precision date/time functions
    uuid        Universally Unique Identifier generat

    /**************************************************************************************************************************************/
    /*   NOTE SOME OF THESE FUNCTION ARE ONLY AVAILABLE ON THE SQLITE COMMAND LINE (IE MODE)                                              */
    /*               name          define_free    json_group_array      math_ceil           radians            stddev       time_fmt_iso  */
    /*                 ->              degrees   json_group_object       math_cos            random        stddev_pop      time_fmt_time  */
    /*                ->>           dense_rank         json_insert      math_cosh        randomblob       stddev_samp           time_get  */
    /*                abs           difference         json_object   math_degrees              rank             stdev       time_get_day  */
    /*               acos         dlevenshtein          json_patch       math_exp          readfile         strfilter      time_get_hour  */
    /*              acosh                dur_h         json_pretty     math_floor            regexp          strftime   time_get_isoweek  */
    /*                age                dur_m          json_quote        math_ln    regexp_capture        string_agg   time_get_isoyear  */
    /*               asin               dur_ms         json_remove       math_log       regexp_like            strpos    time_get_minute  */
    /*              asinh               dur_ns        json_replace     math_log10    regexp_replace            substr     time_get_month  */
    /*               atan                dur_s            json_set      math_log2     regexp_substr         substring      time_get_nano  */
    /*              atan2               dur_us           json_type       math_mod            repeat           subtype    time_get_second  */
    /*              atanh        edit_distance          json_valid        math_pi           replace               sum   time_get_weekday  */
    /*               atn2               encode               jsonb       math_pow         replicate           symlink      time_get_year  */
    /*                avg                 eval         jsonb_array   math_radians           reverse               tan   time_get_yearday  */
    /*         bit_length                  exp       jsonb_extract     math_round             right              tanh         time_micro  */
    /*             blake3        fileio_append   jsonb_group_array       math_sin          rightstr      text_bitsize         time_milli  */
    /*               bm25         fileio_mkdir  jsonb_group_object      math_sinh             round     text_casefold          time_nano  */
    /*              btrim          fileio_mode        jsonb_insert      math_sqrt        row_number       text_concat           time_now  */
    /*           casefold          fileio_read        jsonb_object       math_tan              rpad     text_contains         time_parse  */
    /*         caverphone       fileio_symlink         jsonb_patch      math_tanh          rsoundex        text_count         time_round  */
    /*               ceil         fileio_write        jsonb_remove     math_trunc        rtreecheck   text_has_prefix         time_since  */
    /*            ceiling          first_value       jsonb_replace            max        rtreedepth   text_has_suffix           time_sub  */
    /*            changes                floor           jsonb_set            md5         rtreenode        text_index      time_to_micro  */
    /*               char               format           julianday         median             rtrim         text_join      time_to_milli  */
    /*        char_length       fts3_tokenizer                 lag            min       script_code   text_last_index       time_to_nano  */
    /*   character_length                 fts5   last_insert_rowid          mkdir              sha1         text_left       time_to_unix  */
    /*          charindex      fts5_get_locale          last_value            mod            sha256       text_length         time_trunc  */
    /*           coalesce          fts5_locale                lead          .mode            sha384         text_like          time_unix  */
    /*             concat       fts5_source_id                left          nlike            sha512        text_lower         time_until  */
    /*          concat_ws          fuzzy_caver             leftstr         nlower              sign         text_lpad           timediff  */
    /*                cos         fuzzy_damlev              length            now               sin        text_ltrim       to_timestamp  */
    /*               cosh       fuzzy_editdist         levenshtein      nth_value              sinh       text_repeat              total  */
    /*                cot        fuzzy_hamming                like          ntile           snippet      text_replace      total_changes  */
    /*               coth        fuzzy_jarowin          likelihood         nullif           soundex      text_reverse          translate  */
    /*              count          fuzzy_leven              likely         nupper        split_part        text_right           translit  */
    /*      crypto_blake3        fuzzy_osadist                  ln   octet_length    sqlean_version         text_rpad               trim  */
    /*      crypto_decode       fuzzy_phonetic      load_extension        offsets        sqlite_log        text_rtrim              trunc  */
    /*      crypto_encode       fuzzy_rsoundex                 log       optimize  sqlite_source_id         text_size             typeof  */
    /*         crypto_md5         fuzzy_script               log10   osa_distance    sqlite_version        text_slice           unaccent  */
    /*        crypto_sha1        fuzzy_soundex                log2           padc              sqrt        text_split           undefine  */
    /*      crypto_sha256       fuzzy_translit               lower           padl            square    text_substring              unhex  */
    /*      crypto_sha384      gen_random_uuid      lower_quartile           padr       starts_with        text_title            unicode  */
    /*      crypto_sha512                 glob                lpad   percent_rank      stats_median    text_translate    unicode_version  */
    /*          cume_dist         group_concat              lsmode     percentile         stats_p25         text_trim          unixepoch  */
    /*       current_date              hamming               ltrim  percentile_25         stats_p75        text_upper           unlikely  */
    /*       current_time                  hex           make_date  percentile_75         stats_p90              time              upper  */
    /*  current_timestamp            highlight      make_timestamp  percentile_90         stats_p95          time_add     upper_quartile  */
    /*               date               ifnull               match  percentile_95         stats_p99     time_add_date              uuid4  */
    /*           date_add                  iif           matchinfo  percentile_99        stats_perc        time_after              uuid7  */
    /*          date_part                instr           math_acos  phonetic_hash      stats_stddev       time_before         uuid_blob   */
    /*         date_trunc         jaro_winkler          math_acosh             pi  stats_stddev_pop      time_compare          uuid_str   */
    /*           datetime                 json           math_asin            pow stats_stddev_samp         time_date           var_pop   */
    /*             decode           json_array          math_asinh          power         stats_var        time_equal          var_samp   */
    /*             define    json_array_length           math_atan         printf     stats_var_pop     time_fmt_date          variance   */
    /*       define_cache  json_error_position          math_atan2         proper    stats_var_samp time_fmt_datetime         writefile   */
    /*       json_extract           math_atanh          quote                                                                  zeroblob   */
    /**************************************************************************************************************************************/
    /*               _     _
     _ __  _ __ ___ | |__ | | ___ _ __ ___
    | `_ \| `__/ _ \| `_ \| |/ _ \ `_ ` _ \
    | |_) | | | (_) | |_) | |  __/ | | | | |
    | .__/|_|  \___/|_.__/|_|\___|_| |_| |_|
    |_|
    */

    /*************************************************************************************************************************************/
    /*          INPUT                            |         PROCESS                        |             OUTPUT                           */
    /*          =====                            |         =======                        |             ======                           */
    /*                                           |                                        |                                              */
    /* NAME                                      | 3 PYTHON SQL                           | PYTHON                                       */
    /*                                           | ============                           |                         NAME           match */
    /* investor_name                             |                                        |                             investor_name 0  */
    /* Gujarat Venture Capital Fund-1995         | proc datasets                          |         Gujarat Venture Capital Fund-1995 1  */
    /* Narendra Manibhai Patel                   |   nolist nodetails;                    |                   Narendra Manibhai Patel 0  */
    /* Emirates Bank International Pjsc          |  delete pywant;                        |          Emirates Bank International Pjsc 0  */
    /* Lic Of India Money Plus                   | run;quit;                              |                   Lic Of India Money Plus 0  */
    /* Savasthi Investment Ltd                   |                                        |                   Savasthi Investment Ltd 1  */
    /* Lic Of India Money Plus -1                | %utl_pybeginx;                         |                Lic Of India Money Plus -1 0  */
    /* Life Insurance Corporation Of India Ltd   | parmcards4;                            |   Life Insurance Corporation Of India Ltd 1  */
    /* Norges Bank A/C Government Petroleum Fund | exec(open(                       \     | Norges Bank A/C Government Petroleum Fund 1  */
    /* Reliance Capital Trustee Co Ltd A/C       |  'c:/oto/fn_pythonx.py').read());      |       Reliance Capital Trustee Co Ltd A/C 1  */
    /* Sundaram Bnp Paribas Mutual Fund A/C      | have,meta=ps.read_sas7bdat(      \     |      Sundaram Bnp Paribas Mutual Fund A/C 1  */
    /* Swiss Finance Corporation Mauritius Ltd   |   'd:/sd1/have.sas7bdat');             |   Swiss Finance Corporation Mauritius Ltd 1  */
    /* Acacia Institutional Partners Lp          | want=pdsql('''                         |          Acacia Institutional Partners Lp 0  */
    /* Acacia Partners Lp                        |  select                             \  |                        Acacia Partners Lp 0  */
    /* St. Helens Nominees India Pvt             |    name                             \  |             St. Helens Nominees India Pvt 1  */
    /*                                           |   ,regexp_like(                     \  |                                              */
    /*                                           |      name                           \  |  SAS                                         */
    /*                                           |    ,'\\s(Investment|Ltd|Pvt|Fund)') \  |  NAME                                  MATCH */
    /* options validvarname=upcase;              |      as match                       \  |                                              */
    /* libname sd1 "d:/sd1";                     |  from                               \  |  investor_name                             0 */
    /* data sd1.have;                            |    have                             \  |  Gujarat Venture Capital Fund-1995         1 */
    /*  input name & $44. ;                      |  ''')                                  |  Narendra Manibhai Patel                   0 */
    /* cards4;                                   | print(want);                           |  Emirates Bank International Pjsc          0 */
    /* investor_name                             | fn_tosas9x(                            |  Lic Of India Money Plus                   0 */
    /* Gujarat Venture Capital Fund-1995         |  want                                  |  Savasthi Investment Ltd                   1 */
    /* Narendra Manibhai Patel                   |  ,outlib='d:/sd1/'                     |  Lic Of India Money Plus -1                0 */
    /* Emirates Bank International Pjsc          |  ,outdsn='pywant'                      |  Life Insurance Corporation Of India Ltd   1 */
    /* Lic Of India Money Plus                   |  ,timeest=3);                          |  Norges Bank A/C Government Petroleum Fund 1 */
    /* Savasthi Investment Ltd                   | ;;;;                                   |  Reliance Capital Trustee Co Ltd A/C       1 */
    /* Lic Of India Money Plus -1                | %utl_pyendx;                           |  Sundaram Bnp Paribas Mutual Fund A/C      1 */
    /* Life Insurance Corporation Of India Ltd   |                                        |  Swiss Finance Corporation Mauritius Ltd   1 */
    /* Norges Bank A/C Government Petroleum Fund | proc print data=sd1.pywant;            |  Acacia Institutional Partners Lp          0 */
    /* Reliance Capital Trustee Co Ltd A/C       | run;quit;                              |  Acacia Partners Lp                        0 */
    /* Sundaram Bnp Paribas Mutual Fund A/C      |                                        |  St. Helens Nominees India Pvt             1 */
    /* Swiss Finance Corporation Mauritius Ltd   |                                                                                       */
    /* Acacia Institutional Partners Lp          |                                                                                       */
    /* Acacia Partners Lp                        |                                                                                       */
    /* St. Helens Nominees India Pvt             |                                                                                       */
    /* ;;;;                                      |                                                                                       */
    /* run;quit;                                 |                                                                                       */
    /*************************************************************************************************************************************/

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
     input name & $44. ;
    cards4;
    investor_name
    Gujarat Venture Capital Fund-1995
    Narendra Manibhai Patel
    Emirates Bank International Pjsc
    Lic Of India Money Plus
    Savasthi Investment Ltd
    Lic Of India Money Plus -1
    Life Insurance Corporation Of India Ltd
    Norges Bank A/C Government Petroleum Fund
    Reliance Capital Trustee Co Ltd A/C
    Sundaram Bnp Paribas Mutual Fund A/C
    Swiss Finance Corporation Mauritius Ltd
    Acacia Institutional Partners Lp
    Acacia Partners Lp
    St. Helens Nominees India Pvt
    ;;;;
    run;quit;


    /**************************************************************************************************************************/
    /* Obs    NAME                                                                                                            */
    /*                                                                                                                        */
    /*   1    investor_name                                                                                                   */
    /*   2    Gujarat Venture Capital Fund-1995                                                                               */
    /*   3    Narendra Manibhai Patel                                                                                         */
    /*   4    Emirates Bank International Pjsc                                                                                */
    /*   5    Lic Of India Money Plus                                                                                         */
    /*   6    Savasthi Investment Ltd                                                                                         */
    /*   7    Lic Of India Money Plus -1                                                                                      */
    /*   8    Life Insurance Corporation Of India Ltd                                                                         */
    /*   9    Norges Bank A/C Government Petroleum Fund                                                                       */
    /*  10    Reliance Capital Trustee Co Ltd A/C                                                                             */
    /*  11    Sundaram Bnp Paribas Mutual Fund A/C                                                                            */
    /*  12    Swiss Finance Corporation Mauritius Ltd                                                                         */
    /*  13    Acacia Institutional Partners Lp                                                                                */
    /*  14    Acacia Partners Lp                                                                                              */
    /*  15    St. Helens Nominees India Pvt                                                                                   */
    /**************************************************************************************************************************/

    /*           _   _                             _
     _ __  _   _| |_| |__   ___  _ __    ___  __ _| |
    | `_ \| | | | __| `_ \ / _ \| `_ \  / __|/ _` | |
    | |_) | |_| | |_| | | | (_) | | | | \__ \ (_| | |
    | .__/ \__, |\__|_| |_|\___/|_| |_| |___/\__, |_|
    |_|    |___/                                |_|
    */

    proc datasets
      nolist nodetails;
     delete pywant;
    run;quit;

    %utl_pybeginx;
    parmcards4;
    exec(open(                       \
     'c:/oto/fn_pythonx.py').read());
    have,meta=ps.read_sas7bdat(      \
      'd:/sd1/have.sas7bdat');
    want=pdsql('''
     select                             \
       name                             \
      ,regexp_like(                     \
         name                           \
       ,'\\s(Investment|Ltd|Pvt|Fund)') \
         as match                       \
     from                               \
       have                             \
     ''')
    print(want);
    fn_tosas9x(
     want
     ,outlib='d:/sd1/'
     ,outdsn='pywant'
     ,timeest=3);
    ;;;;
    %utl_pyendx;

    proc print data=sd1.pywant;
    run;quit;

    /**************************************************************************************************************************/
    /* python                                   NAME  match  |  SAS            NAME                         MATCH             */
    /*                                                       |                                                                */
    /* 0                               investor_name      0  |  investor_name                                  0              */
    /* 1           Gujarat Venture Capital Fund-1995      1  |  Gujarat Venture Capital Fund-1995              1              */
    /* 2                     Narendra Manibhai Patel      0  |  Narendra Manibhai Patel                        0              */
    /* 3            Emirates Bank International Pjsc      0  |  Emirates Bank International Pjsc               0              */
    /* 4                     Lic Of India Money Plus      0  |  Lic Of India Money Plus                        0              */
    /* 5                     Savasthi Investment Ltd      1  |  Savasthi Investment Ltd                        1              */
    /* 6                  Lic Of India Money Plus -1      0  |  Lic Of India Money Plus -1                     0              */
    /* 7     Life Insurance Corporation Of India Ltd      1  |  Life Insurance Corporation Of India Ltd        1              */
    /* 8   Norges Bank A/C Government Petroleum Fund      1  |  Norges Bank A/C Government Petroleum Fund      1              */
    /* 9         Reliance Capital Trustee Co Ltd A/C      1  |  Reliance Capital Trustee Co Ltd A/C            1              */
    /* 10       Sundaram Bnp Paribas Mutual Fund A/C      1  |  Sundaram Bnp Paribas Mutual Fund A/C           1              */
    /* 11    Swiss Finance Corporation Mauritius Ltd      1  |  Swiss Finance Corporation Mauritius Ltd        1              */
    /* 12           Acacia Institutional Partners Lp      0  |  Acacia Institutional Partners Lp               0              */
    /* 13                         Acacia Partners Lp      0  |  Acacia Partners Lp                             0              */
    /* 14              St. Helens Nominees India Pvt      1  |  St. Helens Nominees India Pvt                  1              */
    /**************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
