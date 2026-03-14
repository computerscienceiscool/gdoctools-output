---
revision:
  id: 2
  last revised: "2024-07-02T01:01:16.406Z"
---

# **GDocs2MD**

GDocs2MD is a command-line tool that converts Google Docs documents within a specified Google Drive folder to Markdown format and saves them locally. It also fetches comments and revisions from the documents and saves them along with the main content.

## **Prerequisites**

1. **Go**: Ensure you have Go installed. You can download it from golang.org.  
2. **Google API Credentials**: You'll need a Google Cloud project with the Google Drive and Google Docs APIs enabled. Create OAuth 2.0 credentials and download the `credentials.json` file.

## **Setup**

### **Environment Variables**

Set the following environment variables with the credentials from your Google Cloud project:

* GOOGLE\_CLIENT\_ID: Your OAuth 2.0 client ID.  
* GOOGLE\_CLIENT\_SECRET: Your OAuth 2.0 client secret.  
* GOOGLE\_REDIRECT\_URI: Your OAuth 2.0 redirect URI. This is typically set to `http://localhost:8080`.

You can set these variables in your terminal session using:

export GOOGLE\_CLIENT\_ID="your-client-id"  
export GOOGLE\_CLIENT\_SECRET="your-client-secret"  
export GOOGLE\_REDIRECT\_URI="your-redirect-uri"

### **Install Dependencies**

Run the following command to install the required dependencies:

go mod tidy

## **Usage**

1. Run the Program:  
   go run cmd/main.go  
2. Authorize the Application:  
   * The program will prompt you to open a URL in your browser.  
   * Open the URL, log in to your Google account, and grant the necessary permissions.  
   * Copy the authorization code provided and paste it back into the terminal.  
3. Enter the Google Drive Folder URL:  
   * After authentication, the program will prompt you to enter the URL of the Google Drive folder you want to process.  
   * Paste the folder URL into the terminal and press Enter.  
4. Conversion Process:  
   * The program will retrieve the documents from the specified Google Drive folder.  
   * Each document will be converted to Markdown format, including comments and revisions.  
   * The converted files will be saved in a local folder named after the Google Drive folder.

## **Expected Behavior**

### **Inputs**

* Authorization Code: After opening the URL provided by the program and authorizing access, you'll receive an authorization code. Enter this code into the terminal when prompted.  
* Google Drive Folder URL: Enter the URL of the Google Drive folder containing the documents you want to convert.

### **Outputs**

* The program will create a folder in the current directory named after the Google Drive folder.  
* Inside this folder, you'll find:  
  * Markdown files for each Google Doc in the folder.  
  * Separate Markdown files for each revision of the documents.  
  * Comments included at the end of each document's Markdown file.

## **File Structure**

* cmd/main.go: The main program file.  
* internal/auth: Handles OAuth2 authentication.  
* internal/docs: Contains functions for converting Google Docs to Markdown and saving files.  
* internal/drive: Contains functions for interacting with Google Drive API.

## **License**

This project is licensed under the MIT License. See the LICENSE file for details.


