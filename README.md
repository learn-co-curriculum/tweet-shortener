# Manipulating Strings and Hashes: Tweet Shortener

## Objectives

1. Practice iterating over hashes
2. Practice manipulating strings


## Instructions

A client has hired you to automatically post some of their brand messages to twitter, but the problem is that some of the tweets are too long. Your job is to automatically shorten them by replacing longer words with shorter representations (i.e. "two" becomes "2").

* First, write a method, `dictionary`, that contains the words-to-be-substituted and their substitutes. The original words from the list below will be the keys. The substitute of a particular word becomes that key's value. You will use this hash in later methods to look up words and replace them with their substitues. 
* Here is the list of words and their substitutes:

```
"hello" becomes 'hi'
"to, two, too" become '2' 
"for, four" become '4'
'be' becomes 'b'
'you' becomes 'u'
"at" becomes "@" 
"and" becomes "&"
```

* Here is the list of tweets that you'll be shortening. They are contained in the spec file and the test suite will be passed into the methods you build as arguments. 

  
  >1. "Hey guys, can anyone teach me how to be cool? I really want to be the best at everything, you know what I mean? Tweeting is super fun you guys!!!!"

  >2. "OMG you guys, you won't believe how sweet my kitten is. My kitten is like super cuddly and too cute to be believed right?"
  
  >3. "I'm running out of example tweets for you guys, which is weird, because I'm a writer and this is just writing and I tweet all day. For real, you guys. For real."

  >4. "GUISEEEEE this is so fun! I'm tweeting for you guys and this tweet is SOOOO long it's gonna be way more than you would think twitter can handle, so shorten it up you know what I mean? I just can never tell how long to keep typing!"

  >5. "New game. Middle aged tweet followed by #youngPeopleHashTag Example: Gotta get my colonoscopy and mammogram soon. Prevention is key! #swag"

### Methods:

1. Write a method, `word_substituter` that takes in a string of a tweet as an argument and shortens that string based on the allowed substitutes. Use your `dictionary` method that contains your dictionary hash to compare the words in the tweet against the keys in the hash. If there are any matches, replace the word in the tweet with the associated substitute from the hash. 
  * **Hint:** How can you iterate over every word in a tweet and compare it to the hash keys? Convert the tweet into an array to enable this. Then, make sure to convert it back into a string to return the shortened tweet at the end of the method.
  * **Hint:** How can you grab all of the keys of the hash for the purpose of comparing them to the words in the tweet? Use the `.keys` method. 

2. Write a method, `bulk_tweet_shortener` that takes in an array of tweets, iterates over them, shortens them, and `puts` out the results to the screen. 
  * **Hint:** You already wrote a method that shortens tweets. Use it!
  * **Hint:** Remember that you can `puts` out the result of a method by putting `puts` in front of the method call. 



  Now the client has come back to you. They love the program, but they noticed that even tweets that are under 140 characters are being shortened. Now they want you to only shorten the tweet if it's too long.

3. Write a new method, `selective_tweet_shortener`, that only does the substitutions if the tweet is longer than 140 characters. If the tweet is 140 characters or shorter, just return the original tweet.

  Things are going great, but you're noticing that some tweets are too long still, even after substituting shorter words. Being the conscientious developer that you are, you talk to the client about this scenario and decide together that the best thing to do is just truncate the string to 140 characters if it's still too long after you do the substitution.
  
4. Write another method, `shortened_tweet_truncator`, that truncates the tweet to 140 characters. Keep in mind that we count numbers from one 1 and computers from 0. Look at the test expectations for further info.

  * **Hint:** Strings are indexed like arrays. That means you can return string index elements, or a set of string index elements, using the `[]` method. For example: 

```ruby
string = "Hi there, I am a string in this interesting and informative example"
string[0]
# => "H"

string[0..10]
# => "Hi there, I"
```


<p data-visibility='hidden'>View <a href='https://learn.co/lessons/tweet-shortener' title='Manipulating Strings and Hashes: Tweet Shortener'>Manipulating Strings and Hashes: Tweet Shortener</a> on Learn.co and start learning to code for free.</p>

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/tweet-shortener'>Iterating and Manipulating 1</a> on Learn.co and start learning to code for free.</p>
