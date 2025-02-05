---

# Text Summarization Application

This is a Python-based application that provides a simple way to summarize text using multiple summarization methods. The application leverages Gradio to create an interactive user interface for text summarization. The summarization methods include **Extractive Summarization** and **Abstractive Summarization** (available for both English and Arabic).

The application uses **Hugging Face Transformers** for text summarization models and **spaCy** for extractive summarization.

try Live On [Gradio]( https://7af69987c540f22d5e.gradio.live/ )


[screen-capture.mp4.webm](https://github.com/user-attachments/assets/a19aa9f1-8806-41d7-b6c6-5e7e8a56ddfb)

## Features

- **Extractive Summarization**: Selects key sentences from the input text to generate a summary based on word frequency.
- **Abstractive Summarization**:
  - **English**: Uses a pre-trained model (`mT5_multilingual_XLSum`) for summarizing English text.
  - **Arabic**: Uses a custom pre-trained model (`mT5_AraBART-summrize2`) for summarizing Arabic text.
- **Interactive Interface**: Built with Gradio for ease of use, where you can input the text, select the summarization method, and adjust the number of sentences for extractive summarization.

## Requirements

- Python 3.7+
- `transformers` library for Hugging Face models
- `spacy` library for natural language processing
- `gradio` for creating the interactive interface
- `torch` for model inference (required by Hugging Face models)

To install the required libraries, you can use the following command:

```bash
pip install transformers spacy gradio torch
```

You will also need to download the `spaCy` language model for English (`en_core_web_sm`):

```bash
python -m spacy download en_core_web_sm
```

## Setup

1. Clone this repository or download the script to your local machine.

```bash
git clone https://github.com/your-username/text-summarization-app.git
cd text-summarization-app
```

2. Install the required dependencies using `pip`:

```bash
pip install -r requirements.txt
```

3. Run the application script:

```bash
python app.py
```

Once the application is running, a local Gradio interface will open in your web browser where you can interact with the summarization models.

## Usage

Once the Gradio interface is launched, you will see the following input options:

1. **Text to Summarize**: Enter the text that you want to summarize.
2. **Summarization Method**: Select one of the following summarization methods:
   - **Extractive**: Select key sentences based on word frequency.
   - **Abstractive (English)**: Use an abstractive model to summarize English text.
   - **Abstractive (Arabic)**: Use an abstractive model to summarize Arabic text.
3. **Number of Sentences in Summary**: Use the slider to select the number of sentences to include in the extractive summary. The slider value is an integer between 1 and 20. This setting only applies to the **Extractive** method.

After providing the input text and selecting your preferred summarization method and sentence count, click the **Submit** button to generate the summary.

## How the Summarization Works

### 1. **Extractive Summarization**
In the extractive method, the application selects key sentences from the input text based on the frequency of words that appear in the text. The following steps are performed:

- Tokenization: The text is tokenized into words and sentences using **spaCy**.
- Word Frequency Calculation: The frequency of each word (excluding stopwords and punctuation) is calculated.
- Sentence Scoring: Each sentence is scored based on the sum of the frequency of words it contains.
- Summary Generation: The sentences with the highest scores are selected and returned as the summary.

### 2. **Abstractive Summarization**
The abstractive summarization methods generate summaries by paraphrasing and rephrasing the content:

- **Abstractive (English)**: Uses the pre-trained `mT5_multilingual_XLSum` model from Hugging Face to summarize English text.
- **Abstractive (Arabic)**: Uses the `mT5_AraBART-summrize2` model for summarizing Arabic text.

Both models use **transformers** to generate summaries by understanding the context and rewording the content.

## Customization

You can customize the summarization logic in the following ways:

- **Change Models**: You can swap the existing pre-trained models with other models from Hugging Face. Just update the model names in the pipeline setup.
- **Language Support**: Currently, the extractive summarization works for English. If you want to support other languages, you can modify the tokenization process or add other language models for **spaCy**.
- **Summarization Length**: You can adjust the maximum and minimum length of summaries by modifying the `max_length` and `min_length` parameters in the model pipeline.

## Known Issues

- The **Abstractive (Arabic)** model works best with clean and well-formed Arabic text. Text with excessive dialects or slang may result in poor summaries.
- Extractive summarization relies heavily on word frequency, and may not always generate the most coherent summary for all types of texts.

## License

This project is licensed under the MIT License.

## Acknowledgments

- Hugging Face for providing the pre-trained transformer models used in this application.
- spaCy for natural language processing utilities.
- Gradio for enabling an easy-to-use interface for machine learning models.

## Contributing

If you'd like to contribute to this project, please fork the repository and submit a pull request with your changes. Issues and suggestions for improvement are welcome. [Colab](https://colab.research.google.com/drive/1Gz5kb04DKaY52YD0xIR7j7f62yTgeaN_#scrollTo=ModKRWNnMxbW)

---
