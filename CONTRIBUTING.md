# Contributing to [The Frankenwallet](https://frankenwallet.com)

_(if your contribution is feedback or a correction, submit an [issue](https://github.com/rphair/frankenwallet/issues) according to [these guidelines](https://github.com/rphair/frankenwallet#suggesting-updates-to-the-documentation))_

## Overview

The web site is built from the files in the [`/docs`](docs) directory using:
* the [Jekyll](https://jekyllrb.com/) static site generator ([documentation](https://jekyllrb.com/docs/)) which incorporates:
  * the [Liquid](https://shopify.github.io/liquid/) templating language, with [extensions to Liquid syntax for Jekyll](https://jekyllrb.com/docs/liquid/)
  * the [Kramdown](https://jekyllrb.com/docs/configuration/markdown/) (GitHub friendly) variety of Markdown
* [Just the Docs](https://just-the-docs.com) Jekyll theme
* [GitHub pages](https://docs.github.com/en/pages) for hosting and deployment

## Site setup & previewing local changes

1. Ensure dependencies are installed: https://jekyllrb.com/docs/installation
1. Clone the site, as per the `Code` button on the [front page](https://github.com/rphair/frankenwallet).
1. Change into your local `/docs` directory.
1. Run `bundle exec jekyll serve --livereload`.

Clicking the preview link that it shows (generally `http://127.0.0.1:4000`) will produce a web site that updates immediately (from `--livereload`) whenever you update the content files, SCSS, or Javascript.  Note:
* Changes to `_config.yml` will require restarting the `bundle` command.
* Updates that create new style sheets will require reloading the browser preview.

## Submitting changes

Once your intended change looks & works properly in your local fork, you can submit changes to the repository for review as [pull requests](https://github.com/rphair/frankenwallet/pulls).  For more about this process, see GitHub Docs > [Collaborating with pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests), especially:
* [Working with forks](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks)
* [Proposing changes to your work with pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests)

## Automation

The [workflow](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages) (process GitHub uses to build the site) is defined here: [.github/workflows/pages.yml](.github/workflows/pages.yml)
* ... which is based on: [just-the-docs-template](https://github.com/just-the-docs/just-the-docs-template) > [.github/workflows/pages.yml](https://github.com/just-the-docs/just-the-docs-template/blob/main/.github/workflows/pages.yml)

This updates the public web site whenever content is pushed to the `/docs` folder in the `main` branch, which happens whenever:
1. a [pull request](/pulls) that you submit is merged by the maintainer
1. the maintainer pushes content directly

From the time content is pushed or merged, a Jekyll rebuild and content update on frankenwallet.com currently takes 60 to 90 seconds.  Each automatic rebuild of the site can be seen & monitored here: https://github.com/rphair/frankenwallet/deployments
