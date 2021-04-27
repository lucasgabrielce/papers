# Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains

Matthew Tancik and Pratul P. Srinivasan and Ben Mildenhall and Sara Fridovich-Keil and Nithin Raghavan and Utkarsh Singhal and Ravi Ramamoorthi and Jonathan T. Barron and Ren Ng. NeurIPS 2020 (spotlight). [[pdf]](https://arxiv.org/pdf/2006.10739.pdf)

## tl;dr
* Follow up of a previous paper: "NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis" [[pdf]](https://arxiv.org/pdf/2003.08934.pdf);
* Cordinate-based MLPs are not a good learning agent to model functions in low dimensions (e.g. representing images, volume density, texture synthesis, etc.); and,
* Borrowing from [here](https://arxiv.org/pdf/1806.07572.pdf) and [here](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.145.8736&rep=rep1&type=pdf), the authors empirically show that passing the inputs through a Fourier feature input mapping can dramatically improves the performance of coordinate-based MLPs.

## Takeways
* Consider a function defined by an image that maps each (x, y) pixel coordinate to an output (r, g, b) color. MLPs fails in that task due to spectral bias (difficulty on learning high frequency functions).
* Neural Tangent Kernel (NTK) theory suggests that this incapacity is due to MLPs not having a rapid frequency falloff, which means that MLPs can not represent higher frequency details - in ohters worlds, can not create hyper-enough representations of input-pairs.
* NTK of a MLP can be expressed as scalar function of the inner product of two input points. That's very important, because of a complementary property: the dot product of two feature vectors is a stationary function of the two original coordinate points (x, y). If we move (x, y) by the same amount, their feature space dot product stays the same. In general, this is called 'stationary composed NTK function'.
* Changing the scaler of the dot product can manipulate the width of the kernel.
* Multiple experiments: 2D image regression, 3D shape regression, 2D computed tomography (CT), 3D magnetic resonance imaging (MRI), 3D inverse rendering for view synthesis.
* Combining a network with a Fourier feature mapping has dramatic effects on convergence and generalization.

## Questions
* Fourier feature input mapping is very good indeed for cordinated-based MLPs, but would be very cool to see how Meta-Learning (check [here](https://arxiv.org/abs/1909.04630), [here](https://www.youtube.com/watch?v=u5BkO8XMS2I&t=0)] and [here](https://arxiv.org/pdf/1803.02999.pdf)) could be applied here (later on I found one of their recent works on Meta-Learning! Check [here](https://www.youtube.com/watch?v=h0SXP6lJxak&t=1740s) and [here](https://www.youtube.com/watch?v=h0SXP6lJxak)).
* When we talk, in Neural Tangent Kernels, about how Neural Networks can intrinsically store the relationship between pairs of inputs and “positional encoding”, I always remember Professor K. Stanley's work on [HyperNEAT](http://eplex.cs.ucf.edu/hyperNEATpage/) - that basic introduces the concept of 'genetic encondig' borrowed from nature and uses it on a Neural Network to infer weights of another Neural Network. Some years later, HyperNEAT inspired Ha, Dai and Le, on their [HyperNetworks](https://arxiv.org/pdf/1609.09106.pdf) paper.
* In an era that anyone wants the fastest way possible to do everything, I ask: can NeRF, even with Fourier feature maping, be applied in a real-time scenario case? (not to my surprise I must say, I found the authors' [most recent article](https://arxiv.org/pdf/2103.14645.pdf), presenting a reformulation on NeRF's archiecture with Sparse Neural Radiance Grid (SNeRG), enabling real-time rendering).

## Useful links
* (GitHub.io - Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains)[https://bmild.github.io/fourfeat/]
* (Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains)[https://www.youtube.com/watch?v=nVA6K6Sn2S4&t=0s]
* (Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains (10min talk))[https://www.youtube.com/watch?v=iKyIJ_EtSkw&t=0s]
* Computer Vision Seminar @ EPFL VITA: (Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains)[https://www.youtube.com/watch?v=h0SXP6lJxak&t=0] (It is a longer version of the previous two links; in the second part of the video they presented a new paper with a Meta-Learning approach- which is very cool, as I said before. However, I didn't feel much difference on my general understanding in their paper on Fourier transform after watching the whole video, although the viewers' questions are very good)
* (Understanding the Neural Tangent Kernel)[https://rajatvd.github.io/NTK/].  Rajat does an outstanding job here explaining the mathematics behind a Neural Tangent Kernel.
* [Neural Tangent Kernel: Convergence and Generalization in Neural Networks](https://arxiv.org/pdf/1806.07572.pdf)
* [Deep Networks Are Kernel Machines (Paper Explained)](https://www.youtube.com/watch?v=ahRPdiCop3E)
* [NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis (ML Research Paper Explained)](https://www.youtube.com/watch?v=CRlN-cYFxTk)
