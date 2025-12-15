# BAGUA - I-Ching Divination Tool

[![Netlify Status](https://api.netlify.com/api/v1/badges/1f379702-6484-4b3a-af2c-e00964033597/deploy-status)](https://app.netlify.com/projects/qigua/deploys)

## Description

BAGUA is a traditional Chinese divination tool based on the I-Ching (Book of Changes). This web application includes three main divination methods:

1. **大衍筮法 (Dayan Shifa)** - The Great Expansion Method using yarrow stalks
2. **诸葛神数 (Zhuge Shenshu)** - Zhuge Liang's Divine Calculation
3. **玄天上帝靈籤 (Xuantian Shangdi Lingqian)** - Divine Lots of the Black Heavenly Emperor

## Features

- Pure front-end application (no backend required)
- Responsive design for mobile and desktop
- Traditional Chinese divination methods
- Beautiful UI with traditional Chinese aesthetics
- Dark mode support

## Installation

### Local Development

1. Clone the repository:
```bash
git clone https://github.com/bajibaji/BAGUA.git
cd BAGUA
```

2. Open `index.html` in your browser, or use a simple HTTP server:
```bash
npx http-server -p 8080 -o
```

### Deployment

This is a static website that can be deployed to any static hosting service like:
- Netlify
- GitHub Pages
- Vercel
- AWS S3
- Firebase Hosting

## Project Structure

```
BAGUA/
├── index.html              # Main entry point
├── Dayanshifa/            # Great Expansion Method
│   ├── index.html
│   ├── data.js
│   └── other.js
├── linqian/               # Divine Lots
│   ├── index.html
│   └── lot_data.js
├── zhugeshenshu/          # Zhuge's Divine Calculation
│   ├── index.html
│   ├── 384.json
│   └── kangxi_parts/      # Kangxi Dictionary data
├── README.md              # Chinese documentation
└── README_EN.md           # English documentation
```

## Technologies Used

- HTML5
- CSS3 (with Tailwind CSS)
- Vanilla JavaScript
- GSAP (GreenSock Animation Platform)
- Marked.js (Markdown parser)
- Google Fonts (Noto Serif SC)

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Version History

### v0.2.2
- Fixed bagua background issues
- Redesigned Zhuge Shenshu interface

### v0.2.1
- Rewrote homepage code
- Fixed yin-yang symbol errors on some pages

### v0.1.9
- Optimized divine lots page and text

### v0.1.8
- Fixed randomness issues in divine lots algorithm

## Disclaimer

**This tool is for entertainment and cultural appreciation purposes only.**

占卜结果仅供参考，解卦请自行找人。
(Divination results are for reference only. Please consult experts for interpretation.)

## License

MIT License

## Author

元明居士 (Yuanming Jushi) © 2025

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

If you encounter any issues, please open an issue on GitHub.
