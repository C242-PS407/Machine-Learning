# Job Recommendation Application Based on CV

This application provides job recommendations based on the user's uploaded CV. By leveraging machine learning models and text processing techniques, the app matches the skills listed in the CV with available job listings and suggests the top three jobs with the highest matching scores.

## How the Files Work
Each file in this project has a specific role to support the overall system. Below is an explanation of how each file functions:

1. **app.py**  
   The main file containing the API to run the application.  
   - **Main functions:**  
     - Route `/recommend`: Accepts a CV in text format as input, processes it through a pipeline (preprocessing, skill parsing, matching score calculation), and generates job recommendations.

2. **matching_model.h5**  
   A deep learning model trained to match skill scores from the CV with skill scores in the job listings.  
   - **Input:**  
     - Skill vectors processed from the CV and job listings.  
   - **Output:**  
     - Matching scores for each job in the list.  

3. **tfidf_vectorizer.json**  
   Contains the TF-IDF vectorizer representation to ensure consistent text processing during preprocessing and matching.  
   - **Function:**  
     - Converts skill text into numerical vectors to be used by the model.  

4. **valid_skills.json**  
   A JSON file containing a list of valid skills.  
   - **Function:**  
     - Parses the skill section from the CV and validates the skills against the recognized skill list.  

5. **requirements.txt**  
   A file listing the Python libraries required to run the application.  
   - **Used for:**  
     - Ensuring all dependencies are installed with compatible versions.

## System Workflow
1. **CV Input:**  
   The user uploads a CV in text format via the `/recommend` endpoint.  

2. **Preprocessing and Skill Parsing:**  
   - The CV is processed to extract the skill section.  
   - Extracted skills are validated against the list in `valid_skills.json`.  

3. **Matching Score:**  
   - Validated skills are converted into TF-IDF vectors using `tfidf_vectorizer.json`.  
   - The skill vectors are compared with the vectors in the job listings using the `matching_model.h5` model.  

4. **Job Recommendations:**  
   - The top three jobs with the highest matching scores are selected from the job list.  

5. **Output:**  
   - The API responds with a JSON containing:  
     - **Recognized skills from the CV.**  
     - **Top three recommended jobs along with their matching scores.**
