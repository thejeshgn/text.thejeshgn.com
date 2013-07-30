#### [Glances](https://github.com/nicolargo/glances)
Glances is a cross-platform curses-based monitoring tool written in Python.

```
#instlla
$ pip install Glances

#usage
$ glances

```

#### Screen
Screen is a full-screen window manager that multiplexes a physical terminal between several processes, typically interactive shells.

```
#install
$ sudo apt-get install screen

#connect or start
$ screen -R [screen name]

#see the list
$ screen -ls

```

#### [Sshuttle](https://github.com/apenwarr/sshuttle)
Transparent proxy server that works as a poor man's VPN. Forwards over ssh. Doesn't require admin. Works with Linux and MacOS. Supports DNS tunneling.

```
#install
$ git clone git://github.com/apenwarr/sshuttle

#basic usage
$ ./sshuttle -r username@sshserver 0.0.0.0/0 -vv

#with DNS tunneling
$ ./sshuttle --dns -vvr username@sshserver 0/0

```