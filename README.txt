# my_own_translator

The end of person who was not satisfied with just the functionality of a certain ghost.

## What's this

[ukagaka-simultaneous-interpreter](https://github.com/nikolat/ukagaka-simultaneous-interpreter)

Since ↑ doesn't translate choices, I created a ghost that can translate them in a nice way.

Additionally, I have tried to show the text as closely as possible to the original.

## Library

yaya-shiori | BSD+      | https://github.com/YAYA-shiori/yaya-shiori
yaya-dic    | Unlicense | https://github.com/YAYA-shiori/yaya-dic
libcurl     | curl      | https://curl.se/

## Mechanism

Translate "\0This \q[apple,OnFoo] is blue.\e" from en to ja.

```
\0This \q[apple,OnFoo] is blue.\e
```

↓ parse/replace event id

```
----
<0> = <1>This <2> is blue.<4>
<1> = \0
<2> = \q[<3>,OnKeep]
<3> = apple
<4> = \e
```

↓ translate <0>, <3>

```
<0> = <1>この<2>は青色です。<4>
<1> = \0
<2> = \q[<3>,OnKeep]
<3> = りんご
<4> = \e
```

↓ build

```
\0この\q[りんご,OnKeep]は青色です。\e
```

cf. OnKeep -> \C
