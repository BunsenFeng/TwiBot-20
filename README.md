### TwiBot-20 Dataset

#### Introduction to TwiBot-20
TwiBot-20 is a comprehensive sample of the Twittersphere and it is representative of the current generation of Twitter bots and genuine users. It is naturally divided into four domains: politics, business, entertainment and sports and each user has semantics, property and neighborhood information. You can find out more about Twibot-20 in the paper 'TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark'. Work in progress.

#### Affiliated Paper
The affiliated paper of this repository, 'TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark', is accepted at CIKM 2021.

#### TwiBot-20 Sample
We provide a sample of Twibot-20 in 'TwiBot-20_sample.json'. 

Each user sample contains:
- 'ID': the ID from Twitter identifying the user.
- 'profile': the profile information obtained from Twitter API.
- 'tweet': the recent 200 tweets of this user.
- 'neighbor': the random 20 followers and followings of this user.
- 'domain': the domain of this user and the domains include politics, business, entertainment and sports.
- 'label': the label of this user and '1' means it is a bot while '0' means it is a human.

#### Full TwiBot-20 Dataset
Due to privacy issues, we are not directly posting the dataset. If you are interested in using the dataset, please contact wind_binteng at stu.xjtu.edu.cn to obtain permission to download the dataset for research efforts only. 

#### FAQ
Q: How did you create the graph? I mean on what basis have you created the edges (relationships)?

A: We create the graph with users and nodes and follow relationship as edges. If one user follows another, there is an edge between them.

Q: You said "In order to preserve the dense graph structure follow relationship forms, we also provide unsupervised users as the support set of TwiBot-20" in the paper. However, the "neighbor" information in the support set are all "null". Why?

A: We adopt a breadth-first search (BFS) approach to construct TwiBot-20. The train, dev and test set constitute the first two layers of BFS expansion while the support set contains users from the third and the most outside layer. In this way, users in the support set are only connected with the user in the second layer, whose follow information is included in train+dev+test. In this way, there is no need for "neighbor" information in the support set thus they are all "null" in support.json. What we try to convey in the paper is that we also include these unsupervised layer 3 users as support set to enlarge the Twitter graph and allow semi-supervised learning.

Q: I only found at most 10 followers and 10 followings per user. I thought It was supposed to be all set of followings and followers.

A: We use a controlled-BFS approach to select users in TwiBot-20. Specifically, we expand a user's 10 followers and followings to include in TwiBot-20 for each iteration. As a result, we only include these 10 followers and followings in the dataset as users connected by these edges both exist in TwiBot-20. If you are interested in all follow relationships of a specific user, you can retrieve the information with the user ID.
