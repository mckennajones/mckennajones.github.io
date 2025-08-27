# McKenna Jones - Personal Website

A minimal personal website built with Hugo and custom HTML/CSS templates. Inspired by simple, text-focused design.

## Development

### Prerequisites
- [Hugo](https://gohugo.io/installation/) (v0.148.2 or later)

### Getting Started

1. **Start the development server:**
   ```bash
   hugo serve --buildDrafts
   ```
   Site will be available at http://localhost:1313/

2. **Build for production:**
   ```bash
   hugo
   ```
   Static files will be generated in the `public/` directory.

### Adding Content

- **New blog post:** Create a markdown file in `content/posts/`
  ```bash
  hugo new content posts/my-new-post.md
  ```

- **New page:** Create a markdown file in `content/`
  ```bash
  hugo new content about.md
  ```

- **Images:** Place images in `static/images/` and reference with `/images/filename.jpg`
- **Photos:** Add photos to `static/photos/` - they'll automatically appear on the `/photos` page

### Site Structure

```
├── content/           # Markdown content files
│   ├── posts/        # Blog posts
│   ├── about.md      # About page
│   ├── photos.md     # Photos page
│   └── _index.md     # Homepage content
├── layouts/          # HTML templates
│   ├── _default/     # Default templates
│   └── index.html    # Homepage template
├── static/           # Static assets
│   ├── style.css     # Main stylesheet
│   ├── images/       # General image files
│   └── photos/       # Photo gallery images
└── hugo.toml         # Hugo configuration
```

### Customization

- **Styling:** Edit `static/style.css` for visual changes
- **Layout:** Modify templates in `layouts/` directory
- **Site config:** Update `hugo.toml` for site-wide settings

### Deployment

The site is configured for deployment to [mckennajones.com](https://mckennajones.com).
