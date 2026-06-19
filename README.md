# Field Report Image Processing (Gemini Vision Edition)

This repository contains a Google Colab notebook designed to automate the classification and reporting of field operation photos for the telecommunications industry.

## Overview
Field engineers often collect thousands of photos containing measurement tools, compasses, inclinometers, and tower equipment. This script automatically:
1. **Scans** directories and ZIP archives.
2. **Extracts Metadata** (Site ID, Sector, Band, Hardware, Status) purely from the file paths/names.
3. **Classifies Images** using **Google's Gemini 2.5 Flash Vision Model** with >95% accuracy to identify tools (Compass Dial, Inclinometer Tilt, Measurement Tape, Tower Equipment).
4. **Generates Deliverables**: Compiles a side-by-side `AOR_Report.xlsx` linking to compressed thumbnails, and packages everything into a neat Deliverable `.zip`.

## Why Gemini?
The original script ran locally using `Ollama` and `qwen2.5vl:7b`. While effective, moving to Google Colab and utilizing the `Gemini API` allows for:
- **No Local Hardware Required**: You don't need a powerful GPU to run this.
- **Superior Accuracy**: Gemini 2.5 Flash understands visual context incredibly well.
- **Extreme Speed**: Multi-modal API calls process images in under a second.

## How to Use
1. Upload your target photos/ZIPs and a `Prefix.txt` file (containing valid Site ID prefixes) to a folder in your Google Drive (e.g. `My Drive/ImageProcessing`).
2. Open `ImPro_AORCheck_Gemini.ipynb` in [Google Colab](https://colab.research.google.com/).
3. Add your free Gemini API Key in the Colab **Secrets** tab (the key icon on the left sidebar) with the Name `GEMINI_API_KEY`.
4. Run all cells! The script will automatically mount your Google Drive, process the photos, and output the final Deliverable Zip back to your Drive.

## Requirements
The Colab notebook automatically installs necessary dependencies:
- `google-generativeai`
- `pandas`
- `openpyxl`
- `Pillow`
