# Embed-Social-Icons-in-GitHub-README-SVG-Generator

## Project Purpose & Feature Rationale

The Markdown Icon Generator API was built to make it easy for anyone to embed high-quality, brand-accurate icons in markdown (e.g., GitHub READMEs, docs, blogs) with full customization—no design skills or manual SVG editing required. It solves the problem of inconsistent, low-quality, or hard-to-find icons by providing a single, flexible API for social, code, utility, and symbol icons. Features like theme switching, background support, and clickable icons make it perfect for both developers and non-coders.

---

# Markdown Icon Generator API Documentation

## Overview

The Markdown Icon Generator API provides clean, customizable SVG icons for use in GitHub READMEs, documentation, blogs, and more. It supports social, code, utility, and symbol icons with brand-accurate colors, themes, backgrounds, and flexible sizing. The API is designed for short, readable URLs and easy integration.

---

## API Endpoint

```
https://readmecodegen.vercel.app/api/social-icon
```

---

## Parameters

| Parameter | Type     | Required | Description                                                                 | Example Value       |
| --------- | -------- | -------- | --------------------------------------------------------------------------- | ------------------- |
| name      | string   | Yes      | The icon key/name (see available icons below)                               | `github`, `twitter` |
| color     | hex      | No       | Hex color (without #) for the icon. Defaults to brand color or theme logic. | `1da1f2`, `ff0000`  |
| size      | int      | No       | Icon size in pixels. Default: `32`                                          | `48`, `64`          |
| bg        | hex/word | No       | Background color (hex or `transparent`). Default: `transparent`             | `ffffff`, `000000`  |
| theme     | string   | No       | Icon theme: `light`, `dark`, `github`. Default: `light`                     | `dark`              |

---

## Parameter Details & Use Cases

### 1. `name` (required)

- **What:** The unique key for the icon you want (e.g., `github`, `twitter`, `linkedin`, `javascript`, etc.).
- **Why:** Tells the API which icon to render.
- **How to use:**  
  `https://readmecodegen.vercel.app/api/social-icon?name=github`

### 2. `color` (optional)

- **What:** Hex color code (no `#`).
- **Why:** Override the default color (brand color for `light`, white for `dark`, black for `github`).
- **How to use:**  
  `https://readmecodegen.vercel.app/api/social-icon?name=twitter&color=ff0000`
- **When:** Use if you want a custom color for the icon.

### 3. `size` (optional)

- **What:** Integer (pixels).
- **Why:** Change the icon’s size (default is 32px).
- **How to use:**  
  `https://readmecodegen.vercel.app/api/social-icon?name=github&size=64`
- **When:** Use to fit your icon to your design.

### 4. `bg` (optional)

- **What:** Hex color (no `#`) or the word `transparent`.
- **Why:** Set the background color behind the icon (default is transparent).
- **How to use:**  
  `https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=ffffff`
- **When:** Use for contrast, or to match your site’s background.

### 5. `theme` (optional)

- **What:** `light`, `dark`, or `github`.
- **Why:** Quickly switch the icon color for different backgrounds:
  - `light`: Brand color (default)
  - `dark`: White icon (for dark backgrounds)
  - `github`: Black icon (for GitHub-style backgrounds)
- **How to use:**  
  `https://readmecodegen.vercel.app/api/social-icon?name=github&theme=dark`
- **When:** Use to ensure icons are visible on any background.

---

## Usage Examples

### Default Icon (Brand Color, 32px, Transparent)

```markdown
![GitHub](https://readmecodegen.vercel.app/api/social-icon?name=github)
```

### Custom Color & Size

```markdown
![Twitter Blue](https://readmecodegen.vercel.app/api/social-icon?name=twitter&color=1da1f2&size=48)
```

### Dark Theme

```markdown
![GitHub Dark](https://readmecodegen.vercel.app/api/social-icon?name=github&theme=dark)
```

### Solid Background

```markdown
![LinkedIn on White](https://readmecodegen.vercel.app/api/social-icon?name=linkedin&bg=ffffff)
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

- **light** (default): Uses the official brand color for each icon
- **dark**: Uses white (`#ffffff`) for all icons
- **github**: Uses black (`#000000`) for all icons
- If `color` is provided, it overrides the above

---

## Theme & Background Handling

- Transparent backgrounds by default
- When a solid background is set, a 2px padding is automatically applied for visual balance
- For best results, use `theme=dark` on dark backgrounds and `theme=light` on light backgrounds

---

## Why Each Feature Exists

- **Brand color logic:** Ensures icons look authentic and professional by default.
- **Theme switching:** Makes icons readable on any background (light, dark, GitHub).
- **Background support:** Lets you match icons to your site or README style.
- **Size parameter:** Ensures icons fit any layout or design.
- **Custom color:** Gives you full creative control.
- **Short, clean URLs:** Easy to copy, paste, and maintain.
- **Clickable icons:** Perfect for linking to social profiles in markdown.
- **Multiple icon categories:** Social, code, utility, and symbol icons for all use cases.

---

## Available Icon Categories & Names

- **Social:** github, twitter, linkedin, facebook, instagram, x, ...
- **Code:** javascript, python, java, html5, css3, node, react, ...
- **Utility:** search, settings, ...
- **Symbol:** palette, ...

> For a full list, see the icon picker in the app UI or check the registry files in `/src/app/icons/components/registries/`.

---

## How to Find Icon Names

- Use the icon picker in your app UI.
- Or, check the registry files in `/src/app/icons/components/registries/`.

---

## Advanced Usage

- **Combine parameters:** `https://readmecodegen.vercel.app/api/social-icon?name=github&size=48&bg=000&theme=dark`
- **Transparent backgrounds:** `https://readmecodegen.vercel.app/api/social-icon?name=twitter&bg=transparent`
- **Custom brand color:** `https://readmecodegen.vercel.app/api/social-icon?name=linkedin&color=0077b5`
- **GitHub-style black icon:** `https://readmecodegen.vercel.app/api/social-icon?name=github&theme=github`

---

## Best Practices & Tips

- Use only the parameters you need—shorter URLs are cleaner
- Always use the correct icon name (see above)
- For clickable icons, wrap the markdown image in a link
- Use `size` for consistent icon sizing across your README
- Use `theme` to match your background for best contrast

---

## Troubleshooting

- **Icon not showing?** Check the icon name and parameter spelling
- **Wrong color?** Make sure you’re not overriding with a `color` param
- **Hydration error?** Use absolute URLs with your domain for best compatibility
- **SVG not rendering?** Some platforms may block external SVGs—download and host locally if needed

---

## Contributing & Requesting Icons

- To request a new icon, open an issue or PR with the icon name and SVG/FontAwesome reference
- To contribute, see the registry files and follow the existing structure

---

## FAQ

**Q: Can I use these icons outside GitHub?**  
A: Yes! They work anywhere that supports SVG or markdown images.

**Q: How do I find the right icon name?**  
A: Use the icon picker in the app or check the registry files.

**Q: Can I use custom SVGs?**  
A: Yes, contribute your SVG to the registry or request it via an issue.

**Q: Are these icons free to use?**  
A: Yes, for personal and commercial projects (see license).

---

For more, see the app UI or contact the maintainer.
