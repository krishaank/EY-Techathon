Pragati Backend Service

This repository contains the source code for a Flask-based backend service designed to support a multilingual financial management and assistance platform, "Pragati." The platform integrates MongoDB for user data storage, AWS S3 for document uploads, Firebase for user notifications, and Google Translate API for language support.

Features

User Registration: Allows users to register with details such as name, location, income, occupation, and preferred language.

Document Upload: Users can upload documents, which are stored securely in an AWS S3 bucket.

Text Translation: Provides multilingual support by translating user input to the specified language using Google Translate.

Financial Schemes Recommendation: Returns a mock list of government schemes for users.

Financial Goal Setting: Enables users to set and manage financial goals.

User Notifications: Sends push notifications to users using Firebase Cloud Messaging (FCM).

Prerequisites

Python 3.8 or above

MongoDB Atlas Account

AWS Account with S3 bucket

Firebase Project with a Service Account

Google Translate API

Installation

1. Clone the Repository

$ git clone https://github.com/your-repository/pragati-backend.git
$ cd pragati-backend

2. Install Dependencies

$ pip install -r requirements.txt

3. Configure Environment Variables

Set the following environment variables or replace placeholders in the code:

MongoDB Atlas URI: MONGODB_URI (replace <username> and <password> with your credentials)

AWS Credentials: AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, REGION

Firebase Service Account Path: Update path/to/firebase-service-account.json with the path to your Firebase JSON file

4. Run the Application

$ python app.py

The application will start on http://127.0.0.1:5000 by default.

API Endpoints

1. User Registration

Endpoint: /user/registerMethod: POSTPayload:

{
  "name": "John Doe",
  "location": "New York",
  "income": 50000,
  "occupation": "Teacher",
  "language": "en"
}

Response:

{
  "message": "User registered successfully!",
  "user_id": "<generated_user_id>"
}

2. Upload Document

Endpoint: /user/uploadMethod: POSTPayload: Multipart form data containing user_id and file.
Response:

{
  "message": "Document uploaded successfully!",
  "file_url": "https://<bucket_name>.s3.amazonaws.com/<file_path>"
}

3. Translate Text

Endpoint: /user/translateMethod: POSTPayload:

{
  "text": "Hello",
  "language": "es"
}

Response:

{
  "translated_text": "Hola"
}

4. Get Scheme Recommendations

Endpoint: /user/schemesMethod: GETResponse:

{
  "schemes": [
    {"name": "PMJDY", "description": "Jan Dhan Yojana"},
    {"name": "PM MUDRA", "description": "MUDRA Loan Scheme"}
  ]
}

5. Set Financial Goals

Endpoint: /user/goalsMethod: POSTPayload:

{
  "user_id": "<user_id>",
  "goal_name": "Buy a house",
  "target_amount": 100000,
  "current_savings": 20000
}

Response:

{
  "message": "Goal added successfully!"
}

6. Send Notification

Endpoint: /user/notifyMethod: POSTPayload:

{
  "title": "Reminder",
  "body": "Don't forget to save for your goals!",
  "token": "<firebase_device_token>"
}

Response:

{
  "message": "Notification sent successfully!",
  "response": "<firebase_response>"
}

Technologies Used

Flask: Web framework for Python

MongoDB Atlas: Cloud-based NoSQL database

AWS S3: Secure file storage

Firebase: Cloud messaging for user notifications

Google Translate API: Text translation service


Author

Your Name: Krishank Dubey
Email: krishank.dubey2424@gmail.com

