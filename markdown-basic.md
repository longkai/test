Markdown: 基础教程
================

介绍markdown主要的格式化语法
------------------------------------------------

## 段落，标题，引用 ##
一个段落就是简单的一行或者连续多行的文本，段落之间使用一行或者多个空行区分开来
（一个空行是指任何看起来像一个空白的行，包含空格或者制表符的行就会被视为一个空白行）。
正常的段落不应该使用空格或者制表符来缩进。

markdown提供了两种风格的标题： *Setext* 和 *atx*.
Setext风格的 `<h1>` 和 `<h2>` 标题是通过使用多个 (`=`) 和 (`-`) 作为标题内容的下划线来构造的。
构造atx风格的标题，你需要把1-6个 (`#`) 放到标题内容那一行的起始处 -- (`#`) 的个数代表的在html中标题的等级。

引用是通过使用电子邮件风格的 '`>`' 来表示的。

Markdown:

    A First Level Header
    ====================
    
    A Second Level Header
    ---------------------

    Now is the time for all good men to come to
    the aid of their country. This is just a
    regular paragraph.

    The quick brown fox jumped over the lazy
    dog's back.
    
    ### Header 3

    > This is a blockquote.
    > 
    > This is the second paragraph in the blockquote.
    >
    > ## This is an H2 in a blockquote


Output:

    <h1>A First Level Header</h1>
    
    <h2>A Second Level Header</h2>
    
    <p>Now is the time for all good men to come to
    the aid of their country. This is just a
    regular paragraph.</p>
    
    <p>The quick brown fox jumped over the lazy
    dog's back.</p>
    
    <h3>Header 3</h3>
    
    <blockquote>
        <p>This is a blockquote.</p>
        
        <p>This is the second paragraph in the blockquote.</p>
        
        <h2>This is an H2 in a blockquote</h2>
    </blockquote>



### 短语强调 ###

markdown使用星号和下划线来表示短语的强调。

Markdown:

    Some of these words *are emphasized*.
    Some of these words _are emphasized also_.
    
    Use two asterisks for **strong emphasis**.
    Or, if you prefer, __use two underscores instead__.

Output:

    <p>Some of these words <em>are emphasized</em>.
    Some of these words <em>are emphasized also</em>.</p>
    
    <p>Use two asterisks for <strong>strong emphasis</strong>.
    Or, if you prefer, <strong>use two underscores instead</strong>.</p>
   


## 列表 ##

无序列表使用星号，更多的，你也使用连接符 (`*`, `+`, 和 `-`) 来作为列表的标识。
下面三种是可以呼唤的：

这个：

    *   Candy.
    *   Gum.
    *   Booze.

这个:

    +   Candy.
    +   Gum.
    +   Booze.

和这个:

    -   Candy.
    -   Gum.
    -   Booze.

他们都会生成同样html:

    <ul>
    <li>Candy.</li>
    <li>Gum.</li>
    <li>Booze.</li>
    </ul>

有序列表使用常规的数字接着一个句点来作为列表的标记：

    1.  Red
    2.  Green
    3.  Blue

生成:

    <ol>
    <li>Red</li>
    <li>Green</li>
    <li>Blue</li>
    </ol>

如果你将空行放到了列表的项目中间，那么你将会给那个列表的项目的内容得到一个 `<p>` 标签。
你可以通过给段落用4个空格或者1个制表符缩进来构建多个段落的列表项目：

    *   A list item.
    
        With multiple paragraphs.

    *   Another item in the list.

结果:

    <ul>
    <li><p>A list item.</p>
    <p>With multiple paragraphs.</p></li>
    <li><p>Another item in the list.</p></li>
    </ul>
    


### 链接 ###
markdown支持两种风格的链接： *inline* 和 *reference* 。
这两种方式，你都需要使用方括号把你想要变成链接的文本给框住。

例如:

    This is an [example link](http://example.com/).

结果:

    <p>This is an <a href="http://example.com/">
    example link</a>.</p>

此外，你还可以把一些文字插入到括号的作为链接的title：

    This is an [example link](http://example.com/ "With a Title").

结果:

    <p>This is an <a href="http://example.com/" title="With a Title">
    example link</a>.</p>

引用风格的裂解允许你通过名字来引用你定义好的链接内容：

    I get 10 times more traffic from [Google][1] than from
    [Yahoo][2] or [MSN][3].

    [1]: http://google.com/        "Google"
    [2]: http://search.yahoo.com/  "Yahoo Search"
    [3]: http://search.msn.com/    "MSN Search"

结果:

    <p>I get 10 times more traffic from <a href="http://google.com/"
    title="Google">Google</a> than from <a href="http://search.yahoo.com/"
    title="Yahoo Search">Yahoo</a> or <a href="http://search.msn.com/"
    title="MSN Search">MSN</a>.</p>

title属性是可选的，链接的名字可以包含文字，数字和空格，但是 *不是* 大小写敏感的：

    I start my morning with a cup of coffee and
    [The New York Times][NY Times].

    [ny times]: http://www.nytimes.com/

结果:

    <p>I start my morning with a cup of coffee and
    <a href="http://www.nytimes.com/">The New York Times</a>.</p>


### 图片 ###

图片的语法和链接的非常像。

Inline (titles are optional):

    ![alt text](/path/to/img.jpg "Title")

Reference-style:

    ![alt text][id]

    [id]: /path/to/img.jpg "Title"

两者都会得到同样的结果：

    <img src="/path/to/img.jpg" alt="alt text" title="Title" />



### 代码 ###

在一个正常的段落中，你可以使用反引号来显示代码片段。
任何 (`&`) 和 (`<` 或者 `>`) 都将会被自动转义为html相关文本，
这使得通过markdown来编写html代码非常简单：


    I strongly recommend against using any `<blink>` tags.

    I wish SmartyPants used named entities like `&mdash;`
    instead of decimal-encoded entites like `&#8212;`.

结果:

    <p>I strongly recommend against using any
    <code>&lt;blink&gt;</code> tags.</p>
    
    <p>I wish SmartyPants used named entities like
    <code>&amp;mdash;</code> instead of decimal-encoded
    entites like <code>&amp;#8212;</code>.</p>


要想将整个代码块预先格式化，你需要将代码段的每一行通过4个空格或者1个制表符来缩进。
正和一小段代码一样 `&`, `<`, 和 `>` 都将会被自动转义:

Markdown:

    If you want your page to validate under XHTML 1.0 Strict,
    you've got to put paragraph tags in your blockquotes:

        <blockquote>
            <p>For example.</p>
        </blockquote>

结果:

    <p>If you want your page to validate under XHTML 1.0 Strict,
    you've got to put paragraph tags in your blockquotes:</p>
    
    <pre><code>&lt;blockquote&gt;
        &lt;p&gt;For example.&lt;/p&gt;
    &lt;/blockquote&gt;
    </code></pre>
