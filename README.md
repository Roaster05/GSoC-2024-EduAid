# GSoC-2024 EduAid: Refactoring and Publishing EduAid
---

This report details the project work titled **"Refactoring and Publishing EduAid"** undertaken during **Google Summer of Code 2024** under the mentorship of **AOSSIE**. My name is Krishna Madhwani, and as a Computer Science and Engineering student at IIT BHU, I was fortunate to have this incredible opportunity to contribute to **EduAid** during GSoC'24. During my time in GSoC 2024, I focused on significantly advancing the EduAid Chrome extension by incorporating new features and refining its existing functionalities. My primary goal was to enhance the platform’s versatility and usability for both educators and students.

<div style="display: flex; align-items: center;">
  <img src="https://aossie.org/logo1.png" alt="Alt text" style="width: 300px; height: auto; margin-right: 20px;" />
  <img src="https://numfocus.org/wp-content/uploads/2017/11/gsoc2017.png" alt="Alt text" style="width: 600px; height: 300px;" />
</div>

## Overview

- **Organization:** AOSSIE
- **Project:** [EduAid: Refactoring and Publishing EduAid](https://summerofcode.withgoogle.com/programs/2024/projects/tnijgajk)
- **Contributor:** Krishna Madhwani ([Roaster05](https://github.com/Roaster05))
- **Mentors:** Prarabdh Shukla, Divyanshu Singh
- **Repository:** [EduAid Repository](https://github.com/AOSSIE-Org/EduAid)

## Key Contributions

### 1. Enhanced Question Generator Model 🧠

- **Timeline:** Week 1-2
- **PR:** [#40](https://github.com/AOSSIE-Org/EduAid/pull/40)
- **Status:** Merged
- **Description:** Upgraded the question generator to support a wider variety of question types, including Multiple Choice, Single Correct, and Boolean Questions.

  **Implementation Details:**

  - **Multiple Choice Questions (MCQs):**
    - **Model Choice:** Used the T5 model, known for its text-to-text transfer capabilities, to generate concise and relevant questions from given content.
    - **Distractors Generation:** Utilized NLP libraries such as `nltk` and `gensim` for synonym generation and semantic similarity. Techniques like word embeddings and contextual analysis were applied to ensure distractors were plausible and challenging.
    - **Contextual Fit:** Applied Named Entity Recognition (NER) to ensure that generated options were contextually relevant and grammatically correct.
  
  - **One Word Questions:**
    - **Keyword Extraction:** Employed T5 and Multipartite Rank for extracting significant keywords from text. 
    - **Question Generation:** Used these keywords to form questions by analyzing the context and syntactical structure of sentences.
  
  - **Boolean Questions:**
    - **Statement Simplification:** Used T5 for summarizing statements into true/false propositions. 
    - **False Statement Generation:** Generated false statements by altering the sentence structure or using paraphrasing techniques to ensure the statements were grammatically correct and logically sound.
    - **Evaluation:** Used BERT embeddings to evaluate the semantic similarity between true and generated false statements.

### 2. Added Google Docs Support 📄

- **Timeline:** Week 3-4
- **PR:** [#41](https://github.com/AOSSIE-Org/EduAid/pull/41)
- **Status:** Merged
- **Description:** Integrated support for Google Docs, enabling users to generate quizzes directly from shared documents.

  **Implementation Details:**

  - **Google Docs API Integration:**
    - **API Setup:** Configured OAuth 2.0 for authorization to access Google Docs content.
    - **Content Retrieval:** Implemented a parser to extract text from Google Docs using the Google Docs API.
    - **Content Parsing:** Processed and cleaned extracted text to remove unnecessary formatting and extract meaningful content for quiz generation.
    - **Error Handling:** Implemented error handling for cases where documents might not be accessible or content extraction fails.

### 3. Added Support for Other Input/Output Mediums

- **Timeline:** Week 5-6
- **PR:** [#44](https://github.com/AOSSIE-Org/EduAid/pull/44)
- **Status:** Merged
- **Description:** Enabled support for various file formats like `.docx`, `.pdf`, and `.txt`.

  **Implementation Details:**

  - **FileProcessor Class:**
    - **PDF Handling:** Used libraries like `PyMuPDF` and `pdfplumber` to extract text from PDF files while preserving the document structure as much as possible.
    - **DOCX Handling:** Implemented functionality using `python-docx` to read and process `.docx` files, extracting text and handling different document styles.
    - **TXT Handling:** For `.txt` files, implemented basic text reading and parsing techniques to handle plain text extraction.
    - **Error Handling:** Added mechanisms to manage exceptions and errors related to file processing, ensuring robust and fault-tolerant operations.

### 4. Improved Usability with SidePanel API

- **Timeline:** Week 7-8
- **PR:** [#44](https://github.com/AOSSIE-Org/EduAid/pull/44)
- **Status:** Merged
- **Description:** Enhanced user experience by utilizing the SidePanel API for better navigation within the extension.

  **Implementation Details:**

  - **SidePanel Integration:**
    - **HTML/CSS:** Developed a dedicated HTML file for SidePanel, including CSS for styling and JavaScript for dynamic content updates.
    - **Manifest Configuration:** Updated `manifest.json` to incorporate SidePanel features, including necessary permissions and configuration.
    - **UI Improvements:** Designed the SidePanel UI to enhance readability and usability, including features like collapsible sections and interactive elements for quiz management.

### 5. Quiz Storage and Retrieval ⌛

- **Timeline:** Week 7-8
- **PR:** [#46](https://github.com/AOSSIE-Org/EduAid/pull/46)
- **Status:** Merged
- **Description:** Implemented local storage to maintain the last 5 quizzes and allow users to view and manage quizzes.

  **Implementation Details:**

  - **Local Storage Implementation:**
    - **Storage Mechanism:** Used the browser's local storage API to save and retrieve quiz data. Implemented data serialization and deserialization to handle quiz objects.
    - **UI Updates:** Developed a user interface to display recent quizzes, allowing users to select and view previous quizzes. 
    - **State Management:** Incorporated state management techniques to handle quiz data dynamically and ensure consistent behavior across different sessions.

### 6. Added Wiki-Based Support and Answer Generation 🌐

- **Timeline:** Week 9-10
- **PR:** [#47](https://github.com/AOSSIE-Org/EduAid/pull/47)
- **Status:** Merged
- **Description:** Added the ability to generate quizzes from Wikipedia content to expand the range of quiz topics.

  **Implementation Details:**

  - **Wikipedia API Integration:**
    - **API Setup:** Configured access to the Wikipedia API to retrieve articles and content.
    - **Content Extraction:** Implemented a content parser to extract relevant information from Wikipedia articles, including section headings and text.
    - **Content Filtering:** Applied filtering techniques to remove irrelevant sections and focus on key information suitable for quiz generation.

### 7. Generating Form-Based Quiz and Answer Key

- **Timeline:** Week 11-12
- **PR:** [#48](https://github.com/AOSSIE-Org/EduAid/pull/48)
- **Status:** Merged
- **Description:** Added functionality to generate form-based quizzes and answer keys in PDF format.

  **Implementation Details:**

  - **PDF Generation:**
    - **Library Choice:** Used `PDFDocument` to create and format quiz PDFs. Implemented functions to generate questions and answer keys based on quiz content.
    - **Dynamic Fields:** Added support for dynamic form fields in the PDF to allow users to fill in answers directly within the document.
    - **Formatting:** Ensured proper formatting and layout for quizzes and answer keys to enhance readability and usability.

### 8. Backend Script and Documentation

- **Timeline:** Week 11-12
- **PR:** [#50](https://github.com/AOSSIE-Org/EduAid/commit/423be8a2deaaa96df01efad9173888226e032072)
- **Status:** Merged
- **Description:** Automated the Flask app setup and provided detailed documentation for installation and contributions.

  **Implementation Details:**

  - **Backend Script:**
    - **Setup Automation:** Developed a script to automate Flask app setup, including dependency installation and configuration.
    - **Configuration Management:** Included settings and environment variables necessary for running the Flask app.
  
  - **Documentation:**
    - **Installation Instructions:** Provided step-by-step instructions for setting up the development environment and running the Flask app.
    - **Feature Documentation:** Documented features and usage of the EduAid extension and backend, including examples and configuration options.
    - **Contribution Guidelines:** Included guidelines for contributing to the project, including code standards and pull request procedures.

## PR Overview

| PR Link | Description | Status |
| :-------: | ------- | ------- |
| [#40](https://github.com/AOSSIE-Org/EduAid/pull/40) | Initialized Question Generator Model | Merged |
| [#41](https://github.com/AOSSIE-Org/EduAid/pull/41) | Added Google Docs Support | Merged |
| [#44](https://github.com/AOSSIE-Org/EduAid/pull/44) | Added SidePanel, PDF Generation | Merged |
| [#46](https://github.com/AOSSIE-Org/EduAid/pull/46) | Added Previous Quiz Feature, Refactored UI | Merged |
| [#47](https://github.com/AOSSIE-Org/EduAid/pull/47) | Added Wiki-Based Content Support and Refactored Code | Merged |
| [#48](https://github.com/AOSSIE-Org/EduAid/pull/48) | Added Answer Generator | Merged |
| [#50](https://github.com/AOSSIE-Org/EduAid/commit/423be8a2deaaa96df01efad9173888226e032072) | Added Backend Script | Merged |

## Final Outcome

[**Screencast from 2024-08-25**](https://github.com/user-attachments/assets/231861c5-9f47-43c3-82e3-a1e4fe106f4c)

