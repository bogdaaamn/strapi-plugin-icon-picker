# Icon picker custom field

![Icon picker custom field preview. Features a grid of icons.](https://github.com/JonssonWorkwear/strapi-plugin-icon-picker/assets/22895284/11e22408-3c27-4f05-a674-2b690342313a)

This package provides a custom field for Strapi that lets us select an icon. It uses the `IconPicker` component inside Strapi and a collection of generated SVG icons. 

<div align="center">
  <a href="https://github.com/JonssonWorkwear/strapi-plugin-icon-picker/actions/workflows/release.yml">
    <img src="https://github.com/JonssonWorkwear/strapi-plugin-icon-picker/actions/workflows/release.yml/badge.svg?branch=release" alt="Release status">
  </a>
  <a href="https://www.npmjs.com/package/@jonssonworkwear/strapi-plugin-icon-picker">
    <img alt="npm (scoped)" src="https://img.shields.io/npm/v/%40jonssonworkwear/strapi-plugin-icon-picker?logo=npm&label=%40jonssonworkwear%2Fstrapi-plugin-icon-picker&color=%234845F5">
  </a>
</div>

## 🏖️ Features

* **List icons:** to see them all. 
* **Search icons:** to see just a few.

## 🔧 Installation

To install this plugin simply run this command in the Strapi project:

```
yarn add @jonssonworkwear/strapi-plugin-icon-picker
```

## ✨ Usage

When adding a new field to a content type, select **CUSTOM** (instead of **DEAFULT**), then select **Icon picker**.

![Icon picker custom field preview inside the content type builder](https://github.com/JonssonWorkwear/strapi-plugin-icon-picker/assets/22895284/3e97f7f7-8bf8-4499-922d-281ff311fdff)

Inside a content-type, we can use the following schema:

```json
"icon": {
  "type": "customField",
  "customField": "plugin::icon-picker.IconPicker"
}
```

## 🪛 Development

Clone this repository in the Strapi directory.

```
git clone https://github.com/JonssonWorkwear/strapi-plugin-icon-picker.git src/plugins/strapi-plugin-icon-picker
```

Add the plugin to the yarn workspace, inside `./package.json` file, so we won't need to use `yarn` inside plugin itself.

```
"workspaces": ["./src/plugins/strapi-plugin-icon-picker"]
```

Install dependencies.

```
yarn
```

Register the plugin so Strapi can use it. Inside `./config/plugins.js` file add an entry:

```
module.exports = ({ env }) => ({
  "icon-picker": {
    enabled: true,
    resolve: "./src/plugins/strapi-plugin-icon-picker"
  },
});
```

Rebuild the project and start the server.

```
yarn build
yarn develop
```

Or perhaps use the `--watch-admin` flag to toggle hot reloading of the admin panel.

```
yarn develop --watch-admin
```

### Generate icons

All the icons inside `admin/src/components/IconPicker/icons` are generated from SVG files using [svgr](https://github.com/gregberge/svgr). The index file containing the `COMPONENT_ICONS` list is also generated. 

### Release changes

All the changes are commited and pushed to _this_ repository (or its forks), independently from the Strapi directory. The changes on the `release` branch will be published in the `@jonssonworkwear/strapi-plugin-icon-picker` package. If there is a new release published, plugins inside the Strapi project might need their version bumped.
