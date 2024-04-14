## Face Recognition API
Face Recognition API is part of an application designed for student attendance verification during classes. Below you will find basic configuration information and usage instructions.

## Features
Fetches encoded class names to retrieve student images from a database.
Recognizes students based on the provided image using facial recognition.
Marks unrecognized faces and distinguishes between known and unknown individuals.
## Prerequisites
Before you begin, ensure you meet the following requirements:

Python 3.6 or higher
Flask web framework
face_recognition library
NumPy
Pillow
PyODBC
ODBC driver for SQL Server
SQL Server with 'Students' and 'Classes' tables
## Installation
To install the necessary libraries, run the following commands:

```bash
pip install Flask
pip install face_recognition
pip install numpy
pip install Pillow
pip install pyodbc
```
## Configuration
Edit the DATABASE_CONNECTION_STRING to point to your SQL Server instance and provide appropriate authentication credentials.

```bash
DATABASE_CONNECTION_STRING = 'DRIVER={ODBC Driver 17 for SQL Server};Server=YOUR_SERVER;Database=Your_Database;Port=YOUR_PORT;UID=YOUR_UID;PWD=YOUR_PASSWORD;'
```
Set FACE_SIMILARITY_THRESHOLD according to your needs to adjust the sensitivity of face recognition.

## Running the Application
To run the server, navigate to the directory containing the application and execute:

```bash
python app.py
```
## Usage
The application provides two endpoints:

- /class
This endpoint accepts POST requests with a JSON payload containing the key 'klasa', representing the encoded class name.

```json
{
    "klasa": "encoded_class_name"
}
```
It retrieves images of students belonging to the specified class from the database and prepares them for recognition.

- /recognize
This endpoint also accepts POST requests with a JSON payload containing keys 'klasa' and 'image', where 'image' is a base64-encoded string representing the image to be processed.

```json
{
    "klasa": "encoded_class_name",
    "image": "base64_encoded_image"
}
```
It handles recognition of students and detects individuals not belonging to the class.

## SSL Configuration
To run the application with SSL, provide the path to the fullchain.pem and privkey.pem files in the ssl_context argument of the app.run() method.

## Authors
- Jakub Michalski
- Mateusz Snela

## License
This project is licensed under the [MIT License](LICENSE).
