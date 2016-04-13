# Markpress

-----------------------------
## What is it
*markpress* is a tool to convert markdown to an [*impressjs*](https://github.com/impress/impress.js/) html presentation. It is based on [*markdown-impress*](https://github.com/steel1990/markdown-impress) by [steel1990](https://github.com/steel1990)

-----------------------------
## How to install

### Globally
`$ npm install -g markpress`

### For the current project only
`$ npm install markpress`

-----------------------------
## Markdown format
+ Use `------` to separate each slide
+ Use HTML comments to set [impress attrs](https://github.com/impress/impress.js/), such as `<!-- x=0 y=0 rotate=0 scale=1 -->` please note that comments will be ignored if the `layout` option is passed.
+ You can write embedded HTML if you pass the `-h` or `--allow-html` flag.
<!-- + [this page](http://steel1990.github.io/markdown-impress/) is made by *markdown-impress* use [this markdown](https://raw.githubusercontent.com/steel1990/markdown-impress/master/README.md). -->

-----------------------------
## How To Use

![How to use markpress](./markpress-help.png)

## Options

### `-i <path>` or `--input <path>` 

Path to the input file. A [Mardown file](https://daringfireball.net/projects/markdown/) is expected.

### `-o <path>` or `--output <path>`

Path to the output HTMl file.

### `-l` or `--layout` or `{ layout: String }` in code

**Default**: `horizontal`

Automatically generate the layout for the slides. **This option will be ignored if any HTML comment specifying slide positions is found**, so please remove all HTML comments (`<!-- ... -->`) from the markdown file if you want to use this feature.

Available Layouts:

- `horizontal` (default): Slides positioned along the `x` axis. Example
- `vertical`: Slides positioned along the `y` axis. Example
- `3d-push`: Slides positioned along the `z` axis. Slide `n` will be positioned *lower* than `n+1`. Example
- `3d-pull`: Slides positioned along the `z` axis. Slide `n` will be positioned *higher* than `n+1`. Example
- `random-grid`: Slides positioned along the `x` and `y` axis in a grid fashion. Example
- `random`: Slides positioned randomly on the 7D space (`x`,`y`,`z`,`rotate-x`,`rotate-y`,`rotate-z`,`scale`). Note that this layout generator might position slides on top of each other. Re-generate until a satisfactory layout is generated. Example

### `-a` or `--auto-split` or `{ autoSplit: Boolean }` in code

**Default**: `false`

Automatically create a slide for every `H1` (`# Heading 1`) level element (if `------` are present will be removed and ignored)

### `-h` or `--allow-html` or `{ allowHtml: boolean }` in code

**Default**: `false`

Allow HTML code embedded in the Markdown file. Useful if you want to use things like `<kbd></kbd>` tags, embed videos, etc.

### `-t <theme>` or `--theme <theme>` or `{ theme: String }` in code

**Default**: `light`

Chose from the different available themes:

- `light` (default): Light theme with Sans-serif font
- `dark`: Dark theme with Sans-serif font
- `light-serif`: Light theme with Sans-Serif font
- `dark-serif`: Light theme with Serif font

### `-s` or `--silent` or `{ silent: Boolean }` in code

**Default**: `false`

Supress all console outputs.

-------------------------------
## Use in your code

```js
var fs = require('fs');
var markpress = require('markpress');
// defaults:
var options = {
  layout: 'horizontal',
  theme: 'light',
  autoSplit: false,
  allowHtml: false,
  verbose: false
}
var content = markpress('file.md', options).then(() => {
      fs.writeFileSync('file.html', content);
});
```

-------------------------------
## Develop

### Running:

`$ node --harmony ./bin/markpress.js -i input.html -o output.html`

### Debugging

`$ node debug --harmony ./bin/markpress.js -i input.html -o output.html`

### Linking

`npm link`

-------------------------------
## Roadmap

- Improve style for:
  - Ordered lists
  - links
  - Code block highlighting
- Unit tests
- Allow to define slide-specific CSS
- `custom-styles` option to use your own CSS / Less files


## References

- https://www.npmjs.com/package/impress.md
- https://github.com/steel1990/markdown-impress
- Github markdown CSS: https://github.com/sindresorhus/github-markdown-css
