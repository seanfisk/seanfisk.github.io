My Personal Website
===================

Repository Layout
-----------------

There are two ways to publish a Jekyll blog to GitHub Pages:

#### Use GitHub Pages build server

For this technique, the Jekyll source is pushed on the GitHub Pages branch (`master` for user/organization pages, `gh-pages` for project pages). GitHub then uses its software to generate the HTML. If using this technique, Jekyll suggests using the [github-pages gem][] to pin your dependencies to exactly the software GitHub is using to generate your site.

Although this makes deployment easier, it has a few disadvantages:

- GitHub's build server does not use the most current versions of software.
- GitHub's build server [overrides the source setting][], meaning the site needs to be in the root of the repository. This is annoying, as it means all files that should not be in the site (like `Gemfile`) need to be added to the `exclude` option in `_config.yml`. This is in contrast to putting all site files in their own directory (e.g., `src`).
- Jekyll plugins [cannot be used on the GitHub Pages build server][].

[github-pages gem]: https://jekyllrb.com/docs/github-pages/#deploying-jekyll-to-github-pages
[overrides the source setting]: https://help.github.com/articles/generic-jekyll-build-failures/#source-setting
[cannot be used on the GitHub Pages build server]: https://jekyllrb.com/docs/plugins/

#### Build locally

Building locally consists of running Jekyll on the development machine to create the static HTML. Since we are going to do this anyway to preview the site, there's really no reason not to use this approach, other than the idea that the build server approach is "easier". This also avoids all the aforementioned disadvantages of using the build server.

Since we are now using the GitHub Pages branch (`master` for this repo) as a deployment branch only, we need to create another branch for versioning the site's source code. We've called this `source`. The site is deployed by building the HTML locally, commiting the HTML to the `master` branch, then pushing it to GitHub Pages.

The extra effort of deployment is mostly alleviated by the [octopress gem][], a part of Octopress 3. By using `octopress deploy` with a proper `_deploy.yml`, we can easily push our built site to GitHub pages.

[octopress gem]: https://github.com/octopress/octopress

Theming
-------

[Octopress Ink][] is Octopress 3's new component for building Jekyll themes contained inside a Gem. This is much better than what Jekyll has currently — most themes instruction you to clone or copy their entire blog, tweak the config, and insert your own posts. However, [Octopress Genesis], Octopress 3's only theme based on Ink, is not ready for production. As of March 2016, I was having gem installation errors because some gems depend on Jekyll 2. Hopefully this will be fixed in the future, but until then, I've decided to go with a pure Jekyll-based theme.

[Octopress Ink]: https://github.com/octopress/ink
[Octopress Genesis]: https://github.com/octopress/genesis-theme
