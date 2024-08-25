# 📚EduAid: Refactoring and Publishing the Ultimate Quiz Generation Platform🚀
---

This report details the project work titled **"Refactoring and Publishing EduAid"** undertaken during **Google Summer of Code 2024** under the mentorship of **AOSSIE**. My name is Krishna Madhwani, and as a Computer Science and Engineering student at IIT BHU, I was fortunate to have this incredible opportunity to contribute to **EduAid** during GSoC'24. During my time in GSoC 2024, I focused on significantly advancing the EduAid Chrome extension by incorporating new features and refining its existing functionalities. My primary goal was to enhance the platform’s versatility and usability for both educators and students.

![Alt text](https://aossie.org/logo1.png) 
![Alt text](https://numfocus.org/wp-content/uploads/2017/11/gsoc2017.png)

## Overview
---
- **Organization:** AOSSIE
- **Project:** [ EduaAid : Refactoring and publishing EduAid](https://summerofcode.withgoogle.com/programs/2024/projects/tnijgajk)
- **Contributor:** Krishna Madhwani ([Roaster05](https://github.com/Roaster05))
- **Mentors:** Prarabdh Shukla, Divyanshu Singh, Harsh Mishra

## Key Contributions
---
### 1. Enhanced Question Generator Model 🧠: 
**Timeline:** Week 1-2
**PR:** [#40](https://github.com/AOSSIE-Org/EduAid/pull/40)
**Status:** Merged
**Description:** Upgraded the question generator to support a wider variety of question types, including Multiple Choice, Single Correct, and Boolean Questions.
**Implementation Details:**
- **Multiple Choice Questions (MCQs)**

    **Step 1: Point-based Abstractive Summarization** ✏️
    - Integrated T5 (Text-to-Text Transfer Transformer) to create concise summaries of the input text.
    - Ranked text segments with TF-IDF and identified keywords via Entity Recognition for MCQ answers.

    **Step 2: Generating Distractors** 🎯
    - Used Co-Hyponyms and libraries like `nltk.corpus.wordnet` or `gensim.models.word2vec` to find synonyms and related terms for distractors.

    **Step 3: Formulating MCQs** 📝
    - Created MCQ statements with the Stanford Question Answering Dataset and T5 Transformer, ensuring contextual fit and grammatical correctness of answer choices.

- **One Word Questions**

    **Step 1: Keyword Extraction** 🔍
    - Extracted relevant keywords using T5 Transformer and Multipartite Rank.

    **Step 2: Question Formation** 💡
    - Generated one-word questions that align with extracted keywords using the Stanford Question Answering Dataset and T5 Transformer.

- **Boolean Questions**

    **True Statements:** ✅
    - Simplified sentences through summarization to create true statements.

    **False Statements:** ❌
    - Analyzed sentence structure with NLTK or SpaCy and generated alternative phrasings using OpenAI GPT-2. 
    - Evaluated "falsehood" with BERT-based sentence embeddings and cosine similarity to identify the most "false" option.
    
### 2. Added Google Docs Support 📄
**Timeline:** Week 3-4
**PR:** [#41](https://github.com/AOSSIE-Org/EduAid/pull/41)
**Status:** Merged
**Description:** Integrated support for Google Docs, enabling users to seamlessly generate quizzes directly from shared documents. This feature streamlines the quiz creation process, making it more accessible and efficient.
**Implementation Details:**
- Added Google Docs Service to extract the document ID, document content and hence using that content in generation of questions.
- Handled various errors and handled secret keys using secure methods.

### 3. Added Support for Other Input/Output Mediums 
**Timeline:** Week 5-6
**PR:** [#44](https://github.com/AOSSIE-Org/EduAid/pull/44)
**Status:** Merged
**Description:** 
**Implementation Details:**

### 4. Improved Usability with SidePanel API 
**Timeline:** Week 7-8
**PR:** [#44](https://github.com/AOSSIE-Org/EduAid/pull/44)
**Status:** Merged
**Description:**  To provide a more user-friendly experience, I utilized the SidePanel API, allowing for smooth and uninterrupted navigation within the extension. This ensures that users can manage their tasks without disrupting their browsing activities.
**Implementation Details:**
- With the recent introduction of the **SidePanel API** in Google Chrome, we utilized this feature to enhance quiz visualization. By creating a dedicated HTML file for SidePanel content and updating the `manifest.json` file accordingly, we integrated the SidePanel API into the extension.
- When a quiz generation request is made from the extension popup, it is sent to the backend model. The response from the backend is then accessed by the SidePanel script, which **populates the SidePanel with the generated content**, providing an enriched user experience.

### 5. Quiz Storage and Retrieval ⌛
**Timeline:** Week 7-8
**PR:** [#46](https://github.com/AOSSIE-Org/EduAid/pull/46)
**Status:** Merged
**Description:**  Added a feature to fetch the previously generated quiz to maintain persistence in the extension, with a beautiful User Interface.
**Implementation Details:**

### 6. Added Wiki based support and answer generation 🌐
**Timeline:** Week 9-10
**PR:** [#47](https://github.com/AOSSIE-Org/EduAid/pull/47)
**Status:** Merged
**Description:**  To expand the scope of quiz creation, I added the ability to generate quizzes based on **external knowledge sources like Wikipedia**. This feature is particularly useful when the primary text is unavailable, ensuring continuous content generation.
**Implementation Details:**
- Added Wiki based support for question generation to broaden the domain.
- Refactored the code including side panel and PDF generation.
- Added routes to generate answer for MCQs and added UI for adding questions, answering questions and updating as needed.

### 7. Generating Form-Based Quiz and AnswerKey
**Timeline:** 
**PR:** 
**Status:** Merged
**Description:**  
**Implementation Details:**

### 8. Backend Script and Documentation
**Timeline:** Week 11-12
**PR:** [#50](https://github.com/AOSSIE-Org/EduAid/commit/423be8a2deaaa96df01efad9173888226e032072)
**Status:** Merged
**Description:**  I automated the Flask app setup with a backend script, created detailed documentation for installation and contributions, and compiled a GSoC report to guide future contributors.
**Implementation Details:**
- Developed a backend script that automates the setup process for the Flask app, including the configuration of necessary external files on the client side.
- Created comprehensive documentation detailing installation steps, feature descriptions, and a contribution guide to assist users and contributors.
- Compiled a GSoC report to provide future contributors with a clear understanding of the project’s core functionalities and the changes made during the past year.


## PR Overview
---
| PR Link | Description | Status |
| :-------: | ------- | ------- |
| [#40](https://github.com/AOSSIE-Org/EduAid/pull/40) | Initialized Question Generator Model | Merged |
| [#41](https://github.com/AOSSIE-Org/EduAid/pull/41) | Added Google Docs Support | Merged |
| [#44](https://github.com/AOSSIE-Org/EduAid/pull/44) | Added SidePanel, PDF Generation | Merged |
| [#46](https://github.com/AOSSIE-Org/EduAid/pull/46) | Added Previous Quiz Feature, Refactored UI | Merged |
| [#47](https://github.com/AOSSIE-Org/EduAid/pull/47) | Added Wiki based Content Support and refactored code | Merged |
| [#48](https://github.com/AOSSIE-Org/EduAid/pull/48) | Added Answer Generator | Merged |
| [#50](https://github.com/AOSSIE-Org/EduAid/commit/423be8a2deaaa96df01efad9173888226e032072) | Added Backend Script | Merged |

## Demo
---
(insert link)

