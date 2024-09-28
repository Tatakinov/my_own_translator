# my_own_translator

The end of person who was not satisfied with just the functionality of a certain ghost.

## What's this

[ukagaka-simultaneous-interpreter](https://github.com/nikolat/ukagaka-simultaneous-interpreter)

Since ↑ doesn't translate the choice, I created a ghost that can translate them in a nice way.

However, translation takes longer than it.

## Library

yaya-shiori | BSD+      | https://github.com/YAYA-shiori/yaya-shiori
yaya-dic    | Unlicense | https://github.com/YAYA-shiori/yaya-dic
libcurl     | curl      | https://curl.se/

## Mechanism

Translate "\0This \q[apple,OnFoo] is blue." from en to ja.

```
\0This \q[apple,OnFoo] is blue.\e
```

↓ parse

```
${0}This ${1} is blue.${2}
----
${0} = \0
${1} = \q[apple,OnFoo]
${2} = \e
```

↓ translate/replace event id

```
${0}This ${1} is blue.${2}
----
${0} = \0
${1} = \q[りんご,OnKeep]
${2} = \e
```

↓ translate

```
${0}この ${1} は 青色です。${2}
----
${0} = \0
${1} = \q[りんご,OnKeep]
${2} = \e
```

↓ build

```
\0この \q[りんご,OnKeep] は青色です。\e
```

cf. OnKeep -> \C

In this example, the sentence is translated twice: once as a whole and once as the contents of the q tag.
Therefore, sentences with more choices and anchors take longer to translate.
