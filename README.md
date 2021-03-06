## Tiny Tiny RSS Feedlish Theme

"Close enough" clone of [levito's tt-rss-feedly-theme](https://github.com/levito/tt-rss-feedly-theme) working on
[Tiny Tiny RSS](https://tt-rss.org/) 18.12+.

The current philosophy is to have as little code as possible to stay
maintainable/hackable. So, we start from the default theme and modify/override
it just enough to get close enough to the feedly theme.

Some changes might diverge from the feedly theme.

Not all tt-rss configurations (day/night/wide/combined/...) are currently
tested, Issues/PRs are welcome.

### Install

```
cd /path/to/tt-rss/themes.local/

git clone https://github.com/Gravemind/tt-rss-feedlish-theme

ln -s tt-rss-feedlish-theme/feedlish.css
ln -s tt-rss-feedlish-theme/feedlish-night.css
```

### Update

`git pull` should suffice. Feedlish should follow tt-rss updates within a week or
two.

If you need tt-rss latest CSS changes right away (or if you
[customized](#customize) Feedlish), you must [rebuild Feedlish css
files](#rebuild) to include tt-rss default theme latest changes in Feedlish; As
long as the changes does not overlap with Feedlish overrides, it should be
fine. Hint: a git hook could do the trick.

### Customize

There is a bunch of Less CSS variables to make customization easier, see
[feedlish.less](feedlish.less).

To customize them, or add more CSS rules, you can create a file `./local.less`;
for example:

```less
// tt-rss-feedlish-theme/local.less

@default-bg: #e8e8e8;       // darker background
@default-fg: #606060;       // lighter foreground text
@color-accent: #ec8200;     // orange highlights
//@color-accent: #ffe100;   // feedly-yellow-ish highlights

@feedlish-hide-author-in-headlines: true;   // hide author
@feedlish-hide-score-in-headlines: true;    // hide score

// See ./feedlish.less for more variables.

```

**But if you customize, you must [rebuild the CSS files](#Rebuild)!**

### Rebuild

The default `.css` files are rebuilt and commit periodically to make default
installations easier.

But they need to be manually rebuild if any `.less` file changes
(`feedlish*.less`, `local.less`, tt-rss default theme `.less` files):

- install `lessc` (`pacman -S nodejs-less`, `dnf install nodejs-less nodejs-source-map`, ...)
- run `make` here

### Screenshots

![feedlish](./screenshots/feedlish.png)

![feedlish-night](./screenshots/feedlish-night.png)
