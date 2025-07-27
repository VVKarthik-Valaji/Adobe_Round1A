# Adobe - Connecting the Dots Challenge (Round 1A)

## Challenge 1a: PDF Processing Solution

### ✅Overview
This solution processes PDF files located in the `/app/input` directory, extracts the document structure (headings and subheadings), and outputs the extracted content as JSON files in the `/app/output` directory. It uses Python and PyMuPDF (`fitz`) for PDF text extraction. The solution is optimized to meet the Adobe India Hackathon 2025 Challenge requirements, including performance and resource constraints.

The solution is containerized using Docker, ensuring easy deployment and cross-platform compatibility.




---
### 🐳Build Command
To build the Docker image for the PDF processing solution, run the following command:

```bash
docker build --platform linux/amd64 -t adobe-outline-extractor .
```
### ▶️Run Command
To run the solution with the input PDFs located in the input directory and generate output in the output directory, execute the following command:
```bash
docker run --rm -v $(pwd)/input:/app/input -v $(pwd)/output:/app/output --network none adobe-outline-extractor
```
### 📁 Project Structure

```text
Challenge_1a/
├── input/                # Input PDF files
├── output/               # Generated JSON output files
├── Dockerfile            # Docker container configuration
├── main.py               # Main PDF processing script
├── utils.py              # Helper functions for outline extraction
└── requirements.txt      # Required Python dependencies
```
---

### ⚙️Input
Place your `.pdf` files in the `/input` directory.



### 📤Output
The extracted outline will be generated as `.json` files in the `/output` directory.

---

### Output Format

```json
{
  "title": "Document Title",
  "outline": [
    { "level": "H1", "text": "Heading One", "page": 1 },
    { "level": "H2", "text": "Subheading", "page": 2 }
  ]
}

```
### 🧠 How it works

- PDF File Scanning: The solution processes all PDF files found in /app/input.

- Text Extraction: It extracts the document structure, identifying headings and subheadings by analyzing font sizes using PyMuPDF.

- JSON Output: Structured JSON files are generated for each PDF, including the document title and the outline hierarchy.

### Note: 
The heading detection logic is based on the most common font sizes and can be refined for improved accuracy based on specific document layouts.

---

### 📦 Required Libraries
PyMuPDF: Used for PDF text extraction (fitz library).
Install dependencies with:

```bash
pip install PyMuPDF==1.23.7
```
All dependencies are listed in requirements.txt.


### 🪪 License
This project is licensed under the [MIT License](https://opensource.org/licenses/MIT)

