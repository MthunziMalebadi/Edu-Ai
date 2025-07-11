# Edu-Ai

# Custom Educational Content Generator

This is a browser-based application that allows users to generate AI-powered educational content based on a selected topic, educational level, and content type. It is ideal for students, educators, content creators, and self-learners who want custom materials such as summaries, explanations, quizzes, examples, and common misconceptions.

---

## Features

- Accepts any topic of your choice (e.g., "Photosynthesis", "Newton's Laws", "Blockchain").
- Supports multiple educational levels: Beginner, Intermediate, Advanced.
- Generates the following types of content:
  - Summary
  - Step-by-step Explanation
  - Quiz Questions
  - Real-world Examples
  - Common Misconceptions
- Instant AI-generated output via backend API.
- Option to download generated content as a `.txt` file.
- Responsive and visually clean dark theme UI.

---

## Technologies Used

**Frontend**
- HTML
- CSS (Dark Theme)
- JavaScript (Vanilla)

**Backend (Assumed)**
- Node.js
- Express.js
- OpenAI API or similar text-generation model

---

## Project Structure

CustomContentGenerator/
├── index.html # Main web interface
├── style.css # Styling (dark theme)
├── script.js # JavaScript logic for UI and API interaction
├── server.js # Backend API (sample provided below)
└── README.md # Project documentation

---

## How It Works

### 1. User Interface

Users interact with a form where they enter:

- A topic (e.g., "Climate Change")
- An educational level
- A content type (e.g., "Quiz")

Once submitted, the app:

- Generates a prompt based on the input.
- Sends the prompt to a backend server.
- Displays the generated response.
- Provides an option to save the output as a file.

---

### 2. Prompt Templates

Inside `script.js`, prompts are dynamically created using the following templates:

```js
const templates = {
  summary: (topic, level) => `Summarize the topic "${topic}" for ${level} students.`,
  explanation: (topic, level) => `Explain "${topic}" step by step for ${level} students.`,
  quiz: (topic, level) => `Create quiz questions about "${topic}" for ${level} students.`,
  examples: (topic, level) => `Give real-world examples of "${topic}" for ${level} students.`,
  misconceptions: (topic, level) => `List common misconceptions about "${topic}" for ${level} students.`
};
Backend Setup (Sample)
A basic example using Node.js and the OpenAI API:


// server.js
const express = require('express');
const cors = require('cors');
const { Configuration, OpenAIApi } = require('openai');
require('dotenv').config();

const app = express();
app.use(cors());
app.use(express.json());

const openai = new OpenAIApi(new Configuration({
  apiKey: process.env.OPENAI_API_KEY
}));

app.post('/generate', async (req, res) => {
  const { prompt } = req.body;

  try {
    const completion = await openai.createCompletion({
      model: 'text-davinci-003',
      prompt,
      max_tokens: 500
    });

    res.json({ output: completion.data.choices[0].text.trim() });
  } catch (error) {
    console.error('Error:', error.message);
    res.status(500).json({ error: 'Failed to generate content' });
  }
});

app.listen(3000, () => console.log('Server running on http://localhost:3000'));
Install Dependencies
bash
Copy
Edit
npm install express cors openai dotenv
Create a .env file


OPENAI_API_KEY=your_openai_api_key_here
Start the Server

node server.js
Running the Frontend
Open index.html directly in your browser.

Fill in the topic, level, and content type.

Click the "Generate Content" button.

Wait for the AI-generated output to appear.

Click "Save Output" to download the result as a text file.

UI Design
The interface is styled using a dark theme:

Background: #1e1e1e with contrast containers in #2c2c2c

Primary Accent Color: #5ab9ea

Font: Arial, sans-serif

Interactive elements: Smooth hover effects, rounded corners, clear text contrast

Deployment Recommendations
Frontend: Can be deployed on GitHub Pages, Netlify, or Vercel.

Backend: Can be hosted on Render, Railway, Glitch, or Replit.

Author
Mthunzi Malebadi
Sinesipho Sibulo
Ondela Citywayo
Segai Bryton Mampshika
