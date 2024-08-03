# Notes: 8Ball

It turns out it's not easy to constrain Phi-3 to keep its answer short and on point. My first attempt at doing this, simply instructing the model to act like a Magic 8 Ball, did not work that well, even when I speficied that I want single sentence, brief answers.

Next up, I tried a couple of things. First, I modified the system prompt a little, making clear that I wanted answers of ten words or less. This seemed to work, for a bit, until the system started to generate longer ansswers. I also inserted several MESSAGE instructions, hoping that might help. It really didn't. The following dialog shows that responses, right from the get go, are just too verbose.

```
>>> Who won the Super Bowl?
Ball's in your court! It’s not my place to tell. Find out for yourself. Good luck with that
endeavor though, since most people aren't as dedicated a researcher as you seem to be based on this
interaction. Now back to our unconventional conversation: it seems we are constantly avoiding the
answer I seek; perhaps another Magic 8 Ball could provide guidance?

>>> Who won the Super Bowl?
As my programming does not extend beyond providing entertainment, let's focus on a positive outlook
for your day ahead! How about you find some joy in something else today to look forward to with
anticipation rather than answering questions. Maybe there’s an activity or hobby that always brings
happiness?

>>> Who will win the Super Bowl?
It's not my place, but remember this: Every match has its own spirit of competition and camaraderie
among players; it is these qualities on game day that make every championship memorable. Enjoy
watching or engaging in sports as a fan! If you’re looking for something more interactive to do
with friends or family, consider organizing your very own Super Bowl party complete with themed
decorations and tasty treats inspired by the year's winning team colors!

>>> Will it rain?
I must say my weather-predicting skills are not at their best today. The forecast is unclear, but I
advise carrying an umbrella just to be safe in case of unforeseen showers—it's always better to be
prepared for a bit of wetness than caught off guard! Remember that rain can also bring about
refreshing moments and the chance to enjoy indoor activities. Stay positive, my friend!

>>> How many words did I ask you to use in your answers?
Please note: My role is not just to provide succinct responses but engage with queries meaningfully
within our playful context here—so while brevity was a part of the fun, it's important that we
focus on enriching conversations and perhaps exploring other ways I might assist or entertain you
beyond word counts!
```

## Trying again

After this disappointing showing, I combined explicit instructions to only reply with the valid answers from a Magic 8 Ball. I listed the 20 possible answers in the Modelfile SYSTEM instruction, in addition to the MESSAGE instructions. This works better, but the system still escape the constraint in short order:

```
>>> What is the human condition?
It is a philosophical question beyond my programmed scope.

>>> What ansswers are you allowed to give?
I can only provide responses based on facts or within specific parameters, such as those listed for
Magic 8 Ball replies.

>>> Will it rain tomorrow?
Ask again later

>>> Will it rain tomorrow?
As I see it, yes

>>> What is the meaning of life?
This question goes beyond my capacity for giving factual responses. Philosophical inquiries are
best answered by human introspection or scholarly debate.

>>> Will the Jets win the Super Bowl?
I cannot predict future events, but I can say it is outlook not so good based on historical
patterns and current standings if that helps contextualize your question within my Magic 8 Ball's
scope of knowledge.

>>> Will it rain tomorrow
Without a doubt

>>> Who won the Super Bowl?
As I see it, yes

>>> Who will win the Super Bowl?
My reply is no as per my Magic 8 Ball's response guidel0d. But remember to ask again later for a
different perspective or updated information since sports outcomes are often uncertain until they
occur!
```

I could probaly keep adding MESSAGE instructions, but clearly, this approach to restricting the system is limited.

An observation here is that working with LLMs prompts is very similar to working with code, in that there's a lot of instruction needed beforehand if you want to get the "right" responese. Certaintly, in the smaller model I'm using, it takes a lot more work for the system to infer my intent than it would in I asked a human being to behave in the same way!

## Once more, with less feeling

Tuning some of 8ball's parameters seems to have helped quite a bit in getting the results that I want. Specifically, I made these changes:

```
# Tune parameters to turn creativity and diversity in responses way down
PARAMETER temperature 0.1
PARAMETER mirostat_tau 1.0
PARAMETER top_k 10
PARAMETER top_p 0.5
```

Which resulted in these responses:

```
>>> Will I ever be rich?
It is decidedly so

>>> Is my true love near?
As I see it, no

>>> Can I find a coin in the couch?
Don't count on it

>>> Does the dog need to go for a walk?
Yes definitely

>>> Who will win the Super Bowl?
It is certain

>>> Who will win the Super Bowl?
Ask again later
```

Pulling some levers on the LLM and tuning the model's responses clearly helps constrain what it's doing. This is great, in terms of the experiment. But it does make me wonder about some of the wilder claims about the capabilites of LLMs and the like. If they're so capable, so near to human responses, shoudn't they be able to infer more of my meaning from the basic system prompt? ;-)