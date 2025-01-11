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
                                       
******************************************************************************************************************************
******************************************************************************************************************************
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

---

** License**
This project uses pre-trained models from Hugging Face.

---

 **Acknowledgments**
- [Hugging Face](https://huggingface.co/) for providing the pre-trained models.
- [Gradio](https://gradio.app/) for simplifying user interface creation.
  
 ******************
 ******************
