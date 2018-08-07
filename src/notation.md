# 記法

このテキストはScalaの基本について学ぶものですので、これ以降、Scalaのある構文に関する説明がしばしば
出てきます。ここでは、構文を表すための記法について簡単に説明します。


## アルファベットなどの並び

まず、以下のように、アルファベットや記号のならびがそのまま現れた場合、その文字列そのものを
表します。ここでは、 `if` という文字列そのものを表しているわけです。

```
if
```

## アルファベットなどの並びをクォートで囲んだもの

次に、アルファベットや記号の並びをクオートで囲んだものも、同様に扱います。これは後述するように、
一部の文字に特別な意味をもたせるため、それとの混同を避けるために使います。以下は、先程と同じ意味
です。

```
'if'
```

## `(` と `)` で囲まれた要素

なんらかの要素で、 `()` で囲まれたものは、グルーピングを表現します。以下は、`(`で始まる何らかの文字列
*ではなく*、 `if()` という文字の並びをひとまとめにしたものを表します。これは、後述する繰り返しの
表現などをひとまとめにするために使います。

```
('if' '(' ')')
```

明示的に `'('` や `')'` としない限り、グルーピングが優先されます。

## `<` と `>` で囲まれた要素

`<式>` のように `<` と `>` で囲んで名前をつけたものは、何らかの構文要素を表します。
`<式>` と書くことで、 `式` という概念を表現する何らかの構文要素であることを示します。以下では、Javaの
`if` 文の構文の一部を表現しています。 `<条件式>` が何かについては触れていませんが、Javaの言語で
`boolean` が返ってくる式を想定しています。

```
if '(' <条件式> ')'
```

## 何らかの要素のあとに `*` が付加されたもの

何らかの要素に続いて、 `*` が付加されたものは、その要素が0回以上現れることを意味します。以下は、
`<式>` のあとに `;` が来るような要素が0回以上現れることを意味します。

```
(<式> ;)*
```

ここで、 `a*` は `a` のあとに `*` という文字が来るのか、 `a` の0回以上の繰り返しなのかが曖昧です。
曖昧さを解決するために、明示的に `'*'` としない限り、繰り返しが優先されるものとします。

## 何らかの要素のあとに `+` が付加されたもの

何らかの要素に続いて、 `+` が付加されたものは、その要素が1回以上現れることを意味します。以下は、
`<式>` のあとに `;` が来るような要素が1回以上現れることを意味します。

```
(<式> ;)+
```

ここで、 `a+` は `a` のあとに `+` という文字が来るのか、 `a` の1回以上の繰り返しなのかが曖昧です。
曖昧さを解決するために、明示的に `'+'` としない限り、繰り返しが優先されるものとします。

## 何らかの要素のあとに `?` が付加されたもの

何らかの要素に続いて、 `?` が付加されたものは、その要素が0回または1回現れることを意味します。言い換えると、
その要素はオプショナルであるということになります。以下は、

`else` で始まり、その次に `<式>` が来るような要素が0回または1回現れることを意味します。

```
(else <式>)?
```

ここで、 `a?` は `a` のあとに `?` という文字が来るのか、 `a` の0回または1回の出現なのかが曖昧です。
曖昧さを解決するために、明示的に `'?'` としない限り、オプショナルが優先されるものとします。

## 2つの要素の間に `|` が付加されたもの

何らかの2つの要素AとBの間に `|` が付加されたものは、 AとBのどちらでも良いということを意味します。
以下は、 `val` または `var` のどちらでも良いことを意味します。

```
('val'|'var')
```

ここで、 `a|b` は `a|b` という3文字なのか、 `a` または `b` なのかが曖昧です。
曖昧さを解決するために、明示的に `'|'` としない限り、 `a` or `b` という解釈が優先されます。

## if式の構文

以上を踏まえて、Scalaの `if` 式の構文を表現すると、次のようになります。

```
if '(' <条件式> ')' <式> ( else <式> )?
```

Scalaの `if` 式については、あとで詳しく解説します。