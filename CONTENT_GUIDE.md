# Content Authoring Guide

This guide explains how to create and organize content for the Flash Card Learning System.

## 📋 Quick Reference

### Required Files for Each Subject
- `chapters.json` - Lists all chapters for the subject
- `chapter-name/cards.json` - Flash cards for each chapter
- `chapter-name/audio/` - Audio files (optional)
- `chapter-name/images/` - Image files (optional)

### File Structure Template
```
content/
└── primary{level}/
    └── {subject}/
        ├── chapters.json
        └── {chapter-id}/
            ├── cards.json
            ├── audio/
            └── images/
```

## 📂 Directory Structure

### Level Organization
Create directories for each primary level (1-6):
```
content/
├── primary1/
├── primary2/
├── primary3/
├── primary4/
├── primary5/
└── primary6/
```

### Subject Organization
Each level contains subject folders:
```
primary1/
├── english/
├── chinese/
├── malay/
├── science/     # Add more subjects as needed
└── mathematics/
```

### Chapter Organization
Each subject contains chapter folders:
```
english/
├── chapters.json              # Required: Chapter list
├── chapter1-animals/          # Chapter folder
│   ├── cards.json            # Required: Flash cards
│   ├── audio/                # Optional: Audio files
│   └── images/               # Optional: Image files
├── chapter2-colors/
└── chapter3-numbers/
```

## 📝 chapters.json Format

The `chapters.json` file defines which chapters are available for a subject.

### Schema
```json
{
  "chapters": [
    {
      "id": "chapter1-animals",
      "title": "Animals",
      "description": "Learn about different animals",
      "order": 1,
      "difficulty": "beginner"
    }
  ]
}
```

### Field Descriptions
- **id**: Unique identifier, must match folder name
- **title**: Display name shown to users
- **description**: Brief explanation of chapter content
- **order**: Numeric order for chapter sequence
- **difficulty**: `"beginner"`, `"intermediate"`, or `"advanced"`

### Example: Primary 1 English
```json
{
  "chapters": [
    {
      "id": "chapter1-animals",
      "title": "Animals",
      "description": "Learn about different animals",
      "order": 1,
      "difficulty": "beginner"
    },
    {
      "id": "chapter2-colors",
      "title": "Colors",
      "description": "Basic colors and their names",
      "order": 2,
      "difficulty": "beginner"
    },
    {
      "id": "chapter3-numbers",
      "title": "Numbers 1-10",
      "description": "Count from one to ten",
      "order": 3,
      "difficulty": "intermediate"
    }
  ]
}
```

## 🃏 cards.json Format

The `cards.json` file contains all flash cards for a chapter.

### Card Types

#### 1. Text Only Card
```json
{
  "type": "text",
  "front": "Cat",
  "back": "A small furry pet that says meow"
}
```

#### 2. Text + Audio Card
```json
{
  "type": "audio",
  "front": "Dog",
  "back": "A loyal animal that barks",
  "audio": "audio/dog.mp3"
}
```

#### 3. Text + Audio + Image Card
```json
{
  "type": "full",
  "front": "Bird",
  "back": "An animal that can fly",
  "audio": "audio/bird.mp3",
  "image": "images/bird.jpg"
}
```

### Complete Example
```json
[
  {
    "type": "text",
    "front": "Cat",
    "back": "A small furry pet that says meow"
  },
  {
    "type": "audio",
    "front": "Dog",
    "back": "A loyal animal that barks",
    "audio": "audio/dog.mp3"
  },
  {
    "type": "full",
    "front": "Bird",
    "back": "An animal that can fly and has wings",
    "audio": "audio/bird.mp3",
    "image": "images/bird.jpg"
  }
]
```

### Field Requirements
- **type**: Must be `"text"`, `"audio"`, or `"full"`
- **front**: Text shown on front of card (required)
- **back**: Text shown on back of card (required)
- **audio**: Path to audio file (relative to chapter folder)
- **image**: Path to image file (relative to chapter folder)

## 🎵 Audio Files

### Supported Formats
- **MP3**: Best compatibility across all browsers
- **WAV**: High quality, larger file size
- **OGG**: Good compression, supported by modern browsers

### File Guidelines
- **File size**: Keep under 1MB per file
- **Quality**: 128kbps MP3 is usually sufficient
- **Duration**: Keep audio clips short (1-3 seconds for words)
- **Volume**: Normalize audio levels across files

### Naming Convention
Use descriptive names that match the card content:
```
audio/
├── cat.mp3
├── dog.mp3
├── bird.mp3
└── elephant.mp3
```

### Recording Tips
- **Clear pronunciation**: Speak clearly and at moderate pace
- **Background noise**: Record in quiet environment
- **Consistency**: Use the same speaker for related content
- **Native speakers**: Use native speakers when possible

## 🖼️ Image Files

### Supported Formats
- **JPG**: Best for photographs and complex images
- **PNG**: Best for images with transparency or simple graphics
- **WebP**: Modern format with excellent compression
- **GIF**: For animated images (use sparingly)

### File Guidelines
- **File size**: Keep under 500KB per image
- **Dimensions**: Recommended 400x300 pixels or similar aspect ratio
- **Quality**: Optimize for web while maintaining clarity
- **Accessibility**: Ensure good contrast and clear details

### Naming Convention
Use descriptive names that match the card content:
```
images/
├── cat.jpg
├── dog.jpg
├── bird.jpg
└── elephant.jpg
```

### Image Best Practices
- **Educational value**: Choose images that clearly represent the concept
- **Age appropriate**: Select content suitable for target age group
- **Cultural sensitivity**: Use inclusive and diverse imagery
- **Copyright**: Use only royalty-free or properly licensed images

## 🌍 Multi-language Content

### Language-Specific Considerations

#### Chinese Content
- Include pinyin pronunciation in parentheses
- Use simplified or traditional characters consistently
- Consider tone marks for pronunciation guidance

Example:
```json
{
  "type": "audio",
  "front": "妈妈 (māma)",
  "back": "Mother/Mom",
  "audio": "audio/mama.mp3"
}
```

#### Malay Content
- Use standard Bahasa Malaysia spelling
- Include common alternative spellings in descriptions
- Consider regional variations

#### Multi-script Content
- Ensure proper encoding (UTF-8)
- Test display across different browsers
- Consider font requirements for special characters

## 📋 Content Planning Worksheet

### Before Creating Content

1. **Define Learning Objectives**
   - What should students learn from this chapter?
   - What skills will they practice?
   - How does this build on previous knowledge?

2. **Plan Chapter Structure**
   - How many cards are needed?
   - What types of cards work best for this content?
   - What multimedia resources are available?

3. **Determine Progression**
   - How do chapters build on each other?
   - What's the appropriate difficulty curve?
   - Are there prerequisite concepts?

### Content Creation Checklist

#### Chapter Setup
- [ ] Create chapter folder with proper naming
- [ ] Add entry to `chapters.json`
- [ ] Create `cards.json` file
- [ ] Create `audio/` and `images/` folders if needed

#### Content Creation
- [ ] Write clear, age-appropriate text
- [ ] Record or source audio files
- [ ] Create or source appropriate images
- [ ] Test all media files work properly

#### Quality Assurance
- [ ] Check JSON syntax validity
- [ ] Test card display and navigation
- [ ] Verify audio playback works
- [ ] Confirm images display correctly
- [ ] Test on mobile and desktop devices

#### Educational Review
- [ ] Content is age-appropriate
- [ ] Learning objectives are met
- [ ] Progression is logical
- [ ] Cultural sensitivity is maintained

## 🔧 Tools and Validation

### JSON Validation
Use online JSON validators to check syntax:
- [JSONLint](https://jsonlint.com/)
- [JSON Formatter](https://jsonformatter.org/)

### Image Optimization
- [TinyPNG](https://tinypng.com/) - Compress images
- [Squoosh](https://squoosh.app/) - Advanced image optimization
- [ImageOptim](https://imageoptim.com/) - Desktop tool for Mac

### Audio Tools
- [Audacity](https://www.audacityteam.org/) - Free audio editor
- [Online Audio Converter](https://online-audio-converter.com/)
- [Voice Record Pro](https://apps.apple.com/app/voice-record-pro/id546983235) - Mobile recording

### Testing
```bash
# Serve locally for testing
python -m http.server 8000
# or
npx http-server -p 8000
```

## 📚 Example Content Sets

### Beginner English (Primary 1)
```
chapter1-animals/     # 8-10 cards
chapter2-colors/      # 6-8 cards  
chapter3-numbers/     # 10 cards (1-10)
chapter4-family/      # 6-8 cards
chapter5-food/        # 8-10 cards
```

### Intermediate Science (Primary 3)
```
chapter1-plants/      # 10-12 cards
chapter2-weather/     # 8-10 cards
chapter3-magnets/     # 10-12 cards
chapter4-light/       # 8-10 cards
```

### Advanced Mathematics (Primary 5)
```
chapter1-fractions/   # 12-15 cards
chapter2-decimals/    # 10-12 cards
chapter3-geometry/    # 15-20 cards
chapter4-measurement/ # 10-12 cards
```

## 🎯 Content Strategy

### Age-Appropriate Guidelines

#### Primary 1-2 (Ages 6-8)
- Simple vocabulary and concepts
- Bright, engaging images
- Short audio clips
- 5-8 cards per chapter

#### Primary 3-4 (Ages 8-10)
- More complex concepts
- Longer descriptions
- Introduction of academic vocabulary
- 8-12 cards per chapter

#### Primary 5-6 (Ages 10-12)
- Abstract concepts
- Multi-step explanations
- Cross-curricular connections
- 10-15 cards per chapter

### Engagement Strategies
- **Visual variety**: Mix text, audio, and image cards
- **Progressive difficulty**: Start easy, gradually increase complexity
- **Real-world connections**: Use familiar examples and contexts
- **Cultural relevance**: Include diverse perspectives and examples

---

**Need help?** Create an issue on GitHub or refer to the main README.md for additional support.