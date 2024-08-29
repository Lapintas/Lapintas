from docx import Document
import pdfkit

def word_to_pdf(input_file, output_file):
    # Read the Word document
    doc = Document(input_file)
    
    # Save the document text to a temporary HTML file
    temp_html = "temp.html"
    with open(temp_html, "w") as f:
        for paragraph in doc.paragraphs:
            f.write(paragraph.text + "<br>")
    
    # Convert the HTML file to a PDF
    pdfkit.from_file(temp_html, output_file)
    print(f"PDF created successfully: {output_file}")

# Example usage
input_word_file = "example.docx"
output_pdf_file = "output.pdf"
word_to_pdf(input_word_file, output_pdf_file)
