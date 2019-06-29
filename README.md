# check_os_release 2.0.1

[![License][mit-badge]][mit-url]

> Nagios/Icinga Plugin for checking OS Release Schedule

Monitors `/etc/os-release` and warns you before the support for your distribution ends and you should consider upgrading
soon. Currently only Debian, Raspbian and Ubuntu are supported, Pull Requests welcome!

### Install

Place the file `check_os_release` somewhere (e.g. `/usr/local/bin/`) and make it executable.


### Command Line Options

```
usage: check_os_release [ -w value ] [ -c value ] [ -l ]
    -w Warn if supports ends in less then given months      [default: 3]
    -c Critical if supports ends in less then given months  [default: 1]
    -l Use Debian LTS                                       [default: false]
    -h print this help screen
    -v show version
```


### Nagios command and service definition example

```
define command {
        command_name check_os_release
        command_line /usr/local/bin/check_os_release -w $ARG1$ -c $ARG2$ -l
}

define service {
        use                     generic-service
        host_name               servername
        service_description     OS Release
        check_command           check_os_release!2!1
}

```

## License

MIT (c) 2018, 2019 [Sebastian Raff](https://github.com/hobbyquaker)

[mit-badge]: https://img.shields.io/badge/License-MIT-blue.svg?style=flat
[mit-url]: LICENSE
