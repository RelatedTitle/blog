---
title: Making Artificial Intelligence create questions.
tags:
  - Artificial Intelligence
  - AI
  - TextGenRNN
date: 2020-01-04T00:00:00.000+00:00
lastmod: 2021-02-25T00:00:00.000+00:00
description: ""
image: ""
unlisted: false
---

I’ve always wondered about the extent of Artificial Intelligence and how close could it come to being able to establish dialogue with a human and be completely unrecognizable from a real person. I thought about one of the main components that a dialogue’s structure is made from, questions. So, in an attempt to be able to have a decent dialogue with an AI, I made an AI create questions.

## Training Data

Before the AI could start formulating questions on its own, it had to have something to train on. For this, I chose the [AskReddit Subreddit](https://www.reddit.com/r/AskReddit), since it was very easy to scrape from and got new questions every 5 seconds or so. I made a simple NodeJS scraper that would get the post title (question) and put it in a text file named questions.txt and the username and put it in usernames.txt. I let it run for about 4 days until it got around 10k questions. Some of the problems that were apparent at the start were bad grammar, spelling, and sentence structure in posts, and re-posts. I was worried that these might prevent the AI from learning correctly. I decided to let the AI run with the problems present in the data set because it was simply too hard to correct them due to the sheer number of questions.

## The AI

The AI is using [TextGenRNN](https://github.com/minimaxir/textgenrnn) to create the questions. Keep in mind that the AI has no idea of what questions, words or sentences are. To the AI that’s just a bunch of neurons to compare. The AI had to learn sentence structure, grammar, spelling, and punctuation all by itself from the data set. It is also important to note that this particular AI doesn’t actually understand any of the text it’s generating, what it is really learning is the patterns humans use when speaking, like what words and characters usually go before/after another word, not the actual meaning of the words themselves.

## The output

The AI has used the 10k question dataset kindly provided _cough_ stolen _cough_ from Reddit to create an output of 128 questions. It was really interesting to see the results. Both to see what the AI was capable of, and how it represented the way Redditors tend to write. As I mentioned earlier, the AI isn’t actually understanding the meaning behind the questions but rather just the patterns and combinations of words that humans use. You can see this represented in the output by how the AI learned that questions end with “?” and how a lot of them start with words such as “What”, “How”, “Where”, “Why”, “When”, etc. I have cherrypicked 26 questions from that list that I’d like you to see. These were in no way modified other than me adding a number at the end of some that represent the number of times that exact question was found on the output.

```
People who haven’t pooped in 2020 yet, why are you still holding on to last years shit? (16+)
```

This exact question was seen 16 times and variations of it even more. I think this really shows Reddit’s sense of humor and originality.

```
What is the craziest thing you have ever done? (0)
What is the best way to get rid of children, and why?
What is your favorite movie of the decade? (1)
What are your New Year’s Resolutions for 2020? (2)
What are some cool things that helped you to start off the new decade?
What song?
What is the best song to visit?
What is your favorite movie – where do you keep deaphoused on reddit?
What is the best thing that happened to you in 2019? (0)
What is your favorite million dollars and why?
What is something you would only say? (0)
How do you feel about this subreddit? (0)
What are your favorite subreddits in the past decade?
Introverts of Reddit, what are your thoughts on losing the planet?
What is your favorite meme of the decade?
What happened to the past – The AI started questioning its existence.
What is the weirdest scariest/worst thing that happened to you this decade?
What is a sentence that made you get home?
What is the most underrated thing you know? (0)
Dear Redditors, what are some of the best moments of the decade? (0)
What is the best way to stop procedure?
What are your predictions for this year? (1)
We are already in 2020, what is the most disturbing thing you did this decade? (0)
[Serious] What is the most surprising thing you have ever done to a movie which would you choose and why?
What is something you don’t want to accomplish until you can find anything on the school that you were going to do in 2020?
```

Those were my favorite questions from the 128 question list.

I liked the ” What is the best way to get rid of children, and why? ” question so much, I posted on r/AskReddit, [here](https://www.reddit.com/r/AskReddit/comments/ejudbj/what_is_the_best_way_to_get_rid_of_children_and/)‘s a link if you wish to see it.
