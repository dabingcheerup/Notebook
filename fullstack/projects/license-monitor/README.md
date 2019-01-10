# License Monitor

```text
Work Flow

login alnx1 server
Go to the direct you want to keep your github repository e.g. [mkdir github] [cd github]
xieti_alnx1> git clone url
xieti alnx1> cd repo/
xieti_alnx1> cd ci
xieti_alnx1> ls
build_python-3.6.2  build.sh  install_packages.sh  install_production.sh  spec.sh  start_web  toolsetup.lm
xieti_alnx1> source toolsetup.lm (only repeat this part when you activate your proj next time)
xieti_alnx1> build.sh
xieti_alnx1> source toolsetup.lm
xieti_alnx1> which pipenv    // check if pipenv is installed
/u/xieti/Github/license_monitor/python/Python-3.6.2/bin/pipenv
xieti_alnx1> pipenv --three  // create a virtualenv and run with python3
Creating a virtualenv for this project\u2026

move you previous project file to current local repository by using [scp user@host:path/file_to_copy destination_path]
if destination_path is . means copy to current directory
```

