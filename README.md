# Objective
Tracking progress in natural language generation using adversarial training (usng GANs) for high quality samples

# Introduction

* Why GANs and why not just traditional maximum likelihood (ML)?
- ML suffers from exposure bias - during training each word is conditioned on previous ground truth words
- All the useful features of having latent representation are missing: controlling generation (controlling words, style and sentiment) , interpolation, disintengaled codes, etc.

* Can GANs be used for highly categorical distributions?
- Yes they can be! However, with the vanilla GANs it's not possible to do so in a straightforward manner. Either the gradient to the generator quickly goes to zero since the discriminator quickly adapts to the real distribution giving zero gradients everywhere else, or mode collapse happens which is usually more severe than for images.

* What techniques can be used for training GANs for categorical sequences?
There are two broad approaches that researchers have taken for solving the problem of training GANs for text:
1. Instead of using original GAN objective for training the generator, using reinforcement learning (RL) to estimated gradients to the generator. Following is the non-exhaustive list of such methods:
i. SeqGAN
ii. MaliGAN
iii. RankGAN
iv. LeakGAN
v. MaskGAN

2. RL-free methods which use original GAN objective. This category of the solutions can be further differentiated:
a. Methods which relaxes the peaked distribution of text to have a continuous approximation. These methods have a parameter known as temperature, which controls the sharpness of the distribution. 
i. TextGAN
ii. Gumbel-Softmax GAN
iii. FM-GAN

b. Methods which penalizes the gradient
i. WGAN-GP
