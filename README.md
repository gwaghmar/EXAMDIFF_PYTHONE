# Python ExamDiff Pro - Professional File & Directory Comparison Tool

A production-ready, feature-rich file and directory comparison application for Windows with a modern GUI. An enhanced clone of ExamDiff Pro with additional advanced features.

## 🌟 Features

### Core Comparison
- **Myers' Diff Algorithm** - Industry-standard LCS-based diffing
- **Multi-Mode Comparison**:
  - Two-way diff (File A vs File B)
  - Three-way diff (Base, Yours, Theirs)
  - Three-way merge with conflict resolution
- **Text & Binary** - Compare text files with multiple encodings or binary files byte-by-byte
- **Large File Support** - Efficiently handle files up to 1GB

### Visual Interface
- **Dual-Pane Side-by-Side View** with synchronized scrolling
- **Color-Coded Highlighting**:
  - 🟢 Green: Added lines
  - 🔴 Red: Deleted lines
  - 🟡 Yellow: Modified lines
  - ⚪ Gray: Unchanged lines
- **Three-Level Diff Highlighting**:
  - Line-level (entire line)
  - Word-level (changed words)
  - Character-level (individual characters)
- **Diff Navigation** - Previous/Next/Current with keyboard shortcuts
- **Minimap Overview** - Vertical bar showing all differences
- **Jump to Line** - Quick navigation to specific line numbers

### Directory Comparison
- **Recursive Tree Comparison** with file status indicators
- **File Status**:
  - ✅ Identical
  - ⚠️ Different
  - ⬅️ Left only
  - ➡️ Right only
  - 🕒 Newer/Older
- **Flexible Views** - Tree view or flat list
- **Smart Filtering** - By file type, status, name pattern
- **Mass Operations** - Copy, delete, synchronize between directories
- **Directory Snapshots** - Save comparison state as XML

### Syntax Highlighting
- **25+ Languages** - Python, JavaScript, Java, C++, C#, HTML, CSS, SQL, XML, JSON, and more
- **Multiple Themes** - Light and dark color schemes
- **Powered by Pygments** - Professional syntax highlighting

### Intelligent Features
- **Fuzzy Matching** - Align similar but not identical lines
- **Moving Block Detection** - Recognize code blocks moved within file
- **Smart Ignore Options**:
  - Whitespace (leading, trailing, all)
  - Blank lines
  - Case sensitivity
  - Comments (language-aware)
  - Lines matching regex patterns
  - Specific line/column ranges

### Editing & Merging
- **Inline Editing** - Edit files directly in comparison panes
- **Copy Operations** - Left→Right or Right→Left (whole file or selected lines)
- **Merge Changes** - Select and merge specific changes
- **Undo/Redo** - Full undo/redo support

### Reporting & Export
- **HTML Reports** - Interactive navigation
- **PDF Reports** - Print-ready documents
- **Unix Diff Format** - Standard diff output
- **Statistics** - Lines added/deleted/changed
- **Print Preview** - Print directly from the application

### Advanced Features
- **Tabbed Interface** - Multiple comparisons simultaneously
- **Git Integration** - Compare Git commits and branches
- **Bookmark System** - Mark important differences
- **Comparison History** - Save and reload sessions
- **Advanced Search** - Search within differences only
- **Dark Mode** - Full dark theme support
- **Plugin System** - Python plugin API for custom processors

### Windows Integration
- **Explorer Context Menu** - Right-click to compare files
- **File Associations** - Handle .diff and .patch files
- **System Tray Icon** - Quick access
- **Command-Line Interface** - Automate comparisons
- **Drag & Drop** - Drop files/folders to compare

## 📦 Installation

### Prerequisites
- Python 3.11 or higher
- Windows 10/11

### Quick Start

1. **Clone or download the repository**
```bash
cd c:\path\to\EXAMDIFF
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Run the application**
```bash
python main.py
```

### Building Standalone Executable

To create a standalone .exe file:

```bash
pyinstaller examdiff.spec
```

The executable will be in the `dist` folder.

## 🚀 Usage

### GUI Mode

Launch the application:
```bash
python main.py
```

Then use the interface to:
1. Click "File → Compare Files" or press `Ctrl+O`
2. Select two files or directories
3. View the comparison results

### Command-Line Mode

**Compare two files:**
```bash
python main.py file1.txt file2.txt
```

**Compare directories:**
```bash
python main.py --dir folder1 folder2
```

**Three-way merge:**
```bash
python main.py --merge base.txt yours.txt theirs.txt -o output.txt
```

**Options:**
- `--ignore-whitespace` - Ignore whitespace differences
- `--ignore-case` - Case-insensitive comparison
- `--syntax <language>` - Enable syntax highlighting
- `--encoding <enc>` - Specify file encoding
- `--output <file>` - Save results to file
- `--html` - Generate HTML report
- `--pdf` - Generate PDF report

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+O` | Open files/directories |
| `Ctrl+S` | Save current file |
| `Ctrl+W` | Close current tab |
| `F5` | Refresh/Re-compare |
| `F7` | Previous difference |
| `F8` | Next difference |
| `Ctrl+G` | Go to line |
| `Ctrl+F` | Find |
| `Ctrl+H` | Find and replace |
| `Ctrl+Left` | Copy to left pane |
| `Ctrl+Right` | Copy to right pane |
| `Ctrl+Z` | Undo |
| `Ctrl+Y` | Redo |
| `Ctrl+Tab` | Next tab |
| `Ctrl+Shift+Tab` | Previous tab |

## 🎨 Configuration

The application uses a YAML configuration file stored at:
```
%APPDATA%\PythonExamDiff\config.yaml
```

You can customize:
- Color schemes
- Font settings
- Default ignore options
- Keyboard shortcuts
- Plugin settings
- Recent files limit
- And more...

Edit the file directly or use `Settings → Preferences` in the GUI.

## 🔌 Plugin System

Create custom plugins to extend functionality:

```python
# plugins/my_plugin.py
from plugins.plugin_base import PluginBase

class MyPlugin(PluginBase):
    name = "My Custom Plugin"
    version = "1.0.0"
    
    def process_diff(self, diff_result):
        # Your custom processing
        return modified_result
```

Place plugins in the `plugins/` directory and they'll be auto-loaded.

## 📁 Project Structure

```
python_examdiff/
├── main.py                    # Application entry point
├── config.py                  # Configuration management
├── gui/                       # GUI components
│   ├── main_window.py        # Main application window
│   ├── file_comparison_view.py   # File diff view
│   ├── directory_comparison_view.py  # Directory diff view
│   └── dialogs.py            # Dialogs and popups
├── core/                      # Core comparison engine
│   ├── diff_engine.py        # Main diff engine wrapper
│   ├── myers_algorithm.py    # Myers' diff implementation
│   ├── file_handler.py       # File I/O and encoding
│   └── directory_handler.py  # Directory operations
├── utils/                     # Utility modules
│   ├── syntax_highlighter.py # Syntax highlighting
│   ├── report_generator.py   # HTML/PDF reports
│   └── helpers.py            # Helper functions
├── plugins/                   # Plugin system
│   └── plugin_base.py        # Base plugin class
├── tests/                     # Unit tests
│   ├── test_myers.py
│   ├── test_file_handler.py
│   └── test_diff_engine.py
├── resources/                 # Resources
│   ├── icons/                # Application icons
│   └── themes/               # Color themes
├── requirements.txt          # Python dependencies
├── examdiff.spec            # PyInstaller spec
└── README.md                # This file
```

## 🧪 Testing

Run unit tests:
```bash
pytest tests/
```

Run with coverage:
```bash
pytest --cov=. tests/
```

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes with tests
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgments

- **Eugene Myers** - For the Myers diff algorithm
- **ExamDiff Pro** - Inspiration for features
- **CustomTkinter** - Modern GUI framework
- **Pygments** - Syntax highlighting

## 📞 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Email: support@pythonexamdiff.com

## 🗺️ Roadmap

- [ ] Cloud storage integration (Google Drive, OneDrive, Dropbox)
- [ ] Real-time collaboration features
- [ ] AI-powered smart merge suggestions
- [ ] Image comparison with visual diff
- [ ] Multi-language UI (i18n)
- [ ] Web-based interface
- [ ] Integration with more version control systems

---

**Made with ❤️ for developers who need powerful comparison tools**
