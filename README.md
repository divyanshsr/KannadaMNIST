# KannadaMNIST

   Introduction:

Kannada is the official and administrative language of the state of Karnataka in India with nearly 60 million speakers worldwide. Also, as per articles 344(1) and 351 of the Indian Constitution, Kannada holds the status of being one of the 22 scheduled languages of India. The language is written using the official Kannada script, which is an abugida of the Brahmic family and traces its origins to the Kadamba script (325–550 AD).

   About the dataset:

65 volunteers were recruited in Bangalore, India, who were native speakers of the language as well as day-to-day users of the numeral script. Each volunteer filled out an A3 sheet containing a 32 × 40 grid. This yielded filled-out A3 sheets containing 128 instances of each number which we posit is large enough to capture most of the natural intra-volunteer variations of the glyph shapes. All of the sheets thus collected were scanned at 600 dots-per-inch resolution using the Konica Accurio-Press-C6085 scanner that yielded 65 4963 × 3509 png images.
This figure here captures the MNIST-ized renderings of the variations of the glyphs across the following modern fonts: Kedage, Malige-i, Malige-n, Malige-b, Kedage-n, Malige-t, Kedage-t, Kedage-i, Lohit-Kannada, Sampige and Hubballi-Regular.

   Data Pre-processing:

In this sub-phase, each of the 4963 × 3509 sized scanned 32 × 40 grid png images were passed through two preprocessing stages. This approach was originally used as an extraction framework to eke out the digits for a Sudoku-solver. The first pre-processing stage entails: 
1. Applying a Gaussian-blur filter of kernel-size 9 × 9
2. Performing adaptive thresholding using 11 nearest neighbour pixels 
3. Applying a bitwise-NOT operator to perform colour inversion to ensure that the target gridlines have non-zero pixel values
The second pre-processing phase entailed two operations. The first was to estimate the corners of the largest polygon that was then harnessed to crop and warp the 32 × 40 grid-image. The cropped-and-warped image thus obtained was then segmented into 1280 slices to yield the constituent individual digit images which were then MNIST-ized . For this, we followed pixel-thresholding, row-column padding and finally inflicting a Best-shift transformation to drag the current center-of-mass of the digit image to the center of the target MNIST-ized 28 × 28 image. At the end of this phase, we had a 128 × 10 × 28 × 28 image tensor per scanned image. The class-label associated with each image was obtained using the row index of the image in the 32 × 40 grid.

Conclusion:

In this paper, we described in detail the creation of a new handwritten digits dataset for the Kannada language, which we term as Kannada-MNIST dataset. We were able to attain ∼ 97% top-1 accuracy when we trained and tested on what we term as the main dataset with 60000 28 × 28 gray-scale training images and 10000 test images. This is meant to be in a drop-in replacement for the standard MNIST dataset. We also achieved a top-1 accuracy of ∼ 77% when we trained on the 60000 main dataset and tested on 10240 28 × 28 gray-scale test images from what we term as the Dig-MNIST dataset. The images in the Dig-MNSIT dataset are noisier with smudges and grid borders sneaking in during the grid-image segmentation phase. The main reason behind us sharing the raw scan images was to foster research into auto-segmentation algorithms that will parse the individual digit images from the grid, which might in turn lead to higher quality of images in the upgraded versions of the dataset.

References:

[1]. E. X. Gu, "Convolutional Neural Network Based Kannada-MNIST Classification," 2021 IEEE International Conference on Consumer Electronics and Computer Engineering (ICCECE), 2021, pp. 180-185, doi: 10.1109/ICCECE51280.2021.9342474. https://ieeexplore.ieee.org/document/9342474

[2]. Reddy, Mallamma & Hanumanthappa, Prajwal. (2017). Kannada Phonemes to Speech Dictionary: Statistical Approach. International Journal of Engineering Research and Applications. 7. 77-80. 10.9790/9622-0701047780.  https://www.researchgate.net/figure/speech-for-Kannada-numbers_fig2_313113588

[3]. Jiang, Weiwei. "MNIST-MIX: a multi-language handwritten digit recognition dataset." IOP SciNotes 1.2 (2020): 025002. https://arxiv.org/pdf/2004.03848v1.pdf

[4]. Prabhu, Vinay Uday. "Kannada-MNIST: A new handwritten digits dataset for the Kannada language." arXiv preprint arXiv:1908.01242 (2019) https://arxiv.org/pdf/1908.01242v1.pdf

[5].  Mariswamy, Latha & Mahadevappa, Shivakumar & Manjula, R.. (2020). Performance Analysis of Kannada Phonetics: Vowels, Fricatives and Stop Consonants Using LP Spectrum. SN Computer Science. 1. 10.1007/s42979-020-0088-7. https://www.researchgate.net/publication/339932331_Performance_Analysis_of_Kannada_Phonetics_Vowels_Fricatives_and_Stop_Consonants_Using_LP_Spectrum

