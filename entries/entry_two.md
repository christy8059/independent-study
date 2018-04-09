# Twitter Bot! 

After contemplating between studying SASS or Ruby Twitter Bots for my independent studies I decided to stick with Twitter Bots. 

This week was a successful week! I got the Twitter bot to work, meaning I was able to tweet from the command line. 
<br> <br> 
Want to know how?

## Connecting to Twitter 
With the help of a [Ruby Twitter Bot](http://www.codebycodes.com/blog/2015/08/31/creating-a-simeple-twitter-bot-with-ruby) tutorial that I found online, I was able to learn how to connect the command line on [Cloud9](https://c9.io) to an existing twitter account (ie: mine).

Twitter is a social platform was individuals go on from online or on their phones. But with a few lines of code from the command line we can also do the same or even more incredible things. Besides what I mentioned in entry one I learned the syntax needed to tweet and to search for a specific tag then retweeting it. 

First, let me explain how to connect your command line with twitter. 

**Step 1:** Create a [twitter app](https://apps.twitter.com/) in order to connect it to the Twitter API. 
<br>
<img src="../images/twitterapp.png">
<br>
*Fill in the necessary components. For the section that says website you can use  "http://www.example.com" as a filler 

**Step 2:** Log onto Cloud9 and create a new directory ``` mkdir directoryname ```. Then change directory using ```cd directoryname```

**Step 3:** Create a file.  ``` touch filename.rb ```<br> 
*_note: we are using ruby therefore it is an .rb file_*

**Step 4:** In order to use certain syntax we have to install a Twitter Gem using the syntax :``` gem install twitter ```  By doing so c9 knows what we're referring to when using ruby <br> 


**Step 5:** Now to actually connect it to twitter we have to create a client, which is like creating a user. In this client (user) we have to input the configuration variables. 
<br>
The variables consist of keys and tokens. They can be found in the Keys and Access Tokens tab. <br> 
<img src=../images/keyandaccess.png> 
<br> 

** ATTENTION ** Keep this code private because it is the "password" to your twitter account. 
<br> 

<img src=../images/client.png> <br>

Within the parenthesis you fill in your key and access code according to your account. The keys and access code acts as passwords to log into your twitter therefore it is unique. Now you are done and ready to cold from your command line. 



## To Test

Every time you test the line of code you will have to run ```ruby filename```

#### _To post something on twitter:_ 

```
client.update('whatever you want to tweet')
```
### Example: 
<img src=../images/myex.png>

This simply tweets from your command line. We have to call client and tell the object what we want to do. In order to tweet we have to add ```.update``` followed by parenthesis and single quotation mark. 



#### *_To look for tweets with certain keywords or hash tags_*


```
client.search("#school").take(1).each do |tweet|
  puts "#{tweet.user.screen_name}: #{tweet.text}"
end
```

### Example:
<br>
<img src=../images/search.png>
<br> 

The line of code tells the client object to look for any tweets that has the hashtag of school. Then take the first result and puts the username and the tweet in the command line.
<br> 

# Next steps
Since I chose to study twitter bots there are still so many things that I have yet to discover. Therefore, I will continue to test out the different commands that I could do on the command line. I would also like to see if I can use conditions to combine multiple commands. I don't have a complete picture of what I want to do but I believe that while I tinker around with the bot ideas will come to me. 

# Takeaways 

- The internet is your friend. Spend more time looking at different sources.
- Learning on your own means to tinker and test out certain lines of code to understand its functionality. (Code along tutorials) 
- Comments are important because they help me better understand the syntax and also functions as notes for the future self.
