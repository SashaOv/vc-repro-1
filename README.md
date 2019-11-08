# Repro for "gdb gets stuck" problem


## Building

```
> Executing task: g++ -g -o /home/me/learn/c1/hello.out hello.cpp <


Terminal will be reused by tasks, press any key to close it.
```

## Running Without Debugger

```
me@L19:~/learn/c1$ ./hello.out 
Hello
```

## Running With the Debugger


```
=thread-group-added,id="i1"
GNU gdb (Ubuntu 8.1-0ubuntu3.2) 8.1.0.20180409-git
Copyright (C) 2018 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word".
Warning: Debuggee TargetArchitecture not detected, assuming x86_64.
=cmd-param-changed,param="pagination",value="off"
1: (1993) <-1013-exec-run
1: (2004) ->=thread-group-started,id="i1",pid="9345"
1: (2006) ->=thread-created,id="1",group-id="i1"
1: (2021) ->=breakpoint-modified,bkpt={number="1",type="breakpoint",disp="keep",enabled="y",addr="0x00005555555548c9",func="main(int, char const**)",file="hello.cpp",fullname="/home/me/learn/c1/hello.cpp",line="7",thread-groups=["i1"],times="0",original-location="main"}
1: (2022) ->=breakpoint-modified,bkpt={number="2",type="breakpoint",disp="keep",enabled="y",addr="0x00005555555548f1",func="main(int, char const**)",file="hello.cpp",fullname="/home/me/learn/c1/hello.cpp",line="8",thread-groups=["i1"],times="0",original-location="hello.cpp:8"}
1: (2026) ->=library-loaded,id="/lib64/ld-linux-x86-64.so.2",target-name="/lib64/ld-linux-x86-64.so.2",host-name="/lib64/ld-linux-x86-64.so.2",symbols-loaded="0",thread-group="i1",ranges=[{from="0x00007ffff7dd5f10",to="0x00007ffff7df4b20"}]
1: (2034) <-1014-thread-info 1
1: (2073) <-1015-symbol-list-lines /home/me/learn/c1/hello.cpp
1: (2110) ->1013^running
1: (2111) ->*running,thread-id="all"
1: (2111) 1013: elapsed time 117
1: (2112) ->(gdb)
1: (2124) ->~"Stopped due to shared library event (no libraries added or removed)\n"
Stopped due to shared library event (no libraries added or removed)
1: (2125) ->*stopped,reason="solib-event",thread-id="1",stopped-threads="all",core="1"
1: (2130) ->1014^done,threads=[{id="1",target-id="process 9345",name="hello.out",frame={level="0",addr="0x00007ffff7dd8df2",func="dl_main",args=[{name="phdr",value="<optimized out>"},{name="phnum",value="<optimized out>"},{name="user_entry",value="<optimized out>"},{name="auxv",value="<optimized out>"}],file="rtld.c",fullname="/build/glibc-OTsEL5/glibc-2.27/elf/rtld.c",line="1592"},state="stopped",core="1"}]
1: (2130) ->(gdb)
1: (2131) ->1015^done,lines=[{pc="0x00005555555548ba",line="6"},{pc="0x00005555555548c9",line="7"},{pc="0x00005555555548f1",line="8"},{pc="0x00005555555548f6",line="9"},{pc="0x00005555555548f8",line="9"},{pc="0x0000555555554906",line="9"},{pc="0x0000555555554915",line="0"},{pc="0x000055555555493e",line="9"},{pc="0x0000555555554941",line="9"},{pc="0x0000555555554945",line="9"},{pc="0x0000555555554956",line="0"}]
1: (2131) ->(gdb)
1: (2152) 1014: elapsed time 118
1: (2158) Send Event AD7ProcessInfoUpdatedEvent
1: (2159) Send Event AD7ThreadCreateEvent
1: (2172) 1015: elapsed time 98
1: (2172) <-1016-interpreter-exec console "info sharedlibrary"
1: (2175) ->~"From                To                  Syms Read   Shared Object Library\n"
1: (2175) Send Event AD7BreakpointUnboundEvent
1: (2176) ->~"0x00007ffff7dd5f10  0x00007ffff7df4b20  Yes         /lib64/ld-linux-x86-64.so.2\n"
1: (2176) ->1016^done
1: (2177) ->(gdb)
1: (2177) Send Event AD7BreakpointBoundEvent
1: (2178) 1016: elapsed time 5
1: (2182) Send Event AD7ModuleLoadEvent
Loaded '/lib64/ld-linux-x86-64.so.2'. Symbols loaded.
1: (2186) <--exec-continue
1: (2188) ->^running
1: (2189) ->*running,thread-id="all"
1: (2189) ->(gdb)
```

(The debugger gets stuck until I stop the debugging session)
