## Paper Dump (WIP)

**[Learning in Audio-visual Context: A Review, Analysis, and New
Perspective]{.underline}**\
Paper: <https://arxiv.org/pdf/2208.09579.pdf>\
Review paper explaining different approaches in understanding
audio-visual content.

### [Training from scratch:]{.underline}

**[Cross-Modal Attention Consistency for Video-Audio Unsupervised
Learning:]{.underline}**\
Paper: <https://arxiv.org/pdf/2106.06939.pdf>\
**Initial Understanding:** Using Visually Guided Audio Attention and
Audio guided Visual Attention to formulate the areas between audio and
video which are correlated to each other, this could lead to a better
video representation with thematic similarity

**[Evolving Losses for Unsupervised Video Representation
Learning]{.underline}**\
<https://openaccess.thecvf.com/content_CVPR_2020/papers/Piergiovanni_Evolving_Losses_for_Unsupervised_Video_Representation_Learning_CVPR_2020_paper.pdf>\
Brief Initial understanding:

### [Training on top of pretrained encoders(frozen):]{.underline}

**[Distilling Audio-Visual Knowledge by Compositional Contrastive
Learning]{.underline}** (AV transfer learning)

Code: <https://github.com/yanbeic/CCL>\
Paper:<https://yanbeic.github.io/Doc/CVPR21-ChenY.pdf>\
**Initial Understanding:** This paper focuses on using a teacher-student
network to understand a semantic meaning in videos and close the
multimodal gap , ie, the video is of a woman applying lipstick but the
audio is some random instrumental. How their architecture is able to
close such a gap, is still yet to be understood. Drawback: Seems to be a
supervised method

**[Multimodal Open-Vocabulary Video Classification via Pre-Trained
Vision and Language Models:]{.underline}**\
Paper: <https://arxiv.org/pdf/2207.07646.pdf>\
**Initial Understanding:** The paper focuses on learning audio visual
similarity by using pretrained embeddings, cross attention between
features are used to learn this. Loss is calculated separately for video
x audio and audio x video. Drawback: Not a single embedding is learnt.

**[UAVM: Towards Unifying Audio and Visual Models]{.underline}**\
Code:
[https://github.com/YuanGongND/uavm](https://github.com/YuanGongND/uavm){card-appearance="inline"}\
Paper: <https://arxiv.org/pdf/2208.00061v2.pdf>\
**Initial Understanding:** Similar to above, architecture is different.
And we get an fused embedding as well. No cross attention is used
however.

**[Space-Time Crop & Attend: Improving Cross-modal Video Representation
Learning]{.underline}**\
Paper: <https://arxiv.org/pdf/2103.10211.pdf>\
**Initial Understanding:** Augmenting data for self supervised tasks are
expensive computationally, thus the paper suggests we mask the
visual/audio features themselves as a method to crop

### [Training using cluster labels:]{.underline}

**[Self-Supervised Learning by Cross-Modal Audio-Video
Clustering]{.underline}**\
[**Code :**](https://arxiv.org/pdf/1911.12667.pdf)
[https://github.com/HumamAlwassel/XDC](https://github.com/HumamAlwassel/XDC){card-appearance="inline"}\
**Paper:** <https://arxiv.org/pdf/1911.12667.pdf>\
**Initial Understanding:** Clusters are formed using Video and Audio
features (k-means), the cluster labels of video are then used to train a
classifier for Audio and similarly video embeddings are trained over
audio cluster labels.

**[Multimodal Clustering Networks for Self-supervised Learning from
Unlabeled Videos:]{.underline}**\
**Paper**:<https://openaccess.thecvf.com/content/ICCV2021/papers/Chen_Multimodal_Clustering_Networks_for_Self-Supervised_Learning_From_Unlabeled_Videos_ICCV_2021_paper.pdf>\
**Initial Understanding**: Clusters are formed by using contrastive loss
across different modalities (audio, video, text) along with a clustering
loss that groups instances that have semantic similarity.

**[A Clustering-guided Contrastive Fusion for Multi-view Representation
Learning]{.underline}**\
Code:
[https://github.com/guanzhou-ke/cloven](https://github.com/guanzhou-ke/cloven){card-appearance="inline"}\
Paper: <https://arxiv.org/pdf/2212.13726v2.pdf>\
**Initial Understanding:** First a MLP architecture is used to fuse the
embeddings, then 2 types of contrastive losses are used : instance level
and cluster level.

**[CCA based papers :]{.underline}**

**[Robust Canonical Correlation Analysis: Audio-visual fusion for
learning continuous interest]{.underline}**\
Paper:
<https://ibug.doc.ic.ac.uk/media/uploads/documents/icassp_2014.pdf>

**[On Deep Multi-View Representation Learning]{.underline}**\
Brief summary: Summary of most CCA methods used to learn multi modal
representation

<http://proceedings.mlr.press/v37/wangb15.pdf>

**[Audio-Visual Embedding for Cross-Modal Music Video Retrieval through
Supervised Deep CCA:]{.underline}**

Paper:<https://arxiv.org/pdf/1908.03744.pdf>

**[Variational Autoencoder with CCA for Audio-Visual Cross-Modal
Retrieval]{.underline}**\
Paper: <https://arxiv.org/pdf/2112.02601.pdf>

**Initial Understanding:** On initial survey CCA seems to be a distance
metric based on correlation of two vectors, however there seems to be a
method of using CCA to formulate a latent space of fusion between 2
embeddings.\
Furthermore the second paper uses CCA as a loss function
