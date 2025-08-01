# Resume HTML Editor

A visual HTML resume editor built with GrapesJS, designed specifically for editing Angus James' resume templates.

## Features

- **Visual Drag-and-Drop Editor**: Edit your resume HTML visually without coding
- **Real-time Preview**: See changes instantly as you edit
- **Export Functionality**: Save and export your edited resume as HTML
- **Custom Resume Blocks**: Pre-built components for job entries, skills, and sections
- **Responsive Design**: Preview in different device sizes
- **Auto-save**: Automatically saves your work to browser storage

## Quick Start

### Prerequisites
- Python 3.6+ (for local server)
- Node.js 14+ (for dependencies)

### Installation & Setup

1. **Navigate to the project directory**:
   ```bash
   cd /home/gair_/manual-resumes/editable-html
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start the development server**:
   ```bash
   npm start
   ```
   or
   ```bash
   python3 -m http.server 8000
   ```

4. **Open in browser**:
   Navigate to `http://localhost:8000/resume-editor.html`

### Alternative Port
If port 8000 is in use, try the dev server on port 3000:
```bash
npm run dev
```

## How to Use

### Loading Your Resume
1. Click **"Load Resume"** button to import `angus-james-resume.html`
2. The resume content will appear in the visual editor

### Editing
- **Text Editing**: Click any text element to edit directly
- **Drag & Drop**: Reorder sections by dragging them
- **Style Panel**: Use the right panel to adjust fonts, colors, spacing
- **Add Components**: Use the blocks panel to add new sections

### Saving Your Work
- **Save**: Saves to browser storage (persists between sessions)
- **Export HTML**: Downloads the edited resume as an HTML file
- **Auto-save**: Changes are automatically saved as you work

### Custom Blocks Available
- **Section Block**: Add new resume sections
- **Job Entry Block**: Add work experience entries
- **Skill Category Block**: Add skill categories

## Project Structure

```
editable-html/
├── README.md                 # This file
├── CLAUDE.md                # Development guidance for AI assistants
├── package.json             # Node.js dependencies and scripts
├── resume-editor.html       # Main editor interface
├── angus-james-resume.html  # Source resume template
└── node_modules/           # Dependencies (created after npm install)
```

## Technical Details

### Built With
- **GrapesJS**: Visual web builder framework
- **GrapesJS Preset Webpage**: Additional blocks and functionality
- **Python HTTP Server**: Local development server
- **Vanilla JavaScript**: Custom editor functionality

### Browser Compatibility
- Chrome/Chromium (recommended)
- Firefox
- Safari
- Edge

### Storage
- Uses browser localStorage for auto-save
- Exported files are downloaded to your default download folder

## Troubleshooting

### Server Issues
- **Connection refused**: Ensure Python 3.6+ is installed
- **Port in use**: Try `npm run dev` for port 3000
- **Permission denied**: Check folder permissions

### Editor Issues
- **Resume won't load**: Ensure `angus-james-resume.html` exists in the same directory
- **Styles missing**: Check that node_modules installed correctly (`npm install`)
- **Export not working**: Check browser download permissions

### Performance
- Large resumes may load slowly on first import
- Auto-save triggers after each change (can be disabled in code)

## Development

### Adding Custom Blocks
Edit `resume-editor.html` and add new blocks using:
```javascript
editor.BlockManager.add('block-name', {
  label: 'Block Label',
  content: '<div>HTML content</div>',
  category: 'Resume'
});
```

### Customizing Styles
Modify the CSS in `resume-editor.html` or add new stylesheets to the editor configuration.

### Server Configuration
The project uses Python's built-in HTTP server. For production, consider using a proper web server like Apache or Nginx.

## License

MIT License - See package.json for details

## Support

For issues specific to this editor, check:
1. Browser console for JavaScript errors
2. Network tab for failed resource loads
3. Ensure all files are in the correct directory structure

---

**Quick Commands Summary:**
- `npm install` - Install dependencies
- `npm start` - Start server on port 8000
- `npm run dev` - Start server on port 3000
- Access: `http://localhost:8000/resume-editor.html`