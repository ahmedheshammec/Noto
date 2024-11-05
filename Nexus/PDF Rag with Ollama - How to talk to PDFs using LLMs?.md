
the complete documentation can be found in this github link: 
https://github.com/tonykipkemboi/ollama_pdf_rag/tree/main

## Install Ollama and some models

after you install ollama and some models like llama 3.2 for example, install this model: 

```sh
ollama pull nomic-embed-text
```

## Clone the Project and Install the Requirements

→ after you clone the github project use `pyenv` to set a local python for this project as `python 3.8` 

```zsh
pyenv local 3.8
python --version
```

→ create a virtual environment using the following command: 

```zsh
python -m venv .venv
```

→ activate the virtual environment using the following command: 

```zsh
source .venv/bin/activate
```

→ install the requirements through this command: 

```zsh
pip install -r requiremnts.tx
```

→ this step will take some time so be patient! 

## install streamlit & Run 

this is a library that we will use as the front-end for this project, you can install it using this command: 

```zsh
pip install streamlit
```

→ next use the following command: 

```zsh
streamlit run streamlit_app.py
```

Then open your browser to `http://localhost:8501`

## 💡 Usage Tips

1. **Upload PDF**: Use the file uploader in the Streamlit interface or try the sample PDF
2. **Select Model**: Choose from your locally available Ollama models
3. **Ask Questions**: Start chatting with your PDF through the chat interface
4. **Adjust Display**: Use the zoom slider to adjust PDF visibility
5. **Clean Up**: Use the "Delete Collection" button when switching documents
6. you can kill the session using `⌃ + c` from your keyboard. 



