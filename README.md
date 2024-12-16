# CLIP Image Analysis and Caption Generation

This project combines the power of the CLIP model and the Gemini LLM to analyze images and generate meaningful captions. Below are the details on how the code works and how to use it effectively.

---

## Features

### 1. **Image Loading**
- **Functionality**: Load images from a URL or local file path.
- **Implementation**: The `load_image()` function uses PIL to open the image and ensures it is in RGB format.

### 2. **Image Analysis with CLIP**
- **Model**: `openai/clip-vit-base-patch32`.
- **Functionality**:
  - Analyze the image to identify top places using Places365 labels.
  - Detect prominent objects using COCO object labels.
- **Implementation**:
  - The `analyze_image_with_clip()` function combines Places365 and COCO labels.
  - The CLIP model processes the image and text labels to predict places and objects.
  - Top predictions are extracted based on softmax probabilities.

### 3. **Caption Generation with Gemini LLM**
- **API**: Google Gemini LLM.
- **Functionality**:
  - Generate a descriptive caption based on the identified places and objects.
  - Optionally incorporate a user-provided context word.
- **Implementation**:
  - The `generate_image_caption()` function constructs a prompt using CLIP's outputs.
  - The Gemini LLM generates a detailed caption based on the prompt.

---

## How to Use

### 1. Install Dependencies
Ensure you have the following Python libraries installed:
```bash
pip install torch transformers pillow requests google-generativeai
```

### 2. Set Up Gemini API Key
Replace the placeholder in the `genai.configure()` function with your actual Gemini API key:
```python
genai.configure(api_key="YOUR_API_KEY")
```

### 3. Running the Code
1. Load an image from a URL or file path using `load_image(image_path)`.
2. Analyze the image with CLIP using `analyze_image_with_clip(image)`.
3. Generate a caption using `generate_image_caption(image_path, context_word)`.

### Example Usage
```python
image_path = "https://example.com/image.jpg"
caption = generate_image_caption(image_path, context_word="nature")
print("Generated Caption:", caption)
```

---

## Labels Used
- **Places365 Labels**: Common locations such as `beach`, `library`, `stadium`, etc.
- **COCO Labels**: Objects like `person`, `bicycle`, `dog`, `car`, etc.

---

## Error Handling
- Handles invalid image paths or URLs gracefully.
- Prints meaningful error messages for debugging API issues or model exceptions.

---

## Future Enhancements
1. Expand the label set for broader image analysis.
2. Add support for more advanced captioning models.
3. Improve performance for large-scale batch processing.
4. Secure sensitive configurations such as API keys.

---

## Credits
- **CLIP Model**: [OpenAI](https://github.com/openai/CLIP)
- **Gemini LLM**: [Google Generative AI](https://cloud.google.com/gen-ai)

