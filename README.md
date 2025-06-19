# DeepMark

This project helps artists preserve their intellectual property (IP), particularly, their images by utilizing an autoencoder based invisible watermarking technique. Specifically, DeepMark utilizes a custom autoencoder architecture that embeds watermarks within the gradient of the image to encode a unique watermark that can be extracted by a decoder model. 

The encoder and extractor model are trained in parallel, where the extractor loss is propogated to the encoder, to minimize the error. This process is very prone to overfitting, so it is best to train it on a large, diverse dataset. This project uses the [ImageNet Dataset](https://www.image-net.org/download.php) (10% representative subset) for better generalizability.

The result is an image which is visually indistinguishable from the originial, containing a watermark that allows it to be detected by the decoder model to identify the true origin of the image. 

![output](https://github.com/user-attachments/assets/5065a26d-6d4e-4d88-979d-472b945f5dbc)

The watermark is invisible due to the information being encoded within the gradients of the image. The interesting thing to note here is, this was not explicitly trained. Rather, the custom loss function correlates well with human perception, so the model learned to embed the code where the human eye is least likely to detect it. 

![Detection_results](https://github.com/user-attachments/assets/b38406c4-f0b8-4977-a1ba-4007fcdf3c90)

Figure (a) shows the original image, figure (b) shows the watermarked image, which is visually identical. Figure (c) is the difference of figures (b) and (a), revealing the watermark. Figure (d) subtracts the waterk mask (c) from the watermarked image (b).

It is recommended to train the model for a minimum of 3 epochs for the best results.
The trained weights can be found here:

[Encoder](https://drive.google.com/file/d/1xPaG9WmsA6QGrwRd9eeOxbG1M95m0sgC/view?usp=drive_link)

[Decoder](https://drive.google.com/file/d/1UDQ50icwkhPI6pMSZg8sQk_wV6o_WkYS/view?usp=drive_link)
