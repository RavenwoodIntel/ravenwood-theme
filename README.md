# Ravenwood

The Ravenwood theme is a hard fork of Source, the default theme for [Ghost](http://github.com/tryghost/ghost/)! There are features of the Source theme that have been modified or completely removed for simplicity and brand continuity.

***Note:** This theme is highly customized for the specific branding and cooperative needs of Ravenwood Intelligence. While you are free to fork and use it under the MIT License, it is not intended to be a generic, plug-and-play Ghost theme.*

If you're looking to start from the latest Source release instead, head over to the [releases](https://github.com/TryGhost/Source/releases) page.

# First time using a Ghost theme?

Ghost uses a simple templating language called [Handlebars](http://handlebarsjs.com/) for its themes.

This theme has lots of code comments to help explain what's going on just by reading the code. Once you feel comfortable with how everything works, Ghost also has full [theme API documentation](https://ghost.org/docs/themes/) which explains every possible Handlebars helper and template.

**The main files are:**

- `default.hbs` - The parent template file, which includes your global header/footer
- `home.hbs` - The homepage
- `index.hbs` - The main template to generate a list of posts
- `post.hbs` - The template used to render individual posts
- `page.hbs` - Used for individual pages
- `tag.hbs` - Used for tag archives, eg. "all posts tagged with `news`"
- `author.hbs` - Used for author archives, eg. "all posts written by Jamie"

One neat trick is that you can also create custom one-off templates by adding the slug of a page to a template file. For example:

- `page-about.hbs` - Custom template for an `/about/` page
- `tag-news.hbs` - Custom template for `/tag/news/` archive
- `author-ali.hbs` - Custom template for `/author/ali/` archive


# Development

To get started with a local development server, we recommend [nvm](https://github.com/nvm-sh/nvm). With nvm installed setup the Ghost-CLI and local server.

```bash
# set the correct node version for ghost
nvm use 22

# install the Ghost-CLI
npm install ghost-cli@latest -g

# install the ghost server
ghost install local

# start ghost
ghost start

# stop ghost
ghost stop

# view logs
ghost log

# list running servers
ghost ls
```

Configure the theme in a separate project folder outside of the ghost server directory.

```bash
# clone this repo in a new folder outside of your local server
git clone https://github.com/RavenwoodIntel/ravenwood-theme.git

# (optional) hard fork the source theme and start from scratch
npx degit https://github.com/tryghost/starter super-sick-ghost-theme

# navigate to your custom theme's root and install dependencies
npm install

# run development server
npm run dev

# link theme to local Ghost server from server's /content/themes/
ln -s path/to/your/ravenwood-theme .
```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically. The `zip` Gulp task packages the theme files into `dist/<theme-name>.zip`.

```bash
# create .zip file
npm run zip
```

Before committing, it's strongly recommended to run the gscan tool to check for errors, deprecations, and compatability issues.

```bash
# Install the npm package
npm install -g gscan

# Use gscan <file path> anywhere to run gscan against a folder
gscan /path/to/ghost/content/themes/casper

# Run gscan on a zip file in the standard location from project root
gscan -z dist/ravenwood-theme.zip
```


# PostCSS Features Used

- Autoprefixer - Don't worry about writing browser prefixes of any kind, it's all done automatically with support for the latest 2 major versions of every browser.


# SVG Icons

Source uses inline SVG icons, included via Handlebars partials. You can find all icons inside `/partials/icons`. To use an icon just include the name of the relevant file, eg. To include the SVG icon in `/partials/icons/rss.hbs` - use `{{> "icons/rss"}}`.

You can add your own SVG icons in the same manner.

# Translations

Please see [@TryGhost/Themes/theme-translations/README.md](https://github.com/TryGhost/Themes/blob/main/packages/theme-translations/README.md) for how to build, edit, or contribute translations.

# Copyright & License

Copyright (c) 2026 Ravenwood Intelligence Cooperative, Inc.

Copyright (c) 2013-2026 Ghost Foundation

Released under the [MIT license](LICENSE).
