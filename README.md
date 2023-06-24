# rgb-offset
Offset an Image or color channel position.

The rgbOffset package enables you to offset the X & Y position of inputted image pixels or the pixel values for individual RGB channels. This is a common effect in graphics programs like Adobe Photoshop and GIMP.

This package does not require JavaFX. It is built using the Java AWT API only.
No Offset                  |  Offset X= 256, Y= -128   |  Offset RGB channels      |  Offset just Red X&Y = 32         
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![0](https://github.com/aabalke33/rgb-offset/assets/22086435/33fdf9f7-05b6-4b47-82f5-aec24283d8fc)  |  ![256-128](https://github.com/aabalke33/rgb-offset/assets/22086435/0f2dd0fb-8ea8-4cb8-afca-84964ee054ea)  |  ![03264-32](https://github.com/aabalke33/rgb-offset/assets/22086435/cb5126ff-cddd-4186-bb93-acca6fa03417)  |  ![03200](https://github.com/aabalke33/rgb-offset/assets/22086435/12ef6739-0517-4b19-a653-b6545fe9c231)

## Usage
The offset methods take image data expressed as a BufferedImage. An example is provided below for a standard method of creating and inputting BufferedImage parameters.

Input Methods are overloaded. Allowing for method calls with channel values and without. If channel values are not inputted, it is assumed to be 0.
```java
// Without Channel Values
BufferedImage image = rgbOffset.offset(image, xOffset, yOffset);

// With Channel Values
BufferedImage image = BlendMode.screen(image, xOffset, yOffset, rxOffset, ryOffset, gxOffset, gyOffset, bxOffset, byOffset);
```
## Important Considerations
1. Position offset values are measured in pixels
2. Has to be 8 Bit per Channel Image.

## Example
```java
import rgbOffset.offset;

import javax.imageio.ImageIO;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;

public class Example {
    public static void main(String[] args) throws IOException {

        // Set Variable Names
        BufferedImage image = ImageIO.read(new File("input.jpg"));
        int xOffset = 100; // Moves image right 100 pixels
        int yOffset = 1000; // Moves image down 1000 pixels

        // Create Offset Image
        BufferedImage image = rgbOffset.offset(image, xOffset, yOffset);

        // Export Offset Image
        ImageIO.write(image, "jpg", new File("output.jpg"));
    }
}
```

## Roadmap

- Provide measurements other than pixels, perhaps a percentage of the total image size
- Support 16bit and 24bit images
