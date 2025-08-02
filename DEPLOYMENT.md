# Deployment Guide for Flash Card Learning System

## 🚀 GitHub Pages Deployment

### Prerequisites
- GitHub account
- Git installed on your computer (optional for web interface deployment)

### Method 1: Web Interface (Easiest)

#### Step 1: Create Repository
1. Go to [GitHub](https://github.com) and sign in
2. Click **"New"** repository
3. Name it `flash-card` (or any name you prefer)
4. Make it **Public** (required for free GitHub Pages)
5. Click **"Create repository"**

#### Step 2: Upload Files
1. Click **"uploading an existing file"**
2. Drag and drop all files from your flash-card folder
3. Or use **"choose your files"** to select:
   - `index.html`
   - `README.md`
   - `CONTENT_GUIDE.md`
   - The entire `content/` folder
4. Write commit message: "Initial flash card system"
5. Click **"Commit changes"**

#### Step 3: Enable GitHub Pages
1. Go to **Settings** tab in your repository
2. Scroll down to **"Pages"** in the left sidebar
3. Under **"Source"**, select **"Deploy from a branch"**
4. Choose **"main"** branch
5. Keep **"/ (root)"** selected
6. Click **"Save"**

#### Step 4: Access Your Site
- Your site will be available at: `https://yourusername.github.io/flash-card`
- It may take 5-10 minutes to become available
- You'll see a green checkmark when deployment is complete

### Method 2: Git Command Line

```bash
# Create and navigate to your project folder
mkdir flash-card
cd flash-card

# Initialize git repository
git init

# Add your files (copy index.html, content/, etc. here first)

# Add files to git
git add .
git commit -m "Initial flash card learning system"

# Connect to GitHub repository (replace with your username/repo)
git remote add origin https://github.com/yourusername/flash-card.git

# Push to GitHub
git push -u origin main

# Enable GitHub Pages via GitHub web interface (follow Method 1, Step 3)
```

### Method 3: GitHub CLI (Advanced)

```bash
# Create repository
gh repo create flash-card --public --source=. --remote=origin --push

# Enable GitHub Pages
gh api repos/:owner/:repo/pages --method POST --field source.branch=main --field source.path=/
```

## 🔧 Customization for Your Domain

### Custom Domain Setup
1. In your repository settings, scroll to **"Pages"**
2. Under **"Custom domain"**, enter your domain (e.g., `flashcards.yoursite.com`)
3. Add a `CNAME` file to your repository with your domain name
4. Configure your DNS provider to point to GitHub Pages

### CNAME File Example
```
flashcards.yoursite.com
```

## 📁 File Organization for Deployment

### Required Structure
```
your-repository/
├── index.html          # Main application (required)
├── README.md          # Documentation
├── CONTENT_GUIDE.md   # Content creation guide
└── content/           # All learning content
    ├── primary1/
    ├── primary2/
    └── ...
```

### Optional Files
- `CNAME` - For custom domain
- `_config.yml` - Jekyll configuration (if using Jekyll)
- `.gitignore` - To exclude files from version control
- `LICENSE` - License information

## 🌐 Alternative Deployment Options

### Netlify
1. Connect your GitHub repository to [Netlify](https://netlify.com)
2. Set build command to: (none)
3. Set publish directory to: `/`
4. Deploy automatically on every commit

### Vercel
1. Connect your GitHub repository to [Vercel](https://vercel.com)
2. Framework preset: Other
3. Root directory: `./`
4. Deploy automatically

### Traditional Web Hosting
1. Upload all files to your web hosting provider
2. Ensure `index.html` is in the root directory
3. Ensure proper file permissions (644 for files, 755 for directories)

## ✅ Pre-Deployment Checklist

### Content Validation
- [ ] All `chapters.json` files are valid JSON
- [ ] All `cards.json` files are valid JSON
- [ ] File paths in JSON use forward slashes (`/`)
- [ ] Audio/image files exist or have fallback handling
- [ ] No broken links or missing files

### Testing
- [ ] Test on Chrome, Firefox, Safari, Edge
- [ ] Test on mobile devices (iOS/Android)
- [ ] Test all three card types (text, audio, full)
- [ ] Test chapter navigation and progression
- [ ] Test keyboard navigation (Tab, Space, Arrow keys)
- [ ] Test with slow internet connection

### Performance
- [ ] Images optimized for web (under 500KB each)
- [ ] Audio files compressed (under 1MB each)
- [ ] Total repository size under GitHub's 1GB limit
- [ ] No unnecessary large files included

### Accessibility
- [ ] All images have alt text
- [ ] Proper heading hierarchy (h1, h2, h3)
- [ ] Keyboard navigation works
- [ ] Screen reader compatible
- [ ] Color contrast meets WCAG standards

## 🐛 Common Deployment Issues

### Issue: 404 Error on GitHub Pages
**Solution:**
- Check that `index.html` is in the root directory
- Ensure repository is public
- Wait 5-10 minutes after enabling Pages

### Issue: Content Not Loading
**Solution:**
- Check browser console for errors
- Verify JSON file syntax
- Ensure file paths use relative URLs
- Check case sensitivity in file names

### Issue: Audio/Images Not Working
**Solution:**
- Verify file paths in JSON match actual file locations
- Check file extensions are correct
- Ensure files are uploaded to GitHub
- Test file access directly via URL

### Issue: Mobile Layout Problems
**Solution:**
- Test on actual mobile devices
- Check viewport meta tag is present
- Verify CSS breakpoints are working
- Use browser developer tools mobile simulation

## 📊 Monitoring and Analytics

### GitHub Pages Analytics
- View traffic in repository **Insights** → **Traffic**
- Monitor popular content and user behavior
- Track geographic distribution of users

### Adding Google Analytics
Add to `<head>` section of `index.html`:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_TRACKING_ID');
</script>
```

### User Feedback Collection
- Add GitHub Issues link for bug reports
- Include contact email in README
- Consider adding feedback form

## 🔒 Security Considerations

### GitHub Pages Security
- GitHub Pages serves only static content (secure by default)
- HTTPS is automatically enabled
- No server-side code execution
- No database security concerns

### Content Security
- Review all content for appropriateness
- Ensure no sensitive information in public repository
- Use only royalty-free or properly licensed media
- Consider content moderation for user-generated additions

## 📈 Scaling and Growth

### Adding More Content
1. Create new level/subject folders
2. Add corresponding `chapters.json` files
3. Create cards and media files
4. Test thoroughly before deployment
5. Update documentation

### Performance Optimization
- Use WebP images where supported
- Implement lazy loading for images
- Consider service worker for offline support
- Optimize for Core Web Vitals

### Feature Enhancement
- Add progress tracking with localStorage
- Implement spaced repetition algorithms
- Create teacher dashboard functionality
- Add print-friendly layouts

---

**🎯 Ready to Deploy?**

1. Follow Method 1 above for easiest deployment
2. Test your live site thoroughly
3. Share with students and gather feedback
4. Iterate and improve based on usage

**Need Help?** Open an issue on GitHub or refer to the troubleshooting section in README.md.