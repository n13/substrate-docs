<h1 align="center">
  <a href="https://www.docs.substrate.io">
    <img alt="Substrate Logo" src="https://github.com/polkadot-developers/substrate-docs/raw/main/static/img/sub.gif" width="70%" />
  </a>
</h1>
<h1 align="center">Substrate Docs</h1>
<h3 align="center">https://docs.substrate.io</h3>

<!-- Badges -->

<p align="center">
  <a href="https://app.netlify.com/sites/substrate-docs/deploys" alt="Netlify Status">
      <img src="https://api.netlify.com/api/v1/badges/42dec01f-3723-4828-9f01-45ac5b3c8a11/deploy-status" />
  </a>
	<br>
	<br>
	<a href="https://substrate.stackexchange.com/" alt="Substrate Stack Exchange">
        <img style= "height: 30px" src="https://img.shields.io/static/v1?style=for-the-badge&logo=stackexchange&label=Substrate&message=Stack%20Exchange&color=green" /></a>
	<br>
	<br>
    <a href="https://twitter.com/intent/follow?screen_name=substrate_io">
        <img src="https://img.shields.io/twitter/follow/substrate_io?style=social&logo=twitter"
            alt="follow on Twitter"></a>
</p>

## Archived Copy - By REZ

This is the original Substrate Documentation up until 2024. 

It is slightly outdated at this point, but still far more detailed than other available docs as of Jan, 2025. 

The README was modified to 


## Local Development

### Install

Navigate into your cloned local repo directory and install all dependencies.

Updated steps by REZ

```shell
# https://github.com/nvm-sh/nvm is suggested, so that you
# switch to the correct version of node set in the .nvmrc file
nvm use 14.15.1

# Fix linting errors
npx eslint --fix .

#check that 14.15.1 is being used
yarn node -v

# Install dependencies
yarn

# Update submodules
git submodule update --init --recursive
git submodule update --remote

# Copy example.env.development into a new .env.development file
cp example.env.development .env.development

# Start the development server
yarn develop

```

#### Additonal information on the above
**gatsby-plugin-substrate submodule**

This website uses a submodule for shared components. To set it up please refer to the [gatsby-plugin-substrate repository](https://github.com/paritytech/gatsby-plugin-substrate#troubleshooting).

Config URL variables based on your preferable local setup.
URL will be used for links generation between Substrate websites.

Default localhost port configuration:

```env
GATSBY_WEBSITE_URL=http://localhost:8100
GATSBY_DOCS_URL=http://localhost:8200
```

**Troubleshooting**

It is sometimes the case that gastby's cache gets corrupted when making changes.
If you run into issues in local development, try to clean this and restart:

```shell
yarn clean
yarn develop
```

## License

<!-- Substrate **documentation** is license under the [Apache 2 license](./LICENSE). -->

## Contributing (OLD CONTENT - Probably irrelevant)

Thank you for your interest in contributing to documentation for Substrate!
As a member of the community, you are invited and encouraged to contribute by submitting issues, offering suggestions for improvements to existing content in the form of a pull request, adding review comments to existing pull requests and issues, proposing new content, or creating new pull requests to fix issues or provide new content.

### Working with `/docs` content

#### URL paths

All `.md` files added to `./content/md/en/docs/` folder will output an URL path without the `/docs` prefix, eg.:

- `index.md` for a category page : `./content/md/en/docs/reference/index.md` &rarr; `/reference/`
- `<article-name>.md` for an article in its parent category `./content/md/en/docs/reference/glossary.md` &rarr; `/reference/glossary/`

You can use any structure nesting needed, there is no limit of depth.

#### Media / Images

- use `./content/media/images/docs/` folder for images to be included in `/docs/*/*.md` files
- source images in `.md`: `/media/images/docs/path/to/your/image/<image>.ext`

#### Navigation config

- update `./content/config/nav.yaml` to add or amend items and linking to your content
  - an exception being `./content/md/en/docs/reference/how-to-guides/...` files that should _only_ be listed on the main how-to guide page in the index page for these pages: `./content/md/en/docs/reference/how-to-guides/index.md`, not to be included in the sidebar.

This config file is used to generate sidebar menu where:

- menu is populated from the `menu` sequence (respecting order)
- menu supports three level hierarchy
- menu accepts external links, eg.: `https://substrate.io`
