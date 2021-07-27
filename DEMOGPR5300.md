# Blogpost DemoGPR5300

## 1. Introduction

This is a blogpost about the 3D scene demo I had to do for the GPR5300 module at SAE Geneva using OpenGL. I followed some of the tutorials from LearnOpenGL to make my scene :
[https://learnopengl.com/](https://learnopengl.com/)

## 2. Cubemaps

For this scene I used the skybox given by LearnOpenGL : [https://learnopengl.com/Advanced-OpenGL/Cubemaps](https://learnopengl.com/Advanced-OpenGL/Cubemaps)

I first made an array of vertices for my skybox :

![cubemaps](https://user-images.githubusercontent.com/55788730/127165665-f3672916-a048-486a-a71c-85ee933f4702.PNG)

Then I generate the Vertex Array Object (VAO) and Vertex Buffer Object (VBO) and transfer the datas to the GPU :

![cubemaps2](https://user-images.githubusercontent.com/55788730/127166041-5863f82c-e20a-4a3e-a21b-a86e9db6ee66.PNG)

Then we take the textures with the right path from my folders and show them in the scene :

![demopres](https://user-images.githubusercontent.com/55788730/127166287-f5eb115e-4598-4b8c-af98-df3f065aabba.PNG)

## OBJ

For my obj I have a model class which takes care of loading it in the scene. 

![obj](https://user-images.githubusercontent.com/55788730/127166729-5218e524-3838-4941-a140-e74213628bc9.PNG)

![obj2](https://user-images.githubusercontent.com/55788730/127167284-064bb5bc-3b5c-4245-ad6e-997510bb3267.PNG)

And I call this function in the update. We can also change the positions of our obj.

![obj3](https://user-images.githubusercontent.com/55788730/127167364-f6d121c2-ee21-41af-a8cd-be30d4de6a87.PNG)

I paid to get this model and if you'd like to have it too you can find it here : 

[https://www.cgtrader.com/3d-models/exterior/landscape/snowy-mountain-8k-textures](https://www.cgtrader.com/3d-models/exterior/landscape/snowy-mountain-8k-textures)

## Framebuffer

For the framebuffer I first made coordinates for the quad vertices.

![framebuffer](https://user-images.githubusercontent.com/55788730/127167669-6c90e96f-8c76-40e5-a00f-b329d2b1a3d5.PNG)

Then we generate and bind the Framebuffer Object (FBO) and the Renderbuffer Object (RBO) : 

![framebuffer2](https://user-images.githubusercontent.com/55788730/127168038-ebc95068-072b-4fb7-bac3-d16a2390d807.PNG)

![framebuffer3](https://user-images.githubusercontent.com/55788730/127168083-f69fc369-f605-42e6-8688-b42c40e7473e.PNG)

We also generate and bind the quad VAO and quad VBO :

![framebuffer4](https://user-images.githubusercontent.com/55788730/127168260-65c68695-520e-420d-85bb-31a1285f1ce1.PNG)

We also need to make our shaders, here's the fragment shader :

![fbofrag](https://user-images.githubusercontent.com/55788730/127169511-0d51021f-118c-45ad-8d6b-f23b3318f6e9.PNG)

and our vertex shader :

![fbovert](https://user-images.githubusercontent.com/55788730/127169667-c2d9a145-e239-491e-8838-f6e970f36902.PNG)

Then we call the shaders and everything that we need in the update to be able to use the framebuffer in our scene :

![framebuffer5](https://user-images.githubusercontent.com/55788730/127168979-ecf77f4c-d53b-48bd-b26a-24cac177bb3a.PNG)

![framebuffer6](https://user-images.githubusercontent.com/55788730/127169009-e32d43da-4239-49a1-aca6-212bb22bef20.PNG)

![framebuffer7](https://user-images.githubusercontent.com/55788730/127169057-6a2db74b-6a21-44b6-abc5-b74edee9adc6.PNG)

![framebuffer8](https://user-images.githubusercontent.com/55788730/127169107-ca97fc70-460b-4d5d-a779-c791fccb3182.PNG)

and we know it works because if we put this line instead of the other one in our fragment shader, the scene looks like this :

![framebuffer10](https://user-images.githubusercontent.com/55788730/127169957-5715cd0d-d982-484b-8ddd-a49dafb6f0c7.PNG)

![framebuffer9](https://user-images.githubusercontent.com/55788730/127170043-cd059b1c-b184-4161-9c0b-360cd31e8f2c.PNG)


## Directional Light & Normal Map

For the directional light we don't need any position because it lights the whole scene. Since I had shaders for both my directional light and my normal map, I decided to make a "mix" of the two in the normal map vertex and fragment shaders.

I had first encountered a bug where my normal map texture would show in Render Doc but the whole scene was dark as if there wasn't any light.

![normalmapbug3](https://user-images.githubusercontent.com/55788730/127172126-7524817f-8df8-46b6-b637-12f8f3cbff38.PNG)

![normalmapbug2](https://user-images.githubusercontent.com/55788730/127171176-2f9cf409-9e89-4ead-929b-34ac3dee6df0.PNG)

The problem came from this line in the fragment shader with the diffuse light : 

![nmbug](https://user-images.githubusercontent.com/55788730/127171763-6a881cd5-d717-4a35-bbde-179147c37a8a.PNG)

Instead of TangentLightPos - TangentFragPos I only needed to change it to -TangentLightPos :

![nmbug2](https://user-images.githubusercontent.com/55788730/127172036-f75d923e-124e-4dc9-b038-ea7d3bb53830.PNG)

Here's the normal map + directional light vertex shader : 

![nmvert](https://user-images.githubusercontent.com/55788730/127173079-46d547b1-a699-4a2a-ac7f-99372130b40b.PNG)

Here's the normal map + directional map fragment shader :

![nmfrag](https://user-images.githubusercontent.com/55788730/127173221-f12cf465-52cc-4a82-befb-dfe2d87e512b.PNG)

![nmfrag2](https://user-images.githubusercontent.com/55788730/127173258-89177f25-08f4-41d9-ace9-2e1d4fe72d33.PNG)

And then my scene had a light with some shadows and the normal texture.

![finalscene](https://user-images.githubusercontent.com/55788730/127172668-dd96b5cb-3110-468e-a279-0f2da8bb3e84.PNG)













