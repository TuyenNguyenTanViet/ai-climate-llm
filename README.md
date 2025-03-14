# AI-Driven Writing in Climate Change

This project leverages AI to create engaging stories about climate change using large language models (LLMs) and multimodal input/output.

## Prerequisites

Before running the project, ensure you have the following installed on your system:

- **Python 3.9 or higher**  
- **Anaconda** (for environment management)

---

## 1. Clone the Repository

```bash
git clone https://git.soton.ac.uk/ai-driven-writing-in-climate-change/ai-driven-writing-in-climate-change.git
cd ai-driven-writing-in-climate-change
```

## 2. Create and Activate a Conda Environment

Create a new Conda environment using the packages specified in `requirements.txt`.

```bash
# Create the Conda environment
conda create --name ai-climate-llm --file requirements.txt

# Activate the environment
conda activate ai-climate-llm
```

If `requirements.txt` does not work as expected, you can manually install the required packages using:

```bash
conda create --name ai-climate-llm python=3.8
conda activate ai-climate-llm
pip install -r requirements.txt
```

---

## 3. Set Up the Environment Variables

Create a `.env` file in the project root directory and add the following contents:

```plaintext
GROQ_API_KEY=YOUR_GROQ_API_KEY
STABILITY_KEY=YOUR_STABILITY_KEY
SUPABASE_URL=YOUR_SUPABASE_DATABASE_URL
SUPABASE_KEY=YOUR_SUPABASE_DATABASE_KEY
```

> **Note:** Never share or expose your API keys publicly. The keys shown here are for example purposes and should be replaced with your actual API credentials.

---

## 4. Run the Streamlit App

You can now start the Streamlit application by running the following command from the project directory:

```bash
python -m streamlit run src/app.py
```

---

## 5. Access the Application

Once the application is running, open your browser and go to:

```
http://localhost:8501
```

You can now interact with the AI-driven climate change storytelling application.

---

## 6. Troubleshooting

### Common Issues:

- **APIError: Service Unavailable:**  
  This might occur if the API service is temporarily down. Try again after some time or check the service's status.

- **Environment Variable Issues:**  
  Ensure the `.env` file is correctly placed in the project root and contains valid API keys.

---

## 7. Deactivating the Conda Environment

Once you're done, deactivate the Conda environment using:

```bash
conda deactivate
```

---

## 8. Updating Dependencies

If you need to add or update dependencies, modify the `requirements.txt` file and reinstall:

```bash
pip install -r requirements.txt
```

---
## 9. RAG
This project includes a RAG-based system to enhance responses using an external knowledge base. 
### Using the Existing Knowledge Base
By default, the system is pre-loaded with a limited knowledge base. You can directly query it using:
```bash 
python src/RAG.py --index_path "pth/to/index(.idx)" --metadata_path "pth/to/metadata(.json)" --text_query 'what do you know about climate change'
```

### Adding More Data
Since the current knowledge base is limited, users may want to expand it by adding new data. 
#### Adding New Text Data
Use the following function to add data from a .txt file while also rebuilding the index to incorporate new information properly: 
```bash
python src/RAG.py --index_path "pth/to/index(.idx)" --metadata_path "pth/to/metadata(.json)" --new_text_file "path/to/text/file(.txt)"
```
#### Adding New Images
To add new images, you must provide both --new_img_dir (directory containing the images you want to add) and --database_dir (directory where previously added images are stored.):
```bash
python src/RAG.py --index_path "pth/to/index(.idx)" --metadata_path "pth/to/metadata(.json)" --new_img_dir "path/to/new_images/" --database_dir "path/to/image_database/"
```
#### Adding Both Text and Images
```bash
python src/RAG.py --index_path "pth/to/index(.idx)" --metadata_path "pth/to/metadata(.json)" --new_text_file "path/to/text/file(.txt)" --new_img_dir "path/to/new_images/" --database_dir "path/to/image_database/"

```



### Running the script with and without RAG:
#### Without RAG (default):

```bash
python -m streamlit run src/app.py
```
#### With RAG:
```bash
python -m streamlit run src/app.py -- --use_rag --index_path "pth/to/index(.idx)" --metadata_path "pth/to/metadata(.json)" 
```
Note: The -- before --use_rag is required when passing arguments to a Streamlit script. The idx and json files are provided in the faiss_indices folder.




## 9. License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---
