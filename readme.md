# Running Language Models Locally on Apple M-Series Laptops

## Overview

This project is a guide and toolkit for running language models such as **BERT**, **T5**, and **GPT-2** directly on your Apple M-series laptop. The goal is to make it easy for you to experiment with these models without needing expensive cloud services.

### Why is this important?
1. **Cost-Efficient**: Avoid cloud costs by running models locally.
2. **Data Privacy**: Keep your data on your device without uploading it to external servers.
3. **Learning Opportunity**: Understand how model inference works and customize the code as you grow.

The repository starts with simple scripts that use Hugging Face’s powerful `pipeline()` function. This abstracts away a lot of complexity and lets you focus on results. As the project grows, more customizable implementations will be added, giving you a gradual path to learn and control the process.

---

## Project Structure

Here’s how the repository is organized:

```plaintext
.
├── requirements.txt           
├── misc/                      
│   └── txt-generation allowed classes.txt
├── models/                    # CREATE THIS FOLDER BY RUNNING download-models.ipynb
│   └── huggingface/           
│       ├── bert-large-uncased-whole-word-masking_mlm/
│       ├── bert-large-uncased-whole-word-masking-finetuned-squad_qa/
│       ├── gpt2/
│       ├── gpt2-xl/
│       ├── t5-small/
│       └── t5-3b/
├── scripts/                   # Contains scripts for running models.
│   ├── transformers-pipeline/ # Easy-to-use pipeline-based scripts.
│   │   ├── bert.ipynb
│   │   ├── download-models.ipynb
│   │   ├── gpt2.ipynb
│   │   └── t5.ipynb
│   ├── transformers-manual/   # To be filled with more advanced code using Hugging Face directly.
│   └── pytorch/               # To be filled with custom PyTorch scripts.
```

- **`models`**: Contains the different models you can experiment with, organized by type. (Note that the models folder is not on github because of how large it is. I have created a download script to download the relevant models locally)
- **`scripts`**: Contains all the code for running models. Starts simple with `transformers-pipeline` scripts and will grow into more advanced implementations.

---

## Getting Started

### Prerequisites

- **Python 3.12**
- **pip or equivalent package manager**
- **Apple M-series Mac (e.g., M1, M2)**  

Note: I run the notebooks locally on vscode. There are other ways to run the notebooks, but you might have to make a few modifications

### Installation

Follow these steps to set up the environment:

1. **Clone the repository**:
   ```bash
   # Run your code on the terminal
   # Do this in your project folder
   git clone https://github.com/yourusername/your-repo.git
   cd your-repo
   ```

2. **Create a virtual environment**:
   ```bash
   # In the same project folder
   python3 -m venv env
   ```

3. **Activate the virtual environment**:
   On macOS/Linux:
   ```bash
   # In the same project folder
   source env/bin/activate
   ```

4. **Install the required packages**:
   ```bash
   # In the same project folder
   pip install -r requirements.txt
   ```
5. (optional, not recommended) **Allow system wide packages**
   ```bash
   # This is only required if you already have pytorch and other libraries installed globally and don't want to install it again
   # open the configuration file (eg: pyvenv.cfg) and add this line if it doesn't exist:
   include-system-site-packages = true
   ```

---

## How to Use the Scripts

### Step 1: Open a Script
The scripts are located in the `scripts/transformers-pipeline/` directory. Each notebook demonstrates how to load a model and perform inference.

Example:
- `bert.ipynb`: Run BERT for tasks like text classification or question answering.
- `gpt2.ipynb`: Generate text using GPT-2.
- `t5.ipynb`: Perform text-to-text tasks like summarization or translation with T5.

### Step 2: Run Inference
1. Open the desired `.ipynb` file using VS Code (recommended)  
   You can also open it on Jupyter Notebook by running the following command (not recommended)
   ```bash
   jupyter notebook # or ignore this and just open the notebook inside VS Code
   ```
2. Follow the step-by-step instructions in the notebook to load a model and perform inference.

### Step 3: Customize
You can modify the scripts to play around.

---

## Examples

Here are some things you can do right away:  
(This will download the relevant models in a cache folder if you don't already have them)

### Text Classification with BERT
Use the `bert.ipynb` notebook to classify text into predefined categories.

```python
from transformers import pipeline
classifier = pipeline("text-classification", model= "bert-large-uncased-whole-word-masking")
print(classifier("I climbed the highest peak in the world!"))
```

### Text Generation with GPT-2
Use the `gpt2.ipynb` notebook to generate text based on a prompt.

```python
from transformers import pipeline
generator = pipeline("text-generation", model= path_to_models + "gpt2")
print(generator("Once upon a time", max_length=50))
```

---

## Roadmap

This repository is a work in progress. Here’s what’s coming next:

1. **Direct Use of the `transformers` Library**:
   - Scripts without the `pipeline()` abstraction.
   - These will be added to `scripts/transformers-manual/`.

2. **PyTorch Implementations**:
   - Write inference scripts from scratch using PyTorch.
   - More flexibility and control over model behavior.
   - These will be added to `scripts/pytorch/`.

3. **Training scripts**:
   - Write scripts to pre-train or fine-tune language models, 

4. **Support for other devices**:
   - Run the scripts on linux

---

## Contributing

Want to contribute? Here’s how:
1. Fork this repository.
2. Create a feature branch.
3. Make your changes and submit a pull request.

---