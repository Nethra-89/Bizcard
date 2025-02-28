Bizcard
Image Upload and OCR Processing
User uploads an image (.png, .jpg, .jpeg) using Streamlit’s file_uploader.
The uploaded image is displayed using st.image().
OCR Processing:
The image is converted into a NumPy array.
EasyOCR reads the text from the image.
Extracted text is stored in a list.
2. Extracting and Structuring Information
The extracted text is categorized into different fields:

Name → First item in the extracted text.
Designation → Second item.
Contact → Identified using + or digit patterns.
Email → Recognized by "@" and ".com".
Website → Recognized by "www" or variations.
Pincode → Identified based on numeric values or Tamil Nadu references.
Company Name → Detected from proper words.
Address → Remaining unclassified text.
Data is cleaned using regular expressions (RegEx) and stored in a dictionary.

3. Storing Data in a SQLite Database
Extracted information is converted into a DataFrame (pandas.DataFrame).
Image is converted to bytes and stored as binary data.
A SQLite database (bizcardx.db) is created if it doesn’t exist.
Table Structure:
arduino
Copy
Edit
name, designation, company_name, contact, email, website, address, pincode, image
The extracted data is inserted into the database using INSERT queries.
4. Viewing and Modifying Data
Previewing Saved Data
Users can view saved business card data using:
SELECT * FROM bizcard_details → Fetches all records.
Data is displayed in a Streamlit DataFrame.
Modifying Records
User selects a name from the dropdown (selectbox).
Corresponding details are displayed in editable text fields.
User updates values and clicks "Modify".
The selected record is deleted and re-inserted with updated values.
5. Deleting Records
User selects a name and designation from dropdowns.
If a match is found, clicking "Delete" removes the record from the database.
6. Technologies Used
Python → Core programming language.
Streamlit → Web app framework.
EasyOCR → Extracts text from images.
SQLite → Stores extracted data.
Pandas → Data manipulation.
NumPy → Image array conversion.
PIL (Pillow) → Handles image files.
RegEx → Cleans extracted text.
