# &lt;markdown-element&gt;

A lit-html element that renders Markdown using Commonmark.js.  This is a replacement for the Polymer sponsored `<marked-element>`.  `<marked-element>` uses the somewhat outdated Marked parser, while `<markdown-element>` uses the up to date and better maintained [Commonmark parser](https://github.com/commonmark/commonmark.js).

This element is designed to be used with Polymer 3 projects.  If you want to use it elsewhere or figured out how to easily set it up by itself, please open an issue.

## Set up

Install and save to package.json:

```
npm i --save @intcreator/markdown-element
```

Import where needed:

```javascript
import '@intcreator/markdown-element';
```

## Usage

### `markdown` attribute

The markdown source is taken directly from the `markdown` attribute supplied to the element.  The markdown supplied can be dynamically updated to change the rendered markdown.

```html
<markdown-element markdown="This **demo** uses the `markdown` _attribute_, not `src`"></markdown-element>
```

### `src` attribute

The `src` attribute can be used to load a markdown file through AJAX.  It overrides the `markdown` attribute.  The source can be dynamically updated to change the markdown file displayed.

```html
<markdown-element src="./demo.md"></markdown-element>
```

### `<script>` tag

A `<script>` tag can be inserted inside of the `<markdown-element>` to provide the markdown source.  It overrides the `markdown` and `src` attributes.  Support for changing this markdown source dynamically is not yet implemented.

```html
<markdown-element>
    <script type="text/markdown">
        This demo uses a `<script>` tag.
    </script>
</markdown-element>
```

## Properties

### `safe`

Use the `safe` property if you are accepting user input that cannot be trusted (to prevent [XSS attacks](https://en.wikipedia.org/wiki/Cross-site_scripting)).  This will prevent raw HTML and links beginning in `javascript:`, `vbscript:`, etc. from being rendered.  For more details, see the [Commonmark.js README](https://github.com/commonmark/commonmark.js#usage) explanation of `safe`.

```html
<markdown-element safe>
    <script type="text/markdown">
        This <button onclick="alert('JavaScript executed')">button</button> is evil
    </script>
</markdown-element>
```

## Roadmap to 1.0

Here are a few issues that need to be resolved before the 1.0 release:

- Dynamically update markdown when changed in the script tag (if possible) or find another way to dynamically update multiline-markdown

## Contributing

Let's make this element even better!  Want to help?  Found a problem?  Open an issue or contact me on the Polymer Slack, Twitter, etc. @intcreator.