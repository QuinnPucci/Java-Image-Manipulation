# Java Image Processing Playground

This project is a simple **Java image processing toolkit** that uses 2d Arrays to manipulate jpg pixels. It loads an image (`apple.jpg`), applies several transformations, and saves the results as new image files.

## Features

The program currently supports the following operations:

- 🎨 **Negative Filter**  
  Inverts the colors of the image by replacing each RGB value with `255 - value`.

- ↔️ **Horizontal Stretch**  
  Doubles the width of the image by duplicating each pixel horizontally.

- ↕️ **Vertical Shrink**  
  Halves the height of the image by sampling every second row of pixels.

- ✂️ **Trim Borders**  
  Removes a specified number of pixels from each side of the image (top, bottom, left, right).

- 🔁 **Invert Image (Flip Both Ways)**  
  Flips the image horizontally and vertically by reversing both row and column indices.

- 🎛️ **Color Filter (RGB Adjustment)**  
  Adjusts the red, green, and blue channels by customizable offsets, with clamping between 0 and 255.

## How It Works

The core idea is to treat the image as a **2D array of pixels**:

- `imgToTwoD(String path)`  
  Loads an image from a file path or URL and converts it into a `int[][]` where each `int` represents a pixel’s ARGB value.

- `twoDToImage(int[][] imgData, String fileName)`  
  Converts a 2D pixel array back into a `BufferedImage` and writes it to disk as a `.jpg`.

- `getRGBAFromPixel(int pixelColorValue)`  
  Uses `java.awt.Color` to extract `[red, green, blue, alpha]` from a single pixel.

- `getColorIntValFromRGBA(int[] colorData)`  
  Combines RGBA values back into a single `int` pixel.

There is also a helper method:

- `viewImageData(int[][] imageTwoD)`  
  Prints out raw pixel data and RGBA values for a 3×3 section in the top-left corner of the image for debugging/learning.

## Output Files

Given an input file `apple.jpg` in the project directory, the program generates:

- `negative_apple.jpg`
- `stretched_apple.jpg`
- `shrank_apple.jpg`
- `trimmed_apple.jpg`
- `inverted_apple.jpg`
- `colored_apple.jpg`

Each output demonstrates one of the transformations implemented in the code.

## Requirements

- Java 8+ (or any modern JDK)
- `apple.jpg` (or any other image) placed in the project root, or a valid image URL
- The following imports are used:
  ```java
  import java.awt.Color;
  import java.awt.image.BufferedImage;
  import java.io.File;
  import java.net.URL;
  import java.util.Arrays;
  import javax.imageio.ImageIO;
