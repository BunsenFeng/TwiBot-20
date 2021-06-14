### TwiBot-20 Dataset

#### Introduction to TwiBot-20
TwiBot-20 is a comprehensive sample of the Twittersphere and it is representative of the current generation of Twitter bots and genuine users. It is naturally divided into four domains: politics, business, entertainment and sports and each user has semantics, property and neighborhood information. You can find out more about Twibot-20 in the paper 'TwiBot-20: A Novel Twitter Bot Detection Benchmark'. Work in progress.

#### Affiliated Paper
The affiliated paper of this repository, 'TwiBot-20: A Comprehensive Twitter Bot Detection Benchmark', is currently under review at CIKM'21.

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
If you are interested in using the dataset, please contact wind_binteng at stu.xjtu.edu.cn to obtain permission to download the dataset for research efforts only. Due to privacy issues, we are not directly posting the dataset, but temporarily for reviewers at CIKM'21, feel free to download the full TwiBot-20 at https://drive.google.com/drive/folders/1ju-bXk6X3n7FNNzv1aXH7-zgqAAnid1N?usp=sharing.
