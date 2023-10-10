# SEC_Doc_Classification
Project related to document classification, where PDFs are processed to extract text, and then machine learning is applied to classify them into different categories based on their content. The code is well-commented and organized into different sections to perform each specific task in the workflow.

The names of the sub-directories in forms directory represent the 9 document classes namely: 82_Submissions_FS, Form_11K, Form_13F, Form_19B4, Form_6K, Form_D, Form_TA2, Form_X17A5 and Others.

text_based_doc_classification Python script performs the following tasks:

Web Scraping and PDF Downloading: It scrapes the SEC (U.S. Securities and Exchange Commission) website to download PDF files from various directories. It uses the requests library to send HTTP requests, BeautifulSoup for parsing HTML, and pdf2image to convert the first page of PDFs to images. PDFs are downloaded and stored in a directory structure based on the directory hierarchy of the SEC website.

Data Augmentation: After downloading the PDFs, it checks the number of images in each folder and duplicates them to ensure each folder has at least 200 images. This is a form of data augmentation to balance the dataset.

Text Preprocessing: The script defines a function preprocess_text to preprocess text data. It removes common stopwords and performs basic text cleaning.

Text and Image Data Integration: It extracts text from the first page of each PDF image using OCR (Optical Character Recognition) via Tesseract. The extracted text is preprocessed using the preprocess_text function. Both the text and the image data are used in subsequent steps.

Feature Extraction: TF-IDF (Term Frequency-Inverse Document Frequency) vectors are created from the preprocessed text data. This step converts text data into numerical features suitable for machine learning. The TF-IDF scores are computed for each word, and the top 1000 features (words) are selected.

Model Training and Evaluation: It splits the dataset into training and testing sets (80% training, 20% testing). It trains a Support Vector Machine (SVM) classifier with a linear kernel on the TF-IDF features. The model's accuracy is evaluated on the test set, and a classification report is generated.

Printing Top Words: The script prints the top 100 words (features) based on their TF-IDF scores, providing insights into the most important words in the dataset.

Result for the text-based model:

<img width="352" alt="image" src="https://github.com/adishinde2110/SEC_Doc_Classification/assets/93417446/a205284c-c7b7-4ecb-bfaa-f6f0b0a6ee93">


Text-based classification yields better results compared to image-based approach like Convolutional Neural Networks (CNN) when dealing with documents that have similar formats because text carries more semantic information and is inherently more structured and interpretable. In the case of forms or documents with consistent layouts, textual content contains valuable context, keywords, and patterns that can be leveraged for classification. Text-based models can exploit linguistic features, such as keywords, phrases, and the relationship between words, to discern the meaning and purpose of a document effectively. Additionally, text data is usually less resource-intensive to process and requires smaller datasets for training, making it more practical when labeled data is limited. While CNNs excel at image recognition tasks, documents with similar layouts may not have enough visual diversity to differentiate them effectively, and text-based models can provide superior accuracy by focusing on the content of the text.
