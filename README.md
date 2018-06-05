# Personal home page adapted from **minima** default theme

Minima has been scaffolded by the `jekyll new-theme` command and therefore has all the necessary files and directories to have a new Jekyll site up and running with zero-configuration.

## Usage

#### Main Heading and Content-injection

From Minima v2.2 onwards, the *home* layout will inject all content from your `index.md` / `index.html` **before** the **`Posts`** heading. This will allow you to include non-posts related content to be published on the landing page under a dedicated heading. *We recommended that you title this section with a Heading2 (`##`)*.

Usually the `site.title` itself would suffice as the implicit 'main-title' for a landing-page. But, if your landing-page would like a heading to be explicitly displayed, then simply define a `title` variable in the document's front matter and it will be rendered with an `<h1>` tag.

### Customize navigation links

This allows you to set which pages you want to appear in the navigation area and configure order of the links.

For instance, to only link to the `about` and the `portfolio` page, add the following to you `_config.yml`:

```yaml
header_pages:
  - about.md
  - portfolio.md
```

--

## License

The minima theme for Jekyll is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
