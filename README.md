
---

# 🤖 AI Chatbot Toolkit using Python & Ollama (Llama3)

## 📌 Project Overview

This project is a **collection of AI-powered command line tools** built using **Python and a local Large Language Model (LLM)**.
The system connects to **Ollama's local API** and runs the **Llama3 model** to perform multiple AI tasks directly in the terminal.

The goal of this project is to demonstrate how **AI applications can be developed locally without relying on cloud APIs**, while exploring practical use cases of **Generative AI in Python**.

This toolkit includes multiple AI utilities such as:

* Conversational chatbot
* Code generation
* Text summarization
* AI tutoring
* Email writing
* Grammar correction

All tools run in a **simple terminal interface**, making them lightweight and easy to experiment with.

---
# 📦 Installation

## 1️⃣ Install Python

Download Python from:

[https://www.python.org](https://www.python.org)

---

## 2️⃣ Install Ollama

Download Ollama:

[https://ollama.ai](https://ollama.ai)

---

## 3️⃣ Install Llama3 Model

```
ollama pull llama3
```

---

## 4️⃣ Install Python Dependencies

```
pip install openai
```
# Chatbots 

## 1️⃣ AI Terminal Chatbot

A conversational chatbot that interacts with the user in the terminal and maintains conversation context.

**Capabilities**

* Natural language conversations
* Context memory
* Runs locally using Llama3

code :
common model and api
<img width="844" height="175" alt="image" src="https://github.com/user-attachments/assets/4762192f-346d-43f5-b2ce-e9fb1bd0e462" />
```


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
    messages.append({"role":"assistant","content":replay})9
```
-----
<img width="842" height="164" alt="image" src="https://github.com/user-attachments/assets/916cb084-cd9b-4726-a3d1-1900e831a327" />


## 2️⃣ AI Code Generator

Generates programming code based on user prompts.The AI will generate clean and structured code.
code:
```


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

```



---

<img width="797" height="340" alt="image" src="https://github.com/user-attachments/assets/cce1547e-9648-43ef-901d-e5170d92c88d" />


---

## 3️⃣ AI Text Summarizer

Summarizes long text into a short and clear explanation.

code:

```
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
```
<img width="829" height="367" alt="image" src="https://github.com/user-attachments/assets/ef9d1cf8-e6bb-41c8-a6dd-72b209e38343" />

---

## 4️⃣ AI Tutor (Question Answering System)

Acts like an **AI teacher** that explains concepts clearly with examples.

code:
```

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
_ _ _

```
<img width="1307" height="180" alt="image" src="https://github.com/user-attachments/assets/2a611585-10a1-4262-b17f-b7809ceea57e" />

---

## 5️⃣ AI Email Writer

Generates professional emails automatically based on a topic.

Code:
       
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

```
.
```
<img width="1360" height="493" alt="image" src="https://github.com/user-attachments/assets/bc8b84eb-9785-40ba-8cc5-1618486375ff" />

     The AI creates a complete professional email.

## 6️⃣ AI Grammar Corrector
```
----
Corrects grammar and spelling errors in sentences.

code:
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

```
<img width="950" height="405" alt="image" src="https://github.com/user-attachments/assets/4da04933-8ed4-486b-9d3a-4e71ebe0e6da" />

```

---


```
# ⚙️ Technologies Used

* **Python**
* **Ollama (Local LLM Runtime)**
* **Llama3 Model**
* **OpenAI Python SDK**
* **Command Line Interface (CLI)**

---

# 🧠 System Architecture

```
`
User Input
     ↓
Python Application
     ↓
Ollama Local API
     ↓
Llama3 Language Model
     ↓
AI Response
     ↓
Terminal Output



```
# 📁 Project Modules
AI Chatbot Toolkit
│
├── AI Terminal Chatbot
├── AI Code Generator
├── AI Text Summarizer
├── AI Tutor
├── AI Email Writer
└── AI Grammar Corrector
# 👨‍💻 Author

Developed as a **practical AI learning project** to explore **local LLM applications using Python and Ollama**.



