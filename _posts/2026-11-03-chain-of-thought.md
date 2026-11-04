---
layout: post
title: "What I've learned about Chain-of-Thought reasoning"
lang: en
---

Chain-of-Thought prompting is one of those ideas that sounds obvious in retrospect: if you ask a model to think step by step, it performs better on complex tasks. But the more time I spend with it, the more nuanced it becomes.

## Why it works

The intuition is that reasoning out loud forces the model to commit to intermediate steps. Each step narrows the space of plausible next steps, which reduces the chance of a coherent-sounding but wrong final answer.

There's also something interesting happening with attention. When a model generates its reasoning trace before the final answer, the answer can attend to that trace. It's not quite the same as human working memory, but it's not entirely different either.

## Where it breaks down

The failure modes are revealing. Chain-of-Thought helps most with problems that have clear intermediate structure — math, logic, multi-step planning. It helps less with problems that require a kind of tacit knowledge that resists being made explicit.

It can also backfire. A confident but wrong reasoning trace can lead a model further astray than no reasoning at all. The model's commitment to its own logic is both its strength and its weakness.

## What I'm exploring next

I'm currently looking at whether there are reliable signals in the reasoning trace itself that predict when the final answer will be wrong. The hypothesis is that certain patterns — circular reasoning, unsupported jumps, excessive hedging — correlate with errors in ways that could be detected automatically.

Early results are promising, but the base rates make it tricky.
