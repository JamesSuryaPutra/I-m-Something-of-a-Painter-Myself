# I'm Something of a Painter Myself
![header](https://github.com/JamesSuryaPutra/I-m-Something-of-a-Painter-Myself/assets/155945814/7f9f14ae-2f6d-46e1-a790-b6f49e7c1d3e)

# Description
We recognize the works of artists through their unique style, such as color choices or brush strokes. The “je ne sais quoi” of artists like Claude Monet can now be imitated with algorithms thanks to generative adversarial networks (GANs). In this getting started competition, you will bring that style to your photos or recreate the style from scratch!

Computer vision has advanced tremendously in recent years and GANs are now capable of mimicking objects in a very convincing way. But creating museum-worthy masterpieces is thought of to be, well, more art than science. So can (data) science, in the form of GANs, trick classifiers into believing you’ve created a true Monet? That’s the challenge you’ll take on!

# The challenge
A GAN consists of at least two neural networks: a generator model and a discriminator model. The generator is a neural network that creates the images. For our competition, you should generate images in the style of Monet. This generator is trained using a discriminator.

The two models will work against each other, with the generator trying to trick the discriminator, and the discriminator trying to accurately classify the real vs. generated images.

Your task is to build a GAN that generates 7,000 to 10,000 Monet-style images.

# Evaluation
MiFID:
Submissions are evaluated on MiFID (Memorization-informed Fréchet Inception Distance), which is a modification from Fréchet Inception Distance (FID). The smaller MiFID is, the better your generated images are.

# What is FID?
FID, along with Inception Score (IS), are both commonly used in recent publications as the standard for evaluation methods of GANs.

In FID, we use the Inception network to extract features from an intermediate layer. Then we model the data distribution for these features using a multivariate Gaussian distribution with mean µ and covariance Σ. The FID between the real images r and generated images g is computed as:

![Frechet_Inception_Distance](https://github.com/JamesSuryaPutra/I-m-Something-of-a-Painter-Myself/assets/155945814/ab3336b4-c824-45d4-a6cf-7b8dfc562302)

where Tr sums up all the diagonal elements. FID is calculated by computing the Fréchet distance between two Gaussians fitted to feature representations of the Inception network.

# What is MiFID (memorization-informed FID)?
In addition to FID, Kaggle takes training sample memorization into account.

The memorization distance is defined as the minimum cosine distance of all training samples in the feature space, averaged across all user generated image samples. This distance is thresholded, and it's assigned to 1.0 if the distance exceeds a pre-defined epsilon.

In mathematical form:

![mifid_0](https://github.com/JamesSuryaPutra/I-m-Something-of-a-Painter-Myself/assets/155945814/095c8aa2-01e7-402b-b604-7c714739d3f1)


where fg and fr represent the generated/real images in feature space (defined in pre-trained networks); and fgi and frj represent the ith and jth vectors of fg and fr, respectively.

![mifid_1](https://github.com/JamesSuryaPutra/I-m-Something-of-a-Painter-Myself/assets/155945814/8d28b75a-bc0a-42ed-b185-a8d9e0ca6e8a)


defines the minimum distance of a certain generated image (i) across all real images ((j), then averaged across all the generated images.

<img width="350" alt="latex-img-150" src="https://github.com/JamesSuryaPutra/I-m-Something-of-a-Painter-Myself/assets/155945814/faa880ca-b26a-4be2-ad49-399296a81b37">


defines the threshold of the weight only applies when the (d) is below a certain empirically determined threshold.

Finally, this memorization term is applied to the FID:

![mifid_2](https://github.com/JamesSuryaPutra/I-m-Something-of-a-Painter-Myself/assets/155945814/a28e9d26-1387-4421-a473-9106a9a1e35f)
