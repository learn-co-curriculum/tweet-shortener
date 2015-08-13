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