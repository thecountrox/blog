# Blog

Static blog based on [Zola](https://www.getzola.org/)

---

## 🚀 Deployment

This blog is set up with automated deployment workflows:

### GitHub Pages (Recommended)
The site automatically deploys to GitHub Pages when you push to the `main` or `master` branch.

**Step-by-Step Setup:**

1. **Merge this PR** to your `main` or `master` branch

2. **Enable GitHub Pages:**
   - Go to your repository on GitHub
   - Click **Settings** (top menu)
   - Click **Pages** (left sidebar under "Code and automation")
   - Under **Build and deployment**:
     - Set **Source** to "**GitHub Actions**"
   - Click **Save** (if button appears)

3. **Trigger Deployment:**
   - Option A: The workflow will automatically run when you merge/push to main
   - Option B: Manually trigger from **Actions** tab → **Deploy to GitHub Pages** → **Run workflow**

4. **Access Your Site:**
   - After deployment completes (~1-2 minutes), your site will be available at:
     - `https://thecountrox.github.io/blog/` (default)
     - `https://blog.thecount.eu.org/` (if custom domain DNS is configured)

5. **Custom Domain (Optional):**
   - Your CNAME file is already configured for `blog.thecount.eu.org`
   - Add DNS records at your domain provider:
     - Type: `CNAME`, Name: `blog`, Value: `thecountrox.github.io`
   - GitHub will automatically detect the CNAME file and configure the custom domain

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