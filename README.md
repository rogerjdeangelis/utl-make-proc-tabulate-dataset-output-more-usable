# utl-make-proc-tabulate-dataset-output-more-usable
Make tabulate dataset output more usable 
    Make tabulate dataset output more usable                                                                        
                                                                                                                    
    github                                                                                                          
    https://tinyurl.com/wej4jeg                                                                                     
    https://github.com/rogerjdeangelis/utl-make-proc-tabulate-dataset-output-more-usable                            
                                                                                                                    
    This solution may only work with character classification variables?                                            
                                                                                                                    
    I know there are other procedures that can do this more easily, but tabulate offer s rich                       
    set of hierarchies and functions.                                                                               
                                                                                                                    
    It is a shame that tabulate does not honor ods output!!                                                         
    Another way to do this is output to excel and then input the excel output?                                      
                                                                                                                    
    SAS Forum                                                                                                       
    https://tinyurl.com/wgt5u33                                                                                     
    https://communities.sas.com/t5/New-SAS-User/PROC-TABULATE-OUTPUT/m-p/609944                                     
                                                                                                                    
    Problem:                                                                                                        
                                                                                                                    
      proc tabulate                                                                                                 
         DATA=sashelp.cars(keep=make origin drivetrain where=(make in ("Jeep","MINI","Scion","Isuzu")))             
                 out=work.tabout(drop=_page_ _table_ rename=(pctn_000=pct)) ;                                       
              CLASS _CHARACTER_ / ORDER=UNFORMATTED MISSING;                                                        
              TABLE _CHARACTER_, N PctN ;                                                                           
      run;quit;                                                                                                     
                                                                                                                    
    *      _                                                                                                        
      __ _(_)_   _____  ___                                                                                         
     / _` | \ \ / / _ \/ __|                                                                                        
    | (_| | |\ V /  __/\__ \                                                                                        
     \__, |_| \_/ \___||___/                                                                                        
     |___/                                                                                                          
    ;                                                                                                               
                                                                                                                    
     WORK.TABOUT total obs=9                                                                                        
                                                                                                                    
      MAKE     ORIGIN    DRIVETRAIN    _TYPE_    N      PCT                                                         
                                                                                                                    
      Isuzu                             100      2    22.2222                                                       
      Jeep                              100      3    33.3333                                                       
      MINI                              100      2    22.2222                                                       
      Scion                             100      2    22.2222                                                       
               Asia                     010      4    44.4444                                                       
               Europe                   010      2    22.2222                                                       
               USA                      010      3    33.3333                                                       
                           All          001      3    33.3333                                                       
                           Front        001      6    66.6667                                                       
                                                                                                                    
     *                    _                                                                                         
    __      ____ _ _ __ | |_                                                                                        
    \ \ /\ / / _` | '_ \| __|                                                                                       
     \ V  V / (_| | | | | |_                                                                                        
      \_/\_/ \__,_|_| |_|\__|                                                                                       
                                                                                                                    
    ;                                                                                                               
                                                                                                                    
     WORK.WANT total obs=9                                                                                          
                                                                                                                    
      VAR           CAT       N      PCT                                                                            
                                                                                                                    
      MAKE          Isuzu     2    22.2222                                                                          
      MAKE          Jeep      3    33.3333                                                                          
      MAKE          MINI      2    22.2222                                                                          
      MAKE          Scion     2    22.2222                                                                          
      ORIGIN        Asia      4    44.4444                                                                          
      ORIGIN        Europe    2    22.2222                                                                          
      ORIGIN        USA       3    33.3333                                                                          
      DRIVETRAIN    All       3    33.3333                                                                          
      DRIVETRAIN    Front     6    66.6667                                                                          
                                                                                                                    
    *_                   _                                                                                          
    (_)_ __  _ __  _   _| |_                                                                                        
    | | '_ \| '_ \| | | | __|                                                                                       
    | | | | | |_) | |_| | |_                                                                                        
    |_|_| |_| .__/ \__,_|\__|                                                                                       
            |_|                                                                                                     
    ;                                                                                                               
                                                                                                                    
                                                                                                                    
    data have;                                                                                                      
                                                                                                                    
     set sashelp.cars(keep=make origin drivetrain where=(make in ("Jeep","MINI","Scion","Isuzu")));                 
    run;quit;                                                                                                       
                                                                                                                    
                                                                                                                    
    Up to 40 obs WORK.HAVE total obs=9    |      RULES for Origin                                                   
                                          |                                                                         
    Obs    MAKE     ORIGIN    DRIVETRAIN  |                                                                         
                                             ASIZ    Total Count     Pct                                            
     1     Isuzu    Asia        All       |            9     4     44.444                                           
     2     Isuzu    Asia        Front     |                                                                         
     3     Scion    Asia        Front     |                                                                         
     4     Scion    Asia        Front     |                                                                         
                                                                                                                    
                                             USA     Total Count     Pct                                            
     5     Jeep     USA         Front     |            9      3    33.333                                           
     6     Jeep     USA         All       |                                                                         
     7     Jeep     USA         All       |                                                                         
                                             Europe    9      2    22.222                                           
     8     MINI     Europe      Front     |                                                                         
     9     MINI     Europe      Front     |                                                                         
                                                                                                                    
    *            _               _                                                                                  
      ___  _   _| |_ _ __  _   _| |_                                                                                
     / _ \| | | | __| '_ \| | | | __|                                                                               
    | (_) | |_| | |_| |_) | |_| | |_                                                                                
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                               
                    |_|                                                                                             
    ;                                                                                                               
                                                                                                                    
     WORK.WANT total obs=9                                                                                          
                                                                                                                    
      VAR           CAT       N      PCT                                                                            
                                                                                                                    
      MAKE          Isuzu     2    22.2222                                                                          
      MAKE          Jeep      3    33.3333                                                                          
      MAKE          MINI      2    22.2222                                                                          
      MAKE          Scion     2    22.2222                                                                          
      ORIGIN        Asia      4    44.4444                                                                          
      ORIGIN        Europe    2    22.2222                                                                          
      ORIGIN        USA       3    33.3333                                                                          
      DRIVETRAIN    All       3    33.3333                                                                          
      DRIVETRAIN    Front     6    66.6667                                                                          
                                                                                                                    
    *                                                                                                               
     _ __  _ __ ___   ___ ___  ___ ___                                                                              
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                             
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                             
    | .__/|_|  \___/ \___\___||___/___/                                                                             
    |_|                                                                                                             
    ;                                                                                                               
                                                                                                                    
                                                                                                                    
    This solution only works with character classification variablles.                                              
                                                                                                                    
    data want;                                                                                                      
                                                                                                                    
       if _n_=0 then do; %let rc=%sysfunc(dosubl('                                                                  
           proc tabulate                                                                                            
              DATA=sashelp.cars(keep=make origin drivetrain where=(make in ("Jeep","MINI","Scion","Isuzu")))        
                      out=work.tabout(drop=_page_ _table_ rename=(pctn_000=pct)) ;                                  
                   CLASS _CHARACTER_ / ORDER=UNFORMATTED MISSING;                                                   
                   TABLE _CHARACTER_, N PctN ;                                                                      
           run;quit;                                                                                                
           '));                                                                                                     
       end;                                                                                                         
       retain varpos 0 var cat;                                                                                     
                                                                                                                    
       set tabout;                                                                                                  
       by _type_ notsorted;                                                                                         
                                                                                                                    
       array nams[*] _character_;                                                                                   
                                                                                                                    
       cat=cats(of nams[*]);                                                                                        
                                                                                                                    
       * remove sufix of _type_;                                                                                    
       cat=substr(cat,1,length(cat)-length(_type_));                                                                
                                                                                                                    
       if first._type_ then varpos=varpos+1;                                                                        
                                                                                                                    
       * get variable name;                                                                                         
       var=vname(nams[varpos]);                                                                                     
       keep var cat n pct;                                                                                          
                                                                                                                    
    run;quit;                                                                                                       
                                                                                                                    
