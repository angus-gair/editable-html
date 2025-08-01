# CLAUDE.md - Resume HTML Editor

This file provides guidance for Claude Code when working with the Resume HTML Editor project.

## Project Overview

This is a **Visual Resume HTML Editor** built with GrapesJS that allows Angus James to edit his resume HTML files visually without coding. The project provides a drag-and-drop interface for modifying resume content, styling, and layout.

## Architecture

### Core Components
- **resume-editor.html**: Main editor interface with GrapesJS integration
- **angus-james-resume.html**: Source resume template to be edited
- **package.json**: Node.js dependencies and npm scripts
- **node_modules/**: GrapesJS and related dependencies

### Technology Stack
- **Frontend**: GrapesJS visual builder, Vanilla JavaScript
- **Backend**: Python HTTP server (development)
- **Dependencies**: GrapesJS core, GrapesJS preset-webpage
- **Storage**: Browser localStorage for auto-save

## Key Commands

### Development Workflow
```bash
# Navigate to project
cd /home/gair_/manual-resumes/editable-html

# Install dependencies (first time only)
npm install

# Start development server
npm start              # Port 8000
npm run dev           # Port 3000 (alternative)

# Manual server start
python3 -m http.server 8000
```

### Access URLs
- **Editor**: `http://localhost:8000/resume-editor.html`
- **Original Resume**: `http://localhost:8000/angus-james-resume.html`

## Development Guidelines

### File Structure Requirements
The project expects this exact structure:
```
editable-html/
├── resume-editor.html       # Must be in root for relative paths
├── angus-james-resume.html  # Source template (required for Load function)
├── package.json            # Dependencies
└── node_modules/           # Generated after npm install
```

### Working with the Editor

#### Loading Resume Content
- The "Load Resume" button fetches `angus-james-resume.html` via AJAX
- Extracts `<body>` content and `<style>` tags
- Loads them into GrapesJS editor
- **Important**: Resume file must be in same directory as editor

#### Custom Resume Blocks
The editor includes three custom blocks:
1. **Section Block**: Generic resume sections with title and content
2. **Job Block**: Work experience entries with company, dates, title, achievements
3. **Skill Block**: Skill categories with lists

#### Storage Behavior
- **Auto-save**: Saves to localStorage on every change
- **Manual Save**: Stores complete HTML in browser storage
- **Export**: Downloads complete HTML file with embedded CSS

### Troubleshooting

#### Common Issues
1. **"Resume won't load"**: Check `angus-james-resume.html` exists in same directory
2. **"Styles missing"**: Run `npm install` to ensure dependencies are installed
3. **"Server connection refused"**: Verify Python 3.6+ is available
4. **"Port already in use"**: Try `npm run dev` for port 3000

#### File Path Dependencies
- All paths in `resume-editor.html` are relative
- Moving files requires updating script src attributes
- GrapesJS dependencies must be in `node_modules/` subdirectory

### Extending the Editor

#### Adding New Custom Blocks
Add to the JavaScript section in `resume-editor.html`:
```javascript
editor.BlockManager.add('block-id', {
  label: 'Display Name',
  content: '<div class="new-block">HTML content</div>',
  category: 'Resume',
  attributes: { class: 'gjs-block-custom' }
});
```

#### Modifying Editor Configuration
Key configuration areas in the GrapesJS initialization:
- **Storage**: Auto-save settings and localStorage key
- **Style Manager**: Available CSS properties panels
- **Device Manager**: Responsive preview sizes
- **Canvas**: External stylesheets and fonts

#### Styling Considerations
- Resume styles are embedded in the original HTML
- GrapesJS editor has its own UI styles
- Maintain separation between editor UI and resume content styles

### Integration Notes

#### With Main Resume System
This editor is designed to work alongside the main resume generation system:
- **Input**: Takes HTML from existing templates
- **Output**: Produces edited HTML for use in PDF conversion
- **Workflow**: Edit → Export → Convert to PDF using existing Python scripts

#### File Relationships
```
templates-and-reference/latest/angus-james-resume.html  # Source
         ↓ (copy to editor)
editable-html/angus-james-resume.html                  # Editor input
         ↓ (edit & export)
output-resumes-coverletters/angus-james-resume-edited.html  # Final output
```

### Maintenance

#### Updating Dependencies
```bash
npm update                    # Update all packages
npm install grapesjs@latest  # Update specific package
```

#### Backup Considerations
- Browser localStorage can be cleared by user
- Always export important changes to HTML files
- Consider adding server-side storage for production use

#### Performance Optimization
- Large resume HTML files may slow initial load
- Consider chunking very large documents
- Auto-save frequency can be adjusted in editor config

### Security Considerations

#### Local Development
- Python HTTP server is for development only
- No authentication or access control
- All files in directory are publicly accessible

#### Production Deployment
- Use proper web server (Apache, Nginx)
- Implement access controls if needed
- Sanitize exported HTML if accepting user input

## Best Practices

### When Working with This Project
1. Always run `npm install` after cloning or updating
2. Test editor functionality after any modifications
3. Keep backup of original resume HTML
4. Export completed edits immediately
5. Use version control for editor code changes

### Code Modifications
1. Test changes in local development environment
2. Maintain backward compatibility with existing resumes
3. Update README.md if adding new features
4. Document new custom blocks in this file

### File Management
1. Keep source resume files in version control
2. Export edited resumes with descriptive filenames
3. Maintain clean separation between editor and resume content
4. Use consistent naming conventions

---

**Quick Reference:**
- Start: `cd /home/gair_/manual-resumes/editable-html && npm start`
- Access: `http://localhost:8000/resume-editor.html`
- Dependencies: GrapesJS, Python 3.6+, Node.js 14+