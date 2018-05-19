Before deploying it on a server, I wanted to fix the syntax of the bot. The function of the bot is to search for the hashtag "giveaway" and repost it. I thought that this would be a good bot because a lot of times when I see giveaways, I never win. 

The syntax for my MVP has a similar function but it does not exactly retweet it. It takes the user's screen name and the text and tweets it on my page as a tweet. This was a working code but I actually wanted the code to retweet instead. Therefore, I google the retweet method which I got `.retweet`. 

**MVP Code(BEFORE):**

``` ruby 
require 'rufus-scheduler'
require 'twitter'

client = Twitter::REST::Client.new do |config|
  config.consumer_key        = "YOUR CONSUMER KEY"
  config.consumer_secret     = "YOUR CONSUMER SECRET"
  config.access_token        = "YOUR ACCESS TOKEN"
  config.access_token_secret = "YOUR TOKEN SECRET"
end

scheduler = Rufus::Scheduler.new

scheduler.every '5s' do
 client.search("#giveaway").each do |tweet| # Looks for the hashtag, then takes each
  client.update("@#{tweet.user.screen_name}: #{tweet.text}") #take username and tweet and tweet it on my page 
end
end

scheduler.join
```
Looks for the hashtag, then takes each tweet and take username and tweet and tweet it on my page. 

**FINAL Code(AFTER):**

``` ruby 
require 'rufus-scheduler'
require 'twitter'

client = Twitter::REST::Client.new do |config|
  config.consumer_key        = "YOUR CONSUMER KEY"
  config.consumer_secret     = "YOUR CONSUMER SECRET"
  config.access_token        = "YOUR ACCESS TOKEN"
  config.access_token_secret = "YOUR TOKEN SECRET"
end

scheduler = Rufus::Scheduler.new

scheduler.join
scheduler.every '5s' do 
 client.search("#giveaway").each do |tweet| #Looks for the hashtag, then takes each 
  client.retweet(tweet) #retweet it
 end 
end 

scheduler.join
```
Looks for the hashtag, then takes each and retweets it. 


After adjusting the code to function the way I want, I can deploy it onto a server so that it will run without having to type the command `ruby filename.rb`. 

# Deploying 

First, I tried to use [repl.it](https://repl.it/) since it recently updated allowing users to use gems. I came across a dead end because my gems did not work. 

In order to use gems we need the following code 

```ruby
require 'bundler/inline'

gemfile true do
 source 'http://rubygems.org'
 gem ' ' #gem name 
end
```

[<img src="../images/repl.png">](https://repl.it/repls/SurprisedRingedSearch)

Unfortunately, I got an error and can't seem to figure out why. So I googled where and how can deploy my twitter bot. 