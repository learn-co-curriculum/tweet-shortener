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
After putting a `binding.pry` in our method, we know that the passed in `tweet` is a sting.

We need to split the string to get every word individually, then we need to iterate over every word in our string to compare these words to our `dictionary` hash. If the downcased word is a key in our hash, then we need to replace that word with it substitute, else we need to return that word. Also we need to `join` every word back to a string. 


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

The `bulk_tweet_shortener` method will take in an array of tweets and shorten those tweets one by one. We already have a method that does the individual shortening of tweets, let us just use that method and pass in every tweet. The test also expects that we `puts` the tweets.

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

```ruby
def shortened_tweet_truncator(tweet)
  if word_substituter(tweet).length > 140
    word_substituter(tweet)[0..136] + ('...')
  else
    tweet
  end
end
```

All our specs are passing !