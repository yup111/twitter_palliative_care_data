# Mining Twitter to Assess the Determinants of Health Behavior towards Palliative Care in the United States

This is the data repository for our Twitter paper published in AMIA 2020 summit [Mining Twitter to Assess the Determinants of Health Behavior towards Palliative Care in the United States](https://arxiv.org/abs/1905.12469).
 
# Citation
* Please cite this article, if you use the data for your own studies
   * **

> **Abstract:** 
Palliative care is a specialized service with proven efficacy in improving patients’ quality-of-life. Nevertheless, lack
of awareness and misunderstanding limits its adoption. Research is urgently needed to understand the determinants
(e.g., knowledge) related to its adoption. Traditionally, these determinants are measured with questionnaires. In this
study, we explored Twitter to reveal these determinants guided by the Integrated Behavioral Model. A secondary goal
is to assess the feasibility of extracting user demographics from Twitter data—a significant shortcoming in existing
studies that limits our ability to explore more fine-grained research questions (e.g., gender difference). Thus, we
collected, preprocessed, and geocoded palliative care-related tweets from 2013 to 2019 and then built classifiers to:
1) categorize tweets into promotional vs. consumer discussions, and 2) extract user gender. Using topic modeling,
we explored whether the topics learned from tweets are comparable to responses of palliative care-related questions
in the Health Information National Trends Survey.

Contact person: Jiang Bian, ji0ng.bi0n@gmail.com
                Yunpeng Zhao, zhaoyunpeng111@gmail.com


Let us know if you have further questions.

# Dataset Collection
This repository contains the ids of the tweets we used in our paper (`twitter_palliative_care_data.json`).  To collect the actual data, follow the steps below.

## Step one. Install `tweetf0rm`

In order to run the code, you need python 3+. 
First, 
```
git clone git://github.com/bianjiang/tweetf0rm.git
```
Then install the required packages.
```
pip install -r requirements.txt
```

## Step two. Obtain your own Twitter API keys 

* First, you'll want to log onto the twitter dev site and create an applciation at https://dev.twitter.com/apps to have access to the Twitter API!
* Create an access token and grab your applications ``Consumer Key``, ``Consumer Secret``, ``Access token`` and ``Access token secret`` from the OAuth tool tab. Put these information into a ``config.json`` under ``apikeys`` (see an example below).

```json
{
        "apikeys": {
                "i0mf0rmer01": {
                        "app_key": "APP_KEY",
                        "app_secret": "APP_SECRET",
                        "oauth_token": "OAUTH_TOKEN",
                        "oauth_token_secret": "OAUTH_TOKEN_SECRET"
                }
        }
}

```

## Step three. Crawl tweets by tweet ids

In general,
* `-c`: the config file for Twitter API keys
* `-o`: the output folder (where you want to hold your data)
* `-cmd`: the command you want to run
* `-cc`: the config file for the command (each command often needs different config files, see examples below)
* `-wait`: wait `x` secs between calls (only in REST API access)

Run the following command to obtain the lynch syndrome data.
```
python twitter_tracker.py -c ./config.json -o data/tweets_lynch_syndrome -cc ./Lynch_tweet_ids.json -cmd tweets_by_id
```