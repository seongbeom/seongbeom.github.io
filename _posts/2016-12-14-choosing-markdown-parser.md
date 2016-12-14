---
layout: post
title: 마크다운 파서 고르기
published: true
---

간단한 JS 마크다운 에디터 제작을 위해 조사중 아래의 글을 간단히 요약해 보았다.   
마크다운의 기본 기능 및 부가적인 기능 그리고 해당 기능 지원 파서들에 대해 소개한다. 

\* 원글: [Choosing the Right Markdown Parser](https://css-tricks.com/choosing-right-markdown-parser/)

--- 

## 언어별 라이브러리

<table>
<thead>
<tr>
<th>Language</th>
<th>Library (download project)</th>
</tr>
</thead>
<tbody>
<tr>
<td>Perl</td>
<td><a href="http://daringfireball.net/projects/markdown/">Original version</a></td>
</tr>
<tr>
<td>JavaScript</td>
<td><a href="https://github.com/jgm/commonmark.js">CommonMark</a>, <a href="https://github.com/chjj/marked">Marked</a>, <a href="https://github.com/markdown-it/markdown-it">Markdown-it</a>, <a href="https://github.com/jonschlinkert/remarkable">Remarkable</a>, <a href="https://github.com/showdownjs/showdown">Showdown</a></td>
</tr>
<tr>
<td>Ruby</td>
<td><a href="https://github.com/github/markup">Github Flavored Markup</a>, <a href="https://github.com/gettalong/kramdown">Kramdown</a>, <a href="https://github.com/bhollis/maruku">Maruku</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a></td>
</tr>
<tr>
<td>PHP</td>
<td>
        <a href="https://github.com/cebe/markdown">Cebe Markdown</a>, <a href="https://github.com/kzykhys/Ciconia">Ciconia</a>, <a href="https://github.com/erusev/parsedown">Parsedown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>
      </td>
</tr>
<tr>
<td>Python</td>
<td><a href="https://pypi.python.org/pypi/Markdown">Python Markdown</a></td>
</tr>
</tbody>
</table>

기타 다른 언어들에 대한 구현 상황에 대해서는 [이곳](https://github.com/markdown/markdown.github.com/wiki/Implementations) 참고.


## 핵심 기능
기본적으로 마크다운은 다음과 같은 핵심 기능을 지원한다.

><a href="https://daringfireball.net/projects/markdown/syntax#html">Inline HTML</a>, <a href="https://daringfireball.net/projects/markdown/syntax#p">Automatic paragraphs</a>, <a href="https://daringfireball.net/projects/markdown/syntax#header">headers</a>, <a href="https://daringfireball.net/projects/markdown/syntax#blockquote">blockquotes</a>, <a href="https://daringfireball.net/projects/markdown/syntax#list">lists</a>, <a href="https://daringfireball.net/projects/markdown/syntax#precode">code blocks</a>, <a href="https://daringfireball.net/projects/markdown/syntax#hr">horizontal rules</a>, <a href="https://daringfireball.net/projects/markdown/syntax#link">links</a>, <a href="https://daringfireball.net/projects/markdown/syntax#em">emphasis</a>, <a href="https://daringfireball.net/projects/markdown/syntax#code">inline code</a> and <a href="https://daringfireball.net/projects/markdown/syntax#img">images</a>.

## 부가기능
**Fenced Codeblocks**

개발자들에게 유용한 기능중 하나인데, 코드를 쉽게 마크다운 안에 추가할수 있다. 초기에는 4개의 스페이스나 싱글탭으로 들여쓰게 되면 코드로 인식하게 하였는데, 불편함으로 인해 3개의 tickmarks ( ` )  또는 어떤곳에서는 3개의 tilde (~) 를 시작으로 하는 블락을 코드로 인식하도록 구현했다.

    ``` 
    body {
        margin: 0;
        padding: 0;
        color: #222;
        background-color: white;
        font-family: sans-serif;
        font-size: 1.8rem;
        line-height: 160%;
        font-weight: 400;
    }
    ``` 


><strong>Available with:</strong><br>
<a href="http://markdown.cebe.cc/">Cebe Markdown</a>, <a href="http://ciconia.kzykhys.com/">Ciconia</a>, <a href="https://help.github.com/articles/github-flavored-markdown/">Github Flavored Markdown</a>, <a href="http://kramdown.gettalong.org/">Kramdown</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="https://github.com/chjj/marked">Marked</a>, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://parsedown.org/">Parsedown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>

**Syntax Highlighting**

tickmarks( ` ) 의 옆에 코드에 해당하는 언어를 명시해줌으로써 Syntax Highlighting 기능을 구현할 수 있다.

    ```css 
    body {
        margin: 0;
        padding: 0;
        color: #222;
        background-color: white;
        font-family: sans-serif;
        font-size: 1.8rem;
        line-height: 160%;
        font-weight: 400;
    }
    ``` 

><strong>Available with:</strong><br>
<a href="http://ciconia.kzykhys.com/">Ciconia</a>, <a href="https://help.github.com/articles/github-flavored-markdown/">Github Flavored Markdown</a>, <a href="http://kramdown.gettalong.org/">Kramdown</a>*, <a href="https://github.com/chjj/marked">Marked</a>, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://parsedown.org/">Parsedown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>

\* 이 기능을 지원하지 않는 경우 [highlight.js](https://highlightjs.org/) 같은 라이브러리를 통해 구현할 수 있다.

**Tables**

html로 테이블을 작성하는 것은 꽤나 성가신 일이다. 마크다운에서는 간단한 문법을 통해 테이블을 작성할 수 있다

```
Dimensions | Megapixels
---|---
1,920 x 1,080 | 2.1MP
3,264 x 2,448 | 8MP
4,288 x 3,216 | 14MP
```

[Markdown Tables Generator](http://www.tablesgenerator.com/markdown_tables) 와 같은 사이트를 통해 테이블 생성에 도움을 받을 수도 있다.

><strong>Available with:</strong><br>
<a href="http://markdown.cebe.cc/">Cebe Markdown</a>, <a href="http://ciconia.kzykhys.com/">Ciconia</a>, <a href="https://help.github.com/articles/github-flavored-markdown/">Github Flavored Markdown</a>, <a href="http://kramdown.gettalong.org/">Kramdown</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="https://github.com/chjj/marked">Marked</a>, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://parsedown.org/">Parsedown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>

**Metadata**

메타데이터를 작성할 수도 있는데,  [Multi-Markdown structure](https://github.com/fletcher/MultiMarkdown/wiki/MultiMarkdown-Syntax-Guide#metadata) 가 사용 되기도 하고, Jekyll 파서같은 경우는 [YAML](http://www.yaml.org/) 포맷을 사용하기도 한다.

```nohighlight
---
Title:  SVG Article
Author: Ray Villalobos
Date:   January 6, 2016
heroimage: "http://i.imgur.com/rBX9z0k.png"
tags:
- data visualization
- bitmap
- raster graphics
- navigation
---
```
><strong>Available with:</strong><br>
<a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>

**URL Autolinking**

URL 텍스트를 추가 작업없이 자동으로 링크로 변경해준다.

><strong>Available with:</strong><br>
<a href="http://markdown.cebe.cc/">Cebe Markdown</a>, <a href="http://ciconia.kzykhys.com/">Ciconia</a>, <a href="http://commonmark.org/">CommonMark</a>, <a href="https://help.github.com/articles/github-flavored-markdown/">Github Flavored Markdown</a>, <a href="http://kramdown.gettalong.org/">Kramdown</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="https://github.com/chjj/marked">Marked</a>, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://parsedown.org/">Parsedown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>


**Fragments/Cross Reference Links**


HTML에서는 앵커태그 내에서 해쉬 마크를 통해 쉽게 참조 링크를 생성할 수 있는데, 이와 같은 기능을 구현한 것이다. 이 기능은 버전마다 매우 다양한 방법으로 구현되었기 때문에 사용에 주의가 필요하다.

```nohighlight
You can link to a headline called 'myheadline' in your document using this [My Headline][].

## My Headline
The word 'reference' right next to this will get a link that links via an href to the headline above. The headline, in other words, gets an ID that the link points to.
```

><strong>Available with:</strong><br>
<a href="http://ciconia.kzykhys.com/">Ciconia</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://parsedown.org/">Parsedown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>


**Custom IDs on Headlines**

헤드라인에 커스텀 ID를 갖게 하는 기능이다. CSS를 통한 접근을 쉽게 할수 있게 한다. 일부 파서들은 자동으로 모든 헤드라인에 아이디를 부여하기도 해서 (특별히 파서가 fragments/cross references 기능을 지원한다면), 항상 필요한 기능은 아니다.

```nohighlight
### Custom IDs {#custom-id}
The headline above, when rendered by the parser, will have a custom ID that you specify in the curly braces.
```

**Footnotes & Other Link types**

각주에 대한 링크를 생성할 수 있는 기능. 개개의 버전마다 구현이 매우 다르기 때문에 주의 요망.

```nohighlight
You can find a demo of a site[^Demo] built with PostCSS in our footnotes, or you can checkout the [^Github Repo] for the project.

#### Footnotes
[Demo](http://iviewsource.com/exercises/postcsslayouts)
[Github Repo](https://github.com/planetoftheweb/postcsslayouts)
```

><strong>Available with:</strong><br>
<a href="http://markdown.cebe.cc/">Cebe Markdown</a>, <a href="http://kramdown.gettalong.org/">Kramdown</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://parsedown.org/">Parsedown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>

**To-dos**

GFM (GitHub flavored markdown)의 대표적 기능중 하나. todo-list 마크업을 생성할 수 있다.

```nohighlight
- [ ] Run `> npm-install` to install the project dependencies
- [X] Install gulp.js via the Mac terminal or Gitbash on a PC `> npm install -g gulp`
- [ ] Run the Gulp command `> gulp`
```

><strong>Available with:</strong><br>
<a href="http://ciconia.kzykhys.com/">Ciconia</a>, <a href="https://help.github.com/articles/github-flavored-markdown/">Github Flavored Markdown</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="https://github.com/chjj/marked">Marked</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>

**Strikethrough**

취소선 기능.  `&lt;s&gt;` 태그로 감싼다. 

><strong>Available with:</strong><br>
<a href="http://ciconia.kzykhys.com/">Ciconia</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="https://github.com/chjj/marked">Marked</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="http://parsedown.org/">Parsedown</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>, <a href="https://github.com/vmg/redcarpet">Redcarpet</a>, <a href="http://showdownjs.github.io/demo/">Showdown</a>

**Definition Lists**

colon(:) 이나 tilde(~) 를 이용해 작성할 수 있다. colon이 좀 더 일반적이다.

```nohighlight
ES6/ES2015
:   The new version of the popular JavaScript language

TypeScript
  ~ TypeScript is a language that is a superset of JavaScript that can be compiled through a transpiler to JavaScript that will work with most browsers.
```

><strong>Available with:</strong><br>
<a href="http://kramdown.gettalong.org/">Kramdown</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>*, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="https://github.com/piwi/markdown-extended">PHP Markdown Extended</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>, <a href="https://jonschlinkert.github.io/remarkable/demo/">Remarkable</a>

\* 익스텐션 필요.

**Math**

수식 표현.

><strong>Available with:</strong><br>
<a href="http://kramdown.gettalong.org/">Kramdown</a>*, <a href="http://maruku.rubyforge.org/index.html">Maruku</a>, <a href="http://fletcherpenney.net/multimarkdown/">Multi-Markdown</a>, <a href="https://markdown-it.github.io/">Markdown-it</a>, <a href="https://pythonhosted.org/Markdown/">Python Markdown</a>

\* 익스텐션 필요.

___

## 주목할만한 확장 버전들 
많은 마크다운 버전중 다른 버전들에서 종종 인용되는 버전들이 있다. 예를 들어 어떤 라이브러리는 GFM을 지원한다고 한다고 명시되어있는데, 어떤 의미인지 알아보자.

* **GFM**        

  마크다운이 개발자들 사이에서 유명해진 이유중 하나는 깃헙이 사용하는 Github Flavored Markup (GFM) 때문이다. `Fenced Codeblocks, Syntax Highlighting, Tables, URL AutoLinking, To-dos, Strikethrough` 등의 기능을 지원한다. 즉 GFM 을 지원한다는 것은 위의 기능들이 지원된다는 의미다.

* **CommonMark**

  표준 문법 사양 정의에 중점을 둔 프로젝트.

* **Multi-markdown**

  마크다운을 확장한 첫 프로젝트이다. 원래는 펄로 작성되었지만, C로 이동했다. 어떤 프로젝트가 Mult-markdown 을 지원한다고 하면 이 [기능](https://rawgit.com/fletcher/human-markdown-reference/master/index.html) 들을 지원한다고 보면 된다.

___ 

## Oh that sweet I/O

주의해야할 점은 특정 기능을 지원한다 해서 동일한 코드를 생성하는게 아니라는 점이다. 어떤 버전은 동일 기능에 대해 장황한 코드를 생성하는 반면에 어떤 버전은 최소화된 코드를 생성한다.

[Babelmark 2 test](http://johnmacfarlane.net/babelmark2/) 등의 사이트를 통해 각각의 버전들이 어떤 결과물을 생성해 내는지 확인할수 있다.

![Image of Yaktocat](https://cdn.css-tricks.com/wp-content/uploads/2016/02/babelmark.png)

