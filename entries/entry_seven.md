# Scheduler
The hardest thing about learning on your own is that no one is there to tell you the answers to your problem. Everything is done independently. Last week I focused on a way to schedule tasks to run at a certain time or a certain number of times. First, I tried using _**Cron Job**_ [(see last weeks entry)](entries/entry_six.md), but I was unsuccessful in accurately running the cron job. I YouTubed some tutorials on how to work cron jobs but it did not work.

# What did I do next? 
I searched for alternative ways to schedule ruby tasks. By doing so I came across the gem documentation for [rufus-scheduler](https://github.com/jmettraux/rufus-scheduler). This helped me a lot because I was able to find several other gems that schedule ruby tasks. This is beneficial since it is written in the ruby file which I can simply use the command  `ruby filename.rb` to test it out. 


# Scheduler Gem
This is a gem that uses threads to schedule tasks. 

To get started...

1. In your ruby file require the gem `rufus-scheduler`. 
```ruby 
require 'rufus-scheduler'
```
2. Then create a new variable. You can call it scheduler or anything appropriate.

```ruby 
scheduler = Rufus::Scheduler.new
``` 
3. To schedule something, we call on the scheduler variable and attach a method to it.

With Scheduler, we can set it to fulfill our commands. If we want to make it every second (s) or minute (m) we can use the method `.every`. The task will loop until you tell to stop it on the command line or if it crashes. 

**For example:**
```ruby 
scheduler.every '5s' do
    #something every 5s
end 
```
To schedule something "in" a certain amount of time we use the method `.in`. 

**For example:**

```ruby 
scheduler.in '5d' do
  # do something in 5 days
end
```

To schedule "at" a specific time you use the command `.at`. 

**For example:**

```ruby
scheduler.at '2030/12/12 23:30:00' do
  # do something at a given point in time
end
```


4. We finish off with `scheduler.join`. This will let the current thread join the scheduler thread. 

A complete scheduler would look like this 

```ruby 
scheduler.every '5s' do
    #something every 5 seconds.
end

scheduler.join
```

5. To run the ruby file you type `ruby filename.rb`

# Test runs 
Now that we can schedule tasks we can connect it to twitter and do amazing things with it. 

**Example #1**
```ruby 
require 'rufus-scheduler'
require 'twitter'

client = Twitter::REST::Client.new do |config|
  config.consumer_key        = "YOUR KEY"
  config.consumer_secret     = "YOUR SECRET"
  config.access_token        = "YOUR TOKEN"
  config.access_token_secret = "YOUR TOKEN SECRET" 
end

scheduler = Rufus::Scheduler.new

scheduler.every '5s' do
 client.search("#supreme").each do |tweet|
  client.update("#{tweet.user.screen_name}: #{tweet.text}")
 end
end

scheduler.join
```
Every five seconds the bot will look for the specific tag that you specified and tweet the user's screen name and tweet. 

[Link to demo](https://drive.google.com/open?id=0B5qSM1gxTeQFRjBlbGZSak83U0xJeGRKNlhHTEVHVGw4MnVR) 

*Notice:* In the demo, we see the number of tweets increasing gradually as the bot is running. 

**Example #2**
```ruby 
require 'rufus-scheduler'
require 'twitter'

client = Twitter::REST::Client.new do |config|
  config.consumer_key        = "YOUR KEY"
  config.consumer_secret     = "YOUR SECRET"
  config.access_token        = "YOUR TOKEN"
  config.access_token_secret = "YOUR TOKEN SECRET" 
end

scheduler = Rufus::Scheduler.new

scheduler.every '5s' do
 client.create_direct_message('@user_screen_name',"your message")
end

scheduler.join
```
<img src="../images/direct_5s.png">

Every five seconds the bot will send a direct message to the specific user. 


# MVP
After learning how to schedule a ruby task I am now able to make an MVP(minimum viable product) therefore I came up with example one. It is similar to what I want to do since it looked for a tag and then retweets it.I want to make a bot that can retweet posts that has a hashtag of the word giveaway. This would be much easier to enter giveaways and probably be more successful at it. 

# Sources
Github - https://github.com/jmettraux/rufus-scheduler

# Takeaways 
-When encountering an obstacle always keep calm. Take a break or a deep breath before returning to work. This will stimulate the brain to "restart". By doing so you can think through the problem more clearly.

-Look at tutorials to see how it works. Make sure the syntax is correct. 
