# AGENTS.md - Developer Guide for Osaka Jade RemNote Theme

## Project Overview

This is a RemNote theme called "Osaka Jade" - a dark theme with jade/green aesthetic tones.
The project structure follows the RemNote theme template with CSS-based styling.

- **Theme ID**: `theme_osake_jade`
- **Author**: elcokiin
- **Theme Type**: Dark theme
- **Main Files**: `manifest.json` (theme metadata), `theme.css` (theme styles)
- **Reference Files**: `osaka-jade/` directory contains reference configuration files from the author's Arch Linux setup (for color palette reference only - not part of the theme)

## Repository Structure

```
.
├── manifest.json           # Theme metadata and configuration
├── theme.css              # Main theme CSS file (RemNote styles)
├── osaka-jade/            # Reference configs (Alacritty, Kitty, Hyprland, etc.)
│   ├── backgrounds/       # Background images for reference
│   └── *.conf, *.theme    # Various app theme configs (reference only)
└── .github/
    ├── ISSUE_TEMPLATE/
    └── pull_request_template.md
```

## Build/Test/Lint Commands

This is a CSS-only theme project. There are no build, test, or lint scripts currently configured.

### Manual Testing
- Load the theme in RemNote by:
  1. Navigate to Settings → Appearance → Themes
  2. Click "Add Custom Theme"
  3. Select the theme directory containing `manifest.json`
  4. Apply the theme to test visual changes

### Validation
- Ensure `manifest.json` is valid JSON
- Verify `manifestVersion` is set to `1`
- Check that `version` object contains `major`, `minor`, `patch` numbers
- Validate CSS syntax in `theme.css`

## Code Style Guidelines

### CSS Formatting

**Indentation**: Use 2 spaces (no tabs)

**Naming Conventions**:
- Use RemNote's CSS classes (e.g., `.rem-text`, `.rem-container`)
- Keep selectors specific to RemNote elements
- Avoid overly generic selectors that might affect unintended elements

**Property Organization**:
```css
.selector {
  /* Layout properties first */
  display: flex;
  position: relative;
  
  /* Box model */
  width: 100%;
  padding: 8px;
  margin: 0;
  
  /* Visual properties */
  background: #111c18;
  color: #C1C497;
  border: 1px solid #549e6a;
  
  /* Typography */
  font-size: 14px;
  font-weight: 400;
  
  /* Transitions/animations last */
  transition: all 0.2s ease;
}
```

**Color Palette** (based on reference configs):
- Background: `#111c18` (dark green-tinted)
- Foreground: `#C1C497`, `#F7E8B2`, `#F6F5DD` (warm cream/yellow)
- Accents:
  - Green: `#549e6a`, `#459451`, `#2DD5B7`
  - Red: `#FF5345`, `#DB9F9C`
  - Yellow: `#E5C736`, `#DEB266`
  - Magenta: `#D2689C`
  - Muted: `#53685B`, `#32473B`, `#23372B`

**CSS Best Practices**:
- Use CSS custom properties (variables) for colors when possible
- Keep specificity low - avoid `!important` unless absolutely necessary
- Comment sections of related styles
- Group related selectors together
- Use shorthand properties where appropriate

### manifest.json Guidelines

**Required Fields**:
- `manifestVersion`: Always `1`
- `id`: Unique identifier (use `theme_` prefix, lowercase, underscores)
- `name`: Display name (Title Case)
- `author`: Theme author username
- `version`: Object with `major`, `minor`, `patch` integers
- `theme`: Array containing `"dark"` or `"light"`

**Version Bumping**:
- Patch: Bug fixes, minor color tweaks
- Minor: New features, significant style additions
- Major: Complete redesign, breaking changes

**Keep These Empty** (unless needed):
- `repoUrl`: Can be filled with GitHub repo URL
- `description`: Short theme description
- `enableOnMobile`: Keep `false` unless mobile support added
- `requestNative`: Keep `false`
- `requiredScopes`: Keep empty array

### Git Commit Style

Based on commit history, use conventional commit format:

- `Fix` - Bug fixes (e.g., "Fix version", "Fix npm run dev")
- `Add` - New features (e.g., "Add empty theme.css file")
- `Update` - Changes to existing features (e.g., "Update index.tsx")
- `Remove` - Removing code/files (e.g., "Remove plugin styling files")

**Format**: `<type> <description>`
- Keep first line under 72 characters
- Use imperative mood ("Fix bug" not "Fixed bug")
- No period at the end of the subject line
- Body text can provide additional context if needed

## File Organization

### theme.css
- Main styling file for RemNote elements
- Currently minimal - add RemNote-specific class styles here
- Test changes by reloading the theme in RemNote

### osaka-jade/ Directory
- **Do not modify** - reference files only
- Contains color palette inspiration from author's system configs
- Use these files to maintain color consistency across the theme
- Background images can be referenced but aren't loaded by RemNote

## Common Tasks

### Adding New Styles
1. Identify the RemNote element class (use browser DevTools)
2. Add selector to `theme.css`
3. Apply colors from the Osaka Jade palette
4. Test in RemNote
5. Commit with descriptive message

### Changing Colors
1. Reference `osaka-jade/` configs for palette consistency
2. Update colors in `theme.css`
3. Ensure sufficient contrast for readability
4. Test in both light and dark modes (if applicable)

### Version Updates
1. Update `version` in `manifest.json`
2. Follow semantic versioning (patch/minor/major)
3. Commit with "Fix version" or similar message

## Pull Request Guidelines

Use the PR template in `.github/pull_request_template.md`:

```markdown
### Summary 🎯
<!-- Explain the purpose and link relevant issues -->

### Changes 🔁
- List specific changes made
```

Be clear and concise about visual changes and their impact.

## Notes for Agents

- This is a **visual theme project** - focus is on CSS styling, not functionality
- No TypeScript, JavaScript, or build tools are involved
- The `osaka-jade/` directory is for **reference only** - it's not part of the theme package
- When making color changes, maintain the jade/green aesthetic with warm cream accents
- Always validate JSON syntax in `manifest.json` before committing
- Test theme changes by loading in RemNote (manual process)
- RemNote CSS classes are typically prefixed with `.rem-`
- Keep mobile support disabled unless specifically requested
