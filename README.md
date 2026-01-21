# Document-ProcessingOCR

This repository demonstrates document processing using Optical Character Recognition (OCR) with `pytesseract` and agent creation with `LangChain`. It includes examples of extracting text from images, defining custom tools for OCR, and integrating them into an AI agent workflow.

## Features

- **OCR Text Extraction**: Extract text from images and scanned documents using Tesseract OCR
- **LangChain Integration**: Create intelligent AI agents that can process documents
- **Custom Tools**: Define and integrate custom OCR tools into agent workflows
- **Image Processing**: Support for various image formats (PNG, JPG, TIFF, etc.)
- **Automated Workflows**: Build end-to-end document processing pipelines

## Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.8 or higher
- Tesseract OCR engine
- pip (Python package installer)

### Installing Tesseract OCR

**On Ubuntu/Debian:**
```bash
sudo apt-get update
sudo apt-get install tesseract-ocr
```

**On macOS:**
```bash
brew install tesseract
```

**On Windows:**
Download the installer from [GitHub](https://github.com/UB-Mannheim/tesseract/wiki) and follow the installation instructions.

## Installation

1. Clone the repository:
```bash
git clone https://github.com/majortank/Document-ProcessingOCR.git
cd Document-ProcessingOCR
```

2. Create a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install required Python packages:
```bash
pip install pytesseract langchain pillow opencv-python
```

## Usage

### Basic OCR Example

```python
import pytesseract
from PIL import Image

# Load an image
image = Image.open('path/to/your/document.png')

# Extract text
text = pytesseract.image_to_string(image)
print(text)
```

### Using with LangChain Agents

```python
from langchain.agents import Tool
from langchain.agents import initialize_agent
import pytesseract
from PIL import Image

# Define custom OCR tool
def ocr_tool(image_path):
    image = Image.open(image_path)
    return pytesseract.image_to_string(image)

# Create tool for agent
tools = [
    Tool(
        name="OCR",
        func=ocr_tool,
        description="Useful for extracting text from images"
    )
]

# Initialize agent (requires LLM configuration)
# agent = initialize_agent(tools, llm, agent="zero-shot-react-description")
```

## Project Structure

```
Document-ProcessingOCR/
├── README.md           # This file
├── LICENSE            # GPL-3.0 License
├── .gitignore         # Git ignore patterns
└── examples/          # (To be added) Example scripts and notebooks
```

## Technologies Used

- **[Tesseract OCR](https://github.com/tesseract-ocr/tesseract)**: Open-source OCR engine
- **[pytesseract](https://pypi.org/project/pytesseract/)**: Python wrapper for Tesseract
- **[LangChain](https://github.com/langchain-ai/langchain)**: Framework for developing LLM applications
- **[Pillow](https://python-pillow.org/)**: Python Imaging Library for image processing
- **[OpenCV](https://opencv.org/)**: Computer vision library for advanced image preprocessing

## Use Cases

- Invoice and receipt processing
- Business card data extraction
- Document digitization
- Form processing automation
- ID card and passport scanning
- Handwritten text recognition (with appropriate Tesseract training)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Tesseract OCR team for the powerful OCR engine
- LangChain community for the agent framework
- All contributors and users of this project

## Support

If you encounter any issues or have questions, please file an issue on the GitHub repository issue tracker.
