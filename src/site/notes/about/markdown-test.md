---
{"dg-publish":true,"permalink":"/about/markdown-test/","title":"Markdown Test","tags":["markdown"],"created":"2023-03-10T14:03:24.418+07:00","updated":"2023-03-10T16:30:57.970+07:00"}
---


## Markdown Test

Common markdown format for Gitbook, gatsby-starter-bee, and VNote.

### 6. Lists

#### 6.3. Offset in Oredered List

***markdown***

```md
57. will started with offset 57
1. so it will be 58
2. this is 59
```

***display***

1. will started with offset 57
2. so it will be 58
3. this is 59

### 9. Links

#### 9.1. Email Linkify

***markdown***

```md
fake1@example.com  
<fake2@example.com>  
```

**display**

fake1@example.com  
<fake2@example.com>

### 10. Reference-style Links

***markdown***

```
I know [Indonesia][1]  
I also know [etymology of Indonesia][2]  
I knew [History of Indonesia][3]  
It doesn't have [hobbit-hole][hh].

[1]: <https://en.wikipedia.org/wiki/Indonesia>
[2]: https://en.wikipedia.org/wiki/Indonesia#Etymology "Etymology of Indonesia"
[3]: https://en.wikipedia.org/wiki/Indonesia#History 'History of Indonesia'
[hh]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"
```

***display***

I know [Indonesia][1]  
I also know [etymology of Indonesia][2]  
I knew [History of Indonesia][3]  
It doesn't have [hobbit-hole][hh].

[1]: <https://en.wikipedia.org/wiki/Indonesia>
[2]: <https://en.wikipedia.org/wiki/Indonesia#Etymology> "Etymology of Indonesia"
[3]: <https://en.wikipedia.org/wiki/Indonesia#History> 'History of Indonesia'
[hh]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"

### 11. Images

***markdown***

```md
![Wikipedia with Optional Text](https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/Wikipedia_Logo_1.0.png/240px-Wikipedia_Logo_1.0.png "Optional Text")  
![Wikipedia with Alt Text, reference style][id1]  

[id1]: https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/Wikipedia_Logo_1.0.png/240px-Wikipedia_Logo_1.0.png "Optional Text"
```

***display***

![Wikipedia with Optional Text](https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/Wikipedia_Logo_1.0.png/240px-Wikipedia_Logo_1.0.png "Optional Text")  
![Wikipedia with Alt Text, reference style][id1]  

[id1]: <https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/Wikipedia_Logo_1.0.png/240px-Wikipedia_Logo_1.0.png> "Optional Text"

### 13. HTML Code

#### 13.1. HTML: Bold, Italic, Strikethrough

***markdown***

```md
This <em>word</em> is italic.  
This <strong>word</strong> is bold.  
This <del>word</del> is deleted with strikethorouugh.
```

***display***

This <em>word</em> is italic.  
This <strong>word</strong> is bold.  
This <del>word</del> is deleted with strikethorouugh.

### 14. Horizontal Rules

***markdown***

```md
___

---

***

```

***display***

___

---

***

### 16. Code Fencing and Highlighting

***markdown***

    ```
    This is a fenced code block.
    ```
    ~~~
    No language indicated, so no syntax highlighting.
    s = "There is no highlighting for this."
    ~~~

    ```python
    def function():
        #indenting works just fine in the fenced code block
        s = "Python syntax highlighting"
        print s
    ```

    ```javascript
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("ruby syntax highlighting")
    puts markdown.to_html
    ```

***display***

```
This is a fenced code block.
```

~~~
No language indicated, so no syntax highlighting.
s = "There is no highlighting for this."
~~~

```python
def function():
    #indenting works just fine in the fenced code block
    s = "Python syntax highlighting"
    print s
```

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```ruby
require 'redcarpet'
markdown = Redcarpet.new("ruby syntax highlighting")
puts markdown.to_html
```

### 18. Text Formatting

#### 18.1. Strikethrough

***markdown***

```md
~~strikethrough~~  
```

***display***

~~strikethrough~~  

#### 18.2. Highlighting and Underline

```md
==highlight==  
_underline_  
```

***display***

==highlight==  
*underline*  

### 20. Emojies

#### 20.2. Shortcode Emoji

***markdown***

```md
Shortcode emoji examples :grinning: :smiley: :smile: :grin: :laughing: :joy:
```

***display***

Shortcode emoji examples :grinning: :smiley: :smile: :grin: :laughing: :joy:

### 21. Typographic Replacements, Superscript, Subscript

***markdown***

```md
autoreplacement of (c) (C) (r) (R) (tm) (TM) (p) (P) +-  
superscript x^2^ and subscript H~2~O
```

***display***

autoreplacement of (c) (C) (r) (R) (tm) (TM) (p) (P) +-  
superscript x^2^ and subscript H~2~O

### 22. HTML Entities and Character Codes

***markdown***

```md
&copy; &  &uml; &trade; &iexcl; &pound;  
&amp; &lt; &gt; &yen; &euro; &reg; &plusmn; &para; &sect; &brvbar; &macr; &laquo; &middot;  
x&sup2; y&sup3; &frac34; &frac14;  &times;  &divide;   &raquo; &#124;  
18&ordm;C  &quot;  &apos;
```

**display**

&copy; & &uml; &trade; &iexcl; &pound;  
&amp; &lt; &gt; &yen; &euro; &reg; &plusmn; &para; &sect; &brvbar; &macr; &laquo; &middot;  
x&sup2; y&sup3; &frac34; &frac14; &times; &divide; &raquo; &#124;  
18&ordm;C &quot; &apos;

### 23. Latex

#### 23.1. Inline Equation

***markdown***

```
Inline equation with one dollar sign: $E=mc^2$.  
Inline equation with two dollar sign: $E=mc^2$.
```

***display***

Inline equation with one dollar sign: $E=mc^2$.  
Inline equation with two dollar sign: $$E=mc^2$$.

#### 23.2. Newline Equation

***markdown***

```
Newline equation with two dollar signs.

$\sin(\alpha)^{\theta}=\sum_{i=0}^{n}(x^i + \cos(f))$
```

***display***

Newline equation with two dollar signs.

$$

\sin(\alpha)^{\theta}=\sum_{i=0}^{n}(x^i + \cos(f))

$$

### 27. Footnote

***markdown***

```md
Here's a simple footnote,[^1] and here's a longer one,[^bignote], and [^withcode].  

[^1]: This is the first footnote.  
[^bignote]: Here's another one.  
[^withcode]: `code` or code in paragraphs  
```

***display***

Here's a simple footnote,[^1] and here's a longer one,[^bignote], and [^withcode]. 

[^1]: This is the first footnote.  

[^bignote]: Here's another one.  

[^withcode]: `code` or code in paragraphs  
