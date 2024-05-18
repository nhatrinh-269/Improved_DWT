# Improved Discrete Wavelet Transform compression method for Satellite Images

With the development of the space satellite industry, storing satellite images for research and analysis is very important. But the problem is that the volume of satellite images is very large and transmission between satellites and monitoring centers becomes difficult. So image compression becomes important. For traditional compression methods such as DCT (Discrete Cosine Transform), CCSDS (Consultative Committee for Space Data Systems) standards, Discrete Wavelet Transform, Bandelet, and JPEG 2000,... all provide reliability and High efficiency. To further improve compression I propose to improve the Discrete Wavelet Transform by storing the coefficients after quantization and an image that records the position of each coefficient. This way will reduce storage space.

## Feature

- **Image Compression**: Improves the traditional image compression method Discrete Wavelet Transform.
## Evaluation methods
- **PSNR**: Highest Signal-to-Noise Ratio (PSNR).
- **SSIM**: Structural Similarity Index (SSIM)


## Required Python Libraries
Install the necessary Python libraries:
```bash
pip install opencv-python
pip install numpy
pip install matplotlib
pip install PyWavelets
pip install pillow
```

## Method

### Step 1: First we perform quantization on each band of the satellite image and threshold them.
### Step 2:
+ Coefficients greater than the threshold will be retained and lower coefficients will be set to 0.
+ Usually only retains less than 10% for image compression. The total number of pixels before and after quantization is equal. Instead of storing all of those pixels, we only need to save 10% of this coefficient and an image file to save their positions.
+ We create a loop and save only non-zero coefficients into an array called codebook. The positions of the coefficients are stored according to the rule that if the coefficient is not 0 then it is 1, if it is 0 then it is 0 and then saved as a png file called label.
### Step 3: Read the codebook and label files to recreate the image when you want to use it

## Sample Results

After running the code, we see that storing coefficient (coeff_*.npy) and label (binary_im_*.png) files helps reduce the size of the storage and achieves a 50% compression ratio compared to images. original but the rate of PSNR and SSIM is very high.

## License

This project is licensed under the MIT License - see file [LICENSE](LICENSE) for details.

---

Feel free to further customize according to your project's specific requirements.
