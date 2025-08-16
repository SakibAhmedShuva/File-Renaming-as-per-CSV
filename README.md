# CSV-Based File Renaming Utility

[![Python 3.6+](https://img.shields.io/badge/python-3.6+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A robust and safe Python utility for batch renaming files using CSV mappings. Perfect for organizing large collections of files with automated safety features and comprehensive error handling.

## 🎯 Overview

This tool allows you to rename hundreds or thousands of files efficiently by providing a simple CSV mapping file. Built with safety in mind, it includes dry-run capabilities, automatic backups, and interactive confirmations to prevent data loss.

## ✨ Features

- **📊 CSV-Based Mapping**: Define rename operations in a simple CSV format
- **🔍 Dry Run Mode**: Preview all changes before execution
- **💾 Automatic Backups**: Optional backup creation before any modifications
- **✅ Interactive Confirmation**: Explicit user approval required for operations
- **📝 Comprehensive Logging**: Real-time progress updates and detailed summaries
- **🛡️ Error Handling**: Built-in protection against file conflicts and missing files
- **⚡ Batch Processing**: Handle large file collections efficiently

## 📋 Requirements

- Python 3.6 or higher
- pandas library

## 🚀 Quick Start

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/csv-file-renamer.git
   cd csv-file-renamer
   ```

2. **Install dependencies**
   ```bash
   pip install pandas
   ```

### Basic Usage

1. **Create your CSV mapping file** (no headers required):
   ```csv
   old_filename1.txt,new_filename1.txt
   old_filename2.jpg,new_filename2.jpg
   document.pdf,renamed_document.pdf
   ```

2. **Configure and run the script**:
   ```python
   from renaming import quick_rename
   
   # Define paths
   file_directory = "/path/to/your/files"
   csv_mapping_file = "/path/to/your/mapping.csv"
   
   # Execute with backup (recommended)
   quick_rename(file_directory, csv_mapping_file, create_backup_first=True)
   ```

## 📖 Detailed Usage

### CSV File Format

Your CSV file should contain two columns without headers:
- **Column 1**: Current filename (including extension)
- **Column 2**: Desired new filename (including extension)

**Example mapping file (`renaming_map.csv`)**:
```csv
IMG_001.jpg,vacation_beach.jpg
IMG_002.jpg,vacation_sunset.jpg
VID_001.mp4,family_dinner.mp4
document_old.pdf,contract_final.pdf
```

### Configuration Options

```python
quick_rename(
    file_directory,           # Path to directory containing files
    csv_mapping_file,         # Path to CSV mapping file
    create_backup_first=True  # Create backup before renaming (recommended)
)
```

### Workflow Process

1. **📁 Backup Creation** (if enabled)
   - Creates a complete copy of your directory with `_backup` suffix
   - Ensures original files remain untouched

2. **🔍 Dry Run Analysis**
   - Scans all mapping entries
   - Identifies potential issues (missing files, conflicts)
   - Displays preview of all planned changes

3. **✅ User Confirmation**
   - Review the dry run output
   - Type `yes` to proceed or any other input to cancel

4. **🔄 Rename Execution**
   - Performs actual file renaming
   - Provides real-time progress updates
   - Handles errors gracefully

5. **📊 Summary Report**
   - Shows successful renames
   - Lists any failures with reasons
   - Provides operation statistics

## 🛠️ API Reference

### Core Functions

#### `rename_files_from_csv(directory, csv_file, dry_run=True)`
Performs the file renaming operation based on CSV mapping.

**Parameters:**
- `directory` (str): Path to the directory containing files to rename
- `csv_file` (str): Path to the CSV mapping file
- `dry_run` (bool): If True, only shows what would be renamed without making changes

**Returns:**
- Dictionary with operation results and statistics

#### `create_backup(source_directory)`
Creates a backup copy of the specified directory.

**Parameters:**
- `source_directory` (str): Path to directory to backup

**Returns:**
- Path to the created backup directory

#### `quick_rename(directory, csv_file, create_backup_first=False)`
Main workflow function that orchestrates the complete renaming process.

**Parameters:**
- `directory` (str): Path to the directory containing files to rename
- `csv_file` (str): Path to the CSV mapping file  
- `create_backup_first` (bool): Whether to create a backup before renaming

## ⚠️ Safety Features

- **Dry Run First**: Always previews changes before execution
- **Backup Creation**: Optional full directory backup
- **Conflict Detection**: Identifies existing files that would be overwritten
- **Missing File Alerts**: Reports files in CSV that don't exist in directory
- **User Confirmation**: Requires explicit approval before making changes

## 🐛 Troubleshooting

### Common Issues

**Files not found**
- Ensure file paths in CSV exactly match actual filenames (case-sensitive)
- Verify the target directory path is correct

**Permission errors**
- Run with appropriate file system permissions
- Ensure files are not currently open in other applications

**Name conflicts**
- The script will warn about existing files that would be overwritten
- Review dry run output carefully before proceeding

### Error Messages

| Error | Cause | Solution |
|-------|-------|----------|
| `File not found` | CSV references non-existent file | Update CSV or add missing files |
| `Permission denied` | Insufficient file permissions | Run with elevated permissions |
| `File already exists` | Target filename already exists | Choose different target name |

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
