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
including files: lic-reporter.cgi(generate reports), lic_reporter_g1.cgi(generate graph), COMMON.pm(Perl Lib)
```

**Server: alnx35**

```
Access to LM database via sqlplus
>ssh cds@alnx35 
psw:!MENTOR
>source /hwnet/common_r2/env/toolsetup.oracle_agdb //set the ENV for oracle
>sqlplus user/psw  / <sqlplus  username/password@yourdatabasename    // start your sqlplus license_user/license_logs
>SELECT table_name FROM user_tables FETCH FIRST 20 PERCENT ROWS ONLY;
>DESCRIBE table_or_view
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

**Set up key for a server**

```
Eample: set up a key to login cds@axis2.icd.teradyne.com
Step1: Generate public/private key, set a passphrase
<xieti_axis2> cd $HOME/.ssh
<xieti_axis2> ssh-keygen -f xieti_ts_git -C "xiteti toolsetup git key"  //xieti is your personal username
ENTER a passphrase for your public/private key. Remember it!!!

Step2: copy the public key to the ~cds/.ssh/authorized_keys of any machine to which you will need to log in repeatedly
<xieti_axis2>source /hwnet/common_r2/env/toolsetup.hwtools
<xieti_axis2> ter-ssh-copy-id -i xieti_ts_git cds@axis2.icd.teradyne.com

Step3: test that the key works
<xieti_axis2> ssh -i ~/.ssh/xieti_ts_git cds@axis2.icd.teradyne.com "pwd"
if succeed, will show the root path of cds@axis2.icd.teradyne.com which is /u/cds

Step4: making a certificate-authenticated ssh connection, and the certificate passphrase is automagically provided by your VNC session.
<xieti_axis2> /bin/sh
ENTER ssh-add ~/.ssh/xieti_ts_git
ENTER your passphrase
TEST with ssh cds@axis2.icd.teradyne.com "pwd" 
if succeed, will show /u/cds. THAT MEANS you DON't NEED PASSWORD to access axis2.icd.teradyne.com as cds

!!!NOTE!!!: if you want to access to other servers without psw, repeat the process start from step2
```

```
xieti_axis2> ssh cds@axis2.icd.teradyne.com
Warning: the ECDSA host key for 'axis2.icd.teradyne.com' differs from the key for the IP address '131.101.116.245'
Offending key for IP in /u/xieti/.ssh/known_hosts:1
Matching host key in /u/xieti/.ssh/known_hosts:10
Are you sure you want to continue connecting (yes/no)? yes
Last login: Thu Jun  7 11:08:39 2018 from axis2.icd.teradyne.com
cds_axis2> exit
```



