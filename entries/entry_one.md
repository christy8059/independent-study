# Entry 1: Intro / Plan 

For the past week I have been looking through the different topics that I would possibly study for my independent study unit. After completing the sinatra unit I wanted to do something outside of ruby, but I ended up choosing to learn about "twitter bot".

## Why? 
While going through the list of options the word **_bot_** stood out to me. I always heard of different bots so I thought this would be something similar. A bot is set to do different tasks. I know some can autofill, auto checkout, auto tweet, and all sorts of tasks. 

<!--<img src = "https://3vowli249lp13hl4bz2ku62r-wpengine.netdna-ssl.com/wp-content/uploads/index51-1200x1200.png" align = "right" height = 30% width = 30%>  -->
 
A twitter bot is a bot software that allows the system to control a twitter account through the Twitter API. This means that it will require ruby using keys, access token, gems like `gem install twitter` and other ruby related terms. I noticed that this is similar to using MVC (model, view and control), but the view will be on the twitter page. 


The function of a twitter bot is to simply be able to tweet, retweet, like, follow, unfollow, or direct message other accounts on its own. 
This reminds me of how technology has advanced and what other cool bots are out there. 


## Change in plan...
I thought bots were really cool since it could function on its own, but I wasn't sure what I could do with it after learning how to make one. There are plenty of tutorials online teaching users how to make a [twitter bot](http://www.codebycodes.com/blog/2015/08/31/creating-a-simeple-twitter-bot-with-ruby). Therefore, I decided to change my topic to SASS.

## What is SASS 
SASS stands for _Syntactically Awesome StyleSheets_. It is an addition to CSS. SASS is a way to make our code DRY... meaning "don't repeat yourself". This is because there are features like _variables, nesting, mixins, inheritance_ and etc that allows us as users to use css in a more convenient way. 

I also prefer to study SASS because I have prior experience with CSS. This makes my transitioning from CSS to SASS easier while learning  new features with similar syntax. 

## Code Academy
I searched for ways to learn SASS and I found that code academy best for learning as a beginner.  
<br>

#### Uh-oh
   Broswer can not interpret SASS! Uh- Oh.. 
    - I have to convert/compile my file to CSS. (Compiling means to convert it into a lower level code. Another word, making it simplier so that the browser can execute it)  
    <br> 
  `sass main.scss main.css`   
    <br>
    
   This command simply does...  
     a. input into (main.scss)  
        b. output into (main.css)

## Nesting Selector

I learned that nesting is to place selectors in the scope of another selector. 

**_scope_**: the context of a variable. Simply any code that is between its opening,  `{` and closing `}`  



In nesting there are two phrases: parent and children . As seen in the block of code below the `.parent` is the outter layer, while the `.children` is the inner later. The children lives inside the scope of another selector `.parent` . 

SCSS : 

```
.parent{  
    color:blue
    .children {
        font-size: 12px; 
    }
}

```
converts to ..... 

CSS: 

```
.parent {
    color: blue;
}

.parent .child {
    font-size: 12px; 
} 
```


### Nesting Properties

Nesting can work for properties that are the same. For example font, border, padding and etc.
 
To nest common css properties you use a colon `:` after the name of the property


Example:


SCSS 

``` 
.parent {
  font : {
    family: Roboto, sans-serif;
    size: 12px;
    decoration: none;
  }
}
```

converts to... 

```
.parent {
  font-family: Roboto, sans-serif;
  font-size: 12px;
  font-decoration: none;
}

```