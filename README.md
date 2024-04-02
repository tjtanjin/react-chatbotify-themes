<p align="center">
  <img width="200px" src="https://raw.githubusercontent.com/tjtanjin/react-chatbotify/main/assets/logo.png" />
  <h1 align="center">React ChatBotify</h1>
</p>

<p align="center">
  <a href="https://github.com/tjtanjin/react-chatbotify/actions/workflows/lint.yml"> <img src="https://github.com/tjtanjin/react-chatbotify/actions/workflows/lint.yml/badge.svg" /> </a>
  <a href="https://github.com/tjtanjin/react-chatbotify/actions/workflows/build.yml"> <img src="https://github.com/tjtanjin/react-chatbotify/actions/workflows/build.yml/badge.svg" /> </a>
  <a href="https://github.com/tjtanjin/react-chatbotify/actions/workflows/test.yml"> <img src="https://github.com/tjtanjin/react-chatbotify/actions/workflows/test.yml/badge.svg" /> </a>
  <img src="https://badge.fury.io/js/react-chatbotify.svg" />
</p>

## Table of Contents
* [Introduction](#introduction)
* [Add](#features)
* [Technologies](#technologies)
* [Quickstart](#quickstart)
* [Documentation](#documentation)
* [Team](#team)
* [Contributing](#contributing)
* [Support](#support)
* [Attributions](#attributions)

### Introduction

<p align="center">
  <img height="400px" src="https://github.com/tjtanjin/react-chatbotify/assets/43908963/761fcbb3-858e-4a9c-846b-4fddaf218dbc" />
</p>

Welcome to React ChatBotify Themes! This repository contains themes that may be imported for use with the [**React ChatBotify**](https://react-chatbotify.tjtanjin.com/) library. If you're unfamiliar with **React ChatBotify**, it is recommended to go through the repository [**README**](https://github.com/tjtanjin/react-chatbotify) before continuing with this guide.

Note that this themes repository is part of **React ChatBotify 2.0.0** which is **still in early development**. Thus, the decisions for integrating themes is not yet cast in stone (i.e. not finalized). If you're looking to contribute themes to React ChatBotify 2.0.0 **before its release**, please do the following:
- Reach out to me on [**Discord**](https://discord.gg/6R4DK4G5Zh)
- Read the section on [**Creating Themes**](#creating-themes)

Thereafter, you may start creating themes (I will share more details on Discord if you're interested). After the section on adding themes, the content will mostly be geared towards developers who are interested to know how the theming feature will be setup. Once React ChatBotify 2.0.0 is released, these information will be shifted into a proper developer guide so that theme authors have a simpler document to read.

### Creating Themes

React ChatBotify presently allows customizing the appearance of the chatbot via the `options` prop as well as in advanced use cases, CSS files. This remains true for theme authors as well and as such, theme authors will be customizing their chatbot in **the same way that it is currently done**. With that said, the general steps taken would be:
1) Fork/clone the repository (read the setup in the [**Developer Guide**](https://github.com/tjtanjin/react-chatbotify/blob/working-branch-2.0.0/docs/DeveloperGuide.md))
2) On your local environment, [**customize options**](https://react-chatbotify.tjtanjin.com/docs/api/bot_options) and if necessary, use css to target specific classes
3) When you're done:
    - Copy your `options` prop into a **JSON file** named **options.json**
    - Consolidate all your modified CSS classes into a **CSS file** named **styles.css**
4) Create a **meta.json** file containing the following properties (the values don't particularly matter for now, may be changed later):
    ```
    {
        "theme": "Retro",
        "description": "Rocket back into the past!",
        "author": "tjtanjin",
        "github": "tjtanjin",
        "tags": [],
        "version": "0.0.0",
        "created_at": "",
        "updated_at": ""
    }
    ```
5) Take a screenshot of your theme and name the image **display.png**.
6) Next, put the 4 files (**options.json, styles.css, meta.json, display.png**) into a folder named after your theme (lowercase, underscores, no spaces).
7) Finally, open a pull request to the repository with your folder.

The screenshot below contains example themes that are currently being worked on:

![example_themes](https://github.com/tjtanjin/react-chatbotify-themes/assets/43908963/97a18875-e1d8-47c9-8889-798d3b9d64ed)

### Repository Structure

As mentioned earlier, if you're just interested in creating themes, then you need not read the rest of this documentation. The content hereafter are for developers interested to understand how theming will be implemented.

Firstly, this repository adopts a configuration as code approach. Within the repository, you will find a themes folder which houses all supported themes of the package. Within each theme folder, you will find CSS and JSON files, both of which are ingested as configurations by the React ChatBotify package. A basic structure is thus as shown below:

|- themes
    |- dark_theme
        |- styles.css
        |- styles.json
        |- meta.json
        |- display.png
    |- retro_theme
        |- styles.css
        |- styles.json
        |- meta.json
        |- display.png
    |- minimal_midnight_theme
        |- styles.css
        |- styles.json
        |- meta.json
        |- display.png


### Integration with React ChatBotify

For React ChatBotify to use the themes here, it has been slightly adapted (refer to [**working-branch-2.0.0**](https://github.com/tjtanjin/react-chatbotify/tree/working-branch-2.0.0)) to support a `theme` prop. Subsequently, breaking changes will be made within `options` to streamline some existing configurations.

The `theme` prop accepts a string or an array of strings (i.e. 1 or more themes). When a theme is specified, React ChatBotify pulls the relevant CSS and JSON files for the theme via an open-source CDN ([JsDelivr](https://www.jsdelivr.com/)). If multiple themes are specified, then the later themes will override earlier themes if there are style conflicts. That said, theme authors may find the support for multiple themes useful in creating a base template theme which allows variants to be built on top of it. Example theme usage:
- <ChatBot theme={"dark"} />
- <ChatBot theme={["dark", "minimal_midnight"]} />

 If you're keen to try this yourself, you may pull and run the working branch locally to experiment with the `theme` prop.

### Upcoming Work

The work for React ChatBotify 2.0.0 is currently being done on [**working-branch-2.0.0**](https://github.com/tjtanjin/react-chatbotify/tree/working-branch-2.0.0). The modifications to support `theme` prop are largely complete (including multi-theme support), though the refactoring of `options` prop is yet to be done. However, theme authors are advised to create themes against the latest build on `npm` instead of this working branch. The changes will be migrated at a later date.

Having to open pull request and create folders to make a theme is not exactly the most user-friendly approach. Down the road, we will be exploring options to build a theme website for the following purposes:
- Allow users to browse and choose themes
- Allow users to upload their themes for sharing

More details will be shared as we make progress - there's lots to be done!

### Want to Help?

There's a lot of pieces of work involved in elevating the quality of the Chatbot (theme creation, themes website etc) and contributions are always welcome. If you're keen to help, whether it's adding a theme or making improvements to the library directly, please feel free to open a pull request or even [reach out](https://discord.gg/6R4DK4G5Zh) directly to me. Your help will be very much appreciated.
