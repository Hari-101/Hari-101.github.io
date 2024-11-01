---
title: "Unsupervised Early Exit in DNNs with Multiple Exits"
collection: publications
category: conferences
permalink: /publication/2009-10-01-paper-title-number-1
excerpt: 'Deep Neural Networks (DNNs) are generally designed as sequentially cascaded differentiable blocks/layers with a prediction module connected only to its last layer. DNNs can be attached with prediction modules at multiple points along the backbone where inference can stop at an intermediary stage without passing through all the modules. The last exit point may offer a better prediction error but also involves more computational resources and latency. An exit point that is ‘optimal’ in terms of both prediction error and cost is desirable. The optimal exit point may depend on the latent distribution of the tasks and may change from one task type to another. During neural inference, the ground truth of instances may not be available and the error rates at each exit point cannot be estimated. Hence one is faced with the problem of selecting the optimal exit in an unsupervised setting. Prior works tackled this problem in an offline supervised setting assuming that enough labeled data is available to estimate the error rate at each exit point and tune the parameters for better accuracy. However, pre-trained DNNs are often deployed in new domains for which a large amount of ground truth may not be available. We thus model the problem of exit selection as an unsupervised online learning problem and leverage the bandit theory to identify the optimal exit point. Specifically, we focus on the Elastic BERT, a pre-trained multi-exit DNN to demonstrate that it ‘nearly’ satisfies the Strong Dominance (SD) property making it possible to learn the optimal exit in an online setup without knowing the ground truth labels. We develop upper confidence bound (UCB) based algorithm named UEE-UCB that provably achieves sub-linear regret under the SD property. Thus our method provides a means to adaptively learn domain-specific optimal exit points in multi-exit DNNs. We empirically validate our algorithm on IMDb and Yelp datasets.'
date: 2009-10-01
venue: 'Journal 1'
slidesurl: 'http://academicpages.github.io/files/slides1.pdf'
paperurl: 'https://dl.acm.org/doi/10.1145/3564121.3564137'
citation: 'Your Name, You. (2009). &quot;Paper Title Number 1.&quot; <i>Journal 1</i>. 1(1).'
---

The contents above will be part of a list of publications, if the user clicks the link for the publication than the contents of section will be rendered as a full page, allowing you to provide more information about the paper for the reader. When publications are displayed as a single page, the contents of the above "citation" field will automatically be included below this section in a smaller font.
