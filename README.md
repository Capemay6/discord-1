import tweepy

# Authenticate to X (formerly Twitter)
API_KEY = 'your_api_key'
API_SECRET = 'your_api_secret'
ACCESS_TOKEN = 'your_access_token'
ACCESS_TOKEN_SECRET = 'your_access_token_secret'

# Set up authentication
auth = tweepy.OAuth1UserHandler(API_KEY, API_SECRET, ACCESS_TOKEN, ACCESS_TOKEN_SECRET)
api = tweepy.API(auth)

# Function to fetch tweets from a specific account
def fetch_tweets(username, count=10):
    try:
        # Get the user's tweets
        tweets = api.user_timeline(screen_name=username, count=count, tweet_mode='extended')
        
        # Print each tweet
        for tweet in tweets:
            print(f"{tweet.created_at} - {tweet.full_text}\n")
    except tweepy.TweepError as e:
        print(f"An error occurred: {e}")

# Example usage
fetch_tweets('account_username', count=5)

