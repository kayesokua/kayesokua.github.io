---
layout: post
title: Understanding Color Models
summary: A deep dive into commonly used color models, terminologies used in image processing and computer vision
tag: image-processing
---

Color is a perceptual phenomenon that arises from the interaction between light, the human eye, and the brain, and is used in a variety of fields including art, psychology, medicine, and computer graphics. In art, color is used to create pleasing designs and convey emotions. In psychology, color is studied for its effects on our behavior and feelings. In medicine, color is used to diagnose and treat various diseases. To represent color information for different devices and applications, there are various color models, each with its own strengths and limitations. The choice of color model depends on the task at hand. [^1] [^2] [^3] [^4]

* TOC
{:toc}

## Common Color Systems

1. **Red-Green-Blue (RGB)** is an additive model that combines red, green, and blue light to produce a wide range of colors. It stems from the trichromatic theory of vision by Young and Helmholtz in the 19th century, which posits that the human eye has three types of photoreceptors. Additive mixing combines colored light sources to produce various colors, and RGB uses this principle by combining different intensities of red, green, and blue light. RBG is used on electronic displays.
2. **Blue-Green-Red** is an alternative additive model designed to be more efficient in computer vision. BGR is an additive color model that was originally introduced by Intel's OpenCV library for computer vision and image processing. It was designed to be more efficient in handling color data in computer memory and processing, especially for certain hardware architectures. BGR has become popular in the computer vision community because of its efficient memory layout and support for certain image processing algorithms. However, it has a limited color gamut and accuracy compared to RGB due to the reversed order of color components. BGR is commonly used in computer vision applications on hardware such as Intel processors and some cameras that use the Bayer filter.
3. **Hue-Saturation-Luminance** and **Hue-Saturation-Value** are alternative RGB representations closer to human perception. HSL is often used in image editing software and color pickers, while HSV is used in computer graphics and color selection tools.
4. **Hue-Chroma-Luminance** is also based on human perception for direct color control. HCL color space uses polar coordinates to describe colors. Hue is the angle around the color wheel, chroma is the distance from the center, and luminance is the vertical axis. It's used for creating color schemes, designing data visualizations, and creating user interfaces with accessible color contrast.
5. **Lightness-a-b** represents color information using lightness and the chromaticity coordinates "a" and "b". It is often used in color space transformations, color correction, and color matching because it is designed to approximate human visual perception.
6. **CIE XYZ** is a universal color space that represents the color spectrum visible to the average human. It is used in color matching and calibration applications, such as in printing and color management systems.
7. **YCbCr (Luma, Chroma Blue, Chroma Red)** separates image brightness information (luma) from color information (chroma) and is commonly used in image and video compression due to its efficient representation of color information. YCbCr is often used in digital video formats such as MPEG and JPEG.
8. **YUV** is a color model that represents colors as a combination of luminance (Y) and chrominance (UV) components, where Y represents the brightness and UV represent the color information. It is commonly used in video encoding and processing.

**Other Printing and Industrial Color Systems.**

1. **Pantone**: Standardized color reproduction system used in brand marketing and printing applications. Offers high color precision but can be costly due to its use of individual plates for each color.
2. **Cyan-Magenta-Yellow-Black (CMYK)** is a subtractive color model used in printing, known for its efficiency and used in industries such as advertising and publishing.
3. **Munsell Color System** is a color matching system that correlates with the way the human eye perceives color and is used in color matching systems for design and manufacturing. Known for its accuracy and used in industries such as textiles and printing.
4. **RAL** is a color-matching system mainly used in varnish and powder coating applications, with reference panels now available for plastics as well.
5. **HED** is a model representing the saturation for histological stain types and used in medical imaging and analysis applications. Commonly used in digital pathology for the analysis of stained tissue samples.

## Common Color Terminologies

Color terms are commonly used in the field of image processing and computer vision.

| Vocabulary | Definition | Function in Image Processing |
| - | - | - |
| Hue | The name of a color, like red or blue | Differentiate colors. Identify and segment objects/regions. |
| Saturation | How strong or vivid a color is | Control color intensity. Enhance/reduce colorfulness. |
| Value | How light or dark a color is, from black to white with shades of gray in between | Adjust brightness/darkness. Correct exposure, create effects. |
| Luminance | How bright a color is to our eyes | Measure brightness (human perception). Adjust overall brightness, enhance contrast.|
| Chrominance | How pure a color is, without mixing with white, black or gray | Measure color purity. Adjust overall color balance. |
| Luma | The brightness of a color adjusted for human eyes | Optimize brightness for display. Ensure accurate contrast. |
| Contrast | The difference in brightness between two colors | Measure brightness difference. Enhance detail visibility. |
| Tint | Adding white to a color to make it lighter | Adjust color temperature. Correct color balance. |
| Tone | Adding gray to a color to make it softer | Adjust color balance by adding gray. Create effects, adjust overall balance. |
| Shade | Adding black to a color to make it darker | Adjust brightness by adding black. Create dramatic/moody effects, adjust overall brightness. |

## Color Depth and Bit Depth

1. Color depth refers to the total number of colors that can be displayed in an image, while bit depth refers to the number of bits used to represent each color.
2. A higher bit depth allows for more precise color representation and reduces banding and color artifacts.

## Color management systems and color spaces

1. A color management system (CMS) is a software that ensures consistent color reproduction across different devices.
2. A color space is a specific range of colors that can be displayed or printed, and it can be defined by various standards such as ICC profiles and sRGB.
3. ICC profiles help ensure color consistency across devices by defining the color gamut and characteristics of a device.
4. sRGB is a widely used standard color space that is optimized for display on computer monitors and the internet.

## Common Color Conversions

Color conversions are basically applied color equations that allow us to implement color correction, image segmentation, and object recognition. [Bruce Lindbloom's website](http://www.brucelindbloom.com/) contains an overview of mathematical equations for converting among various colorimetric representations, so you should check it out. [^3] [^5]

1. **RGB to Lab** maps the three RGB color channels to three channels in the Lab color space, which is designed to be more perceptually uniform. The need for uniform colors led to the development of CIE (Commission Internationale de l'Eclairage) XYZ color space. It is a device-independent color space that defines colors based on how they are perceived by the human eye. The CIE XYZ color space is used as an intermediate color space in many color conversions, including the conversion from RGB to LAB.The conversion usually goes from RGB to CIE XYZ then XZY to Lab.
2. **RGB to YUV** separates an image into its luminance (Y) and chrominance (UV) components. It is often used in video encoding and processing to reduce the amount of data needed to represent an image while maintaining visual quality.
3. **RGB to grayscale** is a conversion that produces a grayscale version of an RGB image by computing the luminance of each pixel.
4. **Grayscale to binary** is a conversion that converts a grayscale image to a binary image by thresholding the grayscale values.

{% gist 131cfb4c88de9ff137eeb982f87fc123 %}

## Exploring Color Models and Pixels in Digital Media

In this section, I wrote an overview of color models and pixels formats used in digital media, specifically in Adobe Photoshop and AVFoundation. Adobe Photoshop supports various image formats and corresponding color modes with recommended use cases, such as BMP for printing and 3D modeling, JPEG/JPG for photographs and web images, and RAW for professional photography. Understanding the characteristics and limitations of these color models is crucial for color correction, matching, and management. AVFoundation pixel formats are used on Apple platforms and include various formats for different types of images and videos, such as full-color images with transparency for film and television production and grayscale images with transparency for medical imaging applications. This information is important for image processing, as it helps to choose the appropriate color models and pixel formats for various use cases. [^6] [^7]

### Adobe Photoshop Color Modes

|Image Format | Examples | Modes |  Bit Depth |
|-|-|-|-|
| BMP | Windows wallpaper, printing, 3D modeling | Bitmap, Indexed Color, RGB, CMYK, Lab, Grayscale, Duotone, Multichannel| $${2^1,2^4,2^8,2^{16},2^{32}}$$ |
|GIF| Animated online banners, logos, graphics| Indexed Color|$${2^1,2^8}$$|
|JPEG/JPG| Photographs, web images, images with gradients or smooth tones|RGB, CMYK|$${2^8,2^{12},2^{16}}$$|
|PDF | Vector graphics, high-quality printing| Bitmap, Indexed Color, RGB, CMYK, Lab, Grayscale, Duotone, Multichannel|$${2^1,2^8,2^{16}}$$|
|PNG|Web graphics, logos, icons, transparent images, images with text or sharp edges| RGB, Indexed Color, Grayscale, Duotone, Multichannel| $${2^1,2^4,2^8,2^{16},2^{32}}$$|
|PSD|Working files, layers, masks, adjustments|Bitmap, Indexed Color, RGB, CMYK, Lab, Grayscale, Duotone, Multichannel|$${2^1,2^8,2^{16},2^{32}}$$|
|TIFF| High-quality printing, professional photography, scans| Bitmap, Indexed Color, RGB, CMYK, Lab, Grayscale, Duotone, Multichannel| $${2^1,2^8,2^{16},2^{32}}$$|
|EPS|Vector graphics, high-quality printing| Bitmap, Indexed Color, RGB, CMYK, Lab, Grayscale, Duotone, Multichannel| $${2^1,2^8,2^{16}}$$|
|SVG|Vector graphics, web graphics| RGB | $${2^8}$$|
|RAW|Professional photography, post-processing|RGB, CMYK| $${2^{12},2^{14},2^{16}}$$|

### AVFoundation Pixel Formats

Here's an overview of pixel format used on Apple platforms:

| Image Description | Examples | kCVPixelFormatType_ | Bit Depth |
| - | - | - | - |
| B/W Images | QR Code scanning | 1Monochrome| $${2^1}$$ |
|Indexed color images | Indexed color formats used in video processing, where each pixel is represented by an index into a color lookup table, rather than by its own color value. |2Indexed, 4Indexed, 8Indexed| $${2^2,2^4,2^8}$$ |
| Indexed grayscale images | Images where the color range is limited and a small color palette is sufficient, such as diagrams or charts |1IndexedGray_WhiteIsZero, 2IndexedGray_WhiteIsZero, 4IndexedGray_WhiteIsZero, 8IndexedGray_WhiteIsZero | $${2^1,2^2,2^4,2^8}$$ |
Images, videos in pixel formats | Used in gaming consoles, mobile devices, embeded systems applications where processing power and memory storage are limited; and color fidelity and accuracy aren't critical |16BE555, 16LE555, 16LE5551, 16BE565,16LE565 | $${2^{16}}$$ |
| Full color images | Used processing images that require a high dynamic range, such as in medical imaging or scientific visualization | 24RGB, 24BGR, 30RGB, 48RGB, | $${2^{24},2^{30},2^{48}}$$ |
| Full color images with transparency | Accurate color representation and compositing is important in industries where visual fidelity is critical, such as film and television production. |32ARGB, 32BGRA, 32ABGR, 32RGBA, 64ARGB | $${2^{32},2^{64}}$$ |
| Grayscale images with transparency | Used in medical imaging and scientific visualization applications where transparency and grayscale accurary are critical to represent the human body's internal structures is crucial for diagnosis and treatment planning |32AlphaGray, 16Gray | $${2^{16},2^{32}}$$ |
| Video frames | `422YpCbCr8` is used for video capture and playback applications. The rest are commonly used in video editing and compositing applications. `4444AYpCbCr16` for color grading applications. |422YpCbCr8, <br>4444YpCbCrA8,<br>4444YpCbCrA8R, <br>4444AYpCbCr8, <br>4444AYpCbCr16 | $${2^8,2^{16}}$$ |

Other notes:

1. For indexed color images, developers may need to provide a color map that maps index values to specific RGB values. They can also use different techniques like dithering to improve the visual quality of indexed color images. [^8]
2. The endianness of an image format affects how the image data is stored in memory and processed. It can lead to incorrect or distorted images if not handled properly, and byte swapping is required when converting between formats with different endianness. In big endian order, the most significant byte (MSB) of the color component is stored first, while in little endian order, the least significant byte (LSB) is stored first.The choice between big endian and little endian may arise when working with different systems or platforms that have different endianness conventions. [^9]

## References

[^1]: Gurney, J. (2010). Color and light: A guide for the realist painter. Andrews McMeel Publishing.
[^2]: Madsen, R. (2020). Color Models and Color Spaces. Programming Design Systems. programmingdesignsystems.com
[^3]: Lindbloom, B. J. (n.d.). Useful Color Equations. http://www.brucelindbloom.com/
[^4]: Munsell Color Science Laboratory. (n.d.). Rochester Institute of Technology. https://www.rit.edu/science/munsell-color-science-laboratory
[^5]: Adobe Cook Books. (2012). https://web.archive.org/web/20120502065620/http://cookbooks.adobe.com/post_Useful_color_equations__RGB_to_LAB_converter-14227.html)
[^6]: Apple (n.d.). CVPixelFormatDescription. Retrieved March 8, 2023, from https://developer.apple.com/documentation/corevideo/cvpixelformatdescription/
[^7]:Adobe (n.d.). Supported file formats in Photoshop. Retrieved March 8, 2023, from https://helpx.adobe.com/photoshop/using/file-formats.html
[^8]: Kumar, Nishant. (2023). Digital Image Processing Basics. Retrieved March 8, 2023, from https://www.geeksforgeeks.org/digital-image-processing-basics/
[^9]: GeekforGeeks. Little and Big Endian Mystery. (2023). Retrieved March 8, 2023, from https://www.geeksforgeeks.org/little-and-big-endian-mystery/