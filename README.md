# Human-Centered Artificial Intelligence (HCAI)

These three Python-based programs were my hand-ins for the course HCAI. Each one explored a different AI modality, focusing on how users interact with AI systems through text, image and audio/video inputs.

The goal of the course was to provide students with knowledge and skills related to user-centred artificial intelligence, with a particular focus on interaction with AI technologies. The course included both a theoretical component, which covered human interaction with AI systems, different types of interaction, and fundamental concepts such as AI models and classification, as well as a practical, application-oriented part. This hands-on part involved setting up and using specific AI models, including training and evaluating them using relevant data.

# Modality 1 - Text:

For the text modality I created PC build comparator that takes in two text-based PC configurations (usually copied from PCPartPicker) and generates a detailed comparison between them. Users can adjust the complexity level of the explanation, from beginner-friendly to expert-level, and choose a specific focus such as CPU, GPU or storage. Based on these inputs, the system explains which build is faster, potentially more expensive and better suited for specific tasks, offering context-sensitive insights tailored to different levels of technical understanding.
![Text Modality](https://github.com/user-attachments/assets/15664a7b-4e4f-4c96-8b7e-58bfa156ec86)

**How does it work?**

The application is built using LangChain and OpenAI’s GPT-3.5-turbo model, wrapped in a Gradio interface for user interaction. When the user submits two builds and selects their desired comparison parameters, the system constructs a series of prompts accordingly. These include the two PC build descriptions, the desired focus (fx GPU), and the preferred explanation complexity. The prompts are passed into the language model using LangChain's ChatOpenAI, which then returns a natural language comparison. The Gradio interface handles all user inputs and displays the final AI-generated output seamlessly.

# Modality 2 - Image:

This program allows users to capture an image via webcam and transform it into a stylised artwork using well-known artistic styles. Users can choose between a "Painting" or "Drawing" look, and apply one or more famous art styles such as Van Gogh, Picasso, Warhol or Salvador Dalí. Additionally, a custom instruction box lets users input extra commands, such as stylistic tweaks or visual additions like fire or surreal elements, giving them fine-grained control over the artistic output.

![Image Modality](https://github.com/user-attachments/assets/712e18cf-dbf4-496f-9851-46520e8ccdc5)

**How does it work?**

The application uses the [Stable Diffusion InstructPix2Pix](https://huggingface.co/docs/diffusers/training/instructpix2pix) model from Hugging Face, which is a powerful diffusion-based image-to-image transformer that modifies images based on textual prompts. When a user selects their desired style(s), art form, and any additional instructions, the tool generates a tailored prompt combining all these parameters. The image is then preprocessed and passed through the model using specific configuration settings (like number of steps, seed values, and guidance scales). The resulting stylised image is rendered live through a Gradio interface, making the whole process interactive, flexible and visually intuitive.

# Modality 3 - Emotion:

This interactive webcam-based game challenges users to quickly express three specific emotions, happy, angry and surprised, across three timed rounds. The system uses real-time facial analysis to detect whether the correct emotion is being expressed. If the emotion is correctly identified by the model, the player progresses to the next round. Once all rounds are completed, the total time is recorded and added to a persistent leaderboard, rewarding users who complete the game in the shortest time.
![Emotion Modality](https://github.com/user-attachments/assets/c6dab7e5-80b4-4ae1-a0ee-fc965c007cb1)

**How does it work?**

The game is implemented in Python using OpenCV for webcam capture and DeepFace for real-time emotion recognition. When the game starts, the user's webcam is activated via a custom JavaScript bridge for Google Colab. The user is prompted to perform a specific emotion for each round. The system then analyses the webcam feed using DeepFace's analyze method, checking if the detected dominant emotion matches the expected one. The user’s completion time is calculated using Python’s datetime module, and the best times are stored and displayed from a leaderboard.txt file. All visual feedback, such as round number and detection messages, is overlaid directly on the live video stream using OpenCV’s putText.
