# code-language-labels

A [Quarto](https://quarto.org/) extension that labels each highlighted code
block with the name of its language ("R", "Python", "Julia", "Shell", ...),
in HTML and revealjs output.
PDF and other non-HTML formats are left untouched.

It is plain CSS keyed on the class Pandoc already puts on every highlighted
block (`<pre class="sourceCode r">`), attached by a short filter.
It labels executed chunks and plain fences alike, and never labels chunk
output, which carries no language class.
Nothing is written into the page per block.

## Installation

```bash
quarto add d-morrison/code-language-labels
```

## Usage

Add it to `_quarto.yml` to label every page in a project:

```yaml
filters:
  - d-morrison/code-language-labels
```

or to one document's front matter.

- **Opt a block out** with the class `no-language-label`:
  ```` ```{.python .no-language-label} ```` for a plain fence,
  or `#| class-source: no-language-label` in an executed chunk.
- **A block with a `filename`** keeps Quarto's own filename header and gets no
  second label.
  Use `filename` when a block needs a custom title.
- **A language missing from the map** in
  `_extensions/code-language-labels/code-language-labels.css` gets no label;
  add a line there to cover it.

## Why not `andrewheiss/language-name`?

That extension does the same job with a Lua filter that writes a `<style>`
element per block and capitalizes the class name for the label ("Sh", "Yaml").
It also labels nothing unless `language-name: show-all: true` is set.
This one needs no options and gives each language its conventional spelling.

## License

MIT
