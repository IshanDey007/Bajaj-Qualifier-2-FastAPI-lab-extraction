# 🧪 Lab Report Extraction API

This project is a FastAPI-based OCR service to extract lab test results from lab report images. It returns structured JSON data including test name, result, reference range, unit, and whether the value is outside the normal range.

---

## 🚀 Features

- Extracts lab test names, values, reference ranges, and units from scanned lab reports
- Identifies whether test values fall outside the normal range
- FastAPI-based REST API with `/get-lab-tests` endpoint
- Easy to run locally on Windows, Linux, or macOS

---

## 📁 Project Structure

. ├── main.py # FastAPI app ├── parser.py # OCR and parsing logic ├── utils.py # Reference range validation ├── requirements.txt # Python dependencies ├── run_local.sh # Run script (Linux/macOS) ├── run_local.bat # Run script (Windows)

yaml
Copy
Edit

---

## 🛠️ Setup Instructions

### 1. Install Dependencies

#BASH
pip install -r requirements.txt
Or install manually:

bash
Copy
Edit
pip install fastapi uvicorn pytesseract opencv-python

### 2. Install Tesseract OCR
Windows
Download installer: https://github.com/tesseract-ocr/tesseract

Add this to parser.py:

python
Copy
Edit
pytesseract.pytesseract.tesseract_cmd = r"C:\\Program Files\\Tesseract-OCR\\tesseract.exe"
Linux
bash
Copy
Edit
sudo apt update
sudo apt install tesseract-ocr
macOS
bash
Copy
Edit
brew install tesseract
## ▶️ Running the API
## Option 1: Linux/macOS
bash
Copy
Edit
bash run_local.sh
## Option 2: Windows
Double-click run_local.bat
or run:

bash
Copy
Edit
uvicorn main:app --reload
## 🔍 Testing the API
Open in browser:

arduino
Copy
Edit
http://127.0.0.1:8000/docs
Use Swagger UI to upload an image and test the /get-lab-tests POST endpoint.

### DATASET LINK : https://drive.google.com/file/d/1LzG7oJ-cqGHK9KbwXnWfkWgnQ3xi8Cr9/view
Add this data set to your folder if you want to just run the tests on it locally by using the run_ocr.

✅ Example JSON Output
json
Copy
Edit
{
  "is_success": true,
  "data": [
    {
      "test_name": "HB ESTIMATION",
      "test_value": "9.4",
      "bio_reference_range": "12.0-15.0",
      "test_unit": "g/dL",
      "lab_test_out_of_range": true
    }
  ]
}
## 📌 Notes
This project does not use LLMs (as per problem constraints).

Accuracy depends on image clarity and format.

Regex can be adjusted in parser.py if your report formats vary.

## 📄 License
MIT License. Feel free to modify and use.
