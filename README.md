# Sepia Image Converter with Gradio
This project provides a simple Gradio interface to apply a sepia tone filter to uploaded images. It demonstrates how to use Python and Gradio for image processing with a focus on creating vintage-style images.

## Features
- Image Upload: Upload images in common formats (e.g., PNG, JPEG).
- Sepia Filter Application: The interface applies a sepia-tone transformation to the uploaded image.
- Interactive Interface: Built with Gradio, allowing real-time interaction and visualization.
- Customizable Filter: The sepia transformation can be adjusted to create different effects.

##Technologies Used
- Python: Core programming language.
- Pillow (PIL): For image processing.
- Gradio: To build the user interface.

## How It Works
1. Input: The user uploads an image through the Gradio interface.
2. Processing:
- The red, green, and blue (RGB) values of each pixel are modified using the following sepia formula:

                         tr = int(0.393 * r + 0.769 * g + 0.189 * b)
                         tg = int(0.349 * r + 0.686 * g + 0.168 * b)
                         tb = int(0.272 * r + 0.534 * g + 0.131 * b)
  
- The values are clipped to a maximum of 255 to prevent overflow.
3. Output: The processed image with the sepia tone is displayed.
  
## Customization
### Adjusting the Sepia Tone
The sepia effect is controlled by the transformation matrix in the code:

                       tr = int(0.393 * r + 0.769 * g + 0.189 * b)
                       tg = int(0.349 * r + 0.686 * g + 0.168 * b)
                       tb = int(0.272 * r + 0.534 * g + 0.131 * b)
You can modify these coefficients to experiment with different color effects.                     
### Adding Custom CSS
You can style the Gradio interface by providing custom CSS. For example, to change the title and description colors:
