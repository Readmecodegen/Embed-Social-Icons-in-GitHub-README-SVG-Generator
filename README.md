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
- [5. `theme` (optional)](#5-theme-optional)
- [Usage Examples](#usage-examples)
- [Default Icon (Brand Color, 32px, Transparent)](#default-icon-brand-color-32px-transparent)
- [Custom Color & Size](#custom-color--size)
- [Dark Theme](#dark-theme)
- [Solid Background](#solid-background)
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

It addresses the common problem of inconsistent, low-resolution, or difficult-to-locate icons by providing a centralized, adaptable API for social media, code-related, utility, and symbolic icons. Features such as theme switching, background customization, and the ability to create clickable icons make it ideal for both developers and non-technical users.



# Markdown Icon Generator API Documentation



## Overview
The Markdown Icon Generator API delivers clean, customizable SVG icons perfect for enhancing GitHub READMEs, documentation, blogs, and more. It supports a wide range of icons, including social media, code, utility, and symbols, with accurate brand colors, themes, backgrounds, and flexible sizing options. The API is designed for ease of use, featuring short, readable URLs that simplify integration.



## API Endpoint
The base URL for accessing the Social Icon API is:

```
https://readmecodegen.vercel.app/api/social-icon
```

Think of this as the address you'll use to request icons. Instead of a webpage, the API sends back an icon in SVG format. Include this link in your markdown or HTML code to display the icons.



## Parameters
| Parameter | Type     | Required | Description                                                                 | Example Value       |
| --------- | -------- | -------- | --------------------------------------------------------------------------- | ------------------- |
| `name`      | string   | Yes      | The icon's identifier (see available icons below)                             | `github`, `twitter` |
| `color`     | hex      | No       | Hex color code (without `#`) for the icon. Defaults to brand color or theme logic. | `1da1f2`, `ff0000`  |
| `size`      | int      | No       | Icon size in pixels. Default: `32`                                          | `48`, `64`          |
| `bg`        | hex/word | No       | Background color (hex or `transparent`). Default: `transparent`             | `ffffff`, `000000`  |
| `theme`     | string   | No       | Icon theme: `light`, `dark`, `github`. Default: `light`                     | `dark`              |

---



## Parameter Details & Use Cases



### 1. `name` (required)
- **What it is:** The unique identifier for the icon you want to display. This is like the icon's name, such as `github`, `twitter`, `linkedin`, or `javascript`.

- **Why we need it:** The API uses this parameter to determine which icon to generate.

- **How to use it:** Append `?name=` followed by the icon's name to the API endpoint. For example:
`https://readmecodegen.vercel.app/api/social-icon?name=github`

This tells the API to generate the GitHub icon.



### 2. `color` (Optional)
- **What it is:**  A hex color code (without the `#`) to customize the icon's color.

- **Why use it?:** By default, the icon uses a brand-specific color (light theme), white (dark theme), or black (GitHub theme). This parameter allows you to override the default color with a color of your choice.

- **How to use it:**
`https://readmecodegen.vercel.app/api/social-icon?name=twitter&color=ff0000`

In this example, `ff0000` sets the Twitter icon's color to red.

- **When to use it:**  Use this parameter to match the icon's color to your website's color scheme or create a specific visual effect.



### 3. `size` (optional)
- **What it is:** A numerical value representing the icon's size in pixels.
- **Why use it?:**  It allows you to control the dimensions of the icon. The default size is 32 pixels.
- **How to use it:**
`https://readmecodegen.vercel.app/api/social-icon?name=github&size=64`
- **When to use it:** Use this parameter to adjust the icon's size for optimal display within your README or other design.



### 4. `bg` (optional)
- **What it is:**  Specifies the background color for the icon. You can use a hex color code (e.g., `ffffff` for white, without the `#`) or the keyword `transparent` for no background.

- **Why it's useful:** It helps the icon stand out, especially if your website or README already has a background color.

- **How to use it:** Add `&bg=` followed by your color choice to the URL. For example:
`https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=ffffff` adds a white background to the LinkedIn icon.

- **When to use it:**  Use this parameter when the icon's default appearance doesn't provide enough contrast against your background or when you want to integrate the icon seamlessly into your page design.



### 5. `theme` (optional)
- **What:**  Accepts values: `light`, `dark`, or `github`.
- **Why:**  Quickly switch the icon color for different backgrounds:
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

![GitHub](https://readmecodegen.vercel.app/api/social-icon?name=github)



### Custom Color & Size
```markdown
![Twitter Blue](https://readmecodegen.vercel.app/api/social-icon?name=twitter&color=1da1f2&size=48)
```



### Dark Theme
```markdown
![GitHub](https://readmecodegen.vercel.app/api/social-icon?name=github&theme=dark)
```



### Solid Background
```markdown
![LinkedIn](https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=ffffff)
```



### Clickable Icon (Profile Link)
```markdown
[![GitHub](https://readmecodegen.vercel.app/api/social-icon?name=github)](https://github.com/yourusername)
```



### HTML Usage
```html
<img
src="https://readmecodegen.vercel.app/api/social-icon?name=twitter&size=40"
alt="Twitter"
/>
```

---



## Brand Color Logic
- **light** (default): Uses the official brand color for each icon.
- **dark**: Uses white (`#ffffff`) for all icons.
- **github**: Uses black (`#000000`) for all icons.
- If `color` is specified, it overrides the above logic.

---



## Theme & Background Handling
- Transparent backgrounds are applied by default.
- When a solid background color is set, a 2px padding is automatically added to the icon for improved visual balance.
- For optimal visual results, use `theme=dark` on dark backgrounds and `theme=light` on light backgrounds.

---



## Why Each Feature Exists
- **Brand color logic:** Ensures icons maintain an authentic and professional appearance by default.
- **Theme switching:** Guarantees icons are readable across various background colors (light, dark, GitHub).
- **Background support:** Allows you to seamlessly integrate icons into your website or README's style.
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



## How to Find Icon Names
- Use the icon picker within the application's UI.
- Alternatively, inspect the registry files in `/src/app/icons/components/registries/`.

---



## Advanced Usage
- **Combine parameters:** `https://readmecodegen.vercel.app/api/social-icon?name=github&size=48&bg=000&theme=dark`
- **Transparent backgrounds:** `https://readmecodegen.vercel.app/api/social-icon?name=twitter&bg=transparent`
- **Custom brand color:** `https://readmecodegen.vercel.app/api/social-icon?name=linkedin&color=0077b5`
- **GitHub-style black icon:** `https://readmecodegen.vercel.app/api/social-icon?name=github&theme=github`

---



## Best Practices & Tips
- Use only the parameters you need—shorter URLs are cleaner.
- Always use the correct icon name (see above).
- For clickable icons, wrap the markdown image in a link.
- Use `size` to ensure consistent icon sizing throughout your README.
- Use `theme` to optimize contrast with your background.

---



## Troubleshooting
- **Icon not showing?** Double-check the icon name and parameter spelling.
- **Wrong color?** Ensure you are not overriding the default color with an unintended `color` parameter.
- **Hydration error?** Use absolute URLs with your domain for maximum compatibility.
- **SVG not rendering?** Some platforms might block external SVGs. If necessary, download the SVG and host it locally.

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

---

For further information, consult the application's UI or contact the maintainer.