# RestaurantNameGenerator

An AI-powered web app that generates creative restaurant names and menu items based on a selected cuisine, built with **LangChain**, **Groq (LLaMA 3.3)**, and **Streamlit**.

---

##  Demo

> Select a cuisine from the sidebar → get an AI-generated restaurant name + 8 curated menu items instantly.

---

##  Features

-  Powered by **LLaMA 3.3 70B** via the Groq API
-  Uses **LangChain** prompt chaining (`PromptTemplate` + LCEL pipe syntax)
-  Clean **Streamlit** UI with sidebar cuisine selector
-  Supports Indian, Italian, Mexican, Arabic, and American cuisines
-  Two-step chain: generates restaurant name first, then tailored menu items

---

##  Tech Stack

| Layer | Technology |
|---|---|
| LLM | LLaMA 3.3 70B Versatile (via Groq) |
| Orchestration | LangChain + LCEL |
| Frontend | Streamlit |
| Language | Python 3.9+ |

---

##  Project Structure

```
restaurant-name-generator/
├── main.py               # Streamlit UI
├── langchain_helper.py   # LangChain chains & Groq LLM logic
├── resturant.ipynb       # Experimentation notebook
├── requirements.txt      # Dependencies
└── README.md
```

---

##  Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/restaurant-name-generator.git
cd restaurant-name-generator
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Add your Groq API key

Open `langchain_helper.py` and replace the `api_key` value with your own key:

```python
llm = ChatGroq(
    model="llama-3.3-70b-versatile",
    api_key="your_groq_api_key_here"   # ← replace this
)
```

>  Get a free Groq API key at [console.groq.com](https://console.groq.com)

**Recommended:** Store your key in a `.env` file instead of hardcoding it:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Then load it in `langchain_helper.py`:

```python
import os
from dotenv import load_dotenv
load_dotenv()

llm = ChatGroq(
    model="llama-3.3-70b-versatile",
    api_key=os.getenv("GROQ_API_KEY")
)
```

### 4. Run the app

```bash
streamlit run main.py
```

---

##  Requirements

```
streamlit
langchain
langchain-core
langchain-groq
groq
python-dotenv
```

Generate `requirements.txt` with:

```bash
pip freeze > requirements.txt
```

---

##  How It Works

```
User selects cuisine
        ↓
Prompt 1 → LLM → Restaurant Name
        ↓
Prompt 2 (uses name) → LLM → 8 Menu Items
        ↓
Streamlit renders the result
```

The app uses LangChain's LCEL pipe (`|`) syntax to chain a `PromptTemplate` directly into the `ChatGroq` LLM, keeping the code clean and modular.

---

##  Acknowledgements

- [Groq](https://groq.com) — blazing fast LLM inference
- [LangChain](https://langchain.com) — LLM orchestration framework
- [Streamlit](https://streamlit.io) — rapid Python web apps
- [Meta LLaMA 3.3](https://ai.meta.com/blog/meta-llama-3/) — the underlying language model

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).



Screenshots

![image alt](https://github.com/akashcbe/RestaurantNameGenerator/blob/6e12b452108260e1fff01addf05f8dd8d3137d88/Screenshot%202026-04-18%20113050.png)
![image alt](https://github.com/akashcbe/RestaurantNameGenerator/blob/4e92091a13f3b0cfd6d16d58988a6e9163f4db30/Screenshot%202026-04-18%20113634.png)



