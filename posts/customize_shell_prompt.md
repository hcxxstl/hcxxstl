# Customize Bash Shell Prompt

*by* **Terry**
*on* **26/Jan/2021**

## Abstract

This is all about the **Linux environment variable `PS1`**.  
You can customize the shell prompt by editing your `PS1` value in the `~/.bashrc` file.  
For example, add this line to the `~/.bashrc` file:

```shell
export PS1="\[\e[0;33m\]\u@\h:\[\e[m\]\[\e[0;34m\]\W\[\e[m\]\$ "
```

## The `PS1` variable

To check your current `PS1` value

```shell
$ echo $PS1
PS1="\u@\h:\W\$ "
```

## Useful characters

| character| value |
|------|----------|
| `\u` | username |
| `\h` | hostname |
| `\w` | full path of PWD |
| `\W` | base name of PWD |
| `\d` | date in format "Tue May 26" |
| `\D{format}` | date with specified foramt |
| `\n` | new line |
| `\t` | current time in 24-h format "HH:MM:SS" |
| `\T` | current time in 12-h format "HH:MM:SS" |
| `\@` | current time in 12-h format "am/pm" |
| `\A` | current time in 24-h format "HH:MM" |
| `\$` | if the effective UID=0 it's a "#", otherwise a "$" |
| `\[` | start of nun-printing characters |
| `\]` | end of nun-printing characters |

Reference and also a more complete list [here](https://www.howtogeek.com/307701/how-to-customize-and-colorize-your-bash-prompt/).

## Change color

To change the color of your prompt, you can use **color code**. For example:

```shell
PS1="\e[0;33m\u@\h:\W\$ \e[m"
```

Here in the middle we have `"\u@\h:\W\$ "` just the same as original `PS1`. But it is surrounded by color code. The table below explains what those additional characters do.

| character| meaning |
|------|----------|
| `\e[`  | start of color information |
| `x;ym` | color codes |
| `\e[m` | start of color information |

Here we use `x=0` and `y=33`, which change the color of our prompt into brown. To customize, you can find the color code in the tables below.

| `y` value | color |
|------|----------|
| `30` | black  |
| `31` | red    |
| `32` | green  |
| `33` | brown  |
| `34` | blue   |
| `35` | purple |
| `36` | cyan   |

| `x` value | effect |
|------|----------|
| `0` | normal     |
| `1` | bold/light |
| `2` | dim        |
| `4` | underlined |
| ... | ...        |

Hope you can understand what the example line in Abstract section does now.

```shell
export PS1="\[\e[0;33m\]\u@\h:\[\e[m\]\[\e[0;34m\]\W\[\e[m\]\$ "
```

It generate a prompt:  

```shell
username@hostname:directory$
<------brown-----><--blue->
```


## Notes

In case the shell cannot correctly calculated the length of the prompt, surround all the **non-printing** characters with `\[` and `\]`.

bad example

```shell
PS1="\e[0;33m\u@\h:\W\$ \e[m"
```

good example

```shell
PS1="\[\e[0;33m\]\u@\h:\W\$ \[\e[m\]"
```

## References

* [How to Customize (and Colorize) Your Bash Prompt, How-To Geek](https://www.howtogeek.com/307701/how-to-customize-and-colorize-your-bash-prompt/)
* [Why is my bash prompt getting bugged when I browse the history? StackExchange](https://unix.stackexchange.com/questions/28827/why-is-my-bash-prompt-getting-bugged-when-i-browse-the-history)