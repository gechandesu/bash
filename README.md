# Handy Bash scripts

## Installation

I recomend install scripts into the home directory. Place they into `~/.local/bin`. If you don't have it, create it:

```bash
mkdir -p ~/.local/bin
```

Give executing rights for scripts:

```bash
chmod +x <script_name>
```

Check your PATH variable:

```bash
echo $PATH
```

If you don't find `/home/your_username/.local/bin` run:

```bash
echo 'export PATH+=:$HOME/.local/bin' >> ~/.bashrc && source ~/.bashrc
```

Done. Run `<script_name> --help` for check.

---

## http

Python 3 http.server runner.

```
Run Python 3 builtin HTTP Server.

Usage: http [-v | --version] [-h, | --help] [-c | --cgi] [-f | --firefox]
            [<host>[:<port>]] [<port>] [<dir>]

Options:
    -c, --cgi       run as CGI Server.
    -f, --firefox   open URL in Firefox.
    -h, --help      print this help message and exit.
    -v, --version   print version and exit.

Arguments:
    <host>          host to bind. Default: 0.0.0.0
    <port>          port to bind. Default: 8000
    <dir>           directory to serve. Default: current directory.
```

Examples:

```bash
# Run HTTP Server and open http://0.0.0.0:8000/ in Firefox
$ http f
# Run HTTP Server at 0.0.0.0:1234
$ http 1234
```

## prntl

Print log. Simple logging tool.

```
Print formatted log to STDOUT and log file.

Usage: prntl [-v| --version] [-h | --help] [-o | --output=<file>]
             [-f | --log-format=<string>] [-t | --time-format=<string>]
             [-p | --no-print] [-c | --no-color]

Options:
    -o, --output=<file>         set log file name. Default: prntl.log.
    -f, --log-format=<string>   set log format. Formatting options:
        %time   time; see '--time-format'. Default: %d %b %Y %T %z
        %log    log string. Default: %time - %log
    -t, --time-format=<string>  set time format; see 'date --help'
                                or 'man date' for details.
                                Example: prntl -t '%D %T'
    -c, --no-color              remove ANSI color codes from log string.
    -p, --no-print              don't print log to STDOUT.
    -h, --help                  print this help message and exit.
    -v, --version               print version and exit.
```

Usage:

```bash
$ echo 'some log string' | prntl -o /dev/null -f 'BACKUP: %time : %log'
BACKUP: 03 Feb 2021 20:47:03 +0300 : some log string
```

## esc

```
Escape whitespaces and specail characters in string.
Uses 'printf %q'. Read more in 'man printf'.

Usage: esc [-h | --help] [-o | --opts] [<string>...]

Options:
    -o, --opts      add end of the options sign (double dash). See
                    SHELL BUILTIN COMMANDS in 'man bash' for more info.
    -h, --help      print this help message and exit.
    -v, --version   print version and exit.
```

Example:

```bash
$ echo 'my un$escaped \sstring --foo' | esc -o
-- my\ un\$escaped\ \\sstring\ --foo
```

## view

```
Print highlighted text to STDOUT.

Usage: view [-v | version] [-h | --help] [-l | --less] [-n | --lines]
            [<file>]

Options:
    -l, --less      send output to 'less -R'.
    -n, --lines     similar to -l, but shows line nums (less -RN).
    -h, --help      print this help message and exit.
    -v, --version   print version and exit.
```

Script depends on **highlight** package ([link](http://www.andre-simon.de/)):

```bash
$ sudo apt install highlight
```

## rng

```
Expand ranges like "1-4,7,9-12" into a number series.

Usage: rng [-v | --version] [-h | --help] [-d <value>] [-l <value>]
           [-D | --delimiter=<value>] [<string>]

Options:
    -d <value>               digits delimiter. Default: '\n'.
    -l <value>               lines delimiter. Default: '\n'.
    -D, --delimiter=<value>  Set same delimiters for digits and lines.
    -h, --help               print this help message and exit.
    -v, --version            print version and exit.
```
