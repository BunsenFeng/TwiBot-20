### TwiBot-20 Dataset

#### Introduction to TwiBot-20
TwiBot-20 is a comprehensive sample of the Twittersphere and it is representative of the current generation of Twitter bots and genuine users. It is naturally divided into four domains: politics, business, entertainment and sports and each user has semantics, property and neighborhood information. You can find out more about Twibot-20 in the paper 'TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark'. Work in progress.

#### Affiliated Paper
The affiliated paper of this repository, 'TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark', is accepted at CIKM 2021.

```
@inproceedings{10.1145/3459637.3482019,
author = {Feng, Shangbin and Wan, Herun and Wang, Ningnan and Li, Jundong and Luo, Minnan and Luo, Minnan},
title = {TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark},
year = {2021},
isbn = {9781450384469},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3459637.3482019},
doi = {10.1145/3459637.3482019},
abstract = {Twitter has become a vital social media platform while an ample amount of malicious
Twitter bots exist and induce undesirable social effects. Successful Twitter bot detection
proposals are generally supervised, which rely heavily on large-scale datasets. However,
existing benchmarks generally suffer from low levels of user diversity, limited user
information and data scarcity. Therefore, these datasets are not sufficient to train
and stably benchmark bot detection measures. To alleviate these problems, we present
TwiBot-20, a massive Twitter bot detection benchmark, which contains 229,573 users,
33,488,192 tweets, 8,723,736 user property items and 455,958 follow relationships.
TwiBot-20 covers diversified bots and genuine users to better represent the real-world
Twittersphere. TwiBot-20 also includes three modals of user information to support
both binary classification of single users and community-aware approaches. To the
best of our knowledge, TwiBot-20 is the largest Twitter bot detection benchmark to
date. We reproduce competitive bot detection methods and conduct a thorough evaluation
on TwiBot-20 and two other public datasets. Experiment results demonstrate that existing
bot detection measures fail to match their previously claimed performance on TwiBot-20,
which suggests that Twitter bot detection remains a challenging task and requires
further research efforts.},
booktitle = {Proceedings of the 30th ACM International Conference on Information & Knowledge Management},
pages = {4485–4494},
numpages = {10},
keywords = {benchmarking, twitter bot detection, social media, twitter API},
location = {Virtual Event, Queensland, Australia},
series = {CIKM '21}
}

```

#### TwiBot-20 Sample
We provide a sample of Twibot-20 in 'TwiBot-20_sample.json'. 

Each user contains:
- 'ID': the ID from Twitter identifying the user.
- 'profile': the profile information obtained from Twitter API.
- 'tweet': the recent 200 tweets of this user.
- 'neighbor': the random 20 followers and followings of this user.
- 'domain': the domain of this user and the domains include politics, business, entertainment and sports.
- 'label': the label of this user and '1' means it is a bot while '0' means it is a human. (not included in sample)

#### Full TwiBot-20 Dataset
Due to privacy issues, we are not directly posting the dataset. If you are interested in using the dataset, please contact wind_binteng at stu.xjtu.edu.cn to obtain permission to download the dataset for research efforts only. 

#### FAQ
Q: How did you create the graph? I mean on what basis have you created the edges (relationships)?

A: We create the graph with users and nodes and follow relationship as edges. If one user follows another, there is an edge between them.

Q: You said "In order to preserve the dense graph structure follow relationship forms, we also provide unsupervised users as the support set of TwiBot-20" in the paper. However, the "neighbor" information in the support set are all "null". Why?

A: We adopt a breadth-first search (BFS) approach to construct TwiBot-20. The train, dev and test set constitute the first two layers of BFS expansion while the support set contains users from the third and the most outside layer. In this way, users in the support set are only connected with the user in the second layer, whose follow information is included in train+dev+test. In this way, there is no need for "neighbor" information in the support set thus they are all "null" in support.json. What we try to convey in the paper is that we also include these unsupervised layer 3 users as support set to enlarge the Twitter graph and allow semi-supervised learning.

Q: I only found at most 10 followers and 10 followings per user. I thought It was supposed to be all set of followings and followers.

A: We use a controlled-BFS approach to select users in TwiBot-20. Specifically, we expand a user's 10 followers and followings to include in TwiBot-20 for each iteration. As a result, we only include these 10 followers and followings in the dataset as users connected by these edges both exist in TwiBot-20. If you are interested in all follow relationships of a specific user, you can retrieve the information with the user ID.

Q: What is train.json, dev.json, test.json and support.json?

A: These four files contain the training, validation, test and support set of TwiBot-20. As for the support set, "In order to preserve the dense graph structure follow relationship forms, we also provide unsupervised users as the support set of TwiBot-20." (Sec. 4.5) The support set could also enable semi-supervised learning.
