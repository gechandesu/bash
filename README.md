# Handy Bash scripts

## view

```
view — write highlighted text to STDOUT.
Options:
    	-l --less 	send output to less -R
    	-n --lines	less, but shows line nums (less -RN)
    	-h --help 	show this help message and exit.
```

Script depends on **highlight** package ([link](http://www.andre-simon.de/)):

```
$ sudo apt install highlight
```

Installation in home directory:

```
mkdir -p ~/.local/bin
mv view ~/.local/bin
echo 'export PATH=$PATH:$HOME/.local/bin' >> ~/.bashrc
source ~/.bashrc
```
