# Sepia Image Converter with Gradio
This project provides a simple Gradio interface to apply a sepia tone filter to uploaded images. It demonstrates how to use Python and Gradio for image processing with a focus on creating vintage-style images.

## Features
- Image Upload: Upload images in common formats (e.g., PNG, JPEG).
- Sepia Filter Application: The interface applies a sepia-tone transformation to the uploaded image.
- Interactive Interface: Built with Gradio, allowing real-time interaction and visualization.
- Customizable Filter: The sepia transformation can be adjusted to create different effects.

## Tools Used
- [Python](https://www.python.org/): Core programming language.
- [Pillow (PIL)](https://pypi.org/project/pillow/) : For image processing.
- [Gradio](https://www.gradio.app/): To build the user interface.

## How It Works
1. Input: The user uploads an image through the Gradio interface.
2. Processing:
- The red, green, and blue (RGB) values of each pixel are modified using the following sepia formula:
```python
   tr = int(0.393 * r + 0.769 * g + 0.189 * b)
   tg = int(0.349 * r + 0.686 * g + 0.168 * b)
   tb = int(0.272 * r + 0.534 * g + 0.131 * b)
                    
 ``` 
- The values are clipped to a maximum of 255 to prevent overflow.
3. Output: The processed image with the sepia tone is displayed.
  
## Customization
### Adjusting the Sepia Tone
The sepia effect is controlled by the transformation matrix in the code:
```python
   tr = int(0.393 * r + 0.769 * g + 0.189 * b)
   tg = int(0.349 * r + 0.686 * g + 0.168 * b)
   tb = int(0.272 * r + 0.534 * g + 0.131 * b)                    
```  
                
You can modify these coefficients to experiment with different color effects.                     
### Adding Custom CSS
You can style the Gradio interface by providing custom CSS. For example, to change the title and description colors:
```python

   h1 {
   color: #ff5733; /* Title color */
   }
   p {
   color: #4caf50; /* Description color */
   }
   body {
   background-color:black;
   }
```
                                       
*******************************************************************************************************************
*******************************************************************************************************************

# Speech-to-Text Converter
This project provides a simple Speech-to-Text Converter using Python. It allows users to record or upload audio files, which are then transcribed into text using Google's Speech Recognition API. The interface is built with Gradio, providing a clean and user-friendly web application.

## Features
- Audio Input:
Record audio directly using your microphone.
Upload pre-recorded audio files.
- Text Output:
Converts spoken words in the audio file into written text.
- Custom Styling:
The interface is styled with a dark green background for enhanced aesthetics.

## Tools Used
- [Python](https://www.python.org/): Core programming language for the application.
- [Gradio](https://www.gradio.app/): For creating the interactive web interface.
- [SpeechRecognition](https://pypi.org/project/SpeechRecognition/): For converting speech to text using Google's API.
************************************************************************************************
************************************************************************************************
#  Image Captioning Application

## Overview
This project is an **Image Captioning Application** that uses a pre-trained image captioning model to generate captions for any image uploaded by the user. The application is built using the following tools and frameworks:

- **Gradio**: For creating an interactive user interface.
- **Hugging Face Transformers**: For loading and using the image captioning model.
- **Pillow (PIL)**: For image processing.
- **Base64**: For handling image encoding.

The application allows users to upload an image and returns a descriptive caption for the uploaded image.

---

## Features
- **Interactive User Interface**: Built with Gradio for easy interaction.
- **Pre-Trained Model**: Uses the `nlpconnect/vit-gpt2-image-captioning` model for high-quality captions.


---

## Requirements
To run the application, ensure you have the following installed:

- Python 3.7+
- Required Python libraries:
  - `transformers`
  - `torch`
  - `gradio`
  - `Pillow`

You can install the dependencies using:

```bash
pip install transformers torch gradio pillow
```

---

## How to Run
1. Clone the repository or copy the script to your local machine.
2. Install the required dependencies as listed above.
3. Save the script as `app.py` (or any name you prefer).
4. Run the script 
5. Open the application in your web browser using the URL provided by Gradio (usually `http://127.0.0.1:7860`).

---

## Code Explanation
### Key Components:

1. **Model Initialization**:
   - The `nlpconnect/vit-gpt2-image-captioning` model is loaded using Hugging Face Transformers:
     ```python
     model = VisionEncoderDecoderModel.from_pretrained(model_name)
     processor = ViTImageProcessor.from_pretrained(model_name)
     tokenizer = AutoTokenizer.from_pretrained(model_name)
     ```

2. **Image Preprocessing**:
   - The `ViTImageProcessor` converts images into tensors compatible with the model.
     ```python
     pixel_values = processor(images=image, return_tensors="pt").pixel_values
     ```

3. **Caption Generation**:
   - Captions are generated by the model and decoded using the tokenizer.
     ```python
     output_ids = model.generate(pixel_values, max_length=64, num_beams=16)
     caption = tokenizer.decode(output_ids[0], skip_special_tokens=True)
     ```

4. **Gradio Interface**:
   - A user-friendly interface with:
     - An image upload area.
     - A textbox to display the generated caption.
     ```python
     demo = gr.Interface(
         fn=captioner,
         inputs=[gr.Image(label="Upload image", type="pil")],
         outputs=[gr.Textbox(label="Caption")],
         title="Image Captioning",
         description="Caption any image using a pre-trained image captioning model.",
         allow_flagging="never",
         css=".gradio-container {background-color:DarkSlateGrey;}",
        
     )
     ```

5. **Launch**:
   - The application is launched using:
     ```python
     demo.launch()
     ```

---

## Customization
You can customize the application as follows:

1. **CSS**:
   - Update the background color or style in the `css` parameter.

2. **Model**:
   - Replace the `nlpconnect/vit-gpt2-image-captioning` model with another compatible image captioning model from Hugging Face.

3. **Examples**:
   - Add more example images to the `examples` parameter in the `Gradio Interface` section.

---

## Troubleshooting
- **Dependencies Error**: Ensure all required libraries are installed with the correct versions.
- **Model Download Issues**: Check your internet connection when the model is being downloaded.
- **Gradio Not Launching**: Ensure no other application is using the default port (`7860`) or specify a different port with:
  ```python
  demo.launch(server_port=8080)
  ```


 **Acknowledgments**
- [Hugging Face](https://huggingface.co/) for providing the pre-trained models.
- [Gradio](https://gradio.app/) for simplifying user interface creation.
  
 ******************
 ******************
 
 # Text Summarization APP

This project demonstrates a simple interface for summarizing text using the pre-trained T5-Large model from Hugging Face. The application is built with Gradio for easy interaction and styled with custom CSS for a more personalized appearance.

## Features
- Summarize any text input using the T5-Large model.
- Intuitive web-based interface powered by Gradio.
- Custom styling for an improved user experience.

## How It Works
The application leverages the Hugging Face `transformers` library to load the T5-Large model for text summarization. The input text is processed, and the model generates a concise summary, which is then displayed in the interface.

## Requirements
Ensure you have the following Python packages installed:

- `transformers`
- `gradio`
- `google.colab` (if using Google Colab)

You can install the required libraries with:
```bash
pip install transformers gradio
```

## Code Overview
### Importing Libraries
```python
from google.colab import userdata
userdata.get('HF_API_KEY')

import gradio as gr
from transformers import pipeline
```

### Loading the Model
The T5-Large model is loaded using the Hugging Face pipeline for summarization:
```python
summarizer = pipeline("summarization", model="t5-large")
```

### Gradio Interface
The Gradio interface is defined as follows:
```python
demo = gr.Interface(
    fn=summarizer,
    inputs=[gr.Textbox(label="Text to summarize", lines=10)],
    outputs=[gr.Textbox(label="Summarization", lines=6)],
    title="Text Summarization with T5-Large Model",
    description="Summarize any text with the t5-large model under the hood!",
    allow_flagging="never",
    css="""
     .gradio-container {background-color: DarkCyan;}
     button {background-color: Green; color: black; border-radius: 8px; border: none;}
     button:nth-child(1) {background-color: Orange; color: white; border-radius: 8px; border: none;}
    """
)
```
This code:
- Configures the summarizer function to handle user input.
- Adds input and output textboxes for interaction.
- Styles the container and buttons with CSS.

## Example Usage
1. Paste or type the text you want to summarize into the input box.
2. Click the "Submit" button.
3. View the generated summary in the output box.

## Notes
- Ensure you have a valid Hugging Face API key if needed for model access.
- This script is designed for use in a Python environment like Google Colab or Jupyter Notebook.
**********
***********
# Named Entity Recognition (NER) Application.

## **Overview**
This application demonstrates a Named Entity Recognition (NER) tool built using the `dslim/bert-base-NER` model from Hugging Face Transformers library. It identifies entities such as persons, locations, and organizations in a given text and highlights them in the output.

The app leverages the Gradio library to provide an easy-to-use web interface for interacting with the model.

---

## **Features**
- **Entity Recognition:** Extract entities like persons, locations, and organizations from input text.
- **Interactive UI:** Users can enter their text, view the recognized entities highlighted in the output, and try predefined example texts.
- **Example Texts:** Includes various example texts to demonstrate the model’s capabilities.
- **Custom Styling:** Aesthetic design with a green Submit button and a MediumAquaMarine background.

---

### **Prerequisites**
1. Python installed on your machine (Python 3.7 or later recommended).
2. Install the required Python packages:
   ```bash
   pip install gradio transformers
   ```

### **Running the Application**
1. Save the provided code in a Python file, e.g., `ner_demo.py`.
2. Run the file using:
   ```bash
   python ner_demo.py
   ```
3. Open the provided URL in your web browser to interact with the app.

---

## **Code Explanation**

### **Pipeline for Named Entity Recognition**
```python
from transformers import pipeline
NER = pipeline("ner", model="dslim/bert-base-NER")
```
- The `pipeline` function initializes the NER model from the Hugging Face library.

### **Token Merging**
```python
def merge_tokens(tokens):
    merged_tokens = []
    for token in tokens:
        if (
            merged_tokens
            and token['entity'].startswith('I-')
            and merged_tokens[-1]['entity'].endswith(token['entity'][2:])
        ):
            last_token = merged_tokens[-1]
            last_token['word'] += token['word'].replace('##', '')
            last_token['end'] = token['end']
            last_token['score'] = (last_token['score'] + token['score']) / 2
        else:
            merged_tokens.append(token)
    return merged_tokens
```
- This function merges consecutive tokens that belong to the same entity, ensuring accurate results for subword tokens.

### **NER Function**
```python
def ner(input_text):
    output = NER(input_text)
    merged_tokens = merge_tokens(output)
    return {
        "text": input_text,
        "entities": [
            {"start": t["start"], "end": t["end"], "entity": t["entity"]}
            for t in merged_tokens
        ]
    }
```
- This function processes the input text, retrieves raw NER results, merges tokens, and formats the output for display.

### **Gradio Interface**
```python
demo = gr.Interface(
    fn=ner,
    inputs=[gr.Textbox(label="Text to find entities", lines=2)],
    outputs=[gr.HighlightedText(label="Text with entities")],
    title="NER with dslim/bert-base-NER",
    description="Find entities using the `dslim/bert-base-NER` model under the hood!",
    allow_flagging="never",
    examples=[
        "My name is Olfat, and I live in Giza",
        "Dr. John Smith works at Stanford University, and his research focuses on Artificial Intelligence. He lives in Palo Alto, California.",
        "Amal moved to Paris in 2015 and started working at UNESCO as a project manager. Her brother, Karim, is studying medicine in Cairo.",
        "The Eiffel Tower is located in Paris, France, and attracts millions of tourists every year. Marie and Jean visited it during their honeymoon.",
        "Microsoft Corporation, headquartered in Redmond, Washington, was founded by Bill Gates and Paul Allen in 1975. It is one of the largest tech companies in the world.",
        "Barack Obama, the 44th President of the United States, was born in Honolulu, Hawaii, and graduated from Harvard Law School."
    ],
    css="""
        .gradio-container {background-color: MediumAquaMarine;}
        button.gr-button-primary {background-color: green; color: white; border-radius: 8px; border: none;}
    """
)

demo.launch()
```
- The `gr.Interface` object defines the Gradio interface.
- Includes:
  - **Input:** A textbox for user input.
  - **Output:** A highlighted text box showing recognized entities.
  - **Examples:** A list of predefined example texts.
  - **CSS Styling:** Customizes the background and button colors for improved UI.

---

## **Example Texts**
1. **"My name is Olfat, and I live in Giza."**
2. **"Dr. John Smith works at Stanford University, and his research focuses on Artificial Intelligence. He lives in Palo Alto, California."**
3. **"Amal moved to Paris in 2015 and started working at UNESCO as a project manager. Her brother, Karim, is studying medicine in Cairo."**
4. **"The Eiffel Tower is located in Paris, France, and attracts millions of tourists every year. Marie and Jean visited it during their honeymoon."**
5. **"Microsoft Corporation, headquartered in Redmond, Washington, was founded by Bill Gates and Paul Allen in 1975. It is one of the largest tech companies in the world."**
6. **"Barack Obama, the 44th President of the United States, was born in Honolulu, Hawaii, and graduated from Harvard Law School."**

---

## **Customization**
- Modify the CSS to change the background or button styles.
- Add more examples or adjust the `ner` function for additional functionality.

---

## **Acknowledgments**
- Hugging Face for providing the `dslim/bert-base-NER` model.
- Gradio for simplifying the creation of interactive web applications.


***********
## License
This project is licensed under the MIT License. Feel free to modify and use it as needed.


