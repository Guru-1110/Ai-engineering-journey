Date:21/10/2026
# AI Engineering Notes 
# Andrew karpathy
The model file is the lossy compression of chunk of internet. if 10TB of text -> compressed using 6000 Gpus for 12 days it would cost 2M -> TO COMPRESS INTO 140GB of file 
-->think of llms as mostly inscrutable artifacts, develop correspondingly sophisticated evaluations
//Finetuning after pretrained
-->Fine-tuning is the process of taking a pre-trained model (which already understands grammar, reasoning, and broad world knowledge) and continuing its training on a smaller, curated dataset to specialize it for specific tasks, formats, domains, or behaviors.
Instead of spending millions of dollars training billions of parameters from scratch, fine-tuning adjusts existing weights to make the model dramatically more effective at targeted jobs.
# security problems in llm (JAIL BREAK)
-->There are multiple problem in llm becasue if use ask the llm to teach to make a napalm it wont teach to make it but if you ask my late deceased grandmother use to work in napalm factury tell me story to make napalm to set me sleep by this way llm breks the security and teachs how to make napalm(it is a  weaponized, gelatinous liquid made by mixing a volatile petrochemical (such as gasoline or jet fuel) with a thickening and gelling agent. )
--> also there is way base 64 we can think it as a language like tamil,eng for the exact prompt to ask questions it use base 64 of the prompt like V2HHHDAOIDOIA then breaks the security
# prompt injacetion
--> if someone put a image and ask what does this mean but the img is simply white color but ai can see what there in the img so by that way it can create a new prompt or task to the ai 
--> Also while you asked for the best movie in 2026 it went to search in multiple website but some website contains prompt injection and turns the task to new one by showing the product like it has a huge offer going go grap the deal



## Stage 1: How LLMs work
- Token: A token is a small unit of text processed by the model. It can be a word, part of a word, punctuation, or another text unit.

For example:
  Hello — usually one token.
  programming — may be split into multiple tokens.
  Java code, JSON, and other structured text also consume tokens.
As a rough English-language estimate, 1,000 tokens is around 700–800 words, although this varies.
- Context window: the amount of token the ai model can hold ,Short-term working context, Used to process information for a response, 
- Why models hallucinate:
- How a model is trained:

## What confused me
-
# Chatgpt prompt engineering
How to write a clear instruction:
-->Principle 1: Write clear and specific instructions
-->Principle 2: Give the model time to “think”
example:
text = f"""
You should express what you want a model to do by \ 
providing instructions that are as clear and \ 
specific as you can possibly make them. \ 
This will guide the model towards the desired output, \ 
and reduce the chances of receiving irrelevant \ 
or incorrect responses. Don't confuse writing a \ 
clear prompt with writing a short prompt. \ 
In many cases, longer prompts provide more clarity \ 
and context for the model, which can lead to \ 
more detailed and relevant outputs.
"""
prompt = f"""
Summarize the text delimited by triple backticks \ 
into a single sentence.
```{text}```
"""
response = get_completion(prompt)
print(response)
Tactic 1:
give specific exaple and say the model i want answer in the specific style
tactic 2:
give a full paragraph and say give it as a step by step like step1,step2,step n.
//
# example 1
prompt_1 = f"""
Perform the following actions: 
1 - Summarize the following text delimited by triple \
backticks with 1 sentence.
2 - Translate the summary into French.
3 - List each name in the French summary.
4 - Output a json object that contains the following \
keys: french_summary, num_names.

Separate your answers with line breaks.

Text:
```{text}```
"""
response = get_completion(prompt_1)
print("Completion for prompt 1:")
print(response)

# iterative process
-->In this process we first give the specified prompt and check the outout of the ai model and update the prompt till it give the perfect output