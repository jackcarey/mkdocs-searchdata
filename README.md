# mkdocs-searchdata

Mkdocs uses [lunr.js](https://lunrjs.com/) for searching sites. This plugin adds element attributes from each returned heading to the results.

## Setup

Install the plugin using pip:

`pip install mkdocs-searchdata`

Activate the plugin in `mkdocs.yml`:
```yaml
plugins:
  - search
  - searchdata
```

> **Note:** You **need** to add the `search` plugin. MkDocs enables it by default if there is no `plugins` entry set, but now you will have to enable it explicitly.

More information about plugins in the [MkDocs documentation][mkdocs-plugins].

## Config

* `attrs` - The attributes to add to search results.
* `location` - The location of added attributes. `article` or `heading`. Default: `heading`. Useful for styling results with [extra_css](https://www.mkdocs.org/user-guide/configuration/#extra_css) or [custom_dir](https://www.mkdocs.org/user-guide/customizing-your-theme/#using-the-theme-custom_dir).

## How do I add attributes to elements?

* Using the [attr_list](https://python-markdown.github.io/extensions/attr_list/) plugin.
* Your theme may also include attributes or classes on page headings. Refer to its documentation for details.

## Example

```yaml
# mkdocs.yml
plugins:
    - search
    - searchdata
        - attr: data-foo
        - location: article
```

```markdown
<!--markdown.md-->
# My heading 1 {: #someid .someclass data-foo='bar' }
```

```html
<!--search.html (results)-->
<article data-foo='bar'>
<h3>My heading 1</h1>
...
</article>
```

## See Also

More information about templates [here][mkdocs-template].
More information about blocks [here][mkdocs-block].

[mkdocs-plugins]: http://www.mkdocs.org/user-guide/plugins/
[mkdocs-template]: https://www.mkdocs.org/user-guide/custom-themes/#template-variables
[mkdocs-block]: https://www.mkdocs.org/user-guide/styling-your-docs/#overriding-template-blocks
