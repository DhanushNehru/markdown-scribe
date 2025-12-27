# Markdown Scribe

<img width="2848" height="1600" alt="image" src="https://github.com/user-attachments/assets/fbac6a74-efcb-4de6-a9be-0656408c9309" />


A fast and extensible Markdown renderer and editor built in Rust, designed for client-side use with CLI and TUI support. No dependencies on servers or networks.

## Features

- **Markdown Rendering** - Convert Markdown files to HTML with syntax highlighting for code blocks
- **CLI Interface** - Simple command-line tools for rendering and watching files
- **TUI Editor** - Terminal user interface editor for creating and editing Markdown
- **File Watching** - Auto-rerender Markdown when files change
- **Syntax Highlighting** - Code blocks are highlighted using `syntect`
- **Extended Markdown** - Support for tables, task lists, strikethrough, and footnotes
- **PDF Export** - Support for exporting rendered Markdown to PDF (in development)
- **No External Dependencies** - Fully client-side, works offline

## Installation

### From Source

Build using Cargo:

```bash
git clone https://github.com/DhanushNehru/markdown-scribe.git
cd markdown-scribe
cargo build --release
```

The binary will be available at `target/release/markdown-scribe`.

## Usage

### Render Markdown to HTML

```bash
cargo run -- render --input example.md --output output.html
```

**Options:**
- `--input, -i` - Path to input Markdown file (required)
- `--output, -o` - Path to output HTML file (default: `output.html`)
- `--pdf` - Optional path to render as PDF

### Watch Mode

Auto-rerender HTML whenever the Markdown file changes:

```bash
cargo run -- watch --file example.md
```

Opens a live preview in your default browser that updates automatically on file changes.

### TUI Editor

Launch the interactive terminal editor:

```bash
cargo run -- edit
```

Or open and edit an existing file:

```bash
cargo run -- edit --file example.md
```

**Editor Controls:**
- `Esc` - Exit editor
- `Enter` - New line
- Arrow Keys - Navigate cursor
- `Backspace` - Delete character

## Project Structure

```
src/
├── main.rs    - CLI interface and core rendering logic
└── tui.rs     - Terminal user interface implementation
```

## Technical Details

### Markdown Processing

- Uses `pulldown-cmark` for robust Markdown parsing
- Supports CommonMark with GitHub Flavored Markdown extensions
- Custom syntax highlighting for code blocks via `syntect`

### Terminal UI

- Built with `ratatui` for rendering
- Uses `crossterm` for cross-platform terminal control
- Split-pane editor with live preview

### File Watching

- `notify` crate for file system monitoring
- Instant feedback on file changes

## Dependencies

- **clap** (4.5.53) - Command-line argument parsing
- **pulldown-cmark** (0.13.0) - Markdown parsing
- **syntect** (5.3.0) - Syntax highlighting
- **ratatui** (0.30.0) - TUI framework
- **crossterm** (0.29.0) - Terminal manipulation
- **notify** (8.2.0) - File watching
- **webbrowser** (1.0.6) - Open browser preview
- **printpdf** (0.8.2) - PDF generation
- **anyhow** (1.0.82) - Error handling

## Building

### Requirements

- Rust 1.70+ (Edition 2021)
- Cargo

### Build Commands

```bash
# Development build
cargo build

# Release build (optimized)
cargo build --release

# Check without building
cargo check

# Run tests
cargo test
```

## Future Enhancements

- [ ] Full PDF rendering with proper styling
- [ ] Markdown validation and linting
- [ ] Export to additional formats (DOCX, LaTeX, EPUB)
- [ ] Theme customization for syntax highlighting
- [ ] Advanced editor features (find/replace, undo/redo)
- [ ] Configuration file support
- [ ] Plugin system for extensions

## Contributing

Contributions are welcome! Please feel free to:
- Report bugs by opening issues
- Suggest features
- Submit pull requests with improvements

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## Author

[DhanushNehru](https://github.com/DhanushNehru)
