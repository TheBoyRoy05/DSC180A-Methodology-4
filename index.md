**Name:** Issac Roy ([iroy@ucsd.edu](mailto:iroy@ucsd.edu))

**Section:** D38, Efficient AI: Algorithms and Systems for Foundation Models

**Mentor:** Zhijian Liu

**What is the most interesting topic covered in your domain this quarter?**

Quantization, and SpinQuant in particular. The big problem with squeezing a model into 4 bits is outliers: a few channels hold values way bigger than the rest, so the whole range gets stretched to fit them and everything else loses precision. SpinQuant multiplies the weights and activations by a rotation matrix, which leaves the model's output exactly the same but spreads those outliers across all the channels. It's such an elegant fix because it doesn't throw anything away, it just looks at the same numbers from a better angle.

**Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

Beyond quantizing Pi0.5 itself, I'd want to check whether our findings transfer to other robot policies, like OpenVLA-OFT, which is built differently. We'd build the same roofline model for it, predict which stages quantization should speed up, and then test that prediction on real GPUs and on LIBERO success rate. If the predictions hold, the roofline becomes a cheap way to decide how to compress a policy before spending any GPU time on it.

**What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

I'd get onto real GPUs and profile much earlier instead of leaning on the analytic model for so long, and I'd secure GPU quota at the start, since our eval jobs sat waiting for a free GPU for hours. I'd also run more evaluation episodes per task, since with only 10 episodes we can't reliably tell a small drop in success rate apart from noise.

**What other techniques would you be interested in using in your project?**

I think token pruning is promising, since part of the vision input is padding for a camera slot we don't use. I'm also interested in CUDA graphs or kernel fusion to cut the launch overhead in the denoising loop, and in distilling the policy down to fewer denoising steps.
