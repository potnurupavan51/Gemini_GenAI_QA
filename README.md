# Langchain Demo with Gemini

This Streamlit application demonstrates a simple question-answering system powered by Langchain and the Google Gemini 1.5 Pro model. You can ask the chatbot any question, and it will use the Gemini model to generate a response.

Google's Gemini 1.5 Pro as the language model

LangChain to structure the prompt

Streamlit to create the web-based user interface

## Prerequisites

Before running the application, ensure you have the following installed:

* **Python 3.8 or higher:** You likely have this already.
* **pip:** Python package installer.
* **Google Cloud Project and API Key:** You need a Google Cloud project with the Gemini API enabled and an associated API key.

## Setup

1.  **Clone the repository (if you have the code in one):**
    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

2.  **Install the required Python libraries:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: A `requirements.txt` file is not explicitly provided in your code. However, based on the imports, you'll need at least `streamlit`, `python-dotenv`, `langchain-core`, and `langchain-google-genai`. You can create a `requirements.txt` file with these and any other necessary packages from the provided list.)*

    Example `requirements.txt`:
    ```
    streamlit
    python-dotenv
    langchain-core
    langchain-google-genai
    ```

3.  **Set up your environment variables:**
    * Create a `.env` file in the same directory as your Python script (`gemini_app_qa.py`).
    * Add your Google Gemini API key to the `.env` file:
        ```
        GOOGLE_API_KEY=YOUR_API_KEY
        ```
        *(Replace `YOUR_API_KEY` with your actual API key.)*

## Running the Application

1.  **Navigate to the directory containing your Python script (`gemini_app_qa.py`) in your terminal.**

2.  **Run the Streamlit application using the following command:**
    ```bash
    streamlit run gemini_app_qa.py
    ```

3.  **The application will open in your web browser.** You should see a title "Langchain Demo With Gemini" and a text input field labeled "Enter your question here".

## Using the Application

1.  **Type your question into the text input field.**

2.  **Press Enter or click outside the input field.**

3.  **The Gemini model will process your question, and the chatbot's response will be displayed below the input field.**

## Code Explanation

* **`import streamlit as st`:** Imports the Streamlit library for creating the web application.
* **`from dotenv import load_dotenv`:** Imports the `load_dotenv` function from the `python-dotenv` library to load environment variables from the `.env` file.
* **`from langchain_core.prompts import ChatPromptTemplate`:** Imports the `ChatPromptTemplate` for creating structured prompts for the language model.
* **`from langchain_google_genai import ChatGoogleGenerativeAI`:** Imports the `ChatGoogleGenerativeAI` class to interact with the Google Gemini models.
* **`from langchain_core.output_parsers import StrOutputParser`:** Imports the `StrOutputParser` to convert the language model's output into a string.
* **`load_dotenv()`:** Loads the environment variables from the `.env` file, making your API key accessible.
* **`llm = ChatGoogleGenerativeAI(...)`:** Initializes the Gemini 1.5 Pro language model with specified parameters like `temperature` (controls randomness), `max_tokens`, `timeout`, and `max_retries`.
* **`prompt = ChatPromptTemplate.from_messages(...)`:** Creates a chat prompt template with a system message ("You are a chatbot") and a human message that includes the user's question.
* **`st.title('Langchain Demo With Gemini')`:** Sets the title of the Streamlit application.
* **`input_text = st.text_input("Enter your question here")`:** Creates a text input field for the user to enter their question.
* **`output_parser = StrOutputParser()`:** Creates an instance of the string output parser.
* **`chain = prompt | llm | output_parser`:** Creates a Langchain pipeline that first formats the prompt, then passes it to the Gemini model, and finally parses the output to a string.
* **`if input_text:`:** Checks if the user has entered any text in the input field.
* **`st.write(chain.invoke({'question': input_text}))`:** If there is input text, it invokes the Langchain pipeline with the user's question and displays the generated response using `st.write()`.
* **`# To run this code, write- streamlit run gemini_app_qa.py`:** This is a comment reminding the user how to run the application.

This application provides a basic framework for interacting with the Google Gemini language model using Langchain and Streamlit. You can further enhance this application by adding features like conversation history, different prompt templates, and more complex Langchain functionalities.
