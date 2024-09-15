
**Before you read further**: There is already a very comprehensive prompting guide available [here](https://www.promptingguide.ai/) from Elvis Saravia on GitHub. If you want an exhaustive intro with more details, check that out! I make frequent references to that guide below. **My notes here borrow extensivley from this guide**, because it's great!

# What is a prompt?

**A prompt is the *input* to a Large Language Model (LLM)**. The prompt guides the LLM's output (often called a *response* or *completion*).

```mermaid
flowchart LR;
    P(Prompt)-->L(LLM)-->R(Response / Completion);
```

**The prompt is your primary means of guiding the behavior of the LLM**, so building safe, effective prompts is a vitally important task. The process of building effective prompts is sometimes called *Prompt Engineering*.

# What is Prompt Engineering?

[Prompt engineering](https://en.wikipedia.org/wiki/Prompt_engineering) is a collection of techniques for building effective prompts for [Large Language Models](https://en.wikipedia.org/wiki/Large_language_model).

Prompting is a powerful way to adjust a model's behavior to fit your use-case, without the need to make any changes to the model itself.

## Why prompt engineering?

What makes prompt engineering such a popular technique for working with LLMs?

- Cost: compared to training a new LLM or fine-tuning an existing one, prompt engineering is a low cost solution
- Simplicity: prompt engineering can be done without machine learning or coding expertise
- Flexiblity: prompt engineering can be used to adapt existing (open source or commercial) models to a new use case
- Speed: prompt engineering is much faster than training a new model or even fine-tuning an existing one

**Bottom line:** prompt engineering is simpler, faster, and cheaper than the other techniques available to change the behavior of LLMs.

## Prompt structure

[This page](https://www.promptingguide.ai/introduction/elements) has an excellent breakdown of the key elements of a prompt.

The core elements of a prompt are:

1. Instruction: The specific task we want the model to perform.
1. Context: More information about the context of the task, to help the model produce better output.
1. Input data: The input to the prompt. This could be input we insert programmatically or it could come from an end-user.
1. Output Indicator: the type or format of the prompt output.

Let's build an imaginary prompt that includes all these components (we will block off sections with tags `<like this>`, to make it easier to understand the structure:

```xml
<instruction>
Classify the text into neutral, positive, or negative
</instruction>

<context>
You are a marketing agent looking at customer's reviews of a restaurant, and evaluating customer sentiment
</context>

<input-data>
Input: {user_input}
</input-data>

<output>
Sentiment: 
</output>
```

Just imagine that the `<tags>` are not actually present, and you've got the basic idea (although some models *do* allow you to explicitly structure your prompts using XML! Anthropic's [Claude](https://docs.anthropic.com/claude/docs/use-xml-tags) models allow this, for example).

If we replace `{user_input}` with a restaurant review like `The food was just OK`, the model should respond with a classification. In this case, `Neutral` would probably be an acceptable response.

### How much does the format matter?

Short answer: **a lot**. The size (number of parameters) and type of a model will have a significant impact on how the model responds to a prompt. The same prompt can get very different inputs from different models, and switching from one model to another will nearly always require adjusting your prompt.

Most LLMs also care about **the order of information in the prompt itself**. [This paper]((https://arxiv.org/abs/2307.03172).) shows that **LLMs typically pay more attention to information from the *beginning* and *end* of the prompt**.

**Tip:** Always follow the model creator's guidelines for prompting. Most LLM providers have a set of best practices which should be followed:

- [Anthropic Prompt Engineering Guide](https://docs.anthropic.com/claude/docs/prompt-engineering)
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)

## Prompt engineering methodology

Prompt engineering can seem both overwhelming and very subjective. Are there any general principles we can use to improve prompt quality?

**Yes**. One of the most popular frameworks at present is COSTAR:

- **C**ontext: Information about the task we are asking the LLM to do, and how it should be done.
- **O**bjective: The purpose (goal) of the request. For instance, we might want to solve a coding issue, or craft a blog post.
- **S**tyle: The style of writing the LLM should use, for example "technical" or "creative".
- **T**one: The tone of the LLM's output, for instance "casual", "friendly", or "professional".
- **A**udience: Context about the people people the LLM is producing output for.
- **R**esponse: The end goal the model should be striving for (for example "accurate" or "relevant" answers)

```xml
<context>
Help create a Facebook post about the benefits of gardening. The focus should be on the health benefits of growing your own food and the psychological benefits of creating a gardening routine
</context>

<objective>
Create a post for me about growing tomato plants from seed in an indoor setting using instructions that even a beginner can follow.
</objective>

<style>
Use a friendly, engaging writing style.
</style>

<audience>
The audience is people who are new to gardening but are interested in sustainable living, and health and wellness.
</audience>

<response>
The format should be an accurate, engaging Facebook post.
</response>
```
Without the `<tags>` removed, here is a response from Anthropic's Claude 3 Opus model:

```
🌱🍅 Discover the Joys of Growing Tomatoes from Seed Indoors! 🌿🏡

Are you curious about starting your own indoor tomato garden but not sure where to begin? Look no further! Growing tomatoes from seed is a rewarding and fun experience that anyone can enjoy, even if you're new to gardening. 🌱

Here's a simple step-by-step guide to get you started:

1. Choose your tomato seeds. There are many varieties available, so pick one that suits your taste and growing conditions. 🍅
2. Fill small pots or seed trays with a well-draining seed starting mix.
3. Plant the seeds about 1/4 inch deep and gently cover them with soil.
4. Water the soil until it's moist but not soggy, and place the pots in a warm, sunny spot or under grow lights. ☀️
5. Keep the soil moist and wait for the seeds to germinate, which usually takes 7-14 days.
6. Once the seedlings have grown a few inches tall and have their first set of true leaves, transplant them into larger pots.
7. Continue caring for your tomato plants by watering them regularly, providing plenty of light, and fertilizing them every few weeks. 💧

Not only will you enjoy delicious, homegrown tomatoes, but you'll also reap the many health benefits of gardening! Studies show that gardening can reduce stress, improve mental health, and provide gentle physical activity. 💪😊

Plus, by growing your own food, you'll know exactly what goes into it and can enjoy the freshest, most flavorful tomatoes possible. 🍽️

So why not give indoor tomato gardening a try? Share your experiences and photos in the comments below, and let's inspire each other to cultivate a healthier, more sustainable lifestyle! 🌍💚

#IndoorGardening #TomatoesFromSeed #HealthyLiving #SustainableLiving #GardeningForBeginners
```

Note that the model provided the emojis, engaging title, and hashtags all on its own. Compare that to the output below, which was generated from the barebones prompt `Create a facebook post about growing tomato plants indoors`:

```
🍅🌿 Attention all gardening enthusiasts! 🌱

Have you ever wanted to enjoy fresh, juicy tomatoes year-round? Well, I've got great news for you! Growing tomatoes indoors is easier than you might think, and it's a fantastic way to have a constant supply of this delicious fruit. 🍅

Here are a few tips to get you started:

1. Choose the right variety: Opt for smaller, compact tomato plants that are well-suited for indoor growth, such as cherry or plum tomatoes. 🍒

2. Provide plenty of light: Tomatoes need at least 6-8 hours of direct sunlight daily. If you don't have a sunny window, consider using grow lights to ensure your plants receive enough light. ☀️💡

3. Maintain the right temperature: Tomatoes thrive in temperatures between 65-85°F (18-29°C). Keep them away from cold drafts and air conditioning vents. 🌡️

4. Water and fertilize regularly: Keep the soil consistently moist but not soggy, and fertilize your plants every two weeks with a balanced, water-soluble fertilizer. 💦🌿

5. Support your plants: As your tomato plants grow, provide them with a stake, cage, or trellis for support. This will keep the fruits off the ground and improve air circulation. 🪴

Growing tomatoes indoors is a rewarding experience that allows you to enjoy fresh, homegrown produce no matter the season! 🥗 If you have any tips or success stories about indoor tomato gardening, share them in the comments below! 👇

Happy gardening, everyone! 🌿😊

#IndoorGardening #TomatoPlants #GrowYourOwn #GardeningTips #FreshProduce
```

Still OK, but note that the prompt does not include specific, targeted information about physical and psychological benefits of gardening, and the instructions are not beginner friendly.

## Approaches to prompting

Beyond ensuring the prompt includes enough detail (by using a framework like CO-STAR), there are also some approaches to prompting that can give the LLM additional context about what we want it to do.

### Zero-shot prompting

A zero-shot prompt does not include any examples of the required response. The prompts we created above using CO-STAR were zero-shot prompts: we did not include any examples of the expected output.

Zero-shot prompts are **simple to implement** and **cost-effective**. We use a single, relatively short prompt to produce a single output from the LLM. This reduces our token count, which means we pay less.

However zero-shot prompts can be *hard to get right* and can produce **less precise** outputs.

Of course, one way to make an LLM better at zero-shot prompts is by fine-tuning it, as documented [in this paper](https://arxiv.org/abs/2109.01652).

Commercial models like GPT 4 also use RLHF (reinforcement learning with human feedback) to improve performance on zero-shot prompts, as documented [here](https://arxiv.org/abs/1706.03741).

### Few-shot prompting

Few-shot prompts include one or more examples of the model's expected output.

Many LLM creators recommend always using few-shot prompting, because it helps guarantee appropriate output from the model.

However, **more work is needed** to craft the prompt (we must decide what examples to include), and **costs will be higher** as the prompt is longer (and therefore contains more tokens, which will lead to higher costs when calling an LLM API that charges per-token).

Key papers, source from [this page](https://www.promptingguide.ai/techniques/fewshot):

- [LLaMA: Open and Efficient Foundation Language Models](https://arxiv.org/abs/2302.13971)
- [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)
- [Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165)
- [Rethinking the Role of Demonstrations: What Makes In-Context Learning Work?](https://arxiv.org/abs/2202.12837)

### Chain of Thoughts prompting (CoT)

This type of prompting helps models to perform complex reasoning through intermediate reasoning steps.

This improves performance on "common sense" reasoning tasks, as well as symbolic and mathematical reasoning.

Some models have specific features to enable this. **Claude** has a [set of xml tags](https://docs.anthropic.com/claude/docs/let-claude-think), that allow you to see the model's reasoning when it responds to CoT prompts:

```xml
<thinking>The model's thinking will appear here</thinking>
<answer>The model's answer to the end-user will appear here</answer>
```

This can be useful when building a new CoT prompt. Related papers:

- [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903), borrowed from [this page](https://www.promptingguide.ai/techniques/cot)
- [Large Language Models are Zero-Shot Reasoners](https://arxiv.org/abs/2205.11916)

### Variation: Zero-shot CoT

A technique that sometimes works on larger models is simply prompting the model to think out its response. Phrases like "let's think step by step" can prompt some models to carry out a chain or reasoning on their own.

### Variation: Auto-CoT

Another interesting approach proposed in the paper [Automatic Chain of Thought Prompting in Large Language Models](https://arxiv.org/abs/2210.03493), is to generate examples for few-shot CoT prompts automatically using "think step by step", then filtering or selecting reasoning examples from the resulting outputs. The code from the paper can be found [here](https://github.com/amazon-science/auto-cot).

### Few-shot with intermediate steps

This approach lets you combine Chain-of-Thought with few-shot. The model can "review" information before answering.

This can be very helpful when generating code (SQL, JSON). This can be a weak spot for many LLMs because the formatting requirements are so strict.

More information on few-shot prompting can be found [here](https://www.promptingguide.ai/techniques/fewshot).

