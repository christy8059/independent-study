# Scheduler
The hardest thing about learning on your own is that no one is there to tell you the answers to your problem. Everything is done independently. Last week I focused on a way to schedule tasks to run at a certain time or a certain number of times. First, I tried using _**Cron Job**_ [(see last weeks entry)](entries/entry_six.md), but I was unsuccessful in accurately running the cron job. I YouTubed some tutorials on how to work cron jobs but it did not work.

# What did I do next? 
I searched for alternative ways to schedule ruby tasks. By doing so I came across the gem documentation for [rufus-scheduler](https://github.com/jmettraux/rufus-scheduler). This helped me a lot because I was able to find several other gems that schedule ruby tasks. This is beneficial since it is written in the ruby file which I can simply use the command  `ruby filename.rb` to test it out. 


# Scheduler Gem
This is a gem that uses threads to schedule tasks. 

To get started...

1. In your ruby file require the gem `rufus-scheduler`. 

2. Then create a new variable. You can call it scheduler or anything appropriate. By doing so we are calling on a variable giving it a specific command. 

```ruby 
scheduler = Rufus::Scheduler.new
``` 
3. To schedule something, we call on the scheduler variable and attach a method to it.

With Scheduler, we can set it to fulfill our commands. If we want to make it every second (s) or minute (m) we can use the method `.every`. This task is looping until you tell it to stop or it crashes. 

**For example:**
```ruby 
scheduler.every '5s' do
    #something every 5s
end 
```
To schedule something 'in' a certain amount of time we use the method `.in`. 

**For example:**

```ruby 
scheduler.in '5d' do
  # do something in 5 days
end
```

To schedule at a specific time you use the command `.at`. 

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
![](bot1.mp4)

This will look for a specific tag and take the user's screen name and tweet and tweet it on your account. This will be done every 5 seconds. 



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

This will send a direct message to the specific user with the specific message every 5 seconds. 


# MVP
After learning how to schedule a ruby task I am now able to make an MVP(minimum viable product). Example one is my MVP. That is similar to what I want to do. While building my MVP I thought that this would be useful when trying to win giveaways. Therefore, I would change it to look for the hashtag giveaway. Then like and retweet it in order to enter the giveaway. Example 1 is a simple version of my idea. 


# Sources
Github - https://github.com/jmettraux/rufus-scheduler

# Takeaways 
-When encountering an obstacle always keep calm. Take a break or a deep breath before returning to work. This will stimulate the brain to "restart". By doing so you can think through the problem more clearly.

-Look at tutorials to see how it works. Make sure the syntax is correct. 
