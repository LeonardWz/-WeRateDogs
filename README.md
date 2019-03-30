# Data Cleaning of WeRateDogs

The project is to organize (and analyze and visualize) data sets that are archives of Twitter user @dog_rates, nicknamed WeRateDogs.

## Preparation in advance
You need to meet the following software requirements:
+ You need to use **Jupyter Notebook** on your computer,installation procedures and instructions can be found at https://www.anaconda.com/download/.
+ The following packages (Python library) need to be installed. You can install these libraries through CONDA or pip:pandas,numpy,requests,tweepy,json

### Summary
WeRateDogs is a Twitter owner who ratings people's pet dogs in a humorous way. These scores are usually denominated by 10. But the molecule is generally larger than 10:11/10, 12/10, 13/10 and so on.

This file is the basic Twitter data (Twitter ID, timestamp, Twitter text, etc.). It contains more than 5,000 Twitters up to April 1, 2017.

#### Collection
This file contains three files:
1. twitter-archive-enhanced.cs:WeRateDogs Twitter archives. This data file is provided directly.

2. tweet_json.txt:Use the Twitter ID in the WeRateDogs Twitter file, use the Python Tweepy library to query the JSON data of each Twitter in the API, and store all JSON data in a file named tweet_json.txt. Each Twitter JSON data should be written in a separate line. Then read the.Txt file line by line into a pandas DataFrame, containing at least tweet ID, retweet_count, and favorite_count fields.

3. image-predictions.tsv:The predictive data of Twitter images, i.e. the predictive results of the breeds of dogs (or other objects, animals, etc.) that appear in each Twitter, are based on the neural network. This file needs to be downloaded programmatically using Python's Requests library and the URLs provided below:
https://raw.githubusercontent.com/udacity/new-dand-advanced-china/master/%E6%95%B0%E6%8D%AE%E6%B8%85%E6%B4%97/WeRateDogs%E9%A1%B9%E7%9B%AE/image-predictions.tsv

##### Assessment
**Quality:**
+ in_reply_to_status_id、in_reply_to_user_id、retweeted_status_id、retweeted_status_user_id、retweeted_status_timestamp、expanded_urls 列数据缺失 ;
+ timestamp、retweeted_status_timestamp列数据类型应为datatime;
+ 狗狗地位存在双重身份的现象;
+ name列，即狗狗名字存在首字母小写形式,其中None被标记为字符串;
+ 狗狗的分子分母评分存在错误;
+ 本数据集中存在转发的条目和无图片的推特，需删除;
+ P1,P2,P3列的首字母小写形式;
+ 有存在重复的jpg_url;
+ contributors,coordinates,extended_entities,geo,in_reply...5列,place,possibly_sensitive,possibly_sensitive_appealable,quoted_status3列,retweet_status存在缺失值;
+ created_at列数据类型不对;
**Cleanliness**
+ df_twitter表中狗狗地位可以合并成一列‘status’;
+ df_tweet表中display_text_range可分为起始列和结束列;
+ df_tweet表中的retweet_count和favorite_count两列需要提取出来合并到df_twitter表中.

###### Cleaning
1. Backup files are required before any cleaning project starts;
2. The problem of missing values depends on the situation and cannot be dealt with uniformly;
3. Data formats are important, and it takes patience and caution to sort them out;
4. Dog scores and Dog names are not always correct, and regular expressions are needed to extract the correct scores;
5. Pd.merge is needed to merge some columns in this project;

####### Visualization
For more information, please refer to the document:**act_report.pdf**.
