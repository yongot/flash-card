# Flash Card Learning System

A responsive, static web application for educational flash cards targeting primary school students (grades 1-6). Built with pure HTML, CSS, and JavaScript - perfect for GitHub Pages deployment.

## 🚀 Quick Start

1. **Clone or download** this repository
2. **Open `index.html`** in your web browser
3. **Select level, subject, and chapter** to start learning
4. **Click cards to flip** and see answers

## 📁 Project Structure

```
flash-card/
├── index.html                     # Main application file
├── README.md                      # This file
├── CONTENT_GUIDE.md              # Content authoring guide
└── content/                      # All learning content
    ├── primary1/
    │   ├── english/
    │   │   ├── chapters.json     # Chapter list for Primary 1 English
    │   │   ├── chapter1-animals/
    │   │   │   ├── cards.json    # Flash cards for animals
    │   │   │   ├── audio/        # Audio files (MP3, WAV, OGG)
    │   │   │   └── images/       # Image files (JPG, PNG, WebP, GIF)
    │   │   ├── chapter2-colors/
    │   │   └── chapter3-numbers/
    │   ├── chinese/
    │   │   ├── chapters.json
    │   │   ├── chapter1-family/
    │   │   └── chapter2-food/
    │   └── malay/
    │       ├── chapters.json
    │       ├── chapter1-greetings/
    │       └── chapter2-school/
    ├── primary2/
    │   └── english/
    │       ├── chapters.json
    │       ├── chapter1-shapes/
    │       └── chapter2-weather/
    └── primary3-6/              # Extend with more levels
```

## ✨ Features

### 🎯 User Interface
- **Intuitive Selection**: Easy level, subject, and chapter selection
- **Responsive Design**: Works on mobile, tablet, and desktop
- **Smooth Animations**: Card flip animations and transitions
- **Progress Tracking**: Shows current position and chapter completion
- **Accessibility**: Keyboard navigation and screen reader support

### 📚 Flash Card Types

**1. Text Only Cards**
```json
{
  "type": "text",
  "front": "Cat",
  "back": "A small furry pet that says meow"
}
```

**2. Text + Audio Cards**
```json
{
  "type": "audio",
  "front": "Dog",
  "back": "A loyal animal that barks",
  "audio": "audio/dog.mp3"
}
```

**3. Text + Audio + Image Cards**
```json
{
  "type": "full",
  "front": "Bird",
  "back": "An animal that can fly",
  "audio": "audio/bird.mp3",
  "image": "images/bird.jpg"
}
```

### 🎮 Navigation & Controls
- **Card Flipping**: Click/tap cards or press Space
- **Navigation**: Previous/Next buttons or arrow keys
- **Chapter Progression**: Automatic next chapter suggestions
- **Audio Playback**: Built-in audio controls with error handling
- **Back to Selection**: Easy return to level/subject/chapter selection

## 🛠️ Adding Content

### 1. Create Chapter Structure
For a new level and subject:
```bash
mkdir -p content/primary3/science/chapter1-plants/{audio,images}
```

### 2. Create chapters.json
```json
{
  "chapters": [
    {
      "id": "chapter1-plants",
      "title": "Plants",
      "description": "Learn about different plants",
      "order": 1,
      "difficulty": "beginner"
    }
  ]
}
```

### 3. Create cards.json
```json
[
  {
    "type": "full",
    "front": "Rose",
    "back": "A beautiful flower with thorns",
    "audio": "audio/rose.mp3",
    "image": "images/rose.jpg"
  }
]
```

### 4. Add Media Files
- Place audio files in the `audio/` folder
- Place images in the `images/` folder
- Use relative paths in your JSON files

## 🌐 GitHub Pages Deployment

### Method 1: GitHub Interface
1. Fork/upload this repository to GitHub
2. Go to **Settings** → **Pages**
3. Select **Source**: Deploy from a branch
4. Choose **Branch**: main
5. Click **Save**
6. Your site will be available at: `https://yourusername.github.io/flash-card`

### Method 2: GitHub CLI
```bash
# Clone your repository
git clone https://github.com/yourusername/flash-card.git
cd flash-card

# Make changes
# ... add your content ...

# Deploy
git add .
git commit -m "Add flash card content"
git push origin main

# Enable GitHub Pages (one time only)
gh api repos/:owner/:repo --method PATCH --field has_pages=true
```

## 🔧 Customization

### Styling
The CSS is embedded in `index.html`. Key customization areas:

- **Colors**: Modify gradient backgrounds and button colors
- **Fonts**: Change the font-family in the `body` selector
- **Card Size**: Adjust `.card` height and dimensions
- **Animations**: Modify transition durations and effects

### Responsive Breakpoints
- **Mobile**: 480px and below
- **Tablet**: 768px and below
- **Desktop**: 1024px and above

### Audio Formats
Supported formats: MP3, WAV, OGG
- **MP3**: Best browser compatibility
- **WAV**: High quality, larger file size
- **OGG**: Good compression, modern browsers

### Image Formats
Supported formats: JPG, PNG, WebP, GIF
- **JPG**: Photos and complex images
- **PNG**: Images with transparency
- **WebP**: Modern format, best compression
- **GIF**: Animated images (use sparingly)

## 🎨 Accessibility Features

- **Keyboard Navigation**: Full keyboard support
- **Screen Readers**: Proper ARIA labels and roles
- **High Contrast**: Clear color distinctions
- **Focus Indicators**: Visible focus states
- **Semantic HTML**: Proper heading hierarchy
- **Alt Text**: Image descriptions

### Keyboard Shortcuts
- **Space**: Flip current card
- **Left Arrow**: Previous card
- **Right Arrow**: Next card
- **Tab**: Navigate through interface elements

## ⚡ Performance Tips

### File Size Optimization
- **Images**: Keep under 500KB each, optimize for web
- **Audio**: Use compressed formats, aim for under 1MB per file
- **Total Size**: GitHub Pages has a 1GB repository limit

### Loading Performance
- Images load lazily and have fallbacks
- Audio files load on demand
- JSON files are cached by the browser
- Smooth animations use CSS transforms

## 🐛 Troubleshooting

### Common Issues

**Cards not loading:**
- Check that `cards.json` file exists in the chapter folder
- Verify JSON syntax is valid
- Ensure file paths use forward slashes

**Audio not playing:**
- Confirm audio file exists and path is correct
- Check file format is supported (MP3, WAV, OGG)
- Test audio files in browser directly

**Images not displaying:**
- Verify image file exists and path is correct
- Check file format is supported (JPG, PNG, WebP, GIF)
- Ensure images are optimized and not too large

**Chapters not appearing:**
- Check that `chapters.json` exists in the subject folder
- Verify JSON syntax and structure
- Ensure chapter IDs match folder names

### Browser Compatibility
- **Modern browsers**: Chrome 80+, Firefox 75+, Safari 13+, Edge 80+
- **Mobile browsers**: iOS Safari 13+, Chrome Mobile 80+
- **Not supported**: Internet Explorer

### Development Testing
```bash
# Serve locally (Python 3)
python -m http.server 8000

# Serve locally (Node.js)
npx http-server -p 8000

# Open in browser
open http://localhost:8000
```

## 📖 Content Guidelines

### Best Practices
- **Clear language**: Age-appropriate vocabulary
- **Consistent structure**: Follow established patterns
- **Progressive difficulty**: Order chapters from easy to hard
- **Cultural sensitivity**: Inclusive and respectful content
- **Audio quality**: Clear pronunciation and good audio quality

### Chapter Organization
- **Thematic grouping**: Related concepts together
- **Logical progression**: Build on previous knowledge
- **Reasonable length**: 5-10 cards per chapter
- **Clear titles**: Descriptive chapter names

### Content Creation Tips
- **Test thoroughly**: Try all card types and media
- **Mobile first**: Design for smallest screens
- **Fallback content**: Always provide text alternatives
- **User feedback**: Test with actual students

## 🤝 Contributing

1. **Fork** the repository
2. **Create** a new branch for your feature
3. **Add** your content following the structure guidelines
4. **Test** thoroughly on different devices
5. **Submit** a pull request with clear description

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🎯 Roadmap

### Future Enhancements
- [ ] Progress tracking across sessions
- [ ] Multiple choice quiz mode
- [ ] Spaced repetition algorithms
- [ ] Offline support with service workers
- [ ] Print-friendly card layouts
- [ ] Content import/export tools
- [ ] Teacher dashboard for progress monitoring

### Version History
- **v1.0.0**: Initial release with basic flash card functionality
- **v1.1.0**: Added chapter progression and completion tracking
- **v1.2.0**: Enhanced responsive design and accessibility

---

**Built with ❤️ for educational excellence**

For support or questions, please open an issue on GitHub.