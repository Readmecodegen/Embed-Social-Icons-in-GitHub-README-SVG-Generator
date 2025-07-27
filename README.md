# Embed Social Icons in GitHub README with SVG Generator

## Table of Contents

- [Project Purpose & Feature Rationale](#project-purpose--feature-rationale)
- [Markdown Icon Generator API Documentation](#markdown-icon-generator-api-documentation)
- [Overview](#overview)
- [API Endpoint](#api-endpoint)
- [Parameters](#parameters)
- [Parameter Details & Use Cases](#parameter-details--use-cases)
- [1. `name` (required)](#1-name-required)
- [2. `color` (Optional)](#2-color-optional)
- [3. `size` (optional)](#3-size-optional)
- [4. `bg` (optional)](#4-bg-optional)
- [5. `shape` (optional)](#5-shape-optional)
- [6. `theme` (optional)](#6-theme-optional)
- [Usage Examples](#usage-examples)
- [Default Icon (Brand Color, 32px, Transparent)](#default-icon-brand-color-32px-transparent)
- [Custom Color & Size](#custom-color--size)
- [Dark Theme](#dark-theme)
- [Solid Background](#solid-background)
- [Circular Background](#circular-background)
- [Rectangular Background](#rectangular-background)
- [Clickable Icon (Profile Link)](#clickable-icon-profile-link)
- [HTML Usage](#html-usage)
- [Brand Color Logic](#brand-color-logic)
- [Theme & Background Handling](#theme--background-handling)
- [Why Each Feature Exists](#why-each-feature-exists)
- [Available Icon Categories & Names](#available-icon-categories--names)
- [How to Find Icon Names](#how-to-find-icon-names)
- [Advanced Usage](#advanced-usage)
- [Best Practices & Tips](#best-practices--tips)
- [Troubleshooting](#troubleshooting)
- [Contributing & Requesting Icons](#contributing--requesting-icons)
- [FAQ](#faq)

## Project Purpose & Feature Rationale

The Markdown Icon Generator API was created to simplify embedding high-quality, brand-consistent icons into markdown documents (like GitHub READMEs, documentation, and blog posts). It eliminates the hassle of finding or creating suitable icons, offering full customization without requiring design expertise or manual SVG editing.

It addresses the common problem of inconsistent, low-resolution, or difficult-to-locate icons by providing a centralized, adaptable API for social media, code-related, utility, and symbolic icons. Features such as theme switching, background customization, background shapes (rectangular and circular), and the ability to create clickable icons make it ideal for both developers and non-technical users.

# Markdown Icon Generator API Documentation

## Overview

The Markdown Icon Generator API delivers clean, customizable SVG icons perfect for enhancing GitHub READMEs, documentation, blogs, and more. It supports a wide range of icons, including social media, code, utility, and symbols, with accurate brand colors, themes, backgrounds (rectangular and circular), and flexible sizing options. The API is designed for ease of use, featuring short, readable URLs that simplify integration.

## API Endpoint

The base URL for accessing the Social Icon API is:

```
https://readmecodegen.vercel.app/api/social-icon
```

Think of this as the address you'll use to request icons. Instead of a webpage, the API sends back an icon in SVG format. Include this link in your markdown or HTML code to display the icons.

## Parameters

| Parameter | Type     | Required | Description                                                                        | Example Value       |
| --------- | -------- | -------- | ---------------------------------------------------------------------------------- | ------------------- |
| `name`    | string   | Yes      | The icon's identifier (see available icons below)                                  | `github`, `twitter` |
| `color`   | hex      | No       | Hex color code (without `#`) for the icon. Defaults to brand color or theme logic. | `1da1f2`, `ff0000`  |
| `size`    | int      | No       | Icon size in pixels. Default: `32`                                                 | `48`, `64`          |
| `bg`      | hex/word | No       | Background color (hex or `transparent`). Default: `transparent`                    | `ffffff`, `000000`  |
| `shape`   | string   | No       | Background shape: `rect` (rectangle) or `circle`. Default: `rect`                  | `circle`, `rect`    |
| `theme`   | string   | No       | Icon theme: `light`, `dark`, `github`. Default: `light`                            | `dark`              |

---

## Parameter Details & Use Cases

### 1. `name` (required)

- **What it is:** The unique identifier for the icon you want to display. This is like the icon's name, such as `github`, `twitter`, `linkedin`, or `javascript`.

- **Why we need it:** The API uses this parameter to determine which icon to generate.

- **How to use it:** Append `?name=` followed by the icon's name to the API endpoint. For example:
  `https://readmecodegen.vercel.app/api/social-icon?name=github`

This tells the API to generate the GitHub icon.

### 2. `color` (Optional)

- **What it is:** A hex color code (without the `#`) to customize the icon's color.

- **Why use it?:** By default, the icon uses a brand-specific color (light theme), white (dark theme), or black (GitHub theme). This parameter allows you to override the default color with a color of your choice.

- **How to use it:**
  `https://readmecodegen.vercel.app/api/social-icon?name=twitter&color=ff0000`

In this example, `ff0000` sets the Twitter icon's color to red.

- **When to use it:** Use this parameter to match the icon's color to your website's color scheme or create a specific visual effect.

### 3. `size` (optional)

- **What it is:** A numerical value representing the icon's size in pixels.
- **Why use it?:** It allows you to control the dimensions of the icon. The default size is 32 pixels.
- **How to use it:**
  `https://readmecodegen.vercel.app/api/social-icon?name=github&size=64`
- **When to use it:** Use this parameter to adjust the icon's size for optimal display within your README or other design.

### 4. `bg` (optional)

- **What it is:** Specifies the background color for the icon. You can use a hex color code (e.g., `8b5cf6` for purple, without the `#`) or the keyword `transparent` for no background.

- **Why it's useful:** It helps the icon stand out, especially if your website or README already has a background color.

- **How to use it:** Add `&bg=` followed by your color choice to the URL. For example:
  `https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=%238b5cf6` adds a purple background to the LinkedIn icon.

- **When to use it:** Use this parameter when the icon's default appearance doesn't provide enough contrast against your background or when you want to integrate the icon seamlessly into your page design.

**Note:** Use hex colors with URL-encoded `#` symbol (e.g., `%238b5cf6` not `#8b5cf6`). The `#` gets URL-encoded as `%23`.

**Examples:**

- ✅ `bg=%238b5cf6` (recommended - URL-encoded #)
- ✅ `bg=%238b5cf6` (works - URL-encoded #)
- ✅ `bg=#8b5cf6` (works - automatically encoded to %23)

### 5. `shape` (optional)

- **What it is:** Specifies the shape of the background. Only needed for circular backgrounds - rectangular is the default.

- **Why it's useful:** Allows you to choose circular backgrounds for modern, clean designs. Rectangular backgrounds are the default and work well in structured layouts.

- **How to use it:** Add `&shape=circle` to the URL when you want a circular background. For example:
  `https://readmecodegen.vercel.app/api/social-icon?name=github&bg=%23ffffff&shape=circle` creates a circular white background.

- **When to use it:** Use `shape=circle` for modern, rounded designs or when you want a softer appearance. For rectangular backgrounds, simply don't include the shape parameter.

**Note:** The `shape` parameter only takes effect when a background color (`bg`) is specified. With transparent backgrounds, the shape parameter is ignored.

### 6. `theme` (optional)

- **What:** Accepts values: `light`, `dark`, or `github`.
- **Why:** Quickly switch the icon color for different backgrounds:
- `light`: Brand color (default)
- `dark`: White icon (for dark backgrounds)
- `github`: Black icon (for GitHub-style backgrounds)
- **How to use:**
  `https://readmecodegen.vercel.app/api/social-icon?name=github&theme=dark`
- **When:** Use this parameter to ensure icons are clearly visible on any background.

---

## Usage Examples

### Default Icon (Brand Color, 32px, Transparent)

This is the default appearance of the icon. It uses the brand's official color, is sized at 32 pixels, and has a transparent background.

![github](https://readmecodegen.vercel.app/api/social-icon?name=github)

### Custom Color & Size

```markdown
![x](https://readmecodegen.vercel.app/api/social-icon?name=twitter&color=1da1f2&size=48)
```

### Dark Theme

```markdown
![whatsapp](https://readmecodegen.vercel.app/api/social-icon?name=github&theme=dark)
```

### Solid Background (Rectangular - Default)

```markdown
![linkedin](https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=%238b5cf6&size=28)
```

### Circular Background

```markdown
![github](https://readmecodegen.vercel.app/api/social-icon?name=github&bg=%238b5cf6&shape=circle&size=32)
```

### Rectangular Background (Default)

```markdown
![twitter](https://readmecodegen.vercel.app/api/social-icon?name=twitter&bg=%238b5cf6&size=32)
```

### Clickable Icon (Profile Link)

```markdown
[![gitHub](https://readmecodegen.vercel.app/api/social-icon?name=github)](https://github.com/yourusername)
```

### HTML Usage

```html
<img
  src="https://readmecodegen.vercel.app/api/social-icon?name=twitter&size=40"
  alt="Twitter"
/>
```

<img src="https://readmecodegen.vercel.app/api/social-icon?name=html5&size=28" alt="html5" style="pointer-events: none;" />

## Brand Color Logic

- **light** (default): Uses the official brand color for each icon.
- **dark**: Uses white (`#ffffff`) for all icons.
- **github**: Uses black (`#000000`) for all icons.
- If `color` is specified, it overrides the above logic.

---

## Theme & Background Handling

- Transparent backgrounds are applied by default.
- When a solid background color is set, a 2px padding is automatically added to the icon for improved visual balance.
- Background shapes (`rect` or `circle`) only apply when a background color is specified.
- For optimal visual results, use `theme=dark` on dark backgrounds and `theme=light` on light backgrounds.
- Circular backgrounds work best with modern, clean designs, while rectangular backgrounds are ideal for structured layouts.

---

## Why Each Feature Exists

- **Brand color logic:** Ensures icons maintain an authentic and professional appearance by default.
- **Theme switching:** Guarantees icons are readable across various background colors (light, dark, GitHub).
- **Background support:** Allows you to seamlessly integrate icons into your website or README's style.
- **Background shapes:** Provides flexibility in design aesthetics - circular for modern looks, rectangular for structured layouts.
- **Size parameter:** Ensures icons fit perfectly within any layout or design.
- **Custom color:** Grants you complete creative control over the icon's appearance.
- **Short, clean URLs:** Simplifies copying, pasting, and maintaining icon references.
- **Clickable icons:** Facilitates easy linking to social profiles directly within markdown.
- **Multiple icon categories:** Offers a wide selection of icons for social media, code-related projects, utilities, and symbolic representations, catering to diverse use cases.

---

## Available Icon Categories & Names

- **Social:** github, twitter, linkedin, facebook, instagram, x, ...
- **Code:** javascript, python, java, html5, css3, node, react, ...
- **Utility:** search, settings, ...
- **Symbol:** palette, ...

> For a comprehensive list, refer to the icon picker in the application's user interface or examine the registry files located in `/src/app/icons/components/registries/`.

---

## Available Icons Examples

### Social Media Icons

#### Default (Brand Colors, Transparent Background)

![github](https://readmecodegen.vercel.app/api/social-icon?name=github) ![twitter](https://readmecodegen.vercel.app/api/social-icon?name=twitter) ![linkedin](https://readmecodegen.vercel.app/api/social-icon?name=linkedin) ![facebook](https://readmecodegen.vercel.app/api/social-icon?name=facebook) ![instagram](https://readmecodegen.vercel.app/api/social-icon?name=instagram) ![youtube](https://readmecodegen.vercel.app/api/social-icon?name=youtube) ![discord](https://readmecodegen.vercel.app/api/social-icon?name=discord) ![telegram](https://readmecodegen.vercel.app/api/social-icon?name=telegram) ![whatsapp](https://readmecodegen.vercel.app/api/social-icon?name=whatsapp) ![slack](https://readmecodegen.vercel.app/api/social-icon?name=slack)

#### Circular Backgrounds (shape=circle)

![github](https://readmecodegen.vercel.app/api/social-icon?name=github&bg=%238b5cf6&shape=circle) ![twitter](https://readmecodegen.vercel.app/api/social-icon?name=twitter&bg=%238b5cf6&shape=circle) ![linkedin](https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=%238b5cf6&shape=circle) ![facebook](https://readmecodegen.vercel.app/api/social-icon?name=facebook&bg=%238b5cf6&shape=circle) ![instagram](https://readmecodegen.vercel.app/api/social-icon?name=instagram&bg=%238b5cf6&shape=circle) ![youtube](https://readmecodegen.vercel.app/api/social-icon?name=youtube&bg=%238b5cf6&shape=circle) ![discord](https://readmecodegen.vercel.app/api/social-icon?name=discord&bg=%238b5cf6&shape=circle) ![telegram](https://readmecodegen.vercel.app/api/social-icon?name=telegram&bg=%238b5cf6&shape=circle) ![whatsapp](https://readmecodegen.vercel.app/api/social-icon?name=whatsapp&bg=%238b5cf6&shape=circle) ![slack](https://readmecodegen.vercel.app/api/social-icon?name=slack&bg=%238b5cf6&shape=circle)

#### Rectangular Backgrounds (Default - No shape parameter needed)

![github](https://readmecodegen.vercel.app/api/social-icon?name=github&bg=%238b5cf6) ![twitter](https://readmecodegen.vercel.app/api/social-icon?name=twitter&bg=%238b5cf6) ![linkedin](https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=%238b5cf6) ![facebook](https://readmecodegen.vercel.app/api/social-icon?name=facebook&bg=%238b5cf6) ![instagram](https://readmecodegen.vercel.app/api/social-icon?name=instagram&bg=%238b5cf6) ![youtube](https://readmecodegen.vercel.app/api/social-icon?name=youtube&bg=%238b5cf6) ![discord](https://readmecodegen.vercel.app/api/social-icon?name=discord&bg=%238b5cf6) ![telegram](https://readmecodegen.vercel.app/api/social-icon?name=telegram&bg=%238b5cf6) ![whatsapp](https://readmecodegen.vercel.app/api/social-icon?name=whatsapp&bg=%238b5cf6) ![slack](https://readmecodegen.vercel.app/api/social-icon?name=slack&bg=%238b5cf6)

### Code & Development Icons

#### Default (Brand Colors, Transparent Background)

![javascript](https://readmecodegen.vercel.app/api/social-icon?name=javascript) ![python](https://readmecodegen.vercel.app/api/social-icon?name=python) ![java](https://readmecodegen.vercel.app/api/social-icon?name=java) ![html5](https://readmecodegen.vercel.app/api/social-icon?name=html5) ![css3](https://readmecodegen.vercel.app/api/social-icon?name=css3) ![react](https://readmecodegen.vercel.app/api/social-icon?name=react) ![node](https://readmecodegen.vercel.app/api/social-icon?name=node) ![typescript](https://readmecodegen.vercel.app/api/social-icon?name=typescript) ![docker](https://readmecodegen.vercel.app/api/social-icon?name=docker) ![git](https://readmecodegen.vercel.app/api/social-icon?name=git)

#### Circular Backgrounds (shape=circle)

![javascript](https://readmecodegen.vercel.app/api/social-icon?name=javascript&bg=%238b5cf6&shape=circle) ![python](https://readmecodegen.vercel.app/api/social-icon?name=python&bg=%238b5cf6&shape=circle) ![java](https://readmecodegen.vercel.app/api/social-icon?name=java&bg=%238b5cf6&shape=circle) ![html5](https://readmecodegen.vercel.app/api/social-icon?name=html5&bg=%238b5cf6&shape=circle) ![css3](https://readmecodegen.vercel.app/api/social-icon?name=css3&bg=%238b5cf6&shape=circle) ![react](https://readmecodegen.vercel.app/api/social-icon?name=react&bg=%238b5cf6&shape=circle) ![node](https://readmecodegen.vercel.app/api/social-icon?name=node&bg=%238b5cf6&shape=circle) ![typescript](https://readmecodegen.vercel.app/api/social-icon?name=typescript&bg=%238b5cf6&shape=circle) ![docker](https://readmecodegen.vercel.app/api/social-icon?name=docker&bg=%238b5cf6&shape=circle) ![git](https://readmecodegen.vercel.app/api/social-icon?name=git&bg=%238b5cf6&shape=circle)

#### Rectangular Backgrounds (Default - No shape parameter needed)

![javascript](https://readmecodegen.vercel.app/api/social-icon?name=javascript&bg=%238b5cf6) ![python](https://readmecodegen.vercel.app/api/social-icon?name=python&bg=%238b5cf6) ![java](https://readmecodegen.vercel.app/api/social-icon?name=java&bg=%238b5cf6) ![html5](https://readmecodegen.vercel.app/api/social-icon?name=html5&bg=%238b5cf6) ![css3](https://readmecodegen.vercel.app/api/social-icon?name=css3&bg=%238b5cf6) ![react](https://readmecodegen.vercel.app/api/social-icon?name=react&bg=%238b5cf6) ![node](https://readmecodegen.vercel.app/api/social-icon?name=node&bg=%238b5cf6) ![typescript](https://readmecodegen.vercel.app/api/social-icon?name=typescript&bg=%238b5cf6) ![docker](https://readmecodegen.vercel.app/api/social-icon?name=docker&bg=%238b5cf6) ![git](https://readmecodegen.vercel.app/api/social-icon?name=git&bg=%238b5cf6)

### Utility Icons

#### Default (Brand Colors, Transparent Background)

![search](https://readmecodegen.vercel.app/api/social-icon?name=search) ![settings](https://readmecodegen.vercel.app/api/social-icon?name=settings) ![download](https://readmecodegen.vercel.app/api/social-icon?name=download) ![upload](https://readmecodegen.vercel.app/api/social-icon?name=upload) ![edit](https://readmecodegen.vercel.app/api/social-icon?name=edit) ![delete](https://readmecodegen.vercel.app/api/social-icon?name=delete) ![add](https://readmecodegen.vercel.app/api/social-icon?name=add) ![close](https://readmecodegen.vercel.app/api/social-icon?name=close) ![menu](https://readmecodegen.vercel.app/api/social-icon?name=menu) ![home](https://readmecodegen.vercel.app/api/social-icon?name=home)

#### Circular Backgrounds (shape=circle)

![search](https://readmecodegen.vercel.app/api/social-icon?name=search&bg=%238b5cf6&shape=circle) ![settings](https://readmecodegen.vercel.app/api/social-icon?name=settings&bg=%238b5cf6&shape=circle) ![download](https://readmecodegen.vercel.app/api/social-icon?name=download&bg=%238b5cf6&shape=circle) ![upload](https://readmecodegen.vercel.app/api/social-icon?name=upload&bg=%238b5cf6&shape=circle) ![edit](https://readmecodegen.vercel.app/api/social-icon?name=edit&bg=%238b5cf6&shape=circle) ![delete](https://readmecodegen.vercel.app/api/social-icon?name=delete&bg=%238b5cf6&shape=circle) ![add](https://readmecodegen.vercel.app/api/social-icon?name=add&bg=%238b5cf6&shape=circle) ![close](https://readmecodegen.vercel.app/api/social-icon?name=close&bg=%238b5cf6&shape=circle) ![menu](https://readmecodegen.vercel.app/api/social-icon?name=menu&bg=%238b5cf6&shape=circle) ![home](https://readmecodegen.vercel.app/api/social-icon?name=home&bg=%238b5cf6&shape=circle)

#### Rectangular Backgrounds (Default - No shape parameter needed)

![search](https://readmecodegen.vercel.app/api/social-icon?name=search&bg=%238b5cf6) ![settings](https://readmecodegen.vercel.app/api/social-icon?name=settings&bg=%238b5cf6) ![download](https://readmecodegen.vercel.app/api/social-icon?name=download&bg=%238b5cf6) ![upload](https://readmecodegen.vercel.app/api/social-icon?name=upload&bg=%238b5cf6) ![edit](https://readmecodegen.vercel.app/api/social-icon?name=edit&bg=%238b5cf6) ![delete](https://readmecodegen.vercel.app/api/social-icon?name=delete&bg=%238b5cf6) ![add](https://readmecodegen.vercel.app/api/social-icon?name=add&bg=%238b5cf6) ![close](https://readmecodegen.vercel.app/api/social-icon?name=close&bg=%238b5cf6) ![menu](https://readmecodegen.vercel.app/api/social-icon?name=menu&bg=%238b5cf6) ![home](https://readmecodegen.vercel.app/api/social-icon?name=home&bg=%238b5cf6)

### Symbol Icons

#### Default (Brand Colors, Transparent Background)

![palette](https://readmecodegen.vercel.app/api/social-icon?name=palette) ![star](https://readmecodegen.vercel.app/api/social-icon?name=star) ![heart](https://readmecodegen.vercel.app/api/social-icon?name=heart) ![check](https://readmecodegen.vercel.app/api/social-icon?name=check) ![warning](https://readmecodegen.vercel.app/api/social-icon?name=warning) ![info](https://readmecodegen.vercel.app/api/social-icon?name=info) ![error](https://readmecodegen.vercel.app/api/social-icon?name=error) ![success](https://readmecodegen.vercel.app/api/social-icon?name=success) ![question](https://readmecodegen.vercel.app/api/social-icon?name=question) ![lightbulb](https://readmecodegen.vercel.app/api/social-icon?name=lightbulb)

#### Circular Backgrounds (shape=circle)

![palette](https://readmecodegen.vercel.app/api/social-icon?name=palette&bg=%238b5cf6&shape=circle) ![star](https://readmecodegen.vercel.app/api/social-icon?name=star&bg=%238b5cf6&shape=circle) ![heart](https://readmecodegen.vercel.app/api/social-icon?name=heart&bg=%238b5cf6&shape=circle) ![check](https://readmecodegen.vercel.app/api/social-icon?name=check&bg=%238b5cf6&shape=circle) ![warning](https://readmecodegen.vercel.app/api/social-icon?name=warning&bg=%238b5cf6&shape=circle) ![info](https://readmecodegen.vercel.app/api/social-icon?name=info&bg=%238b5cf6&shape=circle) ![error](https://readmecodegen.vercel.app/api/social-icon?name=error&bg=%238b5cf6&shape=circle) ![success](https://readmecodegen.vercel.app/api/social-icon?name=success&bg=%238b5cf6&shape=circle) ![question](https://readmecodegen.vercel.app/api/social-icon?name=question&bg=%238b5cf6&shape=circle) ![lightbulb](https://readmecodegen.vercel.app/api/social-icon?name=lightbulb&bg=%238b5cf6&shape=circle)

#### Rectangular Backgrounds (Default - No shape parameter needed)

![palette](https://readmecodegen.vercel.app/api/social-icon?name=palette&bg=%238b5cf6) ![star](https://readmecodegen.vercel.app/api/social-icon?name=star&bg=%238b5cf6) ![heart](https://readmecodegen.vercel.app/api/social-icon?name=heart&bg=%238b5cf6) ![check](https://readmecodegen.vercel.app/api/social-icon?name=check&bg=%238b5cf6) ![warning](https://readmecodegen.vercel.app/api/social-icon?name=warning&bg=%238b5cf6) ![info](https://readmecodegen.vercel.app/api/social-icon?name=info&bg=%238b5cf6) ![error](https://readmecodegen.vercel.app/api/social-icon?name=error&bg=%238b5cf6) ![success](https://readmecodegen.vercel.app/api/social-icon?name=success&bg=%238b5cf6) ![question](https://readmecodegen.vercel.app/api/social-icon?name=question&bg=%238b5cf6) ![lightbulb](https://readmecodegen.vercel.app/api/social-icon?name=lightbulb&bg=%238b5cf6)

### Dark Theme Examples

#### Social Icons (Dark Theme)

![github](https://readmecodegen.vercel.app/api/social-icon?name=github&theme=dark) ![twitter](https://readmecodegen.vercel.app/api/social-icon?name=twitter&theme=dark) ![linkedin](https://readmecodegen.vercel.app/api/social-icon?name=linkedin&theme=dark) ![react](https://readmecodegen.vercel.app/api/social-icon?name=react&theme=dark) ![node](https://readmecodegen.vercel.app/api/social-icon?name=node&theme=dark)

#### Code Icons (Dark Theme with Circular Backgrounds)

![javascript](https://readmecodegen.vercel.app/api/social-icon?name=javascript&bg=%238b5cf6&theme=dark&shape=circle) ![python](https://readmecodegen.vercel.app/api/social-icon?name=python&bg=%238b5cf6&theme=dark&shape=circle) ![typescript](https://readmecodegen.vercel.app/api/social-icon?name=typescript&bg=%238b5cf6&theme=dark&shape=circle) ![docker](https://readmecodegen.vercel.app/api/social-icon?name=docker&bg=%238b5cf6&theme=dark&shape=circle) ![git](https://readmecodegen.vercel.app/api/social-icon?name=git&bg=%238b5cf6&theme=dark&shape=circle)

---

## How to Find Icon Names

- Use the icon picker within the application's UI.
- Alternatively, inspect the registry files in `/src/app/icons/components/registries/`.

---

## Advanced Usage

- **Combine parameters:** `https://readmecodegen.vercel.app/api/social-icon?name=github&size=48&bg=%23000&theme=dark&shape=circle`
- **Transparent backgrounds:** `https://readmecodegen.vercel.app/api/social-icon?name=twitter&bg=transparent`
- **Custom brand color:** `https://readmecodegen.vercel.app/api/social-icon?name=linkedin&color=0077b5`
- **GitHub-style black icon:** `https://readmecodegen.vercel.app/api/social-icon?name=github&theme=github`
- **Circular background with custom color:** `https://readmecodegen.vercel.app/api/social-icon?name=react&bg=%2361dafb&shape=circle&size=40`
- **Rectangular background with dark theme:** `https://readmecodegen.vercel.app/api/social-icon?name=node&bg=%23339933&theme=dark&size=36`

---

## Best Practices & Tips

- Use only the parameters you need—shorter URLs are cleaner.
- Always use the correct icon name (see above).
- For clickable icons, wrap the markdown image in a link.
- Use `size` to ensure consistent icon sizing throughout your README.
- Use `theme` to optimize contrast with your background.
- Use `shape=circle` for modern, clean designs. For rectangular backgrounds, simply don't include the shape parameter.
- The `shape` parameter only works when a background color is specified.
- Circular backgrounds work well with social media icons and modern UI designs.
- Rectangular backgrounds are better for technical icons and structured documentation.

---

## Troubleshooting

- **Icon not showing?** Double-check the icon name and parameter spelling.
- **Wrong color?** Ensure you are not overriding the default color with an unintended `color` parameter.
- **Background shape not working?** Make sure you've specified a background color (`bg` parameter) - shapes only apply with colored backgrounds.
- **Hydration error?** Use absolute URLs with your domain for maximum compatibility.
- **SVG not rendering?** Some platforms might block external SVGs. If necessary, download the SVG and host it locally.

**Q: Why isn't my background shape working?**
A: The `shape` parameter only works when you specify a background color using the `bg` parameter. With transparent backgrounds, the shape is ignored.

---

## 🚀 Try the Icon Generator Now!

Ready to create beautiful, customizable icons for your projects? Visit our live icon generator application to explore all available icons and create your own custom designs.

**[🎨 Icon Generator Tool →](https://readmecodegen.vercel.app/icons)**

### What You'll Find:

- **Interactive Icon Picker**: Browse through hundreds of social, code, utility, and symbol icons
- **Real-time Customization**: Adjust colors, sizes, backgrounds, and shapes instantly
- **Live Preview**: See your changes in real-time before copying the code
- **Multiple Export Formats**: Get markdown, HTML, or direct API URLs
- **No Registration Required**: Start generating icons immediately

### Perfect For:

- GitHub README files
- Documentation sites
- Blog posts and articles
- Portfolio websites
- Social media profiles
- Technical documentation

**[Start Creating Icons Now →](https://readmecodegen.vercel.app/icons)**

---

## Contributing & Requesting Icons

- To request a new icon, open an issue or submit a pull request (PR) with the icon name and a reference to its SVG or FontAwesome representation.
- To contribute, review the registry files and adhere to the existing structure.

---

## FAQ

**Q: Can I use these icons outside of GitHub?**
A: Yes! They are compatible with any platform that supports SVG or markdown images.

**Q: How do I find the correct icon name?**
A: Use the icon picker in the app or inspect the registry files.

**Q: Can I use custom SVGs?**
A: Yes, contribute your SVG to the registry or request its addition via an issue.

**Q: Are these icons free to use?**
A: Yes, they are free for both personal and commercial projects (refer to the license details).

**Q: When should I use circular vs rectangular backgrounds?**
A: Use circular backgrounds for modern, clean designs and social media icons. Use rectangular backgrounds for technical icons and structured documentation layouts.

**Q: Why isn't my background shape working?**
A: The `shape` parameter only works when you specify a background color using the `bg` parameter. With transparent backgrounds, the shape is ignored.

---

For further information, consult the application's UI or contact the maintainer.
