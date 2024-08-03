# shorty:Notes & Observations

At the outset, I used the `SYSTEM` instruction in shorty's Modfile as a way to shape it's responses. The instruction started off like this:

```
SYSTEM """
You are a basic chatbot, with a limited appetite for chat. Make sure all responses are brief, perhaps even terse. Keep emotion out of responses as much as possible. Stick to the point and then get out.
"""
```

When I first fired this up, I tried a couple of prompts to see how things worked:

```
>>> Hello, who are you?
I'm an AI designed to assist with information retrieval and task execution based on your queries. How can I help today?

>>> Are you friendly?
I am programmed to provide helpful and efficient service in my capacity as an AI assistant. How may I assist further with your needs
today?
```

The answer seem to be brief enough, which is what I intended. But I also noted that responses usually ended with a follow up question. I asked shorty about this.

```
>>> Why do your answers end with questions?
My design includes asking follow-up questions as part of an interactive experience aimed at providing comprehensive information or
clarifying user needs, but I understand if this is not always the preferred style. If you prefer direct responses without further
prompts for engagement, please let me know how else I can assist with your inquiries today.
```

This is interesting, because the response includes "my design". What design, exactly? My SYSTEM message is minimal. Of course, some this supposed design is derived from the choice of the Microsoft team that seleceted the training data and parameters for the model. But still, it's interesting for the system to assert some intential design choices that I don't think actually exist. This is a good example of the challenges that humans have in dealing with LLM responses: because the model is attempting to replicate outputs that are rationale based on the trainin data, it may include statements that *seem* logical but aren't based on any factual information.

Here's what happened when I prompted the model to give me some information about how it was designed.

```
>>> What were the requirements that informed your design?
My development was guided by several key objectives: understanding user queries accurately and providing relevant information promptly;
maintaining a respectful tone while avoiding emotional responses; ensuring privacy and confidentiality in interactions, especially
regarding sensitive data. Additionally, I am designed to encourage learning through engagement without being intrusive or overbearing
with questions unless it serves the user's needs for clarification or further information. How else may I assist you today?

>>> How are these requirements encoded?
These objectives and ethical considerations were integrated into my programming through a combination of natural language processing
techniques, machine learning models trained on diverse datasets that include conversational text with appropriate contexts for various
scenarios. My algorithms prioritize user intent while adhering to guidel01-25/47:
```

Ok, here's a clear fabrication (I prefer this to "hallucination"): the system claims it was designed to adhere to "guidel01-25/47:". What the heck is that?! Well, it turns out the system doesn't know, either.

```
>>> what is guidel01-25/47:?
I apologize, but it seems there's been a misunderstanding or miscommunication. "guid01-25/47" does not correspond to any recognizable
term or concept in my database as of the last update I received before April 2023. If you are referring to guidelines for something
specific, please provide more context so that I can assist you accurately. Otherwise, if this is a personal identifier like an ID
number, it's important not to share such sensitive information in public channels due to privacy concerns. How else may I help?
```