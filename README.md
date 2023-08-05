import tweepy

# Replace with your own Twitter API keys
API_KEY = 'your_api_key'
API_SECRET = 'your_api_secret'
ACCESS_TOKEN = 'your_access_token'
ACCESS_SECRET = 'your_access_secret'

# Authenticate to Twitter
auth = tweepy.OAuthHandler(API_KEY, API_SECRET)
auth.set_access_token(ACCESS_TOKEN, ACCESS_SECRET)
api = tweepy.API(auth)

# Get your Twitter username
username = api.me().screen_name

# Get the list of users you follow
following = set(api.friends_ids(username))

# Get the list of users who follow you
followers = set(api.followers_ids(username))

# Find users you follow but who don't follow you back
not_following_back = following - followers

# Print the usernames of users not following you back
for user_id in not_following_back:
    user = api.get_user(user_id)
    print(user.screen_name)
