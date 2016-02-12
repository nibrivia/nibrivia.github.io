---
layout: post
title: "Democratic primary expectations v actual"
author: "Olivia Brode-Roger"
date: "February 10, 2016"
---

The datum for the expectations come from http://cookpolitical.com/story/9179. At some point I will get around to computing these myself.


{% highlight r %}
#expectations <- read.csv(file = '~/Projects/2016/expectations.csv', stringsAsFactors = FALSE)
expectations <- t(matrix(c(13, 31, 9, 15), nrow=2))
colnames(expectations) <- c("Clinton", "Sanders")
{% endhighlight %}

The delegate data is (so far) manually entered.


{% highlight r %}
delegates <- t(matrix(c(23, 21, 9, 15), nrow=2))
colnames(delegates) <- c("Clinton", "Sanders")
{% endhighlight %}

We can plot these against each other and see how well we do!
This is using log-odds (more on that at later date).
The more positive the number, the more the state is in support of Clinton and vice versa. 0 is perfectly equal. Above the line means Clinton is exceeding expecations, below Sanders, regardless of who "won" the state.


{% highlight r %}
expectations_logodds <- log(expectations[ ,"Clinton"]/expectations[ ,"Sanders"])
delegates_logodds <- log(delegates[ ,"Clinton"]/delegates[ ,"Sanders"])

plot(expectations_logodds, delegates_logodds,
     xlab = "Expectations", ylab = "Results",
     type = "b", col = "blue",
     xlim = c(-1,1), ylim = c(-1,1))
abline(a=0, b=1)
{% endhighlight %}

![center](/../figs/2016-02-10-expectations-v-actual/unnamed-chunk-3-1.png)

This is interesting since it shows that Sanders is winning (points are y-negative), but is also shows that, at this point, Clinton is meeting or exceeding expectations. This disagrees the mainstream media narrative, unfortunately these narratives (apparently) have some influence on the future primaries, so we'll see.
Another interesting thing that this might shed some light as to if momentum really exists.