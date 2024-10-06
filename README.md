<p align="center">
  <img width="200px" src="https://raw.githubusercontent.com/tjtanjin/react-chatbotify/main/assets/logo.png" />
  <h1 align="center">React ChatBotify Themes</h1>
</p>

<p align="center">
  <a href="https://github.com/tjtanjin/react-chatbotify/actions/workflows/ci-cd-pipeline.yml"> <img src="https://github.com/tjtanjin/react-chatbotify/actions/workflows/ci-cd-pipeline.yml/badge.svg" /> </a>
  <a href="https://www.npmjs.com/package/react-chatbotify"> <img src="https://img.shields.io/npm/v/react-chatbotify?logo=semver&label=version&color=%2331c854" /> </a>
  <a href="https://www.npmjs.com/package/react-chatbotify"> <img src="https://img.shields.io/badge/react-16--19-orange?logo=react&label=react" /> </a>
  <a href="https://www.npmjs.com/package/react-chatbotify"> <img src="https://img.shields.io/npm/d18m/react-chatbotify?logo=npm&label=npm%20downloads&color=%232281c2" /> </a>
  <a href="https://discord.gg/6R4DK4G5Zh"> <img src="https://img.shields.io/endpoint?url=https://my-api.tjtanjin.com/aggregator/api/v1/get/rcb_discord_member_count&logo=discord&logoColor=ffffff" /> </a>
</p>

## Table of Contents
* [Introduction](#introduction)
* [Creating Themes](#creating-themes)
* [Repository Structure](#repository-structure)
* [Integration with React ChatBotify](#integration-with-react-chatbotify)
* [Upcoming Work](#upcoming-work)
* [Want to Help?](#want-to-help?)

### Introduction

<p align="center">
  <img height="400px" src="https://github.com/tjtanjin/react-chatbotify/assets/43908963/761fcbb3-858e-4a9c-846b-4fddaf218dbc" />
</p>

Welcome to React ChatBotify Themes! This repository contains themes that may be imported for use with the [**React ChatBotify**](https://react-chatbotify.com/) library. If you're unfamiliar with **React ChatBotify**, it is recommended to go through its repository [**README**](https://github.com/tjtanjin/react-chatbotify) to at least gain a basic understanding before continuing with this document.

Note that this themes repository is created as part of **React ChatBotify v2.0.0**, which was released **late July 2024**. As a relatively new feature/project, it still actively requires open source theme contributions to help grow its collection of themes. If you're looking to contribute as a theme author, please do the following:
- Read the section on [**Creating Themes**](#creating-themes)
- Optionally (but recommended), reach out to me on [**Discord**](https://discord.gg/6R4DK4G5Zh)
- Create an issue (or request to be assigned to an existing one) to track your work for a theme

Thereafter, you may start curating themes following the steps in the section below (feel free to seek help on discord if you require clarifications as well).

### Creating Themes

React ChatBotify presently allows customizing the appearance of the chatbot via the `settings` and `styles` prop as well as in advanced use cases, CSS files. This remains true for theme authors as well and as such, theme authors will be customizing their chatbot in **the same way that it is currently done**. With that said, the general steps taken would be:
1) Fork/clone the **chatbot** repository (read the chatbot setup in the [**Developer Guide**](https://github.com/tjtanjin/react-chatbotify/blob/main/docs/DeveloperGuide.md))
2) On your local environment, customize [**settings**](https://react-chatbotify.com/docs/api/settings) and [**styles**](https://react-chatbotify.com/docs/api/styles) as you deem fit and if necessary, use css to target specific classes
3) When you're done:
    - Copy your `settings` prop into a **JSON file** named **settings.json**
    - Copy your `styles` prop into a **JSON file** named **styles.json**
    - Consolidate all your modified CSS classes into a **CSS file** named **styles.css**
4) Create a **meta.json** file containing the following properties (the values don't particularly matter for now, may be changed later):
    ```
    {
        "name": "Retro",
        "description": "Rocket back into the past!",
        "author": "tjtanjin",
        "github": "tjtanjin",
        "tags": [],
        "version": "0.0.0"
    }
    ```
5) Take a screenshot of your theme and name the image **display.png**
6) Next, put the 5 files (**settings.json, styles.json, styles.css, meta.json, display.png**) into a folder named after your theme (lowercase, underscores, no spaces)
7) Fork/clone the **themes** repository and place your newly created folder inside the **themes** folder
8) Finally, open a pull request to the **themes** repository with your additions

The screenshot below contains example themes that have been worked on:

![example_themes](https://github.com/tjtanjin/react-chatbotify-themes/assets/43908963/97a18875-e1d8-47c9-8889-798d3b9d64ed)

You may also check out the [**Gallery Website**](https://gallery.react-chatbotify.com/themes) to look at the work that others have done before. It might also be helpful to look at some of the [**merged PRs**](https://github.com/tjtanjin/react-chatbotify-themes/pulls?q=is%3Apr+is%3Aclosed) for reference.

Once again as the themes feature is relatively new, I'm happy to do a lot more handholding and streamlining of processes based on feedback. With that in mind, do not hesitate to reach out to me actively on Discord for help and suggestions.

Note: Below are some common issues when creating new themes:
- Forgot to style checkboxes & options
- Forgot to style chat history button, spinner and loaded text
- Forgot to style user chat bubbles

If you're just looking to create themes, **you may stop reading the document here**. The remaining content will mostly be geared towards developers who are interested to know more details about theming integration and setup.

### Repository Structure

As mentioned earlier, if you're just interested in creating themes, then you need not read the rest of this documentation. The content hereafter are for developers interested to understand how themes here will be implemented and integrated with the chatbot.

Firstly, this repository adopts a configuration as code approach. Within the repository, you will find a themes folder which houses all supported themes of the package. Within each theme folder, you will find a `meta.json` file describing the theme and `subfolders` matching version releases. Within these version `subfolders`, you'll find `settings.json`, `styles.json`, `styles.css` and `display.png` files. A basic structure is thus as shown below:
```
|- themes
    |- dark_theme
        |- meta.json
        |- 0.1.0
            |- settings.json
            |- styles.json
            |- styles.css
            |- display.png
        |- 0.2.0
            |- settings.json
            |- styles.json
            |- styles.css
            |- display.png
    |- retro_theme
        |- meta.json
        |- 0.1.0
            |- settings.json
            |- styles.json
            |- styles.css
            |- display.png
        |- 0.1.1
            |- settings.json
            |- styles.json
            |- styles.css
            |- display.png
    |- minimal_midnight_theme
        |- meta.json
        |- 0.1.0
            |- settings.json
            |- styles.json
            |- styles.css
            |- display.png
```

### Integration with React ChatBotify

To utilize the themes in React ChatBotify, users will specify themes within the `themes` prop. You may find the following live examples useful for showcasing how themes are used:
- https://react-chatbotify.com/docs/examples/single_theme
- https://react-chatbotify.com/docs/examples/multiple_themes

The `themes` prop essentially accepts a `Theme` object or an array of `Theme` object (i.e. 1 or more themes). When a theme is specified, React ChatBotify pulls the relevant CSS and JSON files for the theme via an open-source CDN ([JsDelivr](https://www.jsdelivr.com/)). If multiple themes are specified, then the later themes will override earlier themes if there are style conflicts. That said, theme authors may find the support for multiple themes useful in creating a base template theme which allows variants to be built on top of it.

Again, if you're keen to try themes feature yourself, do check out the above 2 examples shared earlier.

### Upcoming Work

Themes are currently available for browsing on the [**Gallery Website**](https://gallery.react-chatbotify.com). The gallery website itself is managed as a separate project over [**here**](https://github.com/tjtanjin/react-chatbotify-gallery-website). Having to open pull requests and create folders to share themes is not exactly the most user-friendly approach. Down the road, we will be revamping the gallery for the following purposes:
- Allow users to browse and choose themes
- Allow users to upload their themes for sharing

Thus, the eventual goal is to allow users to upload themes directly on the website, instead of having to go through the tedious process that theme authors are going through now.

### Want to Help?

There's a lot of pieces of work involved in elevating the quality of the Chatbot (theme creation, themes website etc) and contributions are always welcome. If you're keen to help, whether it's adding a theme or making improvements to the library directly, please feel free to open a pull request or even [reach out](https://discord.gg/6R4DK4G5Zh) directly to me. Your help will be very much appreciated.
