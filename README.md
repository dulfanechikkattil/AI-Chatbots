# 🤖 AI Chatbot Toolkit using LLaMA3 (Ollama)

## 📌 Project Overview
This project is a collection of AI-powered command-line applications built using Python and the LLaMA3 language model running locally with Ollama. The system demonstrates how large language models can be integrated into practical tools for everyday tasks such as chatting, code generation, text summarization, tutoring, email writing, and grammar correction.

The project uses the OpenAI-compatible API provided by Ollama to interact with the LLaMA3 model and build multiple AI utilities in a terminal-based interface.

---

## 🚀 Features

This project includes several AI-powered tools:
⚙️ Technologies Used

Python

Ollama (Local LLM Runtime)

Llama3 Model

OpenAI Python SDK (Ollama compatible API)

Command Line Interface (CLI)
🧠 Architecture

The application connects to the local Ollama API server and sends prompts to the Llama3 model.

User Input → Python Script → Ollama API → Llama3 Model → AI Response → Terminal Output
Output
📦 Installation
1️⃣ Install Python

Download Python from
https://python.org

2️⃣ Install Ollama

Download Ollama from
https://ollama.ai

3️⃣ Pull the Llama3 model
ollama pull llama3
4️⃣ Install required library
pip install openai


### 1️⃣ AI Terminal Chatbot
A conversational chatbot that allows users to interact with an AI assistant through the terminal.

**Capabilities:**
- Natural conversation
- Answer questions
- Provide explanations
- Maintain conversation context

---
<img width="745" height="165" alt="image" src="https://github.com/user-attachments/assets/0d765505-e4e3-4cae-9404-3d4455b692da" />
messages = [{"role":"system","content":"you are a helpful AI Terminal assistant."}]
print("🤖 AI Terminal  Chatbot (Type 'exit' to quit )\n")
while True:
    user_input=input("You: ")
    if user_input.lower() in ["exit","quit"]:
        break
    messages.append({"role":"user","content":user_input})
    response=cilent.chat.completions.create(model=model,messages=messages)
    replay=response.choices[0].message.content
    print("AI:",replay,"\n")
    messages.append({"role":"assistant","content":replay})
    <img width="1386" height="659" alt="image" src="https://github.com/user-attachments/assets/eed5f729-7159-4292-8d35-daff2d7420e6" />




### 2️⃣ AI Code Generator
An AI assistant that generates programming code based on user prompts.

**Capabilities:**
- Generate Python or other programming code
- Assist developers with coding tasks
- Provide structured and readable code output

---
print("⚡ AI Code Generator")
print("Type 'exit' to quit\n")

while True:
    prompt = input("Describe code you want: ")

    if prompt.lower() == "exit":
        break

    response = cilent.chat.completions.create(
        model=model,
        messages=[
            {
                "role": "system",
                "content": "You are an expert programming AI that generates clean code."
            },
            {
                "role": "user",
                "content": f"Generate code for: {prompt}"
            }
        ],
        temperature=0.2
    )

    code = response.choices[0].message.content
    print("\nGenerated Code:\n")
    print(code)
    print("\n" + "-"*50 + "\n")
    
  <img width="1386" height="670" alt="image" src="https://github.com/user-attachments/assets/03dec6a5-2e7b-4351-81a9-5386461942b6" />


### 3️⃣ AI Text Summarizer
A tool that summarizes long text into concise and clear summaries.

**Capabilities:**
- Extract key information from text
- Produce simplified summaries
- Improve readability of long documents

---
def chat_with_ai(user_input):
    response = cilent.chat.completions.create(
        model=model,
        messages=[
            {"role": "system", "content": "You are a helpful AI assistant."},
            {"role": "user", "content": user_input}
        ]
    )
    return response.choices[0].message.content
def summarize_text(text):
    response = cilent.chat.completions.create(
        model=model,
        messages=[
            {"role": "system", "content": "Summarize the following text clearly."},
            {"role": "user", "content": text}
        ]
    )

    return response.choices[0].message.content
# Simple CLI chatbot
while True:
    user = input("\nYou: ")

    if user.lower() == "exit":
        break

    if user.startswith("summarize:"):
        text = user.replace("summarize:", "")
        print("AI Summary:", summarize_text(text))
    else:
        print("AI:", chat_with_ai(user))

   <img width="1282" height="356" alt="image" src="https://github.com/user-attachments/assets/f7d917ad-c56d-4caa-9a84-5e5601b5a092" />
   

### 4️⃣ AI Tutor (Question Answering System)
An educational assistant that explains topics in a simple way for students.

**Capabilities:**
- Answer academic questions
- Provide clear explanations
- Support learning and self-study

---
def ai_tutor(question):

    response = cilent.chat.completions.create(
        model=model,
        messages=[
            {
                "role": "system",
                "content": "You are an AI Tutor that explains topics clearly for students. Give simple explanations with examples."
            },
            {
                "role": "user",
                "content": question
            }
        ]
    )

    return response.choices[0].message.content


print("🎓 AI Tutor Ready (type 'exit' to quit)\n")

while True:

    question = input("Student: ")

    if question.lower() == "exit":
        break

    answer = ai_tutor(question)

    print("\nAI Tutor:", answer)
    
  <img width="671" height="278" alt="image" src="https://github.com/user-attachments/assets/e832dc4f-27e0-4823-82c1-f2ec6cf246a8" />

### 5️⃣ AI Email Writer
Automatically generates professional emails based on a topic.

**Capabilities:**
- Generate formal emails
- Improve professional communication
- Save time writing messages

---
def generate_email(topic):

    response = cilent.chat.completions.create(
        model=model,
        messages=[
            {
                "role": "system",
                "content": "You are a professional email writing assistant. Write clear and polite emails."
            },
            {
                "role": "user",
                "content": f"Write a professional email about: {topic}"
            }
        ]
    )

    return response.choices[0].message.content


print("📧 AI Email Writer Ready (type 'exit' to quit)\n")

while True:

    prompt = input("Email Topic: ")

    if prompt.lower() == "exit":
        break

    email = generate_email(prompt)

    print("\nGenerated Email:\n")
    print(email)
  <img width="1296" height="498" alt="image" src="https://github.com/user-attachments/assets/c92c5e4e-a821-4f69-b4e2-75e91b26db91" />

### 6️⃣ AI Grammar Corrector
Corrects grammar and spelling errors in user-provided text.

**Capabilities:**
- Fix grammar mistakes
- Improve sentence clarity
- Provide corrected versions of text

---
def correct_grammar(text):

    response = cilent.chat.completions.create(
        model=model,
        messages=[
            {"role": "system", "content": "Correct grammar and spelling."},
            {"role": "user", "content": text}
        ]
    )

    return response.choices[0].message.content


while True:

    sentence = input("Enter text: ")

    if sentence.lower() == "exit":
        break

    result = correct_grammar(sentence)

    print("\nCorrected Text:\n", result)
  <img width="776" height="354" alt="image" src="https://github.com/user-attachments/assets/1795b29a-50c1-4076-8f07-b30556ed10bb" />


## 🧠 Technologies Used

- **Python**
- **Ollama**
- **LLaMA3 Language Model**
- **OpenAI Compatible API**
- **Jupyter Notebook**

---

## ⚙️ How It Works

1. The system connects to the **Ollama local API**.
2. The **LLaMA3 model** processes user prompts.
3. Different modules handle specific tasks like chatting, summarizing, or generating code.
4. Users interact with the tools through a **command-line interface (CLI)**.

---

## 📂 Project Structure
AI Chatbot 
│
├── AI Terminal Chatbot
├── AI Code Generator
├── AI Text Summarizer
├── AI Tutor (Question Answering)
├── AI Email Writer
└── AI Grammar Corrector

---

## 🌟 Applications

- AI-powered productivity tools
- Developer coding assistants
- Educational tutoring systems
- Text processing utilities
- Natural language processing applications

---

## 🔮 Future Improvements

- Add a graphical user interface (GUI)
- Deploy as a web application
- Integrate more AI tools
- Add speech input and voice responses

---

## 👨‍💻 Author
Developed as a practical project to explore **AI applications using local large language models and Python.**
