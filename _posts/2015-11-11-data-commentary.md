---
layout: post
title:  "Data Commentary"
date:   2015-11-11  
comments:   true        
---

###Figure 1

![figure1](http://ieeexplore.ieee.org/ielx7/6493539/6506137/6506174/html/img/6506174-fig-1-large.gif)

> [Abutaha, M., & Hamamreh, R. (2013, January). New one way hash algorithm using non-invertible matrix. In Computer Medical Applications (ICCMA), 2013 International Conference on (pp. 1-5). IEEE.](http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=6506174&newsearch=true&queryText=new%20one%20way%20hash)

Figure 1 shows the comparison between three algorithm MD5, SHA1, SHA512 and the proposed algorithm EDIH using different data size. With the growth of data size, the processing time increased fast. They can't be ignore after the data size is larger than 1024Kb. In this comparison, the matrix size is 1x1. As we can see, the EDIH is very close in time per second to MD5 and its faster than SHA1 and SHA512 when the matrix size is 1x1. That is to say, the proposed algorithm has much strong robust but still running as fast as the basic MD5 algorithm.


###Figure 2

![figure2](http://ieeexplore.ieee.org/ielx5/5165411/6084801/5983424/html/img/5983424-fig-6-large.gif)

> [Fouda, M. M., Fadlullah, Z. M., Kato, N., Lu, R., & Shen, X. (2011). A lightweight message authentication scheme for smart grid communications. Smart Grid, IEEE Transactions on, 2(4), 675-685.](http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=5983424&queryText=a%20lightweight%20message&newsearch=true)

Fig. 6 shows the comparison between the proposed and conventional schemes in terms of decryption/verification delay per BAN GW. As evident from the results, the decryption delay increases linearly for both these schemes. However, the conventional ECDSA scheme exhibits higher decryption delay compared to that demonstrated by the proposed one. The reason is that the proposed scheme provides a secure authentication process followed by AES encryption, which is faster than the conventional ECDSA scheme which relies on signature verification along with decryption at the BAN for every message coming from each HAN.


###Table 1

![table1](https://pic.honeyhaw.com/images/picture1.png)

> [Zhou, R., & Hwang, K. (2007). Powertrust: A robust and scalable reputation system for trusted peer-to-peer computing. Parallel and Distributed Systems, IEEE Transactions on, 18(4), 460-473.](http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=4118688&newsearch=true&queryText=powertrust)

Table 1 compares the proposed PowerTrust system with the established EigenTrust and PeerTrust systems in four technical aspects which are Local Trust Evaluation, Global Reputation Aggregation, Implementation Overview, Scalability & Reliability. As we can see in the table, the proposed system has a strong advantage in Scalability & Reliability. Although the proposed system used different methods than the other two, it has its own feature to ensure the robustness and high efficiency. The table just showed a brief summary of whole system. Detailed explaination and evaluation would be stated later.
