# [Simple Word Counter Web App](#simple-word-counter-web-app) <!-- omit in toc -->

This is a minimalist web application that demonstrates the fundamental concept of client-server communication. The front end, built with a single HTML file and JavaScript, sends a text input to a Python back end built with Flask, which then processes the request and returns a simple word count.

This project is a starting point for understanding how a web browser (the client/ front end) interacts with a server (the back end).

## Table of Contents <!-- omit in toc -->
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [How to Run the App](#how-to-run-the-app)
- [How It Works](#how-it-works)

## Features

* **Simple Interface:** A single HTML page with a text input field and a button.

* **Client-Server Communication:** Uses JavaScript's `fetch` API to send data to the back end.

* **Python Back End:** A lightweight Flask server that handles a `POST` request to count words.

* **Combined Functionality:** The Flask server is configured to both serve the HTML file and handle the API logic from the same URL (`/`).

## Project Structure

The project is structured in a common Flask pattern, with the front-end HTML file located in a `templates` folder.

```
python_web_demo/
├── app.py
└── templates/
    └── index.html
```

## Installation

To get started, you'll need **Git**, **Python**, and **[uv](https://docs.astral.sh/uv/)** installed on your system.

1. Clone the repository
    ```bash
    git clone https://github.com/ulisesrey/python_web_demo.git
    ```

2. Navigate to the project directory in your terminal, for example if you have in a local_code folder:
    ```
    cd local_code/python_web_demo
    ```
3. Install the required Python libraries using uv:
    ```
    uv sync
    ```
    This will:

    * Create a virtual environment in .venv/ (if it doesn’t exist)

    * Install the exact versions listed in uv.lock

## How to Run the App

1. Make sure you have saved the `app.py` and `index.html` files in the correct directory structure as shown above.

2. In your terminal, run the Python server:

    Directly using uv:
    ```
    uv run python app/app.py
    ```
    or if you prefer, first activate the environment:
    ```
    source .venv/bin/activate
    ```
    and then run the python script:
    ```
    python app/app.py
    ```

3. Open your web browser and navigate to the following URL:

    http://127.0.0.1:5000/

    The web page will load, and you can begin using the word counter.

## How It Works

1. **Serving the Page (`GET` request):** When you navigate to `http://127.0.0.1:5000/`, your browser sends a `GET` request to the server. The `app.py` script, through the `render_template('index.html')` function, serves the HTML file to your browser.

2. **Counting Words (`POST` request):** When you type a sentence and click the "Count Words" button:

* The JavaScript in `index.html` takes the text from the input field.

* It then sends a `POST` request to the same URL, `http://127.0.0.1:5000/`, with the sentence in a JSON body.

* The `app.py` server receives this `POST` request, retrieves the sentence, splits it into words, and counts the number of items.

* The server sends the word count back to the browser as a JSON response.

* The JavaScript receives the JSON, extracts the word count, and updates the text on the page.

This project uses `Flask-CORS` to ensure that the browser is allowed to make requests to the local server, which is a common security feature in web development.