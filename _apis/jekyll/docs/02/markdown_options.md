---
title: Markdown Options
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Jekyll이 지원하는 여러 Markdown 렌더러(renderer)는 경우에 따라 추가 옵션을 제공한다.

## Kramdown
Kramdown은 Jekyll의 기본 Markdown 렌더러이다. 보통 별도의 설정 없이도 잘 동작하지만 다양한 설정 옵션도 지원한다.

### Kramdown Processor
기본적으로 Jekyll은 Kramdown용 [GitHub Flavored Markdown(GFM) 프로세서](https://github.com/kramdown/parser-gfm)를 사용한다.(<code class="code-inline">input: GFM을</code> 설정 파일에 지정해도 되지만, 이는 중복 설정이다.) GFM은 [kramdown-parser-gfm](https://github.com/kramdown/parser-gfm)에 문서화된 몇 가지 추가 Kramdown 옵션을 지원한다. 이 옵션들은 다음과 같이 Kramdown Jekyll 설정에 직접 지정할 수 있다:

```yaml
kramdown:
  gfm_quirks: [paragraph_end]
```

또한 Kramdown에서 사용하는 프로세서([Kramdown RDoc](https://kramdown.gettalong.org/rdoc/Kramdown/Document.html#method-c-new)에서 <code class="code-inline">input</code> 키로 지정하는 값)를 변경할 수도 있다. 예를 들어, Jekyll에서 GFM이 아닌 Kramdown 프로세서를 사용하려면 설정 파일에 다음과 같이 지정한다.

```yaml
kramdown:
  input: Kramdown
```

Kramdown 파서에 관련 내용은 [Kramdown 문서](https://kramdown.gettalong.org/parser/kramdown.html)에서 확인할 수 있다. Kramdown이나 GFM 외의 Kramdown 파서를 사용한다면 해당 파서용 gem을 추가해야 한다.

### Syntax Highlighting (CodeRay)
Kramdown에서 [CodeRay](http://coderay.rubychan.de/) 구문 하이라이터를 사용하려면 <code class="code-inline">kramdown-syntax-coderay</code> gem에 대한 의존성을 추가해야 한다(예: <code class="code-inline">bundle add kramdown-syntax-coderay</code>). 이제 <code class="code-inline">syntax_highlighter</code> 설정에 CodeRay를 지정할 수 있다:

```yaml
kramdown:
  syntax_highlighter: coderay
```

CodeRay는 여러 가지 설정 옵션을 자체적으로 지원하며, 이는 [kramdown-syntax-coderay](https://github.com/kramdown/syntax-coderay) 문서에 정리되어 있다. 이 설정 옵션들은 다음과 같이 <code class="code-inline">syntax_highlighter_opts</code>로 전달할 수 있다:

```yaml
kramdown:
  syntax_highlighter: coderay
  syntax_highlighter_opts:
    line_numbers: table
    bold_every: 5
```

### Advanced Kramdown Options
Kramdown은 <code class="code-inline">header_offset</code>, <code class="code-inline">smart_quotes</code>와 같은 다양한 고급 옵션도 지원한다. 관련 내용은 [Kramdown 설정 문서](https://kramdown.gettalong.org/options.html)에 정리되어 있으며, 다음과 같이 Kramdown 설정에 추가할 수 있다:

```yaml
kramdown:
  header_offset: 2
```

<div class="red-caution">
⚠️ 지원되지 않는 kramdown 옵션
Jekyll은 Kramdown의 HTML 변환기를 사용한다. 따라서 RemoveHtmlTags 변환기에서 사용하는 <code class="code-inline">remove_block_html_tags</code>처럼 다른 변환기에서만 쓰이는 Kramdown 옵션은 동작하지 않는다.
</div>

## CommonMark
[CommonMark](https://commonmark.org/)는 Markdown 문법을 표준화한 규격으로, C로 구현되어 Ruby로 구현된 기본 Kramdown보다 더 빠르다. 원래의 Markdown과는 다소 [차이](https://github.com/commonmark/commonmark-spec#differences-from-original-markdown)가 있으며, Kramdown이 지원하는 모든 문법 요소(예: [Block Inline Attribute Lists](https://kramdown.gettalong.org/syntax.html#block-ials))를 지원하지는 않는다.

CommonMark는 두 가지 방식으로 제공된다: [jekyll-commonmark](https://github.com/jekyll/jekyll-commonmark) 플러그인을 사용하는 기본 CommonMark와, [GitHub Pages에서 지원하는 GitHub Flavored Markdown](https://github.com/github/jekyll-commonmark-ghpages)이 있다.

## Custom Markdown Processors
사용자 정의 Markdown 프로세서를 만들고 싶다면 다음과 같이 <code class="code-inline">Jekyll::Converters::Markdown</code> 네임스페이스에 새 클래스를 작성하면 된다:

```markdown
class Jekyll::Converters::Markdown::MyCustomProcessor
  def initialize(config)
    require 'funky_markdown'
    @config = config
  rescue LoadError
    STDERR.puts 'You are missing a library required for Markdown. Please run:'
    STDERR.puts '  $ [sudo] gem install funky_markdown'
    raise FatalException.new("Missing dependency: funky_markdown")
  end

  def convert(content)
    ::FunkyMarkdown.new(content).convert
  end
end
```

클래스를 만든 뒤 <code class="code-inline">_plugins</code> 폴더의 플러그인으로 두거나 gem으로 올바르게 설정했다면, <code class="code-inline">_config.yml</code>에서 다음처럼 지정한다:

```yaml
markdown: MyCustomProcessor
```
