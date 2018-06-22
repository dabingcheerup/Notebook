| Syntax Check list |  |
| :--- | :--- |
| if, else, elsif |  |
| next unless... = next if not... | [r1](https://stackoverflow.com/questions/40940001/need-further-understanding-in-the-next-unless-code-im-reading) |
| share JSON btw Python and Perl | [r1](https://stackoverflow.com/questions/39082512/sharing-json-data-between-python-and-perl-scripts),[ r2](https://stackoverflow.com/questions/22521399/how-do-i-encode-a-simple-array-into-json-in-perl), [r3](https://www.sitepoint.com/community/t/perl-json/96190) |
| substr\(str, start, length\) | [r1](https://perlmaven.com/string-functions-length-lc-uc-index-substr) |
| $dt-&gt;epoch  :  Return the UTC epoch value for the datetime object. | [r1](https://perlmaven.com/datetime), [r2, ](https://www.epochconverter.com/programming/perl) |
| last = break | [r1](http://www.perltutorial.org/perl-last/) |
| Source a shell script in perl script | system\("cmd"\) [r1](https://stackoverflow.com/questions/3675646/can-we-source-a-shell-script-in-perl-script) |
| Run Perl "one liner" command line script | perl -e "statements;"[r1](https://stackoverflow.com/questions/2748738/how-do-i-access-a-value-of-a-nested-perl-hash) |
| Run a Perl Lib Sub routine via command | [r1](https://stackoverflow.com/questions/23477235/execute-a-perl-sub-routine-via-the-command-prompt), [r2](https://stackoverflow.com/questions/23039028/calling-perl-subroutines-from-the-command-line) |
| Access Hash reference | %$hash\_ref [r1](https://perlmonks.org/?node=References+quick+reference), [r2](https://metacpan.org/pod/Perl::Critic::Policy::References::ProhibitDoubleSigils), [r3](https://stackoverflow.com/questions/5249362/how-to-use-foreach-with-a-hash-reference) $hash\_ref-&gt;{key} [r4](https://stackoverflow.com/questions/2748738/how-do-i-access-a-value-of-a-nested-perl-hash) |
| Traverse hash key or value or pairs | [r1](https://stackoverflow.com/questions/3033/whats-the-safest-way-to-iterate-through-the-keys-of-a-perl-hash) |

**Python run Perl Lib**

```
// Run_Perl.py

  perl1 = '/hwnet/open_source/RH7.4/x86_64/perl-5.14.2/bin/perl'

  def get_user_info():
      cmd = ['ssh','cds@alnx1', perl1, perl_script, 'get_user_info']
      return run_subprocess(cmd)

// PerlScript.pl
  * Call (Perl lib) USERMAP::get_user_info() to get return value
  * USERMAP.pm path: /hwnet/common_r2/lib/USERMAP.pm
  * Must Log into AH servers(alnx35 or alnx1) as cds to run USERMAP.pm

  sub get_user_info{
    system("source /hwnet/common_r2/env/toolsetup.perl-5.14.2"); // Specify Perl Version To run oracle 
    my $user = USERMAP::get_user_info();
    // Manually print the return value, so that it can be show in the terminal and captured by python subprocess
    foreach my $id (keys(%$user)){
      print "$id:$user->{$id}{div_id}:$user->{$id}{division}\n";
    }
  }
```



