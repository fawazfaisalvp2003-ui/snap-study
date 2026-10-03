# 📚 Snap & Study

**Snap & Study** is an AI-powered study assistant that helps students understand difficult study materials using **Google Gemini**.

Instead of manually searching for explanations, students can simply **take or upload a photo of a textbook page, problem, diagram, notes, or other study material**, or type a question directly into the application.

Snap & Study analyzes the provided material and explains it in **simple, student-friendly language**. Students can also send the generated explanation directly to their **WhatsApp** for later reference.

## ✨ Features

### 📸 Snap a Study Material

Students can upload a:

* Textbook page
* Mathematical problem
* Diagram
* Handwritten notes
* Technical question
* Study-related image
* Other learning material

Supported image formats:

```text
JPG
JPEG
PNG
```

The uploaded image is analyzed by Google Gemini.

### 💬 Ask Questions

Students can also type questions directly into the chat.

For example:

```text
Explain the difference between TCP and UDP.
```

or:

```text
How does this algorithm work?
```

Snap & Study uses Gemini to provide an explanation based on the student's question.

### 🧠 AI-Powered Explanation

When a student uploads study material, Snap & Study asks the AI to:

1. Identify what is shown.
2. Explain what it is.
3. Explain the key concept.
4. Provide a step-by-step solution or breakdown when applicable.
5. Highlight important points to remember.

The goal is to make difficult study material easier to understand.

### 🎓 Student-Friendly Responses

The application is designed to explain concepts in language that is easy for students to understand rather than simply returning a complex technical answer.

Students can continue asking questions within the same conversation.

### 💭 Conversational Study Session

Snap & Study maintains the Gemini chat session during the current application session.

This allows students to continue discussing a topic instead of starting a completely new conversation for every question.

### 📱 Send Explanation to WhatsApp

Students can send the generated study explanation to their WhatsApp.

When the student clicks:

```text
📤 Send to WhatsApp
```

Snap & Study:

1. Creates a study explanation/summary from the conversation.
2. Formats it for WhatsApp.
3. Sends it to the student's registered WhatsApp number using Twilio.

This allows students to keep important explanations on their phone for later revision.

### 👤 Simple Student Onboarding

When the application starts, the student enters:

* Name
* WhatsApp number with country code

Example:

```text
Name: Fawaz
WhatsApp: +91XXXXXXXXXX
```

After onboarding, the student can start the study session.

## 🔄 How Snap & Study Works

```text
              Student
                 │
                 ▼
       Enter Name & WhatsApp
                 │
                 ▼
          Snap & Study
           Streamlit App
                 │
          ┌──────┴──────┐
          │             │
          ▼             ▼
    Upload Photo    Ask Question
          │             │
          └──────┬──────┘
                 ▼
          Google Gemini
                 │
                 ▼
       Understand Material
                 │
                 ▼
       Explain in Simple
       Student-Friendly Way
                 │
                 ▼
            AI Answer
                 │
                 ▼
        Continue Studying
                 │
                 ▼
       Send to WhatsApp
                 │
                 ▼
              Twilio
                 │
                 ▼
          📱 WhatsApp
```

## 🛠️ Technology Stack

| Technology           | Purpose                                                      |
| -------------------- | ------------------------------------------------------------ |
| **Python**           | Application development                                      |
| **Streamlit**        | Web application and chat interface                           |
| **Google Gemini**    | Understanding images, questions, and generating explanations |
| **Google GenAI SDK** | Gemini API integration                                       |
| **Twilio**           | WhatsApp messaging                                           |
| **Git & GitHub**     | Version control and source code management                   |

## 📁 Project Structure

```text
snap-study/
│
├── .streamlit/
│   └── secrets.toml
│
├── app.py
├── prompts.py
├── requirements.txt
├── .gitignore
└── README.md
```

### `app.py`

The main application file.

It handles:

* Streamlit interface
* Student onboarding
* Image uploads
* Text questions
* Gemini communication
* Conversation management
* Study explanations
* WhatsApp message sending

### `prompts.py`

Contains the instructions used to control how the AI responds to students.

It includes:

* System prompt
* Welcome message
* Study summary prompt

### `requirements.txt`

Contains the Python packages required to run the application.

## 📦 Requirements

The project uses:

```text
google-genai
streamlit
twilio
```

You also need:

* Python 3.10 or later
* Google Gemini API key
* Twilio account
* Twilio WhatsApp configuration

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/fawazfaisalvp2003-ui/snap-study.git
cd snap-study
```

### 2. Create a virtual environment

On Windows:

```powershell
python -m venv venv
```

### 3. Activate the virtual environment

```powershell
.\venv\Scripts\Activate.ps1
```

If PowerShell prevents activation, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then activate the environment again:

```powershell
.\venv\Scripts\Activate.ps1
```

### 4. Install dependencies

```powershell
pip install -r requirements.txt
```

## 🔐 Configuration

Snap & Study requires Google Gemini and Twilio credentials.

Create:

```text
.streamlit/secrets.toml
```

Add:

```toml
GEMINI_API_KEY = "your_gemini_api_key"

TWILIO_ACCOUNT_SID = "your_twilio_account_sid"
TWILIO_AUTH_TOKEN = "your_twilio_auth_token"
TWILIO_WHATSAPP_FROM = "your_twilio_whatsapp_sender"
TWILIO_CONTENT_SID = "your_twilio_content_sid"
```

**Never upload `secrets.toml` to GitHub.**

Your `.gitignore` should keep sensitive configuration out of version control.

## ▶️ Run the Application

Activate the virtual environment and run:

```powershell
python -m streamlit run app.py
```

The application will normally be available at:

```text
http://localhost:8501
```

## 📱 WhatsApp Integration

Snap & Study uses **Twilio WhatsApp messaging** to send study explanations to the student's registered WhatsApp number.

When the student selects **Send to WhatsApp**, the application asks Gemini to prepare an explanation based on the current study conversation and then sends the result through Twilio.

## 🤖 AI Processing

Google Gemini is used for both text and image-based study assistance.

For an uploaded study image, the application can:

* Understand the content of the image
* Identify the topic or problem
* Explain the concept
* Provide a step-by-step breakdown when applicable
* Highlight important information

For text questions, Gemini provides conversational study assistance.

## 🔒 Security

Never publish:

* Gemini API keys
* Twilio Account SID
* Twilio Auth Token
* WhatsApp credentials
* Other private credentials

Store these values in:

```text
.streamlit/secrets.toml
```

and make sure the file is excluded by `.gitignore`.

## 🌐 Deployment

Snap & Study can be deployed using **Streamlit Community Cloud**.

Use:

```text
Repository: fawazfaisalvp2003-ui/snap-study
Branch: main
Main file: app.py
```

Configure the required API credentials through Streamlit's deployment secrets rather than uploading `secrets.toml` to GitHub.

## 🎯 Use Cases

Snap & Study can be useful for students who want to:

* Understand textbook content
* Get help with difficult questions
* Understand diagrams
* Break down complex concepts
* Get step-by-step explanations
* Review study notes
* Keep AI-generated explanations on WhatsApp

## 🔗 GitHub Repository

https://github.com/fawazfaisalvp2003-ui/snap-study

## 👨‍💻 Author

**Fawaz Faisal**

Snap & Study is an AI-powered educational assistant combining image understanding, conversational AI, and WhatsApp messaging to make studying easier and more accessible.
