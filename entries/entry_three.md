# Continuing to explore Ruby Twitter Bot! 

After figuring out how to tweet from the console I was excited to lean other cool comands that I could do. Thus, I was surfing for documentations. There wasn't alot of people who did tutorials on Ruby twitter bots therefore my sources were limited. I was able to find one documentation. (linked below).  
[Ruby Documentation](http://www.rubydoc.info/gems/twitter) I tired each one out to understand how the syntax works.

These command can be used by inputting their screen name or id. 

#### To follow: 
```client.follow('userscreenname')``` 
```client.follow (id#)```

#### To unfollow: 
```client.unfollow('userscreenname')```  
```client.follow (id#)```


#### To see how many follower: 
```client.user(screen_name).followers_count```

<img src="../images/followers.png">

This image shows that I am looking at a specific username (mine) and putting the nummer of followers into the console.


This weeks focus was mainly to look for more documentation and other souces that can help me learn. I was able to learn how to follow, unfollow and see how many followers. 

I decided to create something with what I leared so far. 

<img src="../images/trial.png">

So what this block of code means is check if I have more than 20 followers. If I have more than 20 followers than I would tweet "I have more than 20 followers". If I have less than 20, then I would look for someone who posted a hashtag of hi and follow them. 

```
client.search("#hi").take(1).each do |tweet|
    @name = "#{tweet.user.screen_name}"
      end 
       
followers = client.user('me').followers_count

if followers > 20 
    client.update('I have more than 20 followers')
else 
  client.follow(@name)
       
end

```

* I also noticed that I needed an instance variable because I am reusing it in my if-else statement* 



