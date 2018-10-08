# DRN: A Deep Reinforcement Learning Framework for News Recommendation

links: http://delivery.acm.org/10.1145/3190000/3185994/p167-zheng.html?ip=203.88.133.50&id=3185994&acc=OPEN&key=4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E6D218144511F3437&__acm__=1537373033_c677ac0de46140950c2e59eadce4c1c8

http://delivery.acm.org/10.1145/3190000/3185994/p167-zheng.pdf?ip=203.88.133.50&id=3185994&acc=OPEN&key=4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E6D218144511F3437&__acm__=1537354541_effe38335d89a92752e1a8df8dd88a37

[local link](reading/ material\DRN.pdf)



**Why Reinforcement Learning ?**

- There are some online recommendation methods that can capture the dynamic change of news features and user preference through online model updates, they only try to optimize the current reward (e.g., Click Through Rate), and hence ignore what effect the current recommendation might bring to the future. 

- Example 1.1.
  - When a user Mike requests for news, the recommendation agent foresees that he has almost the same probability to click on two pieces of news: one about a thunderstorm alert, and the other about a basketball player Kobe Bryant. However, according to Mike's reading preference, features of the news, and reading patterns of other users, our agent speculates that, after reading about the thunderstorm, Mike will not need to read news about this alert anymore, but he will probably read more about basketball after reading the news about Kobe. This suggests, recommending the latter piece of news will introduce larger future reward. Therefore, considering future rewards will help to improve recommendation performance in the long run.