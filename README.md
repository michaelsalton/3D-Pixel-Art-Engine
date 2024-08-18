# 3D-Pixel-Art-Engine

## Whats been implemented

Here is a very high level list of what I've made so far. More details on each one further down: Pixellated camera, Toon shader, Grass shader, Isometric camera, Grass spawner (Poisson-Disc Sampling), Dynamic day night cycle, Isometric player movement, Particle effects.

## Features Explained
Here I'll explain each feature in more detail.

### Pixellated Camera

![pae1](https://github.com/user-attachments/assets/a448d820-f550-41c9-aab6-a9700bdf3fd5)

The pixellated camera creates a cool retro aesthetic. It was done by lowering the resolution of the camera to 640 x 320 then sizing it up to the monitors resolution.

The camera also implements pixel-perfect rendering and sub-pixel camera movement.

Pixel-perfect rendering ensures that the rendered graphics align precisly with the pixels on the screen, preserving the crispness of the visuals. It ensures the objects appear sharp and clear without blurring or distortion caused by non-integer scaling or interpolation.

![pae2](https://github.com/user-attachments/assets/9fbd78bb-3fbd-4ca8-b0cb-dc4d1321aa41)

Sub-pixel camera movement allows for smooth and precise camera motion, even at sub-pixel increments. In traditional rendering, the camera's movement may result in jittery or uneven motion due to the discrete nature of pixel coordinates. However, with sub-pixel movement, the camera can smoothly interpolate its position between pixel boundaries. resulting in fluid motion without noticable jumps or stuttering.

### Toon Shader

![image3](https://github.com/user-attachments/assets/60bbc341-4a46-461a-bf97-2045d82a0a6f)

"Toon shading" is a common shading technique done in art to give the image a stylized look that often resembles a cartoon. The same effect can be done in video games with a shader.

My toon shader uses diffuse and specular lighting calculations, along with rim lighting effects, to enhance the object's contours and highlights. The shader allows for the customization of parameters such as color, glossiness, and rim intensity, allowing for control over the final look.

![image4](https://github.com/user-attachments/assets/906bad91-909a-4780-a0fc-6fec8d830754)

### Grass Shader

![pae3](https://github.com/user-attachments/assets/56bf57c6-2025-46ec-a80a-359ad7c9ff65)

The shader uses 2D billboard sprites to simulate the look of grass over a 3D terrain. By blending textures and simulating the effect of wind, it crafts a natural aesthetic.

An orthographic camera points down at the terrain, culling out anything else, and renders that to a render texture. This render texture is then used to sample the color of the terrain under each of the grass's vertices. That color is then applied to that vertex of the grass sprite. Since the grass is sprites, each one has 4 vertices, however only 2 have unique x,z coordinates. Which means that each sprite can blend between 2 colors, if the sprite is placed in a spot where the terrain underneath has 2 colors.

This color sampling adds a really cool effect to the grass.

The grass shader also has color blending options for further configurations.

![image7](https://github.com/user-attachments/assets/f835cdf9-d30a-455a-9b68-81d347843a85)

![image10](https://github.com/user-attachments/assets/019463b2-8510-4d0e-97a7-137b8a74d74a)

### Isometric Camera

I implemented an isometric camera that can rotate around the player in 45 degree increments. This adds a really cool effect that really makes the world feel more 3D. Even though the world is 3D, due to the camera orientation and lack of vertical movement, a cool 2D retro effect emerges. The 2D feel combined with the rotatable camera makes for a really unique blend between retro and modern.

The player can click the middle mouse button to return the camera to the default angle.

![image13](https://github.com/user-attachments/assets/fe53a88b-2911-4409-9c70-d4975d8fb115)

![image8](https://github.com/user-attachments/assets/f9b5d366-ea86-4897-8985-083675d089ce)

### Grass spawner

I created a grass spawning tool that uses an algorithm called Poisson Disc Sampling - a technique used to generate a set of points with a minimum distance between each other.

![image5](https://github.com/user-attachments/assets/a401ab53-d193-4f7b-a88b-bc23a5f24a74)

Using this algorithm ensures that the area will be evenly covered in grass, which is important for the style I'm going for. It also ensures maxmimum performance as no 2 sprites will ever spawn in the same spot, which would waste compute resources for no visual difference.

I also made the tool so that the points can be seen from the scene view and the bounding box can be easily moved or its size adjusted, and the algorithm will re-render the points in real time.

### Dynamic Day-Night Cycle

I implemented a time mechanic with seconds, minutes, hours, days, months, and years. The sun (directional-light) is on a schedule to rotate around based on the time of day. I have a sunset time and sunrise time and as the day goes by different lighting moods fill the scene.

![image11](https://github.com/user-attachments/assets/94d85f4a-2bba-4f47-a010-e4c7743c131a)

![image2](https://github.com/user-attachments/assets/73d0fa7f-45ad-4dff-b456-f674cb3c6297)

![image6](https://github.com/user-attachments/assets/ea7ac645-3e6b-42b9-9709-278ba6ee8694)

![image9](https://github.com/user-attachments/assets/52b852af-e975-40e2-b240-426e38b17893)

![image15](https://github.com/user-attachments/assets/7099f38d-2426-4aa6-82bb-a674871b53a1)

Thanks for reading!
