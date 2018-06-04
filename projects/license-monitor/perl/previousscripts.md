|  |  |  |
| :--- | :--- | :--- |
| show\_licenses\( $q, $selected\_server, $selected\_vendor, $selected\_feature \); | $SERVERS                                                   @lic\_files stores all corresponding license file paths which are license.dat or license.lic                                                  Traverse @lic\_files to open license files, read them, and display them to html  /hwnet/ttg/LIC\_MGR/SERVER\_SNAPSHOT/license\_snapshot/$site/licenses/$vendor/keys/ | my $SNAPSHOT    = "/hwnet/ttg/LIC\_MGR/SERVER\_SNAPSHOT";                  my $SNAP\_CUR    = "$SNAPSHOT/license\_snapshot";                                       my $SNAPS\_DIR    = COMMON::get\_the\_literal\( "SNAP\_CUR" \);                            opendir DP, "$SNAPS\_DIR/$site/licenses/$vendor/keys/";                                   \# LOOK FIRST FOR "license.dat", THEN FOR "license.lic"          |
| show\_usage\( $q, $CACHE, $selected\_server, $selected\_vendor, $selected\_feature \) | $CACHE |  |
| show\_expirations\( $q, $CACHE, $selected\_server, $selected\_vendor, $selected\_feature \); | $CACHE |  |
| chart\_dailypeak\( $q, $dbh, $selected\_server, $selected\_vendor, $selected\_feature,$selected\_start, $selected\_end, 1,\) | $dbh |  |
| show\_raw\_data\( $q, $dbh, $selected\_server, $selected\_vendor, $selected\_feature,$selected\_start, $selected\_end \); | $dbh |  |
| chart\_detail\( $q, $dbh, $selected\_server, $selected\_vendor, $selected\_feature,$selected\_start, $selected\_end \) | $dbh |  |
|  | $dbh |  |



