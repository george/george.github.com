---
layout: post
title: "Temporarily Redirect STDOUT in Ruby"
date: 2011-03-08 11:00
comments: true
categories: 
---
{% highlight ruby %}
def silence
  orig_stdout = $stdout
  $stdout = File.new('/dev/null', 'w')
  yield
ensure
  $stdout = orig_stdout
end

puts 'now you see it'

silence do
  puts "now you don't"
end

puts 'now you see it again'
{% endhighlight %}