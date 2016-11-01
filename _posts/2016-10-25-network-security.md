---
layout: post
title:  "Network Security"
date:   2016-10-25  
comments:   true  
---

# HW4 – Network Security

Kaidi He		G31860481

---

## 1)

I choose to use `netcat` as my port scanner. Using `-z -n` flags to avoid DNS request and using `netcat` as a scanner without sending any data. The command comes as:

```
# for TCP ports
$ netcat -z -n -w 1 172.32.16.1 [ports] -vv
# for UDP ports
$ netcat -z -n -u -w 1 172.32.16.1 [ports] -vv
```

Our target ports states as:

| Protocol | Ports |      | Protocol | Ports |
| -------- | ----- | ---- | -------: | ----: |
| TCP      | 5900  |      |      UDP |  5060 |
| TCP      | 23    |      |      UDP |  6537 |
| TCP      | 25    |      |      UDP |  1337 |
| TCP      | 22    |      |      UDP |    53 |
| TCP      | 445   |      |          |       |
| TCP      | 3389  |      |          |       |
| TCP      | 80    |      |          |       |
| TCP      | 1337  |      |          |       |
| TCP      | 12345 |      |          |       |
| TCP      | 1     |      |          |       |

See the dump file in q1.pcap.

## 2)

As far as I understand, a default scan contains no flags which can alter the result of the scanning. And we also know that default scan only contains TCP ports. So, I used this command to determine the ports in a default scan.

```
$ nmap 172.32.16.1 -d -d
```

- `172.32.16.1` is the IP address of my host machine.

| #    | Ports | Protocol | Common Name  |
| ---- | ----- | -------- | ------------ |
| 1    | 1     | tcp      | tcpmux       |
| 2    | 3     | tcp      | compressnet  |
| 3    | 4     | tcp      | unknown      |
| 4    | 6     | tcp      | unknown      |
| 5    | 7     | tcp      | echo         |
| 6    | 9     | tcp      | discard      |
| 7    | 13    | tcp      | daytime      |
| 8    | 17    | tcp      | qotd         |
| 9    | 19    | tcp      | chargen      |
| 10   | 20    | tcp      | ftp-data     |
| 11   | 21    | tcp      | ftp          |
| 12   | 22    | tcp      | ssh          |
| 13   | 23    | tcp      | telnet       |
| 14   | 24    | tcp      | priv-mail    |
| 15   | 25    | tcp      | smtp         |
| 16   | 26    | tcp      | rsftp        |
| 17   | 30    | tcp      | unknown      |
| 18   | 32    | tcp      | unknown      |
| 19   | 33    | tcp      | dsp          |
| 20   | 37    | tcp      | time         |
| 21   | 42    | tcp      | nameserver   |
| 22   | 43    | tcp      | whois        |
| 23   | 49    | tcp      | tacacs       |
| 24   | 53    | tcp      | domain       |
| 25   | 70    | tcp      | gopher       |
| 26   | 79    | tcp      | finger       |
| 27   | 80    | tcp      | http         |
| 28   | 81    | tcp      | hosts2-ns    |
| 29   | 82    | tcp      | xfer         |
| 30   | 83    | tcp      | mit-ml-dev   |
| 31   | 84    | tcp      | ctf          |
| 32   | 85    | tcp      | mit-ml-dev   |
| 33   | 88    | tcp      | kerberos-sec |
| 34   | 89    | tcp      | su-mit-tg    |
| 35   | 90    | tcp      | dnsix        |
| 36   | 99    | tcp      | metagram     |
| 37   | 100   | tcp      | newacct      |
| 38   | 106   | tcp      | pop3pw       |
| 39   | 109   | tcp      | pop2         |
| 40   | 110   | tcp      | pop3         |
| 41   | 111   | tcp      | rpcbind      |
| 42   | 113   | tcp      | ident        |
| 43   | 119   | tcp      | nntp         |
| 44   | 125   | tcp      | locus-map    |
| 45   | 135   | tcp      | msrpc        |
| 46   | 139   | tcp      | netbios-ssn  |
| 47   | 143   | tcp      | imap         |
| 48   | 144   | tcp      | news         |
| 49   | 146   | tcp      | iso-tp0      |
| 50   | 161   | tcp      | snmp         |
| 51   | 163   | tcp      | cmip-man     |
| 52   | 179   | tcp      | bgp          |
| 53   | 199   | tcp      | smux         |
| 54   | 211   | tcp      | 914c-g       |
| 55   | 212   | tcp      | anet         |
| 56   | 222   | tcp      | rsh-spx      |
| 57   | 254   | tcp      | unknown      |
| 58   | 255   | tcp      | unknown      |
| 59   | 256   | tcp      | fw1-securere |
| 60   | 259   | tcp      | esro-gen     |
| 61   | 264   | tcp      | bgmp         |
| 62   | 280   | tcp      | http-mgmt    |
| 63   | 301   | tcp      | unknown      |
| 64   | 306   | tcp      | unknown      |
| 65   | 311   | tcp      | asip-webadmi |
| 66   | 340   | tcp      | unknown      |
| 67   | 366   | tcp      | odmr         |
| 68   | 389   | tcp      | ldap         |
| 69   | 406   | tcp      | imsp         |
| 70   | 407   | tcp      | timbuktu     |
| 71   | 416   | tcp      | silverplatte |
| 72   | 417   | tcp      | onmux        |
| 73   | 425   | tcp      | icad-el      |
| 74   | 427   | tcp      | svrloc       |
| 75   | 443   | tcp      | https        |
| 76   | 444   | tcp      | snpp         |
| 77   | 445   | tcp      | microsoft-ds |
| 78   | 458   | tcp      | appleqtc     |
| 79   | 464   | tcp      | kpasswd5     |
| 80   | 465   | tcp      | smtps        |
| 81   | 481   | tcp      | dvs          |
| 82   | 497   | tcp      | retrospect   |
| 83   | 500   | tcp      | isakmp       |
| 84   | 512   | tcp      | exec         |
| 85   | 513   | tcp      | login        |
| 86   | 514   | tcp      | shell        |
| 87   | 515   | tcp      | printer      |
| 88   | 524   | tcp      | ncp          |
| 89   | 541   | tcp      | uucp-rlogin  |
| 90   | 543   | tcp      | klogin       |
| 91   | 544   | tcp      | kshell       |
| 92   | 545   | tcp      | ekshell      |
| 93   | 548   | tcp      | afp          |
| 94   | 554   | tcp      | rtsp         |
| 95   | 555   | tcp      | dsf          |
| 96   | 563   | tcp      | snews        |
| 97   | 587   | tcp      | submission   |
| 98   | 593   | tcp      | http-rpc-epm |
| 99   | 616   | tcp      | sco-sysmgr   |
| 100  | 617   | tcp      | sco-dtmgr    |
| 101  | 625   | tcp      | apple-xsrvr- |
| 102  | 631   | tcp      | ipp          |
| 103  | 636   | tcp      | ldapssl      |
| 104  | 646   | tcp      | ldp          |
| 105  | 648   | tcp      | rrp          |
| 106  | 666   | tcp      | doom         |
| 107  | 667   | tcp      | disclose     |
| 108  | 668   | tcp      | mecomm       |
| 109  | 683   | tcp      | corba-iiop   |
| 110  | 687   | tcp      | asipregistry |
| 111  | 691   | tcp      | resvc        |
| 112  | 700   | tcp      | epp          |
| 113  | 705   | tcp      | agentx       |
| 114  | 711   | tcp      | cisco-tdp    |
| 115  | 714   | tcp      | iris-xpcs    |
| 116  | 720   | tcp      | unknown      |
| 117  | 722   | tcp      | unknown      |
| 118  | 726   | tcp      | unknown      |
| 119  | 749   | tcp      | kerberos-adm |
| 120  | 765   | tcp      | webster      |
| 121  | 777   | tcp      | multiling-ht |
| 122  | 783   | tcp      | spamassassin |
| 123  | 787   | tcp      | qsc          |
| 124  | 800   | tcp      | mdbs_daemon  |
| 125  | 801   | tcp      | device       |
| 126  | 808   | tcp      | ccproxy-http |
| 127  | 843   | tcp      | unknown      |
| 128  | 873   | tcp      | rsync        |
| 129  | 880   | tcp      | unknown      |
| 130  | 888   | tcp      | accessbuilde |
| 131  | 898   | tcp      | sun-manageco |
| 132  | 900   | tcp      | omginitialre |
| 133  | 901   | tcp      | samba-swat   |
| 134  | 902   | tcp      | iss-realsecu |
| 135  | 903   | tcp      | iss-console- |
| 136  | 911   | tcp      | xact-backup  |
| 137  | 912   | tcp      | apex-mesh    |
| 138  | 981   | tcp      | unknown      |
| 139  | 987   | tcp      | unknown      |
| 140  | 990   | tcp      | ftps         |
| 141  | 992   | tcp      | telnets      |
| 142  | 993   | tcp      | imaps        |
| 143  | 995   | tcp      | pop3s        |
| 144  | 999   | tcp      | garcon       |
| 145  | 1000  | tcp      | cadlock      |
| 146  | 1001  | tcp      | unknown      |
| 147  | 1002  | tcp      | windows-icfw |
| 148  | 1007  | tcp      | unknown      |
| 149  | 1009  | tcp      | unknown      |
| 150  | 1010  | tcp      | surf         |
| 151  | 1011  | tcp      | unknown      |
| 152  | 1021  | tcp      | exp1         |
| 153  | 1022  | tcp      | exp2         |
| 154  | 1023  | tcp      | netvenuechat |
| 155  | 1024  | tcp      | kdm          |
| 156  | 1025  | tcp      | NFS-or-IIS   |
| 157  | 1026  | tcp      | LSA-or-nterm |
| 158  | 1027  | tcp      | IIS          |
| 159  | 1028  | tcp      | unknown      |
| 160  | 1029  | tcp      | ms-lsa       |
| 161  | 1030  | tcp      | iad1         |
| 162  | 1031  | tcp      | iad2         |
| 163  | 1032  | tcp      | iad3         |
| 164  | 1033  | tcp      | netinfo      |
| 165  | 1034  | tcp      | zincite-a    |
| 166  | 1035  | tcp      | multidropper |
| 167  | 1036  | tcp      | nsstp        |
| 168  | 1037  | tcp      | ams          |
| 169  | 1038  | tcp      | mtqp         |
| 170  | 1039  | tcp      | sbl          |
| 171  | 1040  | tcp      | netsaint     |
| 172  | 1041  | tcp      | danf-ak2     |
| 173  | 1042  | tcp      | afrog        |
| 174  | 1043  | tcp      | boinc        |
| 175  | 1044  | tcp      | dcutility    |
| 176  | 1045  | tcp      | fpitp        |
| 177  | 1046  | tcp      | wfremotertm  |
| 178  | 1047  | tcp      | neod1        |
| 179  | 1048  | tcp      | neod2        |
| 180  | 1049  | tcp      | td-postman   |
| 181  | 1050  | tcp      | java-or-OTGf |
| 182  | 1051  | tcp      | optima-vnet  |
| 183  | 1052  | tcp      | ddt          |
| 184  | 1053  | tcp      | remote-as    |
| 185  | 1054  | tcp      | brvread      |
| 186  | 1055  | tcp      | ansyslmd     |
| 187  | 1056  | tcp      | vfo          |
| 188  | 1057  | tcp      | startron     |
| 189  | 1058  | tcp      | nim          |
| 190  | 1059  | tcp      | nimreg       |
| 191  | 1060  | tcp      | polestar     |
| 192  | 1061  | tcp      | kiosk        |
| 193  | 1062  | tcp      | veracity     |
| 194  | 1063  | tcp      | kyoceranetde |
| 195  | 1064  | tcp      | jstel        |
| 196  | 1065  | tcp      | syscomlan    |
| 197  | 1066  | tcp      | fpo-fns      |
| 198  | 1067  | tcp      | instl_boots  |
| 199  | 1068  | tcp      | instl_bootc  |
| 200  | 1069  | tcp      | cognex-insig |
| 201  | 1070  | tcp      | gmrupdateser |
| 202  | 1071  | tcp      | bsquare-voip |
| 203  | 1072  | tcp      | cardax       |
| 204  | 1073  | tcp      | bridgecontro |
| 205  | 1074  | tcp      | warmspotMgmt |
| 206  | 1075  | tcp      | rdrmshc      |
| 207  | 1076  | tcp      | sns_credit   |
| 208  | 1077  | tcp      | imgames      |
| 209  | 1078  | tcp      | avocent-prox |
| 210  | 1079  | tcp      | asprovatalk  |
| 211  | 1080  | tcp      | socks        |
| 212  | 1081  | tcp      | pvuniwien    |
| 213  | 1082  | tcp      | amt-esd-prot |
| 214  | 1083  | tcp      | ansoft-lm-1  |
| 215  | 1084  | tcp      | ansoft-lm-2  |
| 216  | 1085  | tcp      | webobjects   |
| 217  | 1086  | tcp      | cplscrambler |
| 218  | 1087  | tcp      | cplscrambler |
| 219  | 1088  | tcp      | cplscrambler |
| 220  | 1089  | tcp      | ff-annunc    |
| 221  | 1090  | tcp      | ff-fms       |
| 222  | 1091  | tcp      | ff-sm        |
| 223  | 1092  | tcp      | obrpd        |
| 224  | 1093  | tcp      | proofd       |
| 225  | 1094  | tcp      | rootd        |
| 226  | 1095  | tcp      | nicelink     |
| 227  | 1096  | tcp      | cnrprotocol  |
| 228  | 1097  | tcp      | sunclustermg |
| 229  | 1098  | tcp      | rmiactivatio |
| 230  | 1099  | tcp      | rmiregistry  |
| 231  | 1100  | tcp      | mctp         |
| 232  | 1102  | tcp      | adobeserver- |
| 233  | 1104  | tcp      | xrl          |
| 234  | 1105  | tcp      | ftranhc      |
| 235  | 1106  | tcp      | isoipsigport |
| 236  | 1107  | tcp      | isoipsigport |
| 237  | 1108  | tcp      | ratio-adp    |
| 238  | 1110  | tcp      | nfsd-status  |
| 239  | 1111  | tcp      | lmsocialserv |
| 240  | 1112  | tcp      | msql         |
| 241  | 1113  | tcp      | ltp-deepspac |
| 242  | 1114  | tcp      | mini-sql     |
| 243  | 1117  | tcp      | ardus-mtrns  |
| 244  | 1119  | tcp      | bnetgame     |
| 245  | 1121  | tcp      | rmpp         |
| 246  | 1122  | tcp      | availant-mgr |
| 247  | 1123  | tcp      | murray       |
| 248  | 1124  | tcp      | hpvmmcontrol |
| 249  | 1126  | tcp      | hpvmmdata    |
| 250  | 1130  | tcp      | casp         |
| 251  | 1131  | tcp      | caspssl      |
| 252  | 1132  | tcp      | kvm-via-ip   |
| 253  | 1137  | tcp      | trim         |
| 254  | 1138  | tcp      | encrypted_ad |
| 255  | 1141  | tcp      | mxomss       |
| 256  | 1145  | tcp      | x9-icue      |
| 257  | 1147  | tcp      | capioverlan  |
| 258  | 1148  | tcp      | elfiq-repl   |
| 259  | 1149  | tcp      | bvtsonar     |
| 260  | 1151  | tcp      | unizensus    |
| 261  | 1152  | tcp      | winpoplanmes |
| 262  | 1154  | tcp      | resacommunit |
| 263  | 1163  | tcp      | sddp         |
| 264  | 1164  | tcp      | qsm-proxy    |
| 265  | 1165  | tcp      | qsm-gui      |
| 266  | 1166  | tcp      | qsm-remote   |
| 267  | 1169  | tcp      | tripwire     |
| 268  | 1174  | tcp      | fnet-remote- |
| 269  | 1175  | tcp      | dossier      |
| 270  | 1183  | tcp      | llsurfup-htt |
| 271  | 1185  | tcp      | catchpole    |
| 272  | 1186  | tcp      | mysql-cluste |
| 273  | 1187  | tcp      | alias        |
| 274  | 1192  | tcp      | caids-sensor |
| 275  | 1198  | tcp      | cajo-discove |
| 276  | 1199  | tcp      | dmidi        |
| 277  | 1201  | tcp      | nucleus-sand |
| 278  | 1213  | tcp      | mpc-lifenet  |
| 279  | 1216  | tcp      | etebac5      |
| 280  | 1217  | tcp      | hpss-ndapi   |
| 281  | 1218  | tcp      | aeroflight-a |
| 282  | 1233  | tcp      | univ-appserv |
| 283  | 1234  | tcp      | hotline      |
| 284  | 1236  | tcp      | bvcontrol    |
| 285  | 1244  | tcp      | isbconferenc |
| 286  | 1247  | tcp      | visionpyrami |
| 287  | 1248  | tcp      | hermes       |
| 288  | 1259  | tcp      | opennl-voice |
| 289  | 1271  | tcp      | excw         |
| 290  | 1272  | tcp      | cspmlockmgr  |
| 291  | 1277  | tcp      | miva-mqs     |
| 292  | 1287  | tcp      | routematch   |
| 293  | 1296  | tcp      | dproxy       |
| 294  | 1300  | tcp      | h323hostcall |
| 295  | 1301  | tcp      | ci3-software |
| 296  | 1309  | tcp      | jtag-server  |
| 297  | 1310  | tcp      | husky        |
| 298  | 1311  | tcp      | rxmon        |
| 299  | 1322  | tcp      | novation     |
| 300  | 1328  | tcp      | ewall        |
| 301  | 1334  | tcp      | writesrv     |
| 302  | 1352  | tcp      | lotusnotes   |
| 303  | 1417  | tcp      | timbuktu-srv |
| 304  | 1433  | tcp      | ms-sql-s     |
| 305  | 1434  | tcp      | ms-sql-m     |
| 306  | 1443  | tcp      | ies-lm       |
| 307  | 1455  | tcp      | esl-lm       |
| 308  | 1461  | tcp      | ibm_wrless_l |
| 309  | 1494  | tcp      | citrix-ica   |
| 310  | 1500  | tcp      | vlsi-lm      |
| 311  | 1501  | tcp      | sas-3        |
| 312  | 1503  | tcp      | imtc-mcs     |
| 313  | 1521  | tcp      | oracle       |
| 314  | 1524  | tcp      | ingreslock   |
| 315  | 1533  | tcp      | virtual-plac |
| 316  | 1556  | tcp      | veritas_pbx  |
| 317  | 1580  | tcp      | tn-tl-r1     |
| 318  | 1583  | tcp      | simbaexpress |
| 319  | 1594  | tcp      | sixtrak      |
| 320  | 1600  | tcp      | issd         |
| 321  | 1641  | tcp      | invision     |
| 322  | 1658  | tcp      | sixnetudr    |
| 323  | 1666  | tcp      | netview-aix- |
| 324  | 1687  | tcp      | nsjtp-ctrl   |
| 325  | 1688  | tcp      | nsjtp-data   |
| 326  | 1700  | tcp      | mps-raft     |
| 327  | 1717  | tcp      | fj-hdnet     |
| 328  | 1718  | tcp      | h323gatedisc |
| 329  | 1719  | tcp      | h323gatestat |
| 330  | 1720  | tcp      | h323q931     |
| 331  | 1721  | tcp      | caicci       |
| 332  | 1723  | tcp      | pptp         |
| 333  | 1755  | tcp      | wms          |
| 334  | 1761  | tcp      | landesk-rc   |
| 335  | 1782  | tcp      | hp-hcip      |
| 336  | 1783  | tcp      | unknown      |
| 337  | 1801  | tcp      | msmq         |
| 338  | 1805  | tcp      | enl-name     |
| 339  | 1812  | tcp      | radius       |
| 340  | 1839  | tcp      | netopia-vo1  |
| 341  | 1840  | tcp      | netopia-vo2  |
| 342  | 1862  | tcp      | mysql-cm-age |
| 343  | 1863  | tcp      | msnp         |
| 344  | 1864  | tcp      | paradym-31   |
| 345  | 1875  | tcp      | westell-stat |
| 346  | 1900  | tcp      | upnp         |
| 347  | 1914  | tcp      | elm-momentum |
| 348  | 1935  | tcp      | rtmp         |
| 349  | 1947  | tcp      | sentinelsrm  |
| 350  | 1971  | tcp      | netop-school |
| 351  | 1972  | tcp      | intersys-cac |
| 352  | 1974  | tcp      | drp          |
| 353  | 1984  | tcp      | bigbrother   |
| 354  | 1998  | tcp      | x25-svc-port |
| 355  | 1999  | tcp      | tcp-id-port  |
| 356  | 2000  | tcp      | cisco-sccp   |
| 357  | 2001  | tcp      | dc           |
| 358  | 2002  | tcp      | globe        |
| 359  | 2003  | tcp      | finger       |
| 360  | 2004  | tcp      | mailbox      |
| 361  | 2005  | tcp      | deslogin     |
| 362  | 2006  | tcp      | invokator    |
| 363  | 2007  | tcp      | dectalk      |
| 364  | 2008  | tcp      | conf         |
| 365  | 2009  | tcp      | news         |
| 366  | 2010  | tcp      | search       |
| 367  | 2013  | tcp      | raid-am      |
| 368  | 2020  | tcp      | xinupageserv |
| 369  | 2021  | tcp      | servexec     |
| 370  | 2022  | tcp      | down         |
| 371  | 2030  | tcp      | device2      |
| 372  | 2033  | tcp      | glogger      |
| 373  | 2034  | tcp      | scoremgr     |
| 374  | 2035  | tcp      | imsldoc      |
| 375  | 2038  | tcp      | objectmanage |
| 376  | 2040  | tcp      | lam          |
| 377  | 2041  | tcp      | interbase    |
| 378  | 2042  | tcp      | isis         |
| 379  | 2043  | tcp      | isis-bcast   |
| 380  | 2045  | tcp      | cdfunc       |
| 381  | 2046  | tcp      | sdfunc       |
| 382  | 2047  | tcp      | dls          |
| 383  | 2048  | tcp      | dls-monitor  |
| 384  | 2049  | tcp      | nfs          |
| 385  | 2065  | tcp      | dlsrpn       |
| 386  | 2068  | tcp      | avocentkvm   |
| 387  | 2099  | tcp      | h2250-annex- |
| 388  | 2100  | tcp      | amiganetfs   |
| 389  | 2103  | tcp      | zephyr-clt   |
| 390  | 2105  | tcp      | eklogin      |
| 391  | 2106  | tcp      | ekshell      |
| 392  | 2107  | tcp      | msmq-mgmt    |
| 393  | 2111  | tcp      | kx           |
| 394  | 2119  | tcp      | gsigatekeepe |
| 395  | 2121  | tcp      | ccproxy-ftp  |
| 396  | 2126  | tcp      | pktcable-cop |
| 397  | 2135  | tcp      | gris         |
| 398  | 2144  | tcp      | lv-ffx       |
| 399  | 2160  | tcp      | apc-2160     |
| 400  | 2161  | tcp      | apc-agent    |
| 401  | 2170  | tcp      | eyetv        |
| 402  | 2179  | tcp      | vmrdp        |
| 403  | 2190  | tcp      | tivoconnect  |
| 404  | 2191  | tcp      | tvbus        |
| 405  | 2196  | tcp      | unknown      |
| 406  | 2200  | tcp      | ici          |
| 407  | 2222  | tcp      | EtherNetIP-1 |
| 408  | 2251  | tcp      | dif-port     |
| 409  | 2260  | tcp      | apc-2260     |
| 410  | 2288  | tcp      | netml        |
| 411  | 2301  | tcp      | compaqdiag   |
| 412  | 2323  | tcp      | 3d-nfsd      |
| 413  | 2366  | tcp      | qip-login    |
| 414  | 2381  | tcp      | compaq-https |
| 415  | 2382  | tcp      | ms-olap3     |
| 416  | 2383  | tcp      | ms-olap4     |
| 417  | 2393  | tcp      | ms-olap1     |
| 418  | 2394  | tcp      | ms-olap2     |
| 419  | 2399  | tcp      | fmpro-fdal   |
| 420  | 2401  | tcp      | cvspserver   |
| 421  | 2492  | tcp      | groove       |
| 422  | 2500  | tcp      | rtsserv      |
| 423  | 2522  | tcp      | windb        |
| 424  | 2525  | tcp      | ms-v-worlds  |
| 425  | 2557  | tcp      | nicetec-mgmt |
| 426  | 2601  | tcp      | zebra        |
| 427  | 2602  | tcp      | ripd         |
| 428  | 2604  | tcp      | ospfd        |
| 429  | 2605  | tcp      | bgpd         |
| 430  | 2607  | tcp      | connection   |
| 431  | 2608  | tcp      | wag-service  |
| 432  | 2638  | tcp      | sybase       |
| 433  | 2701  | tcp      | sms-rcinfo   |
| 434  | 2702  | tcp      | sms-xfer     |
| 435  | 2710  | tcp      | sso-service  |
| 436  | 2717  | tcp      | pn-requester |
| 437  | 2718  | tcp      | pn-requester |
| 438  | 2725  | tcp      | msolap-ptp2  |
| 439  | 2800  | tcp      | acc-raid     |
| 440  | 2809  | tcp      | corbaloc     |
| 441  | 2811  | tcp      | gsiftp       |
| 442  | 2869  | tcp      | icslap       |
| 443  | 2875  | tcp      | dxmessagebas |
| 444  | 2909  | tcp      | funk-dialout |
| 445  | 2910  | tcp      | tdaccess     |
| 446  | 2920  | tcp      | roboeda      |
| 447  | 2967  | tcp      | symantec-av  |
| 448  | 2968  | tcp      | enpp         |
| 449  | 2998  | tcp      | iss-realsec  |
| 450  | 3000  | tcp      | ppp          |
| 451  | 3001  | tcp      | nessus       |
| 452  | 3003  | tcp      | cgms         |
| 453  | 3005  | tcp      | deslogin     |
| 454  | 3006  | tcp      | deslogind    |
| 455  | 3007  | tcp      | lotusmtap    |
| 456  | 3011  | tcp      | trusted-web  |
| 457  | 3013  | tcp      | gilatskysurf |
| 458  | 3017  | tcp      | event_listen |
| 459  | 3030  | tcp      | arepa-cas    |
| 460  | 3031  | tcp      | eppc         |
| 461  | 3052  | tcp      | powerchute   |
| 462  | 3071  | tcp      | csd-mgmt-por |
| 463  | 3077  | tcp      | orbix-loc-ss |
| 464  | 3128  | tcp      | squid-http   |
| 465  | 3168  | tcp      | poweronnud   |
| 466  | 3211  | tcp      | avsecuremgmt |
| 467  | 3221  | tcp      | xnm-clear-te |
| 468  | 3260  | tcp      | iscsi        |
| 469  | 3261  | tcp      | winshadow    |
| 470  | 3268  | tcp      | globalcatLDA |
| 471  | 3269  | tcp      | globalcatLDA |
| 472  | 3283  | tcp      | netassistant |
| 473  | 3300  | tcp      | ceph         |
| 474  | 3301  | tcp      | unknown      |
| 475  | 3306  | tcp      | mysql        |
| 476  | 3322  | tcp      | active-net   |
| 477  | 3323  | tcp      | active-net   |
| 478  | 3324  | tcp      | active-net   |
| 479  | 3325  | tcp      | active-net   |
| 480  | 3333  | tcp      | dec-notes    |
| 481  | 3351  | tcp      | btrieve      |
| 482  | 3367  | tcp      | satvid-datal |
| 483  | 3369  | tcp      | satvid-datal |
| 484  | 3370  | tcp      | satvid-datal |
| 485  | 3371  | tcp      | satvid-datal |
| 486  | 3372  | tcp      | msdtc        |
| 487  | 3389  | tcp      | ms-wbt-serve |
| 488  | 3390  | tcp      | dsc          |
| 489  | 3404  | tcp      | unknown      |
| 490  | 3476  | tcp      | nppmp        |
| 491  | 3493  | tcp      | nut          |
| 492  | 3517  | tcp      | 802-11-iapp  |
| 493  | 3527  | tcp      | beserver-msg |
| 494  | 3546  | tcp      | unknown      |
| 495  | 3551  | tcp      | apcupsd      |
| 496  | 3580  | tcp      | nati-svrloc  |
| 497  | 3659  | tcp      | apple-sasl   |
| 498  | 3689  | tcp      | rendezvous   |
| 499  | 3690  | tcp      | svn          |
| 500  | 3703  | tcp      | adobeserver- |
| 501  | 3737  | tcp      | xpanel       |
| 502  | 3766  | tcp      | sitewatch-s  |
| 503  | 3784  | tcp      | bfd-control  |
| 504  | 3800  | tcp      | pwgpsi       |
| 505  | 3801  | tcp      | ibm-mgr      |
| 506  | 3809  | tcp      | apocd        |
| 507  | 3814  | tcp      | neto-dcs     |
| 508  | 3826  | tcp      | wormux       |
| 509  | 3827  | tcp      | netmpi       |
| 510  | 3828  | tcp      | neteh        |
| 511  | 3851  | tcp      | spectraport  |
| 512  | 3869  | tcp      | ovsam-mgmt   |
| 513  | 3871  | tcp      | avocent-adsa |
| 514  | 3878  | tcp      | fotogcad     |
| 515  | 3880  | tcp      | igrs         |
| 516  | 3889  | tcp      | dandv-tester |
| 517  | 3905  | tcp      | mupdate      |
| 518  | 3914  | tcp      | listcrt-port |
| 519  | 3918  | tcp      | pktcablemmco |
| 520  | 3920  | tcp      | exasoftport1 |
| 521  | 3945  | tcp      | emcads       |
| 522  | 3971  | tcp      | lanrevserver |
| 523  | 3986  | tcp      | mapper-ws_et |
| 524  | 3995  | tcp      | iss-mgmt-ssl |
| 525  | 3998  | tcp      | dnx          |
| 526  | 4000  | tcp      | remoteanythi |
| 527  | 4001  | tcp      | newoak       |
| 528  | 4002  | tcp      | mlchat-proxy |
| 529  | 4003  | tcp      | pxc-splr-ft  |
| 530  | 4004  | tcp      | pxc-roid     |
| 531  | 4005  | tcp      | pxc-pin      |
| 532  | 4006  | tcp      | pxc-spvr     |
| 533  | 4045  | tcp      | lockd        |
| 534  | 4111  | tcp      | xgrid        |
| 535  | 4125  | tcp      | rww          |
| 536  | 4126  | tcp      | ddrepl       |
| 537  | 4129  | tcp      | nuauth       |
| 538  | 4224  | tcp      | xtell        |
| 539  | 4242  | tcp      | vrml-multi-u |
| 540  | 4279  | tcp      | vrml-multi-u |
| 541  | 4321  | tcp      | rwhois       |
| 542  | 4343  | tcp      | unicall      |
| 543  | 4443  | tcp      | pharos       |
| 544  | 4444  | tcp      | krb524       |
| 545  | 4445  | tcp      | upnotifyp    |
| 546  | 4446  | tcp      | n1-fwp       |
| 547  | 4449  | tcp      | privatewire  |
| 548  | 4550  | tcp      | gds-adppiw-d |
| 549  | 4567  | tcp      | tram         |
| 550  | 4662  | tcp      | edonkey      |
| 551  | 4848  | tcp      | appserv-http |
| 552  | 4899  | tcp      | radmin       |
| 553  | 4900  | tcp      | hfcs         |
| 554  | 4998  | tcp      | maybe-verita |
| 555  | 5000  | tcp      | upnp         |
| 556  | 5001  | tcp      | commplex-lin |
| 557  | 5002  | tcp      | rfe          |
| 558  | 5003  | tcp      | filemaker    |
| 559  | 5004  | tcp      | avt-profile- |
| 560  | 5009  | tcp      | airport-admi |
| 561  | 5030  | tcp      | surfpass     |
| 562  | 5033  | tcp      | jtnetd-serve |
| 563  | 5050  | tcp      | mmcc         |
| 564  | 5051  | tcp      | ida-agent    |
| 565  | 5054  | tcp      | rlm-admin    |
| 566  | 5060  | tcp      | sip          |
| 567  | 5061  | tcp      | sip-tls      |
| 568  | 5080  | tcp      | onscreen     |
| 569  | 5087  | tcp      | biotic       |
| 570  | 5100  | tcp      | admd         |
| 571  | 5101  | tcp      | admdog       |
| 572  | 5102  | tcp      | admeng       |
| 573  | 5120  | tcp      | barracuda-bb |
| 574  | 5190  | tcp      | aol          |
| 575  | 5200  | tcp      | targus-getda |
| 576  | 5214  | tcp      | unknown      |
| 577  | 5221  | tcp      | 3exmp        |
| 578  | 5222  | tcp      | xmpp-client  |
| 579  | 5225  | tcp      | hp-server    |
| 580  | 5226  | tcp      | hp-status    |
| 581  | 5269  | tcp      | xmpp-server  |
| 582  | 5280  | tcp      | xmpp-bosh    |
| 583  | 5298  | tcp      | presence     |
| 584  | 5357  | tcp      | wsdapi       |
| 585  | 5405  | tcp      | pcduo        |
| 586  | 5414  | tcp      | statusd      |
| 587  | 5431  | tcp      | park-agent   |
| 588  | 5432  | tcp      | postgresql   |
| 589  | 5440  | tcp      | unknown      |
| 590  | 5500  | tcp      | hotline      |
| 591  | 5510  | tcp      | secureidprop |
| 592  | 5544  | tcp      | unknown      |
| 593  | 5550  | tcp      | sdadmind     |
| 594  | 5555  | tcp      | freeciv      |
| 595  | 5560  | tcp      | isqlplus     |
| 596  | 5566  | tcp      | westec-conne |
| 597  | 5631  | tcp      | pcanywhereda |
| 598  | 5633  | tcp      | beorl        |
| 599  | 5666  | tcp      | nrpe         |
| 600  | 5678  | tcp      | rrac         |
| 601  | 5679  | tcp      | activesync   |
| 602  | 5718  | tcp      | dpm          |
| 603  | 5730  | tcp      | unieng       |
| 604  | 5800  | tcp      | vnc-http     |
| 605  | 5801  | tcp      | vnc-http-1   |
| 606  | 5802  | tcp      | vnc-http-2   |
| 607  | 5810  | tcp      | unknown      |
| 608  | 5811  | tcp      | unknown      |
| 609  | 5815  | tcp      | unknown      |
| 610  | 5822  | tcp      | unknown      |
| 611  | 5825  | tcp      | unknown      |
| 612  | 5850  | tcp      | unknown      |
| 613  | 5859  | tcp      | wherehoo     |
| 614  | 5862  | tcp      | unknown      |
| 615  | 5877  | tcp      | unknown      |
| 616  | 5900  | tcp      | vnc          |
| 617  | 5901  | tcp      | vnc-1        |
| 618  | 5902  | tcp      | vnc-2        |
| 619  | 5903  | tcp      | vnc-3        |
| 620  | 5904  | tcp      | unknown      |
| 621  | 5906  | tcp      | unknown      |
| 622  | 5907  | tcp      | unknown      |
| 623  | 5910  | tcp      | cm           |
| 624  | 5911  | tcp      | cpdlc        |
| 625  | 5915  | tcp      | unknown      |
| 626  | 5922  | tcp      | unknown      |
| 627  | 5925  | tcp      | unknown      |
| 628  | 5950  | tcp      | unknown      |
| 629  | 5952  | tcp      | unknown      |
| 630  | 5959  | tcp      | unknown      |
| 631  | 5960  | tcp      | unknown      |
| 632  | 5961  | tcp      | unknown      |
| 633  | 5962  | tcp      | unknown      |
| 634  | 5963  | tcp      | indy         |
| 635  | 5987  | tcp      | wbem-rmi     |
| 636  | 5988  | tcp      | wbem-http    |
| 637  | 5989  | tcp      | wbem-https   |
| 638  | 5998  | tcp      | ncd-diag     |
| 639  | 5999  | tcp      | ncd-conf     |
| 640  | 6000  | tcp      | X11          |
| 641  | 6001  | tcp      | X11:1        |
| 642  | 6002  | tcp      | X11:2        |
| 643  | 6003  | tcp      | X11:3        |
| 644  | 6004  | tcp      | X11:4        |
| 645  | 6005  | tcp      | X11:5        |
| 646  | 6006  | tcp      | X11:6        |
| 647  | 6007  | tcp      | X11:7        |
| 648  | 6009  | tcp      | X11:9        |
| 649  | 6025  | tcp      | x11          |
| 650  | 6059  | tcp      | X11:59       |
| 651  | 6100  | tcp      | synchronet-d |
| 652  | 6101  | tcp      | backupexec   |
| 653  | 6106  | tcp      | isdninfo     |
| 654  | 6112  | tcp      | dtspc        |
| 655  | 6123  | tcp      | backup-expre |
| 656  | 6129  | tcp      | unknown      |
| 657  | 6156  | tcp      | unknown      |
| 658  | 6346  | tcp      | gnutella     |
| 659  | 6389  | tcp      | clariion-evr |
| 660  | 6502  | tcp      | netop-rc     |
| 661  | 6510  | tcp      | mcer-port    |
| 662  | 6543  | tcp      | mythtv       |
| 663  | 6547  | tcp      | powerchutepl |
| 664  | 6565  | tcp      | unknown      |
| 665  | 6566  | tcp      | sane-port    |
| 666  | 6567  | tcp      | esp          |
| 667  | 6580  | tcp      | parsec-maste |
| 668  | 6646  | tcp      | unknown      |
| 669  | 6666  | tcp      | irc          |
| 670  | 6667  | tcp      | irc          |
| 671  | 6668  | tcp      | irc          |
| 672  | 6669  | tcp      | irc          |
| 673  | 6689  | tcp      | tsa          |
| 674  | 6692  | tcp      | unknown      |
| 675  | 6699  | tcp      | napster      |
| 676  | 6779  | tcp      | unknown      |
| 677  | 6788  | tcp      | smc-http     |
| 678  | 6789  | tcp      | ibm-db2-admi |
| 679  | 6792  | tcp      | unknown      |
| 680  | 6839  | tcp      | unknown      |
| 681  | 6881  | tcp      | bittorrent-t |
| 682  | 6901  | tcp      | jetstream    |
| 683  | 6969  | tcp      | acmsoda      |
| 684  | 7000  | tcp      | afs3-fileser |
| 685  | 7001  | tcp      | afs3-callbac |
| 686  | 7002  | tcp      | afs3-prserve |
| 687  | 7004  | tcp      | afs3-kaserve |
| 688  | 7007  | tcp      | afs3-bos     |
| 689  | 7019  | tcp      | doceri-ctl   |
| 690  | 7025  | tcp      | vmsvc-2      |
| 691  | 7070  | tcp      | realserver   |
| 692  | 7100  | tcp      | font-service |
| 693  | 7103  | tcp      | unknown      |
| 694  | 7106  | tcp      | unknown      |
| 695  | 7200  | tcp      | fodms        |
| 696  | 7201  | tcp      | dlip         |
| 697  | 7402  | tcp      | rtps-dd-mt   |
| 698  | 7435  | tcp      | unknown      |
| 699  | 7443  | tcp      | oracleas-htt |
| 700  | 7496  | tcp      | unknown      |
| 701  | 7512  | tcp      | unknown      |
| 702  | 7625  | tcp      | unknown      |
| 703  | 7627  | tcp      | soap-http    |
| 704  | 7676  | tcp      | imqbrokerd   |
| 705  | 7741  | tcp      | scriptview   |
| 706  | 7777  | tcp      | cbt          |
| 707  | 7778  | tcp      | interwise    |
| 708  | 7800  | tcp      | asr          |
| 709  | 7911  | tcp      | unknown      |
| 710  | 7920  | tcp      | unknown      |
| 711  | 7921  | tcp      | unknown      |
| 712  | 7937  | tcp      | nsrexecd     |
| 713  | 7938  | tcp      | lgtomapper   |
| 714  | 7999  | tcp      | irdmi2       |
| 715  | 8000  | tcp      | http-alt     |
| 716  | 8001  | tcp      | vcom-tunnel  |
| 717  | 8002  | tcp      | teradataordb |
| 718  | 8007  | tcp      | ajp12        |
| 719  | 8008  | tcp      | http         |
| 720  | 8009  | tcp      | ajp13        |
| 721  | 8010  | tcp      | xmpp         |
| 722  | 8011  | tcp      | unknown      |
| 723  | 8021  | tcp      | ftp-proxy    |
| 724  | 8022  | tcp      | oa-system    |
| 725  | 8031  | tcp      | unknown      |
| 726  | 8042  | tcp      | fs-agent     |
| 727  | 8045  | tcp      | unknown      |
| 728  | 8080  | tcp      | http-proxy   |
| 729  | 8081  | tcp      | blackice-ice |
| 730  | 8082  | tcp      | blackice-ale |
| 731  | 8083  | tcp      | us-srv       |
| 732  | 8084  | tcp      | unknown      |
| 733  | 8085  | tcp      | unknown      |
| 734  | 8086  | tcp      | d-s-n        |
| 735  | 8087  | tcp      | simplifymedi |
| 736  | 8088  | tcp      | radan-http   |
| 737  | 8089  | tcp      | unknown      |
| 738  | 8090  | tcp      | unknown      |
| 739  | 8093  | tcp      | unknown      |
| 740  | 8099  | tcp      | unknown      |
| 741  | 8100  | tcp      | xprint-serve |
| 742  | 8180  | tcp      | unknown      |
| 743  | 8181  | tcp      | intermapper  |
| 744  | 8192  | tcp      | sophos       |
| 745  | 8193  | tcp      | sophos       |
| 746  | 8194  | tcp      | sophos       |
| 747  | 8200  | tcp      | trivnet1     |
| 748  | 8222  | tcp      | unknown      |
| 749  | 8254  | tcp      | unknown      |
| 750  | 8290  | tcp      | unknown      |
| 751  | 8291  | tcp      | unknown      |
| 752  | 8292  | tcp      | blp3         |
| 753  | 8300  | tcp      | tmi          |
| 754  | 8333  | tcp      | bitcoin      |
| 755  | 8383  | tcp      | m2mservices  |
| 756  | 8400  | tcp      | cvd          |
| 757  | 8402  | tcp      | abarsd       |
| 758  | 8443  | tcp      | https-alt    |
| 759  | 8500  | tcp      | fmtp         |
| 760  | 8600  | tcp      | asterix      |
| 761  | 8649  | tcp      | unknown      |
| 762  | 8651  | tcp      | unknown      |
| 763  | 8652  | tcp      | unknown      |
| 764  | 8654  | tcp      | unknown      |
| 765  | 8701  | tcp      | unknown      |
| 766  | 8800  | tcp      | sunwebadmin  |
| 767  | 8873  | tcp      | dxspider     |
| 768  | 8888  | tcp      | sun-answerbo |
| 769  | 8899  | tcp      | ospf-lite    |
| 770  | 8994  | tcp      | unknown      |
| 771  | 9000  | tcp      | cslistener   |
| 772  | 9001  | tcp      | tor-orport   |
| 773  | 9002  | tcp      | dynamid      |
| 774  | 9003  | tcp      | unknown      |
| 775  | 9009  | tcp      | pichat       |
| 776  | 9010  | tcp      | sdr          |
| 777  | 9011  | tcp      | unknown      |
| 778  | 9040  | tcp      | tor-trans    |
| 779  | 9050  | tcp      | tor-socks    |
| 780  | 9071  | tcp      | unknown      |
| 781  | 9080  | tcp      | glrpc        |
| 782  | 9081  | tcp      | unknown      |
| 783  | 9090  | tcp      | zeus-admin   |
| 784  | 9091  | tcp      | xmltec-xmlma |
| 785  | 9099  | tcp      | unknown      |
| 786  | 9100  | tcp      | jetdirect    |
| 787  | 9101  | tcp      | jetdirect    |
| 788  | 9102  | tcp      | jetdirect    |
| 789  | 9103  | tcp      | jetdirect    |
| 790  | 9110  | tcp      | unknown      |
| 791  | 9111  | tcp      | DragonIDSCon |
| 792  | 9200  | tcp      | wap-wsp      |
| 793  | 9207  | tcp      | wap-vcal-s   |
| 794  | 9220  | tcp      | unknown      |
| 795  | 9290  | tcp      | unknown      |
| 796  | 9415  | tcp      | unknown      |
| 797  | 9418  | tcp      | git          |
| 798  | 9485  | tcp      | unknown      |
| 799  | 9500  | tcp      | ismserver    |
| 800  | 9502  | tcp      | unknown      |
| 801  | 9503  | tcp      | unknown      |
| 802  | 9535  | tcp      | man          |
| 803  | 9575  | tcp      | unknown      |
| 804  | 9593  | tcp      | cba8         |
| 805  | 9594  | tcp      | msgsys       |
| 806  | 9595  | tcp      | pds          |
| 807  | 9618  | tcp      | condor       |
| 808  | 9666  | tcp      | zoomcp       |
| 809  | 9876  | tcp      | sd           |
| 810  | 9877  | tcp      | unknown      |
| 811  | 9878  | tcp      | kca-service  |
| 812  | 9898  | tcp      | monkeycom    |
| 813  | 9900  | tcp      | iua          |
| 814  | 9917  | tcp      | unknown      |
| 815  | 9929  | tcp      | nping-echo   |
| 816  | 9943  | tcp      | unknown      |
| 817  | 9944  | tcp      | unknown      |
| 818  | 9968  | tcp      | unknown      |
| 819  | 9998  | tcp      | distinct32   |
| 820  | 9999  | tcp      | abyss        |
| 821  | 10000 | tcp      | snet-sensor- |
| 822  | 10001 | tcp      | scp-config   |
| 823  | 10002 | tcp      | documentum   |
| 824  | 10003 | tcp      | documentum_s |
| 825  | 10004 | tcp      | emcrmirccd   |
| 826  | 10009 | tcp      | swdtp-sv     |
| 827  | 10010 | tcp      | rxapi        |
| 828  | 10012 | tcp      | unknown      |
| 829  | 10024 | tcp      | unknown      |
| 830  | 10025 | tcp      | unknown      |
| 831  | 10082 | tcp      | amandaidx    |
| 832  | 10180 | tcp      | unknown      |
| 833  | 10215 | tcp      | unknown      |
| 834  | 10243 | tcp      | unknown      |
| 835  | 10566 | tcp      | unknown      |
| 836  | 10616 | tcp      | unknown      |
| 837  | 10617 | tcp      | unknown      |
| 838  | 10621 | tcp      | unknown      |
| 839  | 10626 | tcp      | unknown      |
| 840  | 10628 | tcp      | unknown      |
| 841  | 10629 | tcp      | unknown      |
| 842  | 10778 | tcp      | unknown      |
| 843  | 11110 | tcp      | sgi-soap     |
| 844  | 11111 | tcp      | vce          |
| 845  | 11967 | tcp      | sysinfo-sp   |
| 846  | 12000 | tcp      | cce4x        |
| 847  | 12174 | tcp      | unknown      |
| 848  | 12265 | tcp      | unknown      |
| 849  | 12345 | tcp      | netbus       |
| 850  | 13456 | tcp      | unknown      |
| 851  | 13722 | tcp      | netbackup    |
| 852  | 13782 | tcp      | netbackup    |
| 853  | 13783 | tcp      | netbackup    |
| 854  | 14000 | tcp      | scotty-ft    |
| 855  | 14238 | tcp      | unknown      |
| 856  | 14441 | tcp      | unknown      |
| 857  | 14442 | tcp      | unknown      |
| 858  | 15000 | tcp      | hydap        |
| 859  | 15002 | tcp      | onep-tls     |
| 860  | 15003 | tcp      | unknown      |
| 861  | 15004 | tcp      | unknown      |
| 862  | 15660 | tcp      | bex-xr       |
| 863  | 15742 | tcp      | unknown      |
| 864  | 16000 | tcp      | fmsas        |
| 865  | 16001 | tcp      | fmsascon     |
| 866  | 16012 | tcp      | unknown      |
| 867  | 16016 | tcp      | unknown      |
| 868  | 16018 | tcp      | unknown      |
| 869  | 16080 | tcp      | osxwebadmin  |
| 870  | 16113 | tcp      | unknown      |
| 871  | 16992 | tcp      | amt-soap-htt |
| 872  | 16993 | tcp      | amt-soap-htt |
| 873  | 17877 | tcp      | unknown      |
| 874  | 17988 | tcp      | unknown      |
| 875  | 18040 | tcp      | unknown      |
| 876  | 18101 | tcp      | unknown      |
| 877  | 18988 | tcp      | unknown      |
| 878  | 19101 | tcp      | unknown      |
| 879  | 19283 | tcp      | keysrvr      |
| 880  | 19315 | tcp      | keyshadow    |
| 881  | 19350 | tcp      | unknown      |
| 882  | 19780 | tcp      | unknown      |
| 883  | 19801 | tcp      | unknown      |
| 884  | 19842 | tcp      | unknown      |
| 885  | 20000 | tcp      | dnp          |
| 886  | 20005 | tcp      | btx          |
| 887  | 20031 | tcp      | unknown      |
| 888  | 20221 | tcp      | unknown      |
| 889  | 20222 | tcp      | ipulse-ics   |
| 890  | 20828 | tcp      | unknown      |
| 891  | 21571 | tcp      | unknown      |
| 892  | 22939 | tcp      | unknown      |
| 893  | 23502 | tcp      | unknown      |
| 894  | 24444 | tcp      | unknown      |
| 895  | 24800 | tcp      | unknown      |
| 896  | 25734 | tcp      | unknown      |
| 897  | 25735 | tcp      | unknown      |
| 898  | 26214 | tcp      | unknown      |
| 899  | 27000 | tcp      | flexlm0      |
| 900  | 27352 | tcp      | unknown      |
| 901  | 27353 | tcp      | unknown      |
| 902  | 27355 | tcp      | unknown      |
| 903  | 27356 | tcp      | unknown      |
| 904  | 27715 | tcp      | unknown      |
| 905  | 28201 | tcp      | unknown      |
| 906  | 30000 | tcp      | ndmps        |
| 907  | 30718 | tcp      | unknown      |
| 908  | 30951 | tcp      | unknown      |
| 909  | 31038 | tcp      | unknown      |
| 910  | 31337 | tcp      | Elite        |
| 911  | 32768 | tcp      | filenet-tms  |
| 912  | 32769 | tcp      | filenet-rpc  |
| 913  | 32770 | tcp      | sometimes-rp |
| 914  | 32771 | tcp      | sometimes-rp |
| 915  | 32772 | tcp      | sometimes-rp |
| 916  | 32773 | tcp      | sometimes-rp |
| 917  | 32774 | tcp      | sometimes-rp |
| 918  | 32775 | tcp      | sometimes-rp |
| 919  | 32776 | tcp      | sometimes-rp |
| 920  | 32777 | tcp      | sometimes-rp |
| 921  | 32778 | tcp      | sometimes-rp |
| 922  | 32779 | tcp      | sometimes-rp |
| 923  | 32780 | tcp      | sometimes-rp |
| 924  | 32781 | tcp      | unknown      |
| 925  | 32782 | tcp      | unknown      |
| 926  | 32783 | tcp      | unknown      |
| 927  | 32784 | tcp      | unknown      |
| 928  | 32785 | tcp      | unknown      |
| 929  | 33354 | tcp      | unknown      |
| 930  | 33899 | tcp      | unknown      |
| 931  | 34571 | tcp      | unknown      |
| 932  | 34572 | tcp      | unknown      |
| 933  | 34573 | tcp      | unknown      |
| 934  | 35500 | tcp      | unknown      |
| 935  | 38292 | tcp      | landesk-cba  |
| 936  | 40193 | tcp      | unknown      |
| 937  | 40911 | tcp      | unknown      |
| 938  | 41511 | tcp      | unknown      |
| 939  | 42510 | tcp      | caerpc       |
| 940  | 44176 | tcp      | unknown      |
| 941  | 44442 | tcp      | coldfusion-a |
| 942  | 44443 | tcp      | coldfusion-a |
| 943  | 44501 | tcp      | unknown      |
| 944  | 45100 | tcp      | unknown      |
| 945  | 48080 | tcp      | unknown      |
| 946  | 49152 | tcp      | unknown      |
| 947  | 49153 | tcp      | unknown      |
| 948  | 49154 | tcp      | unknown      |
| 949  | 49155 | tcp      | unknown      |
| 950  | 49156 | tcp      | unknown      |
| 951  | 49157 | tcp      | unknown      |
| 952  | 49158 | tcp      | unknown      |
| 953  | 49159 | tcp      | unknown      |
| 954  | 49160 | tcp      | unknown      |
| 955  | 49161 | tcp      | unknown      |
| 956  | 49163 | tcp      | unknown      |
| 957  | 49165 | tcp      | unknown      |
| 958  | 49167 | tcp      | unknown      |
| 959  | 49175 | tcp      | unknown      |
| 960  | 49176 | tcp      | unknown      |
| 961  | 49400 | tcp      | compaqdiag   |
| 962  | 49999 | tcp      | unknown      |
| 963  | 50000 | tcp      | ibm-db2      |
| 964  | 50001 | tcp      | unknown      |
| 965  | 50002 | tcp      | iiimsf       |
| 966  | 50003 | tcp      | unknown      |
| 967  | 50006 | tcp      | unknown      |
| 968  | 50300 | tcp      | unknown      |
| 969  | 50389 | tcp      | unknown      |
| 970  | 50500 | tcp      | unknown      |
| 971  | 50636 | tcp      | unknown      |
| 972  | 50800 | tcp      | unknown      |
| 973  | 51103 | tcp      | unknown      |
| 974  | 51493 | tcp      | unknown      |
| 975  | 52673 | tcp      | unknown      |
| 976  | 52822 | tcp      | unknown      |
| 977  | 52848 | tcp      | unknown      |
| 978  | 52869 | tcp      | unknown      |
| 979  | 54045 | tcp      | unknown      |
| 980  | 54328 | tcp      | unknown      |
| 981  | 55055 | tcp      | unknown      |
| 982  | 55056 | tcp      | unknown      |
| 983  | 55555 | tcp      | unknown      |
| 984  | 55600 | tcp      | unknown      |
| 985  | 56737 | tcp      | unknown      |
| 986  | 56738 | tcp      | unknown      |
| 987  | 57294 | tcp      | unknown      |
| 988  | 57797 | tcp      | unknown      |
| 989  | 58080 | tcp      | unknown      |
| 990  | 60020 | tcp      | unknown      |
| 991  | 60443 | tcp      | unknown      |
| 992  | 61532 | tcp      | unknown      |
| 993  | 61900 | tcp      | unknown      |
| 994  | 62078 | tcp      | iphone-sync  |
| 995  | 63331 | tcp      | unknown      |
| 996  | 64623 | tcp      | unknown      |
| 997  | 64680 | tcp      | unknown      |
| 998  | 65000 | tcp      | unknown      |
| 999  | 65129 | tcp      | unknown      |
| 1000 | 65389 | tcp      | unknown      |

See the dump file in q2.pcap.



## 3)

Command I used:

```
echo -e "GET http://www.example.com HTTP/1.0\nUser-Agent:Firefox\n\n" | nc example.com 80 | nc -lvp 9999
```

IP address using:

- Host(macOS): 172.16.32.1
- Kali VM: 172.16.32.136

![](http://ww3.sinaimg.cn/large/006y8lVagw1f930y91r9rj31kw0sdqby.jpg)

![](http://ww4.sinaimg.cn/large/006y8lVagw1f930yss5pfj30o00j9gnq.jpg)

See the dump file in q3.pcap.

## 4)

As far as I understand, this question asked me to add a NS glue record with the IP of 127.0.0.1 into the response of a DNS query. Which I did some investigation, if someone whant to add a glue record which is like a local or customized DNS server, one have to go to upper DNS service provider to register the record on his/her account. So, in this way it's not gonna work to add a glue record. However, I did find something when I did some experiment on it. 

```Python
import dns.name
import dns.message
import dns.query
import dns.flags

localhost = '127.0.0.1'
domain = 'tiwaz.net'
name_server = '8.8.8.8'
ADDITIONAL_RDCLASS = 65535

domain = dns.name.from_text(domain)
if not domain.is_absolute():
    domain = domain.concatenate(dns.name.root)

request = dns.message.make_query(domain, 'A', 'IN')
request.flags |= dns.flags.AD
request.find_rrset(request.additional, dns.name.root, ADDITIONAL_RDCLASS,
                   dns.rdatatype.OPT, create=True, force_unique=True)
response = dns.query.udp(request, name_server, 1, 53, None, localhost, 53)


print response
```

The code above can display a DNS query response. And also we can use `dig` command to do the same thing. But at the end, I still can not figure out how to "redirect" the response to 127.0.0.1 and also add a glue record. As what I leaned is that your address in the glue record should also be a DNS server. So I did setup a local DNS server at 127.0.0.1. However it returned to me error states `Invalid argument` and I failed to find a way to program it right since the documentation are limited online.  The pcap file I got was during a DNS query using `dig` from my local setup DNS whose address is 127.0.0.1 

See the dump file in q4.pcap.



## 5)

By review the pcap file, I found that based on time stamps there are 8 times intereaction between address 172.16.40.134 and 172.16.40.138. Seems like some kind of trusted data transfer. Each one of them follow the same rules. Start by several times handshake and after that start a ssl connection to transfer data. And from the target port `443` we can tell that this is a HTTPS connection. 

Since our pcap file only contains defautl SSL connections, we can use `main.bro` under `/usr/share/bro/base/protocols/ssl`(using Kali Linux) to establish the traffic. However, I just found out that simply using rules below could do the same result in `conn.log`:

```
event ssl_client_hello(c: connection, version: count,
	possible_ts: time, client_random: string, session_id: string
	, ciphers: index_vec)
```

Due to time limitation, this is what I've done right now. I'll upload a revised updated version of this homework if possible.



### Optional #7

The question asked us to write a program to identify TCP connection by specific predefined strings. After target connection detected, disrupt the TCP session. 

I used `scapy` to solve this problem. Code like this:

```Python
from scapy.all import *
import sys

filtre = "host " + sys.argv[1] + " and port " + sys.argv[2]

def resetHijack(p):
	print "TCP:"
	print "."	#to mark 1 time tcp packet
	print str(p[IP].src) + ':' + str(p[TCP].sport) + '->' + str(p[IP].dst) + ':' + str(p[TCP].dport)
	print "payload: " + str(p[TCP].payload)
	ether = Ether(dst=p[Ether].src, src=p[Ether].dst)
	ip = IP(src=p[IP].dst, dst=p[IP].src, ihl=p[IP].ihl, flags=p[IP].flags, frag=p[IP].frag, proto=p[IP].proto, id=29321)
	
	#flag RST	
	tcp = TCP(sport=p[TCP].dport, dport=p[TCP].sport, seq=p[TCP].ack, ack=p[TCP].seq, dataofs=p[TCP].dataofs, reserved=p[TCP].reserved, flags="R", window=p[TCP].window, options=p[TCP].options)
	
	reset=ether/ip/tcp
	
	if 'hello' in str(p[TCP].payload):
		print "Cut off TCP connection!"
		sendp(reset)
		sys.exit()

sniff(count=0, prn = lambda p : resetHijack(p),filter=filtre,lfilter=lambda(f): f.haslayer(IP) and f.haslayer(TCP))
```

In this tiny program, I chose string `hello` as the identifier of our TCP session. The basic setup of this experiment is:

| Machine | OS         | IP Address    | Command                 |
| ------- | ---------- | ------------- | ----------------------- |
| Server  | Kali VM    | 172.16.32.136 | `nc -lvp 9999`          |
| Client  | macOS Host | 172.16.32.1   | `nc 172.16.32.136 9999` |

![](http://ww1.sinaimg.cn/large/006y8mN6gw1f9da02reblj30bs08jdg3.jpg)

![](http://ww2.sinaimg.cn/large/006y8mN6gw1f9da0b9remj31kw0pltd8.jpg)

As we can see, to start a tcp connection it contains 3 times handshake.

![](http://ww1.sinaimg.cn/large/006y8mN6gw1f9da1gjdbnj30bs08j0t0.jpg)

![](http://ww1.sinaimg.cn/large/006y8mN6gw1f9da1tjcjyj31kw0pbgq2.jpg)

If we send a non-identified string, the tcp session would not be disrupted.

![](http://ww4.sinaimg.cn/large/006y8mN6gw1f9da36r2qgj30bs08jt92.jpg)

![](http://ww4.sinaimg.cn/large/006y8mN6gw1f9da3h4wdaj31kw0pmdky.jpg)

If the tcp payload contains our predefined string, which is `hello`. The tcp connection would be cut off.

See the dump file in q7.pcap