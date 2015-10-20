# Guide to Solving and Reviewing Tweet Shortener

Before we start coding our methods, we need to create a hash where our methods can look up which word needs to be substituted.

```ruby
def dictionary
  dictionary = {
    "too" => "2",
    "to" => "2",
    "two" =>"2",
    "four" => "4",
    "for" => "4",
    "be" => "b",
    "you" => "u",
    "at" => "@",
    "and" => "&"
  }
end
```

### `word_substituter`

Let us start with defining our `word_substituter` method. This method will also take in an argument `tweet`.

```ruby
def word_substituter(tweet)
end
```

To see what the passed in tweet is, we will put a `binding.pry` and play with it in our console. To do so, first we need to `require 'pry'` and then write `binding.pry` into our method.

```ruby
require 'pry'

def word_substituter(tweet)
  binding.pry
end
```

```bash
17: def word_substituter(tweet)
    18:   binding.pry
 => 19: end

[1] pry(#<RSpec::ExampleGroups::TweetShortener::WordSubstituter>)> tweet
=> "Hey guys, can anyone teach me how to be cool? I really want to be the best at everything, you know what I mean? Tweeting is super fun you guys!!!!"
```

Now we know that the `tweet` is a string. 

The next would be to split the string into individual words, to compare them with against the dictionary we create to find any words that we can shorten. The problem is we are given a string. 

If we were doing this in real life, we would go word by word looking for the words we need to replace. How can we do that? If we google `"iterate over words string ruby"` you'll notice the `split` method that converts a string into an array!

So we are going to convert our string into an array, then use some array methods to iterate over our array. While iterating we'll need to check each word, and then replace. We downcase so that incase a word is at a beginning of a sentence the case doesn't matter. After all this iteration we are given an array of words, but our method is supposed to return a string. So after googling "convert array to string ruby" we'll find the `join` method.


```ruby
def word_substituter(tweet)
  tweet.split.collect do |word|
    if dictionary.keys.include?(word.downcase)
      word = dictionary[word.downcase]
    else
      word
    end
  end.join(" ")
end
```

### `#bulk_tweet_shortener`

The `bulk_tweet_shortener` method will take in an array of tweets and shorten those tweets one by one. We already have a method that does the individual shortening of tweets, we could just copy and paste that method into out iteration but we would repeat the same code. The solution here would be just to call that method and pass in the tweet thats need shortening. The test also expects that we `puts` the tweets.

```ruby
def bulk_tweet_shortener(tweets)
  tweets.each do |tweet|
    puts word_substituter(tweet)
  end
end
```

### `#selective_tweet_shortener`

The two tests we have to pass for this method are:

```bash
shortens tweets that are more than 140 characters
does not shorten tweets that are less than 130 characters
```
After passing a tweet, this method should check if the tweet is longer than 140 characters. If the answer is yes, we should use our first method `word_substituter` to shorten the tweet, else we just have to return the unchanged tweet.

```ruby
def selective_tweet_shortener(tweet)
  if tweet.length > 140
    word_substituter(tweet)
  else
    tweet
  end
end
```

### `#shortened_tweet_truncator`

This `shortened_tweet_truncator` method will truncate your tweet if the tweet is still longer than 140 character after the `word_substituter` method has run. The truncated tweet should only be 140 characters including `...` in the end. 

According to ruby-doc.org we can use the `[]`. If passed a range, its beginning and end are interpreted as offsets delimiting the substring to be returned.
Example:

```ruby
a = "hello there"

a[2..3]                
#=> "ll"
```

In our case we can pass in the range 0..136 that would be the first character to the 137th character and then we would add `…` to the end.


```ruby
def shortened_tweet_truncator(tweet)
  if word_substituter(tweet).length > 140
    word_substituter(tweet)[0..136] + '...'
  else
    tweet
  end
end
```

All our specs are passing !