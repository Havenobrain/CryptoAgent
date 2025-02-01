1. Cloning the repository
First, you need to download the project from GitHub.

Clone the repository with submodules:

git clone --recurse-submodules https://github.com/Havenobrain/TwitterCryptoAgent.git – enter this into the terminal

cd TwitterCryptoAgent – enter this into the terminal

Installing dependencies
Go to the agent-twitter-client folder and install all dependencies:
cd agent-twitter-client – enter this into the terminal
npm install – enter this into the terminal
cd .. – enter this into the terminal

Now go to the twitter-scraper-finetune folder and install dependencies:

cd twitter-scraper-finetune – enter this into the terminal
npm install – enter this into the terminal
cd .. – enter this into the terminal

Configuring the .env file
Before starting the agent, you need to create a .env file inside the twitter-scraper-finetune folder and add your Twitter credentials:
TWITTER_USERNAME=your_twitter_username
TWITTER_PASSWORD=your_twitter_password
TWITTER_EMAIL=your_twitter_email

This is necessary for the bot to log in and collect tweets.

Configuring keywords and filters
To let the bot know which tweets to collect, create two text files inside the twitter-scraper-finetune folder:
Keywords (keywords.txt)
Go to src/twitter/keywords.txt
Add words or phrases that must be in a tweet for it to be processed.

Example keywords.txt:
Bitcoin
Crypto
Investing
Ethereum

Filter words (filter.txt)
Go to src/twitter/filter.txt
Add words that should cause a tweet to be ignored.

Example filter.txt:
scam
giveaway
free money

If a tweet contains at least one word from keywords.txt and does not contain any words from filter.txt, it will be processed.

Running the bot
Go to the twitter-scraper-finetune folder and start monitoring tweets:
cd twitter-scraper-finetune – enter this into the terminal
npm run twitter -- benny_cryp36211 – enter this into the terminal

If everything is set up correctly, the bot will start collecting tweets, paraphrasing them in a philosophical style, and publishing them.

Changing bot settings
Changing keywords and filters
Modify the contents of keywords.txt if you want to track different topics.
Edit filter.txt to exclude unwanted tweets.

Changing the tweet posting interval
By default, the bot posts tweets every 2 hours.
To change the interval, open TwitterPipeline.js and find this line:

setInterval(() => this.publishScheduledTweet(), 2 * 60 * 60 * 1000);

Change 2 * 60 * 60 * 1000 to the desired interval:

Every 3 hours
setInterval(() => this.publishScheduledTweet(), 3 * 60 * 60 * 1000);

Every 5 minutes
setInterval(() => this.publishScheduledTweet(), 5 * 60 * 1000);

Once per day
setInterval(() => this.publishScheduledTweet(), 24 * 60 * 60 * 1000);

Changing the monitored Twitter account
To track a different Twitter account, update the parameter in TwitterPipeline.js:

this.username = "New_Account";

How it works?
The bot collects tweets from the specified account or based on keywords.
It filters tweets, checking if they contain keywords and do not contain filtered words.
It paraphrases tweets in a philosophical style (e.g., replacing "crypto" with "digital gold").
It publishes paraphrased tweets every 2 hours (or at another specified interval).