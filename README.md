# 📄 Document Scanner & Business Card Reader

A Flask web application that scans physical documents using a webcam or uploaded image, performs perspective correction, and extracts structured information (name, phone, email, etc.) using OCR and a custom NER (Named Entity Recognition) model.

---

## Features

- **Document Detection** – Automatically locates document corners using OpenCV
- **Perspective Transform** – Corrects skewed/angled document images to a flat, readable view
- **OCR Extraction** – Uses Tesseract OCR to extract raw text from the corrected image
- **NER Predictions** – Identifies and labels entities: `NAME`, `ORG`, `DES`, `PHONE`, `EMAIL`, `WEB`
- **Bounding Box Visualization** – Draws labeled bounding boxes around detected entities on the image

---

## Project Structure

```
├── app.py                  # Main Flask application
├── predictions.py          # NER model inference + OCR pipeline
├── utils.py                # Document scanning + image utilities
├── settings.py             # Path/config constants
├── output/
│   └── model-best/         # Trained spaCy NER model
├── media/                  # Uploaded and processed images
└── templates/
    ├── scanner.html         # Upload + coordinate selection UI
    ├── predictions.html     # Results display
    └── about.html
```

---

## Requirements

- Python 3.8+
- [Tesseract OCR](https://github.com/UB-Mannheim/tesseract/wiki) installed on your system

Install Python dependencies:

```bash
pip install flask opencv-python pytesseract spacy numpy pandas
```

---

## Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/document-scanner.git
   cd document-scanner
   ```

2. **Install Tesseract OCR**
   - Windows: Download installer from [here](https://github.com/UB-Mannheim/tesseract/wiki) and install to `C:\Program Files (x86)\Tesseract-OCR\`
   - macOS: `brew install tesseract`
   - Linux: `sudo apt install tesseract-ocr`

3. **Add your trained NER model**
   Place your spaCy NER model in `./output/model-best/`

4. **Run the app**
   ```bash
   python app.py
   ```

5. Open your browser at `http://127.0.0.1:5000`

---

## Usage

1. **Upload** a photo of a business card or document on the home page
2. **Adjust** the detected corner points if needed
3. Click **Transform** to apply perspective correction
4. Click **Predict** to extract structured entities from the document
5. View labeled results with bounding boxes on the predictions page

---

## NER Labels

| Label   | Description         |
|---------|---------------------|
| `NAME`  | Person's name       |
| `ORG`   | Organization        |
| `DES`   | Job designation     |
| `PHONE` | Phone number        |
| `EMAIL` | Email address       |
| `WEB`   | Website / URL       |

---

## Notes

- The Tesseract path in `predictions.py` is currently set for Windows. Update it for your OS if needed.
- The NER model in `./output/model-best/` must be trained separately using spaCy before running predictions.

---

## License

MIT License
