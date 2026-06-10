# Main Commands in Metasploit

Understanding the essential commands of Metasploit is key to using the framework effectively.

## 1. Start Console
```bash
msfconsole
```
### Example
```
└─$ msfconsole
                                                  

      .:okOOOkdc'           'cdkOOOko:.
    .xOOOOOOOOOOOOc       cOOOOOOOOOOOOx.
   :OOOOOOOOOOOOOOOk,   ,kOOOOOOOOOOOOOOO:
  'OOOOOOOOOkkkkOOOOO: :OOOOOOOOOOOOOOOOOO'
  oOOOOOOOO.MMMM.oOOOOoOOOOl.MMMM,OOOOOOOOo
  dOOOOOOOO.MMMMMM.cOOOOOc.MMMMMM,OOOOOOOOx
  lOOOOOOOO.MMMMMMMMM;d;MMMMMMMMM,OOOOOOOOl
  .OOOOOOOO.MMM.;MMMMMMMMMMM;MMMM,OOOOOOOO.
   cOOOOOOO.MMM.OOc.MMMMM'oOO.MMM,OOOOOOOc
    oOOOOOO.MMM.OOOO.MMM:OOOO.MMM,OOOOOOo
     lOOOOO.MMM.OOOO.MMM:OOOO.MMM,OOOOOl
      ;OOOO'MMM.OOOO.MMM:OOOO.MMM;OOOO;
       .dOOo'WM.OOOOocccxOOOO.MX'xOOd.
         ,kOl'M.OOOOOOOOOOOOO.M'dOk,
           :kk;.OOOOOOOOOOOOO.;Ok:
             ;kOOOOOOOOOOOOOOOk:
               ,xOOOOOOOOOOOx,
                 .lOOOOOOOl.
                    ,dOd,
                      .

       =[ metasploit v6.3.27-dev                          ]
+ -- --=[ 2335 exploits - 1220 auxiliary - 413 post       ]
+ -- --=[ 1385 payloads - 46 encoders - 11 nops           ]
+ -- --=[ 9 evasion                                       ]

Metasploit tip: Tired of setting RHOSTS for modules? Try 
globally setting it with setg RHOSTS x.x.x.x
Metasploit Documentation: https://docs.metasploit.com/

msf6 > 

```

## 2. Search Modules
``` 
search <keyword>
```
### Example
```bash
msf6 > search http html title

Matching Modules
================

   #  Name                                          Disclosure Date  Rank    Check  Description
   -  ----                                          ---------------  ----    -----  -----------
   0  auxiliary/scanner/http/emby_ssrf_scanner                       normal  No     Emby SSRF HTTP Scanner
   1  auxiliary/scanner/http/title                                   normal  No     HTTP HTML Title Tag Content Grabber
   2  exploit/windows/fileformat/vlc_realtext       2008-11-05       good    No     VLC Media Player RealText Subtitle Overflow
   3  exploit/windows/fileformat/visiwave_vwr_type  2011-05-20       great   No     VisiWave VWR File Parsing Vulnerability


Interact with a module by name or index. For example info 3, use 3 or use exploit/windows/fileformat/visiwave_vwr_type
```

## 3. Use a Module
```bash
use <module_path>
```
```bash
```

## 4. Set Module Options
```bash
set RHOSTS 192.168.1.10
set LHOST 192.168.1.5
```

## 5. Show Options
```bash
show options
```

## 6. Run or Exploit
```bash
run         # for auxiliary/post modules
exploit     # for exploit modules
```

## 7. Sessions Management
```bash
sessions
sessions -i 1
background
```

## 8. Database Commands
```bash
db_status
hosts
services
vulns
```

## 9. General Help
```bash
help
exit
```