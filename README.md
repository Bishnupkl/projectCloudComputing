# Auth Application - Final Project  
**Name:** Bishnu Pokhrel  
**Student ID:** 618084

## Project Summary  
This project is a serverless authentication application that allows users to register, log in, and manage their profiles, including the ability to upload a profile image. It meets the following functional requirements:

## Key Features  

### 1. **User Registration (Sign Up)**  
Users can create an account by providing the following information:
- **Email**: Used as the unique identifier for the user.
- **Password**: Stored securely in hashed form.
- **Name**: Displayed on the user’s profile.
- **Profile Image**: Users can upload a profile image to an S3 bucket via a signed URL.

### 2. **User Login**  
Once registered, users can log in by entering their email and password. Upon successful login, a token is generated and the user is redirected to their profile page.

### 3. **Profile Management**  
- **View Profile**: After logging in, users can view their profile, which includes their email, the date their account was created, and their profile image.
- **Update Profile Image**: Users can select and preview a new profile image before uploading it. When a new image is uploaded, the old one is deleted from S3, and the new image URL is saved in DynamoDB.
- **Logout**: Users can log out, which removes the session token and redirects them to the login page.

### 4. **Session Handling**  
- A token is stored in the browser's localStorage on login, allowing users to stay logged in and access their profile without needing to reauthenticate when reopening the app.
- Logging out clears the session token and redirects the user back to the login page.

## Technology Stack  

### Frontend:
- **ReactJS**: The frontend is built with React, utilizing a component-based architecture.
- **S3**: The frontend is hosted in an S3 bucket for scalable, cost-effective static web hosting.
- **CloudFront**: A CDN (Content Delivery Network) is used to deliver the frontend efficiently and with low latency.

### Backend:
- **Node.js 20.x**: The backend consists of serverless AWS Lambda functions that handle user registration, login, and profile management.
- **AWS API Gateway**: Acts as the HTTP endpoint that routes requests to the appropriate Lambda functions.
- **DynamoDB**: A NoSQL database stores user data, including email, hashed passwords (with salt), names, and profile image URLs.
- **S3**: Used to store user profile images, with signed URLs generated for secure uploads and updates.

### Serverless Architecture:  
The entire application is built using AWS serverless services, ensuring scalability, cost efficiency, and minimal management effort.

### CloudFormation:  
A CloudFormation template is used to provision the required AWS infrastructure, including S3, CloudFront, API Gateway, Lambda, and DynamoDB. This simplifies the deployment and setup of the application.

### CI/CD Pipeline:  
A continuous integration and deployment (CI/CD) pipeline is set up for the frontend using AWS tools. The pipeline automatically builds and deploys the React application to S3 and invalidates the CloudFront cache to reflect updates.

## Setup and Deployment  

### Prerequisites:
- An AWS account
- Node.js installed for local development
- AWS CLI configured for managing AWS resources

### Frontend Setup:  
1. Clone the repository and navigate to the frontend directory:
   ```bash
   git clone <repository-url>
   cd frontend
   ```