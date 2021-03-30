# Identifying and Analyzing Cryptocurrency Manipulations in Social Media
This repository includes the datasources used for the analysis in https://arxiv.org/abs/1902.03110.

# Datasets:
- Twitter: The original dataset collected from Sept 2017 to Aug 2018 includes all the tweets mentioning at least one cashtag in coin_list.csv. The resulting dataset contains 30,760,831 tweets and 3,708,176 users in total. To preserve users' privacy, only the timeseries extracted from the dataset are provided here.
  - sentiment-ts: Average sentiment of the tweets mentioning a coin at a timestamp.
  - tweets-ts: Number of tweets mentioning a coin at a timestamp.
  - users-ts: Number of unique users mentioning a coin in their tweets at a timestamp.
- Telegram: 
  - channels: Cryptocurrency related Telegram channels.
  - classified: The result of the processing Telegram messages corresponding to a pump attempt, labeled by the classifier explained in Section 4 of the [paper](https://arxiv.org/abs/1902.03110).

# Format:
- Twitter timeseries: Each `Twitter/x-ts` consists of **_$coin_symbol.json_** files, containing x timeseries of the **_coin_**, where x could be sentiment, tweets or users. For example `sentiment-ts/$BTC.json` contains the average sentiment of the tweets mentioning $BTC, at each time stamp, with the following format:  
`{"data": [[{"$date": 1524700800000}, 0.1], [{"$date": 1524700860000}, 0.2], ...]}` 
- Telegram channels: `Telegram/channels` consists of **_channel_id.jl_** files, where each .jl file includes all the messages posted in a channel. Each line of a .jl file is a json object corresponding to a [Telegram message object](https://python-telegram-bot.readthedocs.io/en/stable/telegram.message.html)
- Pump Attempts: Each record in a `Telegram/classified/coin-pump.csv` corresponds to a pump attempt, and includes the following fields:
  - Message ID: The id of the message provoking a pump attempt.
  - Channel ID: The id of the channel that the message has been posted on.
  - Date: The date that the message has been posted on the Telegram channel.
  - Time: The time that the message has been posted on the Telegram channel.
  - Coin: The coin that is the target of the pump operation.
  
- Price Extracts: `Telegram/classified/price_extract.csv` includes the price extracted from Telegram messages corresponding to a pump attempt. Each record has the following fields:
  - Message ID: The id of the message provoking a pump attempt.
  - Channel ID: The id of the channel that the message has been posted on.
  - Date: The date that the message has been posted on the Telegram channel.
  - Time: The time that the message has been posted on the Telegram channel.
  - Coin: The coin that is the target of the pump operation.
  - Buy: The price to buy the coin mentioned in the message.
  - Sell: A list of target prices that scammer wish to achieve by their pump operation mentioned in the message. 
  
# Citation
More detail on data collection and data analysis can be found in [Identifying and Analyzing Cryptocurrency Manipulations in Social Media](https://arxiv.org/abs/1902.03110). Please cite our paper if you use the dataset.  

    @article{mirtaheri2019identifying,
      title={Identifying and Analyzing Cryptocurrency Manipulations in Social Media},
      author={Mirtaheri, Mehrnoosh and Abu-El-Haija, Sami and Morstatter, Fred and Steeg, Greg Ver and Galstyan, Aram},
      journal={arXiv preprint arXiv:1902.03110},
      year={2019}
    }
