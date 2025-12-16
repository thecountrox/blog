# Blog

Static blog based on [Zola](https://www.getzola.org/)

---

## 🚀 Deployment

This blog is set up with automated deployment workflows:

### GitHub Pages (Recommended)
The site automatically deploys to GitHub Pages when you push to the `main` or `master` branch.

**Setup:**
1. Go to your repository Settings → Pages
2. Set Source to "GitHub Actions"
3. Push to main/master branch or trigger manually via Actions tab

### Docker Image
Alternatively, a Docker image is built and pushed to GitHub Container Registry.

**Setup:**
1. The workflow automatically builds and pushes the image
2. Pull and run the image:
   ```bash
   docker pull ghcr.io/thecountrox/blog:latest
   docker run -d -p 8080:80 ghcr.io/thecountrox/blog:latest
   ```

---

## 🛠️ Local Development

### Using Docker (Recommended)
Build the site:
```bash
docker run --rm -v $(pwd):/app -w /app \
  ghcr.io/getzola/zola:v0.19.2 build
```

Serve locally:
```bash
docker run --rm -p 1111:1111 -v $(pwd):/app -w /app \
  ghcr.io/getzola/zola:v0.19.2 serve --interface 0.0.0.0
```

### Using Native Zola
1. [Install Zola](https://www.getzola.org/documentation/getting-started/installation/)
2. Run `zola serve` for development
3. Run `zola build` to generate static files

---

## 📁 Project Structure

- `content/` - Blog posts and content
- `templates/` - HTML templates
- `static/` - Static assets (images, etc.)
- `sass/` - Stylesheets
- `config.toml` - Site configuration
- `public/` - Generated site (ignored in git)