## Chapter 3

# Image processing

Common image processing operations 
1. Contrast 
2. Posterized (quantized colors) : Posterization is the result of reducing the number of colors present in an image.
The effect therefore resembles a graphic poster.
If we try to view a 24-bit color image on an old 16 color CRT monitor, the screen will render a posterized version of the image.
3. Blur
4. Rotation

Image transforms manipulating each pixel independent of its neighbors are called point operators or point processes.
  


#### 3.1 Point operators


Each output pixel’s value depends on only the corresponding input pixel value.
Ex.:  brightness, contrast adjustments, color correction and transformations

###### 3.1.1 Pixel transforms

Two commonly used point processes are multiplication and addition with a constant
$$ g(x) = af(x) + b $$

The parameters $a > 0$ and $b$ are often called the gain and bias parameters; sometimes these
parameters are said to control contrast and brightness

The bias and gain parameters can also be spatially varying
$$ g(x) = a(x)f(x) + b(x) $$

Multiplicative gain (both global and spatially varying) is a linear operation, since it obeys
the superposition principle,
$$ h(f_0 + f_1) = h(f_0) + h(f_1) $$

Operators such as image squaring (which is often used to get a local estimate of the energy in a bandpass filtered signal), are not linear.

Commonly used dyadic (two-input) operator is the linear blend operator
$$ g(x) = (1-\alpha)f_0(x) + \alpha f_1(x) $$
By varying $\alpha$ from $0 \leftarrow 1$, this operator can be used to perform a temporal cross-dissolve
between two images or videos, as seen in slide shows and film production, or as a component of image morphing algorithms

One highly used non-linear transform that is often applied to images before further processing is gamma correction, which is used to remove the 
non-linear mapping between input radiance and quantized pixel values. To invert the gamma mapping applied by the sensor, we can use
$$g(x) = [f(x)]^{1/\gamma}$$
where a gamma value of $\gamma \approx$ 2.2 is a reasonable fit for most digital cameras

###### 3.1.2 Color transforms

###### 3.1.3 Compositing and matting

The process of extracting the object from the original image is often called matting.
The process of inserting it into another image (without visible artifacts) is called compositing.
Visual artifacts (also artefacts) are anomalies apparent during visual representation.

The intermediate representation used for the foreground object between these two stages
is called an alpha-matted color image
In addition to the three color RGB channels, an alpha-matted image contains a fourth alpha channel $\alpha$ (or A)
that describes the relative amount of opacity or fractional coverage at each pixel 

Pixels on the boundary of the object vary smoothly between these two extremes, which hides
the perceptual visible jaggiesthat occur if only binary opacities are used.

To composite a new (or foreground) image on top of an old (background) image, the over
operator, is used
$$ C = (1 - \alpha)B + \alpha F $$

###### 3.1.4 Histogram equalization

While the brightness and gain controls described in Section 3.1.1 can improve the appearance
of an image, how can we automatically determine their best values?

One approach might be to look at the darkest and brightest pixel values in an image and map them to pure black
and pure white. Another approach might be to find the average value in the image, push it
towards middle gray, and expand the range so that it more closely fills the displayable values

How can we visualize the set of lightness values in an image in order to test some of
these heuristics?

The answer is to plot the histogram of the individual color channels and
luminance values , from this distribution, we can compute relevant
statistics such as the minimum, maximum, and average intensity values. 

Performing histogram equalization, is to find an intensity mapping function $f(I)$ such that the resulting histogram 
is flat. The trick to finding such a mapping is the same one that people use to generate random samples from
a probability density function, which is to first compute the cumulative distribution function $c(I)$
$$ c(I) = c(I-1) + \frac{1}{n}f(I) $$

For any given  intensity, we can look up its corresponding percentile c(I) and determine the final value that
pixel should take. When working with eight-bit pixel values, the I and c axes are rescaled from [0, 255].

*Locally adaptive histogram equalization* : 

#### 3.2 Linear filtering

#### 3.3 More neighborhood operators

#### 3.4 Fourier transforms 

#### 3.5 Pyramids and wavelets

#### 3.6 Geometric transformations

#### 3.7 Global optimization
