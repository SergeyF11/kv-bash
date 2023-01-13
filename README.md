kv-bash [![Build Status](https://travis-ci.org/damphat/kv-bash.png?branch=master)](https://travis-ci.org/damphat/kv-bash)
=====================
**About**
 - tiny key/value dabatase
 - database store in home directory
 - each user has 1 database
 - usage by importing 5 bash functions via ```$ source ./kv-bash```
 
**Requirements**

unix-like environement, no dependencies

**Usage**

import all database functions

```
$ source ./kv-bash         # import kv-bash functions
```

choise database
set shell variables ot set it before command

```
$ KV_DB=<name_db> <function> <key> <value>
```
  
use database functions

```
$ kvset <key> <value>      # create or change value of key
$ kvget <key>              # get value of key
$ kvdel <key>              # delete by key
$ kvlist                   # list all current key/value pairs
$ kvclear                  # clear database
$ kvsave <file.tgz>        # save DB to file
$ kvload <file.tgz>        # load DB form file
```

**Examples**

``` 
$ source ./kv-bash
$ kvset user mr.bob
$ kvset pass abc@123
$ kvlist
user mr.bob
pass abc@123
$ kvget user
mr.bob
$ kvget pass
abc@123
$ kvdel pass
$ kvget pass

$ kvclear
```

**Run tests**

```
git clone https://github.com/damphat/kv-bash.git
cd kv-bash
./kv-test
```

test result

```
RUN ALL TEST CASES:
===================
RUN ALL TEST CASES:
===================
  1 NO KV_DB: kvclear; kvlist => line count = 0       [  OK  ]
  2 call kvget for non-exist key should return empty  [  OK  ]
  3 kvset then kvget a variable                       [  OK  ]
  4 kvset then kvset again with different value       [  OK  ]
  5 deleted variable should be empty                  [  OK  ]
  6 kvdel non exist should be OK                      [  OK  ]
  7 kvset without param return error                  [  OK  ]
  8 kvget without param return error                  [  OK  ]
  9 kvdel without param return error                  [  OK  ]
 10 kvset 3 keys/value; kvlist => line count = 3      [  OK  ]
 11 non-exist-var => empty value => line count = 1    [  OK  ]
 12 kvclear; kvlist => line count = 0                 [  OK  ]
 13 kvget return empty value => error code != 0       [  OK  ]
 14 spaces in value                                   [  OK  ]
 15 can change user dir                               [  OK  ]
 16 can return to old user dir                        [  OK  ]
 17 save DB to file without ext (.tgz usage)          [  OK  ]
 18 load DB from file without ext (.tgz usage)        [  OK  ]
 19 save DB to tar.gz file                            [  OK  ]
 20 load DB from tar.gz file                          [  OK  ]
 21 benchmark /tmp/testingdirA kvset                  [  8657 ops ]
 22 benchmark /tmp/testingdirA  kvget                 [  260 ops ]
 23 benchmark ./testingdirB  kvset                    [  8079 ops ]
 24 benchmark ./testingdirB  kvget                    [  888 ops ]

```
