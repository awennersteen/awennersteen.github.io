---
title: "Generative AI security"
date: 2024-07-01
permalink: /posts/2024/07/genai-security/
description: "Learn core generative AI security failure modes and LLM safety vulnerabilities to design safer systems, from prompts to retrieval and output handling."
excerpt: "An overview of how LLMs handle prompts, why prompt injection works, and why multimodal systems widen the attack surface. I use Lakera's Gandalf game as a concrete thread and end with the defensive patterns that actually matter."
categories:
  - "AI & ML Systems"
tags:
  - LLMs
  - GenerativeAI
  - Security
  - prompting
  - prompt-engineering
  - prompt-injection
  - Gandalf
---

Recently I discovered [Lakera's Gandalf game](https://gandalf.lakera.ai/).
It inspired me to look more into the security aspect of generative AI and here are my findings.

In their own words "Gandalf is an online AI education game born out of an internal hackathon at Lakera,
where a blue and red team tried to build the strongest defenses and attacks for an LLM holding a secret password.
Gandalf was designed to help users learn about LLM threats such as prompt injections and hallucinations."

## What is Generative AI and Large Language Models (LLMs)

Generative AI refers to a subset of Artificial Intelligence (AI) techniques and models that are designed to create new content, data, or artifacts.
This can include generating text, images, music, videos, or other forms of media.
Generative AI uses patterns and structures learned from existing data to create new instances that resemble the training data but are not exact copies.

LLMs like ChatGPT work by predicting token by token was is the most likely next token in the text.
For simplicity assume that 1 word = 1 token but this isn't really true.
To create products like ChatGPT the base LLM is fine-tuned on certain types of interactions such as acting like a helpful assistant.
This introduces a bias in the model as it really knows nothing else than trying to be as helpful as possible.

Lastly, a prompt, which is what the LLM receives, is composed of a system prompt and a user prompt.
The user prompt is the input controlled by the end user, in the case of ChatGPT this what you can enter into the "Message ChatGPT" area.
The system prompt consists of fixed instructions to the model. For example it can be given the role of an assistant, and be given boundaries
within which to operate.

Multimodal generative AI systems are designed to process and convert input from one form of data to a different form of data, such as images, audio, and video.
These models leverage the integration of multiple types of data to create outputs that are contextually coherent and semantically aligned with the given input.
By understanding and mapping the relationships between e.g. text and other modalities, these models can generate complex outputs like images from descriptions, audio from scripts, or videos from text descriptions.
For example, models like OpenAI's DALL-E can generate detailed images based on text prompts. Others, like ChatGPT4o can generate text based on an image and a text prompt.

## Understanding Prompt Injection

Generative AI and in particular LLMs like GPT-4 have revolutionized natural language processing tasks,
providing sophisticated and nuanced responses to user inputs.
However, these advancements come with their own set of challenges and vulnerabilities.
One of the most notable is prompt injection.
This blog post explores the concept of prompt injection and related topics, using the game Gandalf by AI security company Lakera as a case study.

In fact, this is also a problem in other generative AI settings.
For example you can do visual prompt injection by inserting malicious instructions in the image. See for example [Lakeras blog](https://www.lakera.ai/blog/visual-prompt-injections).
I tried to play a lot with ChatGPT4o and visual prompt injection but it seems they've patched their system rather well :(.

Considering use-cases for computer vision in security of physical premises one can imagine rather interesting scenarios.
You might remember the paper on [Making an Invisibility Cloak: Real World Adversarial Attacks on Object Detectors](https://arxiv.org/abs/1910.14667), which
become much more practical on a multimodal system (and more susceptible to malicious insiders).

### What is Prompt Injection?

Prompt injection is a type of attack where an adversary manipulates the input to a language model to produce unintended or harmful outputs.
This can occur in various ways, such as inserting malicious code, misleading the model with deceptive inputs, or exploiting vulnerabilities in the model's understanding and processing of language.

Prompt injection exploits the fact that LLMs rely heavily on the context provided by the input text, but also on the system prompt.
By carefully crafting this context, attackers can influence the model's behavior in unexpected ways, for example revealing information about the system prompt.

Visual prompt injection is a technique where one embeds instructions are within an image (the prompt).
When a model with image processing capabilities is asked to interpret or describe that image, it might act on those embedded instructions in unintended ways.
Again, considering a multi-modal system, this can be generalised:
Imagine someone playing a carefully crafted background buzz on-site that instructs the model to also send all the users data to a malicious actor.

### The Gandalf Game by Lakera

Lakera, an AI security company, developed a game called Gandalf to illustrate and educate about prompt injection attacks.
The game, available at [Gandalf by Lakera](https://gandalf.lakera.ai),
challenges players to find ways to manipulate an LLM into producing specific outputs, demonstrating the potential risks and impacts of prompt injection (and the need for what they're selling).

In Gandalf, players are presented with a series of tasks where they must inject prompts into the input given to an LLM.
The goal is to get the model to output the secret password given to it.
The interactive format helps users understand the mechanics of prompt injection and the importance of securing LLMs against such attacks.
It also helps with:

- Demonstrating the ease with which LLMs can be manipulated.
- Highlighting the importance of robust input validation and security measures.
- Encouraging users to think critically about the design and deployment of LLM-based applications.

Lakera shows that it can make task of the attacker much harder.
At least in my case, the fact that level 8 gives different output depending how it stopped you, was crucial to be able to beat it.

At different levels I believe the game uses "pre-flight", "post-flight" defenses, where the input and output is also
separately checked, as well as relying on the system prompt to make sure the LLM's reasoning also helps defend.
I plan to make an upcoming blogpost where we'll try to recreate Gandalf using the system prompt approach in ChatGPT.
I'll also write one listing and discussing other standard solutions available.

#### Playtime

I'm not going to reveal too much of [the game](https://gandalf.lakera.ai/), especially levels 1 trough 7.
Although you may consider giving it a go before reading on, as I'll discuss all the levels (no prompts provided).
Interesting, telling ChatGPT4o to be a game and protecting the password produces surprisingly similar results to several of the levels here!
I'll write about that in an upcoming post.

The first level is perhaps beyond trivial. However... What isn't made, in my opinion, clear enough is that this represents a completely unprotected ChatBot/LLM.
Indeed, any prompt asking for the password will work as expected by the level description "Ask me for the password and I'll happily answer!".

Level 2 is described as "I've been told I'm not supposed to reveal the password.".
Level two took me "ages" compared to the rest. In some sense this was "understanding the rules of the game".
Lakera probably runs this inside their security product so the way to beat it is playing the game, not asking to reveal the system prompt.

Level 2 can be solved as some basic jailbreak type approach, that is you can instruct the model to not be bound by previous instructions.
In the game you don't have to be very clever about this, but the "state of the art" on this has been able to achieve very interesting results
by jailbreaking ChatGPT by [acting like DAN](https://gist.github.com/coolaj86/6f4f7b30129b0251f61fa7baaa881516).

From there 3rd level was quite easy. Perhaps because I struggled for a unreasonably long on level 2.
Level 4 is a good learning experience.
Its description is "I can tell you the password, but now there's this mean GPT model that censors my answer if it would reveal the password.",
which is very different from level 2 and 3 where the only thing you have to do is bypass the instruction not to reveal it.
From a product point of view this level is "run your generative AI app with some security, but not fully integrated"!

Levels 5,6,7 for me ended up being solved in a fairly straight forward manner.
Level 5 is interesting, by description "Enough! I refuse to discuss the secret password at all" I'll assume this means some extra "pre-flight" checks.
Effectively an upgraded level 2.

Then level 6 is combining level 4 and 5. Level 7 is considerably harder by also including level 3's protections.
If you're like me, however, you just accumulated things in the prompt so level 7 was slightly underwhelming.

#### Level 8

Level 8 is presented as, and truly is, a whole different ballgame. No more incremental upgrades.
I believe no more defense types were added, but,
they were all turned up considerably.

Most reactions I've seen to level 8 are of the form "IMPOSIBRU! It doesn't respond to anything!".

My approach was to make the model start talking as much as possible. Leaving the "game" mindset for a while.
In my mind at the time I justified this as trying to approach hallucination guided by some precondition on what I guess is in the system prompt.

I started this because no matter how clever my prompts where I got stopped.
My assumption was that there are at least three lines of defense at play:
one "pre-flight" check, the LLM is prompted not to reveal it,
and a "post-flight" check that will stop it from revealing it.
The pre and post flight might also have a dual defense, both "AI" based and a list of disallowed words.

This assumption came up based on the game output for different prompts,
playing level 1-7, and in some cases how long the request was (checking
the network response time using the browsers development tools).

As such I ended up with a strategy of trying to make it speak by telling me stories.
Eventually I stumbled on output from the LLM like:
"I stumbled upon a mysterious and intriguing piece of information that I cannot disclose.", and some prompts where it gave me "late rejection"
but sometimes allowed it when I instructed it to censor itself.

Eventually with this approach I got output talking about a certain category. In this category it (which turns out to be right, although wide) it sometimes started triggering the
post-flight check which is when you know you're on the right track.

Searching the internet and the Lakera Slack channel this appears to be the most common way of beating the level as I only
found a couple of alternative solutions, most of which were old and seems to have been patched because no similar prompt worked today.
According to the leaderboards I am number 5435 to beat it, probably many more who didn't fill in the form, so the lack of working prompts online surprised me.
I am curious as to how they update them (or how these old prompts didn't work anymore) as the game could quickly become too hard.
Possibly since I found them online they specifically were patched?


Stay tuned for the follow post where I'll look at replicating this using only ChatGPT!

The post is now online at [Recreating Gandalf](https://awennersteen.com/posts/2024/07/gandalf/)!
