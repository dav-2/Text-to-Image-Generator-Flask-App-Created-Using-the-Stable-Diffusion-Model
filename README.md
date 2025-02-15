<h1>AI Text-to-Image Generator with Stable Diffusion</h1>

An easy-to-use AI text-to-image generator created using Flask and the Stable Diffusion model.

text_to_image_generator.ipynb is the model running inside Colab.

text_to_image_generator_app.ipynb opens a small web app where the user interacts with the image generator.

Stable Diffusion Model version used: stable-diffusion-2-1. Even though the stable-diffusion-2-1 version was released in December 2022, it still offers a good balance beween precision, speed and resources counsumption. The main reason behind the decision to use this version was to optimise Google Colab resources. However, if a better image quality and/or prompt interpretation is needed, newer versions of the model can be used by changing the version in the code.

Google Colab runs in a cloud-based environment where each notebook is executed on a virtual machine. This VM is isolated from the internet for security and privacy reasons. Ngrok is a tool that creates secure tunnels to your localhost, allowing you to expose a local development server to the internet. When working in Google Colab, ngrok can be particularly useful for creating web applications or APIs that you want to test or share with others, as it creates tunnels that securely expose the services running inside these VMs to the internet. To use ngrok it is needed to create a free ngrok account and use the authtoken provided in it.

<h3>How to Use the Text to Image Generator App</h3>

1. Open the file text_to_image_generator_app.ipynb.

2. Create a free ngrok account.

3. Copy the authtoken provided in your ngrok account and paste it in the code in the following line after the word "authtoken": !ngrok authtoken  # Write your ngrok authtoken here.

4. Run the code.

5. Click on the ngrok-free.app link in the output. It opens a page reminding you that you are opening a website served for free through ngrok.com.
   
7. Click on the 'Visit Site' button.

<h2>Examples of Images Generated with the App</h2>

Prompt: green square

![green square prompt](https://github.com/user-attachments/assets/a38e6289-62bd-47d0-abf4-25e939482d04)

Prompt: Las meninas Velazquez Van Gogh like

![Las meninas Velazquez Van Gogh like prompt](https://github.com/user-attachments/assets/4e74da51-b62e-4be3-a9ff-45ec316909ca)

Prompt: Edinburgh castle

![Screenshot 2024-07-23 at 20-29-11 (PNG Image 768 × 768 pixels)](https://github.com/user-attachments/assets/acfade24-ba58-4645-8122-de1b7d045adb)

Prompt: yellow square

![yellow square prompt](https://github.com/user-attachments/assets/42f6bc83-d6a7-4c49-8d46-af498f03153b)

Prompt: white cat

![white cat prompt](https://github.com/user-attachments/assets/50ec151d-052f-4334-b9ee-ba4eaa8f3091)

Prompt: sea with beach Van Gogh like

![sea with beach Van Gogh like](https://github.com/user-attachments/assets/bda5c80b-7260-4e91-99c7-3fc9d68806bf)

Prompt: black square

![black square prompt](https://github.com/user-attachments/assets/8ca983f7-f65c-4fde-baee-17ec8335315c)

Prompt: New York city

![Screenshot 2024-07-23 at 20-30-35 (PNG Image 768 × 768 pixels)](https://github.com/user-attachments/assets/ccfb679b-4f13-42f0-810a-8fe81c78bfd0)

Prompt: realistic image of New York city

![Screenshot 2024-07-23 at 20-31-31 (PNG Image 768 × 768 pixels)](https://github.com/user-attachments/assets/a54cc6fa-6ec6-4617-b4b3-184fa05f1ebd)

Prompt: stormy sea with an island

![Screenshot 2024-07-23 at 20-27-48 (PNG Image 768 × 768 pixels)](https://github.com/user-attachments/assets/4b823948-03b8-4ef7-908b-5cca301924a7)


<h1>The AI Image Generator Behind the App: Stable Diffusion Model</h1>

<h2>Diffusion Models</h2>

Diffusion models are a type of machine learning model that has gained significant attention in the field of generative modelling. These models are particularly notable for their ability to generate high-quality images.

<h4>Overview of Diffusion Models</h4>

Diffusion models, also known as score-based generative models or denoising diffusion probabilistic models (DDPMs), generate data by reversing a diffusion process. The key idea is to start with a simple distribution (like Gaussian noise) and progressively refine it into a complex data distribution (like images) through a series of denoising steps.

<h4>Forward Diffusion Process</h4>

The forward process involves gradually adding noise to the data in a sequence of steps. This process transforms the data into a noise distribution. Over many steps, this process ensures that the data becomes indistinguishable from Gaussian noise.

<h4>Reverse Diffusion Process</h4>

The reverse process aims to gradually remove the noise, reconstructing the data from the noisy version. This involves learning a denoising function that can predict the clean data from the noisy data at each step. 

<h4>Training the Model</h4>

Training a diffusion model involves optimising the parameters to minimise the difference between the predicted clean data and the actual clean data at each step.

<h4>Generation Process</h4>

Once trained, generating new data involves starting with a sample from the Gaussian noise distribution and iteratively applying the learned denoising steps. This gradually transforms the noise into a coherent sample from the data distribution.

<h4>Applications and Advantages</h4>

Diffusion models have been shown to generate high-quality images and are competitive with other generative models like GANs (Generative Adversarial Networks) and VAEs (Variational Autoencoders). They have several advantages:
- Stable Training: Unlike GANs, diffusion models do not suffer from mode collapse or instability during training.
- High-Quality Outputs: They can produce high-resolution and detailed images.


<h2>Latent Diffusion Models</h2>

Latent Diffusion Models (LDMs) are an extension of the basic diffusion models that operate in a latent space instead of directly in the pixel space. This can lead to more efficient and scalable generative modelling, particularly for high-dimensional data like images.

<h4>Overview of Latent Diffusion Models</h4>

Latent Diffusion Models leverage the idea of performing the diffusion process in a lower-dimensional latent space rather than in the original high-dimensional data space. This is achieved by using an autoencoder to encode the data into a latent representation and then applying the diffusion process within this latent space.

<h4>Components of Latent Diffusion Models</h4>

LDMs consist of three main components:
- Autoencoder (Encoder-Decoder Network): This network compresses the high-dimensional data (e.g., images) into a lower-dimensional latent space and then reconstructs the data from this latent representation. The autoencoder has two parts: 
    - Encoder: Compresses the high-dimensional data  into a latent representation.
    - Decoder: Reconstructs the data from the latent representation.
- Diffusion Process in Latent Space: The diffusion model operates on the latent representations, adding noise and learning to denoise these representations.
- Latent Variable Model: This model captures the distribution of the latent representations.


<h4>Forward Diffusion Process in Latent Space</h4>

Similar to standard diffusion models, the forward diffusion process involves adding noise to the latent representations over a sequence of steps.

<h4>Reverse Diffusion Process in Latent Space</h4>

The reverse diffusion process aims to denoise the latent representations.

<h4>Training the Latent Diffusion Model</h4>

Training involves optimising the parameters to minimise the difference between the true and predicted distributions in the latent space.

<h4>Generation Process</h4>

To generate new data, the process involves:
1. Sampling from the Gaussian noise distribution in the latent space.
2. Applying the learned denoising steps to obtain a latent representation.
3. Using the decoder to reconstruct the high-dimensional data from the latent representation.

<h4>Advantages of Latent Diffusion Models</h4>

- Efficiency: Operating in a lower-dimensional latent space reduces the computational complexity and memory requirements compared to working in the high-dimensional pixel space.
- Scalability: LDMs can handle higher resolutions and larger datasets more efficiently.
- Quality: By focusing the diffusion process on essential features in the latent space, LDMs can achieve high-quality generation with fewer steps.


<h2>Stable Diffusion Models</h2>

The Stable Diffusion Model is a specific implementation of the latent diffusion model (LDM) architecture that leverages the strengths of both diffusion processes and latent space representations to generate high-quality images from text prompts.

<h4>Detailed Architecture</h4>

1. Latent Space Encoder-Decoder

    - Encoder: A convolutional neural network (CNN) that compresses high-dimensional image data into a lower-dimensional latent space.
    - Decoder: Another CNN that reconstructs images from the latent representations. This setup helps in reducing the computational cost and memory requirements compared to operating directly on high-resolution images.

2. Diffusion Process in Latent Space

    - Forward Diffusion Process: Gradually adds noise to the latent representations over a series of time steps.
    - Reverse Diffusion Process: The model learns to denoise the latent representations, starting from pure noise and progressively reducing the noise to generate coherent images.

3. Text Encoder

    - Text Encoder: Typically uses a pre-trained transformer-based model (such as CLIP from OpenAI) to encode text prompts into high-dimensional embeddings.
    - Text Embeddings: These embeddings condition the diffusion process, guiding the model to generate images that correspond to the text prompts.

4. U-Net-based Denoising Network

   U-Net Architecture: The core of the denoising process is a U-Net, which is a convolutional neural network with an encoder-decoder structure and skip connections.
   - Encoder: Downsamples the noisy latent representation, capturing hierarchical features.
   - Bottleneck: Processes the compressed features, integrating the text embeddings as conditioning information.
   - Decoder: Upsamples the processed features back to the original latent space size, combining information from the encoder through skip connections to preserve spatial details.
   - Skip Connections: Connect corresponding layers of the encoder and decoder, allowing the network to retain high-resolution features and improve gradient flow during training.

6. Scheduler for Diffusion Steps

    - Step Scheduler: Controls the noise addition and removal process, ensuring a smooth transition between the forward and reverse diffusion steps.
    - Adaptive Scheduling: Some implementations use adaptive schedulers to dynamically adjust the noise levels based on the current state of the image generation process.

<h4>Workflow of the Stable Diffusion Model</h4>

1. Text Encoding: The text prompt is encoded into a high-dimensional embedding using a pre-trained text encoder.
2. Latent Encoding: An initial image (if provided) is encoded into a latent representation. For purely generative tasks, this step might be skipped, and the process starts with pure noise in the latent space.
3. Forward Diffusion: Noise is progressively added to the latent representation over a series of time steps, following a predefined noise schedule.
4. Conditioned Denoising: The noisy latent representation, along with the text embeddings, is passed through the U-Net-based denoising network. The U-Net iteratively reduces the noise, guided by the text embeddings, to generate a coherent image in the latent space.
5. Latent Decoding: The denoised latent representation is decoded back into the image space using the decoder network.
6. Image Generation: The final image is generated, corresponding to the input text prompt.

<h4>Summary of the Stable Diffusion Model Architecture</h4>

- Encoder-Decoder: Compresses and reconstructs images into/from a latent space to reduce computational complexity.
- Diffusion Process: Applies noise in the latent space and learns to reverse this process to generate images.
- Text Encoder: Uses transformer-based models to encode text prompts into conditioning embeddings.
- U-Net Denoising Network: Performs the core denoising task, integrating text embeddings to guide image generation.
- Scheduler: Manages the noise levels during the diffusion process, ensuring smooth transitions between steps.

The combination of these components allows the Stable Diffusion Model to efficiently generate high-quality images that align well with the provided text prompts, leveraging the power of diffusion processes and the efficiency of latent space representations.

The Stable Diffusion models are tuned to produce art. They are trained on LAION-5B; a large-scale dataset containing billions of image-text pairs.


<h2>References</h2>

Abdal, R., Zhu, P., Mitra, N. J., & Wonka, P. (2021). Image Synthesis with Disentangled Diffusion Probabilistic Models. arXiv preprint arXiv:2106.01321.

Croitoru, I., Bogojeski, M., & Amiranashvili, T. (2023). Diffusion Models: A Comprehensive Review of Methods and Applications. arXiv preprint arXiv:2301.04971.

Goodfellow, I., Bengio, Y., & Courville, A. (2016). Deep Learning. MIT Press.

Ho, J., Jain, A., & Abbeel, P. (2020). Denoising Diffusion Probabilistic Models. arXiv preprint arXiv:2006.11239.

Rombach, R., Blattmann, A., Lorenz, D., Esser, P., & Ommer, B. (2022). High-Resolution Image Synthesis with Latent Diffusion Models. arXiv preprint arXiv:2112.10752.

Rombach, R., Blattmann, A., Lorenz, D., Esser, P., & Ommer, B. (2022). Stable Diffusion: High-Resolution Image Synthesis with Latent Diffusion Models. CompVis GitHub Repository. Available at: https://github.com/CompVis/stable-diffusion.

Song, Y., & Ermon, S. (2019). Generative Modeling by Estimating Gradients of the Data Distribution. arXiv preprint arXiv:1907.05600.

Song, Y., & Ermon, S. (2020). Improved Techniques for Training Score-Based Generative Models. arXiv preprint arXiv:2006.09011.

