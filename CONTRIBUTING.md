# Contributing to [The Frankenwallet](https://frankenwallet.com)

[//]: # (note it's impossible to link back to the repository root with a relative link:)
[//]: # (https://stackoverflow.com/questions/40422790/relative-link-to-repos-root-from-markdown-file)
[//]: # (https://github.com/github/markup/issues/1502)

_(if your contribution is feedback or a correction, or if you simply want to discuss the material, follow [these guidelines](https://github.com/rphair/frankenwallet#community-discussion-questions-and-support))_

<a id="review"></a>
## Review the Frankenwallet

To guarantee the best operational results, and to achieve the best possible assurances of privacy and security, the project would benefit greatly from [community discussion](https://github.com/rphair/frankenwallet#community) by knowledgeable users, operators and developers taking an overall view of the Frankenwallet process and principles: rather than just particular problems.

These categories of reviewers have been described here for the Cardano user community in particular:
* [Call for general user review](https://forum.cardano.org/t/frankenwallet-call-for-general-user-review/150242)
* [Call for operator review](https://forum.cardano.org/t/frankenwallet-call-for-spo-preliminary-review/150243)
* [Call for developer review](https://forum.cardano.org/t/frankenwallet-call-for-developer-review/150245)

... though the author hopes that users of other blockchains — as well as operators and developers having a general interest in practical security — will identify with common elements in these initial calls for review and contribute according to their own experience.

### Submitting changes

If your review has been confident enough to submit a change directly, the maintainer(s) would be happy to consider your Pull Request (though generally it will be help to [post a related issue or discussion](https://github.com/rphair/frankenwallet#community) first).

Once your intended change looks & works properly in the site built locally from your own fork, you can submit changes to the repository for review.  For more about this process, see GitHub Docs > [Collaborating with pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests), especially:
* [Working with forks](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks)
* [Proposing changes to your work with pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests)

## Build the Frankenwallet web site locally

For both the public web site and any local copies, the web site is built from the files in the [`/docs`](docs) directory using:
* the [Jekyll](https://jekyllrb.com/) static site generator ([documentation](https://jekyllrb.com/docs/)) which incorporates:
  * the [Liquid](https://shopify.github.io/liquid/) templating language, with [extensions to Liquid syntax for Jekyll](https://jekyllrb.com/docs/liquid/)
  * the [Kramdown](https://jekyllrb.com/docs/configuration/markdown/) (GitHub friendly) variety of Markdown
* [Just the Docs](https://just-the-docs.com) Jekyll theme
* [GitHub pages](https://docs.github.com/en/pages) for hosting and deployment

### Site setup & previewing local changes

1. Ensure dependencies are installed: https://jekyllrb.com/docs/installation
1. Clone the site, as per the `Code` button on the [front page](https://github.com/rphair/frankenwallet).
1. Change into your local `/docs` directory.
1. Run `bundle exec jekyll serve --livereload`.

Clicking the preview link that it shows (generally `http://127.0.0.1:4000`) will produce a web site that updates immediately (from `--livereload`) whenever you update the content files, SCSS, or Javascript.  Note:
* Changes to `_config.yml` will require restarting the `bundle` command.
* Updates that create new style sheets will require reloading the browser preview.

## Automation of public web site build

The [workflow](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages) (process GitHub uses to build the site) is defined here: [.github/workflows/pages.yml](.github/workflows/pages.yml)

... which is based on: [just-the-docs-template](https://github.com/just-the-docs/just-the-docs-template) > [.github/workflows/pages.yml](https://github.com/just-the-docs/just-the-docs-template/blob/main/.github/workflows/pages.yml)

This updates the public web site whenever content is pushed to the `/docs` folder in the `main` branch, which happens whenever:
1. a [pull request](https://github.com/rphair/frankenwallet/pulls) that you submit is merged by the maintainer
1. the maintainer pushes content directly

From the time content is pushed or merged, a Jekyll rebuild and content update on frankenwallet.com currently takes about a minute.  Each automatic rebuild of the site can be seen & monitored here: https://github.com/rphair/frankenwallet/deployments
