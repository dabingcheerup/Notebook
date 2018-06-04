| Linux Version\(Red hat\) | Server | Location | user / psw |
| :--- | :--- | :--- | :--- |
| RH6 | tnrlnx1.icd | NR | xieti / 6\*5 |
| RH7 | axi2.icd?\(ter\) | NR | xieti / 6\*5 |
| RH6 | alnx35.std | AH | cds / !mentor |
| RH7 | alnx1.std | AH |  |
|  | dice.license.teradyne.com |  | cds / !mentor |
|  | wplcluster.std |  | cds / NotMentor |

**Previous LM Page: **[http://ttg.std.teradyne.com](http://ttg.std.teradyne.com)

**Server: axis2**

```
Access to Previous LM code
<cd /hwnet/tools_web/cgi-bin>
including files: lic-reporter.cgi(generate reports), COMMON.pm(Perl Lib)
```

**Server: alnx35**

```
Access to LM database via sqlplus
<ssh cds@alnx35>
</li> //set the ENV for oracle
<sqlplus user/psw > / <sqlplus  username/password@yourdatabasename>    // start your sqlplus license_user/license_logs
<SELECT table_name FROM user_tables FETCH FIRST 20 PERCENT ROWS ONLY;>
<DESCRIBE table_or_view>
```

```
Access to License_Monitor_Cache which content is Server,Vendor, Feature info 
<cd /hwnet/ttg/LIC_MGR/LICENSE_SAMPLE/cachedir/license_monitor_cache>
```

```

```

**Server: dice.license.teradyne.com**

```
Access to log file:
Go to VNC pick any servers
Command <ssh dice.license.teradyne.com> 
Log in with [user:] cds or <ssh cds@dice.license.teradyne.com> [psw:] !mentor
<cd /data_vol/licenses/[vendor]/logs>    //Choose the vendor you want to look at press tab to get “_”; cd / root directory
<ls -rlt>    //display the latest log file on the bottom
<vi license.log>    //pick one log file and use vi to open it
```

```
Run below commands to get lmstat which is the data for license_status.pl
<ssh cds@dice.license.teradyne.com>
/data_vol/licenses/cadence/bin/lmutil lmstat -a -c /data_vol/licenses/cadence/keys
```

```
Access to license_status.pl:
<ssh cds@dice.license.teradyne.com>
psw: !mentor
<cd /etc/teradyne>
<vi license_status>

Run license_status.pl: it outputs the data for CURRENT USAGE REPORT
<ssh dice.license.teradyne.com -l cds -i /u/cds/.ssh/licsrvkey /etc/teradyne/license_status -only [cadence]>
psw for cds
```



