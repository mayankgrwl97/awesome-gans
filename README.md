## GAN Readings

### Relevant Workshops
- [ ] [AI for Content Creation Workshop](http://visual.cs.brown.edu/workshops/aicc2020/)

### Tutorials and Blogs
- [X] [StyleGAN v2: notes on training and latent space exploration (Fashion Dataset)](https://towardsdatascience.com/stylegan-v2-notes-on-training-and-latent-space-exploration-e51cf96584b3)
    - [ ] [Improving Initialization for GAN inversion](https://github.com/rolux/stylegan2encoder/issues/2)
    - [ ] [Making Anime Faces With StyleGAN[1/2] - Tips and tricks for effective StyleGAN use](https://www.gwern.net/Faces)
- [X] [CVPR'20 iMLCV tutorial: Exploring and Exploiting Interpretable Semantics in GANs by Bolei Zhou](https://youtu.be/rfx3whKgFVo) `0:46:46`
- [ ] [Using Artificial Intelligence to Augment Human Intelligence](https://distill.pub/2017/aia/)
- [X] [Apple Machine Learning Blog](https://machinelearning.apple.com/research/gan)


### GAN Architectures (StyleGAN, ProgressiveGAN types)
- [X] CVPR 2020: [StyleGAN2 - Analyzing and Improving the Image Quality of StyleGAN](https://arxiv.org/abs/1912.04958)
    - [ ] [Summary Blog](https://medium.com/analytics-vidhya/from-gan-basic-to-stylegan2-680add7abe82)
- [X] CVPR 2019: [StyleGAN - A Style-Based Generator Architecture for Generative Adversarial Networks](https://arxiv.org/abs/1812.04948)
- [X] ICLR 2018: [Progressive GAN - Progressive Growing of GANs for Improved Quality, Stability, and Variation](https://arxiv.org/abs/1710.10196)


### GAN Inversion: Inverting Real Faces to Latent Code (Image2StyleGAN types)
- [ ] ECCV 2020: [Transforming and Projecting Images into Class-conditional Generative Networks](https://minyoungg.github.io/pix2latent/)
- [ ] arxiv 2020: [Generative Hierarchical Features from Synthesizing Images](https://arxiv.org/abs/2007.10379)
- [ ] SIGGRAPH ASIA 2020: [StyleFlow: Attribute-conditioned Exploration of StyleGAN-Generated Images using Conditional Continuous Normalizing Flows](https://arxiv.org/abs/2008.02401)
- [X] ECCV 2020: [StyleGAN2 Distillation for Feed-forward Image Manipulation](https://arxiv.org/abs/2003.03581)
    -**Comments**: Create synthetic datasets using style mixing and linear interpolation. Train paired pix2pixhd on these synthetic datasets for tasks such as male->female, female->male, etc.
- [ ] ECCV 2020: [Rewriting a Deep Generative Model](https://rewriting.csail.mit.edu/)
- [ ] ECCV 2020: [Exploiting Deep Generative Prior for Versatile Image Restoration and Manipulation](https://arxiv.org/abs/2003.13659)
- [ ] ECCV 2020: [DeepLandscape: Adversarial Modeling of Landscape Videos](https://saic-mdal.github.io/deep-landscape/)
- [ ] CVPR 2020: [Image Processing Using Multi-Code GAN Prior](https://arxiv.org/abs/1912.07116)
- [X] CVPR 2020: [Image2StyleGAN++: How to Edit the Embedded Images?](https://arxiv.org/abs/1911.11544)
- [ ] SIGGRAPH 2019: [Semantic Photo Manipulation with a Generative Image Prior](https://ganpaint.io/)
- [X] ICCV 2019: [Image2StyleGAN - How to Embed Images Into the StyleGAN Latent Space?](https://arxiv.org/abs/1904.03189)
    - **Comments**: Introduce extended latent codes to embed real images that are different from the dataset on which GAN has been trained. Each layer of Generator receives different latent codes from this extend latent space. *Problem*: Overfitting to given image; doesn't very well support the manipulation. Resulting code might be outside the original latent domain (due to unconstrained optimization)

#### Adding encoder to GAN generator (Reconstructions are not good)
- [ ] ECCV 2020: [In-Domain GAN Inversion for Real Image Editing](https://arxiv.org/abs/2004.00049)
    - **Comments** Resolves out-of-domain image inversion (from Image2StyleGAN) by doing an Encoder-constrained Optimization. They compute loss on both reconstructed image and the predicted latent code. Hence, we can use these latent codes for image editing. Check application: Semantic Diffusion
- [ ] CVPR 2020: [Adversarial Latent Autoencoders](https://arxiv.org/abs/2004.04467)
- [ ] NeurIPS 2019: [BigBiGAN - Large Scale Adversarial Representation Learning](https://arxiv.org/abs/1907.02544)

### Interpretability
#### Require supervision in form of off-the-shelf supervised classifiers
- [ ] ICLR 2020: [On the "steerability" of generative adversarial networks](https://ali-design.github.io/gan_steerability/)
    - **Comments**: Explore correspondence of latent space trajectories in GANs to simple image transformations. Dataset biases limit the extent of transformations (e.g: can't convert red firetruck to blue firetruck by moving in the blueness direction in the latent space). Data augmentation and jointly training the walk trajectory and the generator weights imroves steerability, resulting in larger transformation effects.
- [ ] CVPR 2020: [InterFaceGAN - Interpreting the Latent Space of GANs for Semantic Face Editing](https://genforce.github.io/interfacegan/)
    - **Comments**: Similar to HiGAN below, they use off-the-shelf image classifiers (like male/female, old/young, smile/no-smile, artifacts/no-artifacts) to find semantic boundaries in the latent space. Check for metrics to measure the disentanglement of faces.
- [ ] CVPRW 2020: [HiGAN - Semantic Hierarchy Emerges in Deep Generative Representations for Scene Synthesis](https://arxiv.org/abs/1911.09267)
    - **Comments**: Investigates the causality between latent space vectors and generated image attributes/semantics. For normal GANs, they use off-the-shelf image classifiers (like cloud/no-cloud, lighting/no-lighting) to find semantic boundaries in the latent space. For StyleGAN-like architectures, where stochasticity/randomness is introduced at multiple layers, they find that by perturbing input latent vectors at different layer depths, different semantics are controlled: Layout -> Objects -> Attributes -> Color Schemes
- [ ] ICCV 2019: [GANalyze: Toward Visual Definitions of Cognitive Image Properties](http://ganalyze.csail.mit.edu/)
    - **Comments**: Learn transformation in latent space (via a Transformer network) to improve memorability of generated images. Also check [MemNet](https://arxiv.org/abs/1708.02209)
- [ ] ICLR 2019: [GAN Dissection: Visualizing and Understanding Generative Adversarial Networks](https://gandissect.csail.mit.edu/), [Video](https://www.youtube.com/embed/yVCgUYe4JTM?rel=0&autoplay=1)
    - **Comments**: It's a framework to interpret and label the internal units inside the Generator. Labels are associated by checking correlation of feature activations of individual units with the segmentation mask of the generated image

#### Unsupervised Attribute Discovery in GANs
- [ ] arxiv 2020: [GANSpace: Discovering Interpretable GAN Controls](https://arxiv.org/abs/2004.02546)
    - **Comments** Discover Interpretable latent space directions by performing PCA analysis on the latent activations
- [ ] ICML 2020: [Unsupervised Discovery of Interpretable Directions in the GAN Latent Space](https://arxiv.org/abs/2002.03754)
    - **Comments**: They learn a set of directions in the latet space that induce "orthogonal" image transformations that are easy to distinguish from each other. E.g. -background blur+, -background removal+, -hair+, etc.

### Disentanglement of Variation Factors in Generative Models
- [ ] arxiv 2020: [Closed-Form Factorization of Latent Semantics in GANs](https://arxiv.org/abs/2007.06600)
- [ ] ECCV 2020: [The Hessian Penalty - A Weak Prior for Unsupervised Disentanglement](https://arxiv.org/abs/2008.10599)
- [ ] CVPR 2020: [DiscoFaceGAN - Disentangled and Controllable Face Image Generation via 3D Imitative-Contrastive Learning](https://openaccess.thecvf.com/content_CVPR_2020/papers/Deng_Disentangled_and_Controllable_Face_Image_Generation_via_3D_Imitative-Contrastive_Learning_CVPR_2020_paper.pdf)
- [ ] arxiv 2020: [Encoding in Style: a StyleGAN Encoder for Image-to-Image Translation](https://arxiv.org/abs/2008.00951)
- [X] arxiv 2020: [Face Identity Disentanglement via Latent Space Mapping](https://arxiv.org/abs/2005.07728)


### Image to Image (Pix2Pix and CycleGAN types)
- [ ] ECCV 2020: [Contrastive Learning for Unpaired Image-to-Image Translation](https://arxiv.org/abs/2007.15651)
- [ ] ECCV 2020: [Learning to Factorize and Relight a City](https://arxiv.org/abs/2008.02796)
- [ ] arxiv 2020: [Swapping Autoencoder for Deep Image Manipulation](https://arxiv.org/abs/2007.00653)
- [ ] CVPR 2020: [StarGAN v2 - Diverse Image Synthesis for Multiple Domains](https://arxiv.org/abs/1912.01865)
- [X] ICLR 2020: [Mask Based Unsupervised Content Transfer](https://arxiv.org/abs/1906.06558)
    - **Comments**: They tackle the problem of translating domain specific content (such as glasses/no-glasses, moustache/no-moustache) between two domains. Their proposed method disentangles the common and separate parts of these domains, and, through the generation of a mask, focuses the attention of the underlying network to the desired augmentation alone, without wastefully reconstructing the entire target.
- [ ] ICCV 2019: [SinGAN - Learning a Generative Model from a Single Natural Image](https://arxiv.org/abs/1905.01164)
- [ ] CVPR 2018: [StarGAN - Unified Generative Adversarial Networks for Multi-Domain Image-to-Image Translation](https://arxiv.org/abs/1711.09020)
- [X] CVPR 2018: [Pix2PixHD - High-Resolution Image Synthesis and Semantic Manipulation with Conditional GANs](https://arxiv.org/abs/1711.11585)
- [X] ICCV 2017: [CycleGAN - Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks](https://arxiv.org/abs/1703.10593)
- [X] CVPR 2017: [Pix2Pix - Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004)
- [ ] CVPR 2017: [SimGAN - Learning from Simulated and Unsupervised Images through Adversarial Training](https://arxiv.org/abs/1612.07828v2)
    - [X] [Apple Blog](https://machinelearning.apple.com/research/gan)
- [ ] SURVEY, Aug'20: [Generative Adversarial Networks for Image and Video Synthesis: Algorithms and Applications](https://arxiv.org/abs/2008.02793)


### Other Applications
- [ ] CVPR 2020: [Learning to Simulate Dynamic Environments with GameGAN](https://nv-tlabs.github.io/gameGAN/)
- [ ] CVPR 2020: [Controllable Person Image Synthesis with Attribute-Decomposed GAN](https://arxiv.org/abs/2003.12267)
- [ ] WACV 2020: [TailorGAN: Making User-Defined Fashion Designs](https://arxiv.org/abs/2001.06427v2)
- [ ] SIGGRAPH 2020: [Unpaired Motion Style Transfer from Video to Animation](https://deepmotionediting.github.io/style_transfer)
- [ ] ICCV 2019: [InGAN: Capturing and Remapping the "DNA" of a Natural Image](https://arxiv.org/abs/1812.00231)
- [ ] SIGGRAPH 2018: [Non-Stationary Texture Synthesis by Adversarial Expansion](https://arxiv.org/abs/1805.04487)


### Quantitative Analysis
- [ ] CVPR 2019: [Perceptual Path Metric: StyleGAN](https://arxiv.org/abs/1812.04948)
- [ ] NeurIPS 2019: [Improved Precision and Recall Metric for Assessing Generative Models](https://arxiv.org/abs/1904.06991)
- [ ] NeurIPS 2018: [Assessing Generative Models via Precision and Recall](https://arxiv.org/abs/1806.00035)
- [ ] NeurIPS 2017: [Frechet Inception Distance](https://arxiv.org/abs/1706.08500)



### ====
- https://genforce.github.io/
- https://github.com/zhoubolei/awesome-generative-modeling/blob/master/README.md
