# Tweets as an Image

This project is created using [Canvas](https://www.npmjs.com/package/canvas), [Puppeteer](https://github.com/puppeteer/puppeteer), and [Twitter API](https://developer.twitter.com/en/docs), initially created  for integration with [Github Profilinator](https://github.com/rishavanand/github-profilinator)( P.S. You can use it anywhere you want to add your Tweets in Image format :wink: ).


**Installation**
1. Create Developer Account on twitter.
2. Register your app.
3. [Generate Bearer Token](https://developer.twitter.com/en/docs/authentication/oauth-1-0a/obtaining-user-access-tokens).
4. Link your github repository on [Heroku](https://www.heroku.com/).
5. Set [environment variable](https://devcenter.heroku.com/articles/config-vars) TWITTER_OAUTH_TOKEN="Your bearer auth token".


## Version 2:

### API available for use:
 - `https://tweets-as-an-image.herokuapp.com/tweet?twitterHandle={your_twitter_handle}`
 - `https://tweets-as-an-image.herokuapp.com/tweet?twitterHandle={your_twitter_handle}&id={your_tweet_id}&theme={light_or_dark}&maxwidth={max_width_of_your_tweet_image}&height={height_of_the_image}&lang={language}`

 #### Optional Query Arguements:
 - `id`(User's Tweet ID, Default: user's last tweet)
 - `theme` (light or dark, Default: dark)
 - `maxwidth` (maxWidth of your tweet image(+10px for border will be added), Default: 550)
 - `height` (height of the image, Default: Min(2000, Height of your tweet))
 - `lang` (Languages Supported by twitter, check [here](https://developer.twitter.com/en/docs/twitter-for-websites/supported-languages), Default: en)

 ### Note:
 - This project is using oembed response of the tweets, and the height of the any tweets are not fixed, as there can be media content too, so it is not returned in the response. Read more about it [here](https://developer.twitter.com/en/docs/twitter-api/v1/tweets/post-and-engage/api-reference/get-statuses-oembed). I am evaluating the height in the puppeteer itself, which is set to Minimum of 2000px and Height of Your Tweet. If you want to clip the part of the tweet, you can pass height as an optional query.
 - I am using [Puppeteer](https://github.com/puppeteer/puppeteer), a headless Chromium based browser to load the oembed response and take the screenshot of it.
 - The Deployement part on heroku is same as the above one, but you need to add `puppeteer buildpack` in the deployement. You can know more about that [here](https://github.com/jontewks/puppeteer-heroku-buildpack)
