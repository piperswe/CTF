# Hijacked!
Someone planted a file on our computer (the [shell server](https://www.easyctf.com/shell)), but we don't know what it is! The only clue that we have is that it's owned by a user called l33t_haxx0r. Can you figure out the flag?

## Hint
Try to look up useful Linux commands.

## Writeup
Since we know the file is owned by `l33t_haxx0r`, we can easily find the file with a simple `find` command:

```
$ find / -user l33t_haxx0r 2> /dev/null
```

This command recursively looks for files under `/` owned by `l33t_haxx0r` then dumps any errors (such as access denied) to `/dev/null`. When I run it on the EasyCTF 2015 shell server, I get:

```
/var/www/html/index.html
```

That must be where the flag is! Let's take a look...

```
$ more /var/www/html/index.html
<random junk>
<!--
t
h
e

f
l
a
g

i
s

e
a
s
y
c
t
f
{
c
0
m
p
l
e
t
3
l
y
_
r
3
k
t
}
-->
<more random junk>
```

Remove all the whitespace and HTML comment notation and we get "the flag is __easyctf{c0mplet3ly_r3kt}__", the flag!
