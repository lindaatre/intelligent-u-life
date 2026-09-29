---
name: airprint-mac
description: Print files via AirPrint on macOS. Use when the user asks to print documents, images, web pages, or cloud files. Supports physical printing to AirPrint-enabled printers.
---

# AirPrint for Mac

Print files using AirPrint on macOS. Supports physical printing of PDF documents, images, web pages, and cloud storage files.

## Supported File Types

- PDF documents
- Images (JPEG, PNG, TIFF, etc.)
- Web pages (URLs)
- Text files
- Office documents

## Usage

When the user requests printing, follow these steps:

1. **Detect available printers**:
   - Run `lpstat -p -d` to list all available printers
   - Check if any printers are connected and ready
   - If no printers found, instruct user to check printer connectivity

2. **Select printer**:
   - Use default printer if available
   - Or let user choose from available printers
   - Or specify printer by name

3. **Identify the source**:
   - Local file path
   - URL for web content
   - Cloud storage file reference

4. **Prepare the file**:
   - For web pages: download content
   - For Office documents: convert to printable format
   - For images: ensure proper format

5. **Print via AirPrint**:
   - Use the `lpr` command with AirPrint printer
   - Or use macOS printing system via `lp` command

## Commands

### List available printers
```bash
lpstat -p -d
```

### Check printer status
```bash
lpstat -p "Printer Name"
```

### Print a file
```bash
lpr -P "Printer Name" /path/to/file.pdf
```

### Print with options
```bash
lpr -P "Printer Name" -o media=A4 -o sides=one-sided /path/to/file.pdf
```

### Print web page
```bash
# Download web page content
curl -o /tmp/page.html "https://example.com"

# Print the downloaded content
lpr -P "Printer Name" /tmp/page.html
```

## Error Handling

- If no printer is found, instruct user to check printer connectivity
- If file format is unsupported, suggest conversion to supported format
- For cloud files, ensure proper authentication and download first
- If printer is not responding, check printer status and network connection

## Notes

- AirPrint printers must be on the same network
- Some printers may require specific drivers
- Large files may take time to process
- Physical printing requires actual printer hardware connected to the network
- The skill will automatically detect available printers and use the default printer if available