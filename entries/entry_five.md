# Direct Message(DM)

After last week’s unsuccessful trial on methods for direct messages, I was determined to figure it out this week. I looked at the syntax, possible spacing errors, and even googled what the problem could possibly be but nothing really helped to make the method work.

Since I had no idea what was wrong, I decided to double check on the permission page on the [twitter app](https://apps.twitter.com/) I made sure it was on "read, write, and direct messages". Afterward, I regenerated the access token and key, and as well as the consumer key and secret, I replaced the old "passwords" with the new ones. Finally, it worked, allowing me to do more advanced things with direct messages. 

## Create Direct Message
<br>
<img src="../images/send_message.png">
<br>

``` ruby 
client.create_direct_message('@user_screen_name',"The message you want to send them")

```
As shown in the snippet above to create a direct message we can use the method `.create_direct_message`. The first one is the user's screen name which is wrapped in one quotation mark with the "@" symbol. Then followed by a comma and double quotes with the message you would like to send to that person. 

As always to run the file you would have to go to your console and type `ruby filename.rb` 

## DM Sent
<br> 
<img src="../images/sent_dm.png">
<br> 

``` ruby 
client.direct_messages_sent.each do |message|
    puts message.text
end
```

This is a random function that I made. This function puts all the messages that I've sent before and prints it out in the console. The most recent one is always the first one. This uses iteration and the method `.each` to print each one out. 

## Destroying DMs 
**Note**: To delete direct messages we have to use the ID number. Each message that is sent and received is labeled with a number (like a tag).
### How to get ID numbers for direct messages that you sent
<br> 
<img src="../images/sent_id.png">
<br>

``` ruby 
puts client.direct_messages_sent # show sent dm id
```

The line above uses the command `puts` and the method `.direct_messages_sent` to show the id number. The default of the method is an ID number. Note: there are only two ID numbers because I only sent two direct messages in total. 

### How to get ID numbers for messages that you receive
<br> 
<img src="../images/receive_id.png">
<br> 

``` ruby 
puts client.direct_messages #show received direct message id
```
The line above uses the command `puts` and the method `.direct_messages` to show the id number for messages that I've received. The default of the method is an ID number. Note: there is only one ID number because I only received one direct message in total. 

### To delete messages sent

<br> 
<img src="../images/delete_sent.png">
<br> 

``` ruby 
client.destroy_direct_message(client.direct_messages)#delete messages I receive
```

This method uses ID numbers to delete direct messages that are received, therefore we can use `client.direct_messages` as the value to pass as an argument in order to know the which message to delete. **Remember** `client.direct_messages` prints out the ID number of the messages that are being received.

### To delete messages received  
<br> 
<img src="../images/delete_recieve.png">
<br> 

``` ruby 
client.destroy_direct_message(client.direct_messages_sent) #delete message I sent 
```

This method uses ID numbers to delete direct messages that are sent, therefore we can use `client.direct_messages_sent` as the value to pass as an argument in order to know which message to delete. **Remember `client.direct_messages_sent` prints out the ID nu,ber of the messages that are sent. 

# Timeline 
After studying methods for direct messaging I also learned two more methods that grab the tweets on my timeline. 

<br> 
<img src="../images/timeline_tweet_id.png">
<br> 

``` ruby 
puts client.home_timeline # prints the tweet ID on my timeline 
```
 
The default for this message is to print out the 20 recent tweet ID into the console using `puts`.

## To print the text of the tweet from timeline
<br> 
<img src="../images/timeline_text.png">
<br> 

```ruby 
client.home_timeline.take(1).each do |tweet| #takes the tweets on my timeline 
      puts "#{tweet.user.screen_name}: #{tweet.text}" # take each tweets user screen name and post their tweets in the console.
end 
```
This grabs the first tweet on my feed and prints the user's screen name and the text that they've posted or retweeted. 

# Obstacle
When I was messing around with direct messaging I couldn't get the user's screen name to print out. I tried

``` ruby
client.direct_messages.each do |user,message|
    puts "#{user.name}: #{message.text}"
end 
```
but when I run ruby it shows an error saying the method `.name` does not exist. It was very frustrating so I decided to move on from it and come back to it later. 


# Takeaways 
- move onto another topic and then come back if I get stuck on something 
- take breaks and try other ways to fix the problem
- be determined and pushed through until you accomplished your goal
