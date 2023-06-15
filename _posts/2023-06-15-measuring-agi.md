---
layout: post
title: "How do we measure AGI?"
description: ""
author: miroojin
tags: [agi]
llm_examples: ["/assets/images/llm_1.png", "/assets/images/llm_2.png"]
---

## Introduction

---

**L**arge **L**anguage **M**odels have taken the internet by storm and their magical capabilities have sparked a conversation about AGI and its near imminence.
Many individuals believe that LLMs have the potential to pave the way for the development of systems with general intelligence, mostly because they have demonstrated a striking ability to perform a variety of complex cognitive tasks that were not even foreseen by their creators. Moreover, LLMs are capable of accomplishing these tasks with minimal or no training examples.

<div style="display:flex;justify-content:center">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">All the best examples of GPT-4, from OpenAI:</p>&mdash; Ben Tossell (@bentossell) <a href="https://twitter.com/bentossell/status/1636003418144915457?ref_src=twsrc%5Etfw">March 15, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

This ability to be able to understand and perform a wide range of unforeseen tasks in different environments with minimal or no guidance might be one of the most important capabilities that can be engineered into AI systems. It is also the most common interpretation of general intelligence. But general intelligence is a really hard ability to measure. As the developer of an AI system, you cannot predict your system’s performance on unfamiliar tasks in unknown environments using the conventional black box testing approaches, commonly used in AI model evaluation. As a shallow proxy, we base our assessments on the system’s ability to do things that are cognitively challenging for humans. But this approach has been [infamously misleading](#misleading-tests){:.footnote-link}, primarily due to our anthropomorphic bias. What is challenging for us might not be challenging for machines. Achieving impressive results on cherry-picked tasks is no guarantee of an agent possessing human-level general intelligence. LLMs serve as the most recent testament to this principle.

The potential of general-purpose systems is virtually limitless, they possess capabilities that extend beyond their original intended applications. Human beings are prime examples of systems exhibiting general-purpose intelligence. It is therefore understandable why many individuals and organisations aspire to develop AI systems that can match the level of general intelligence observed in humans. But before we make any progress towards developing these systems, we need to have a clear and precise understanding of _general intelligence_ so that we know what we’re working towards and more importantly, come up with a comprehensive and reliable set of benchmarks and tests that can measure general intelligence in AI systems.

## What, exactly, are we measuring?

---

> _"Viewed narrowly, there seem to be almost as many definitions of intelligence as there were experts asked to define it."_ - Robert Sternberg

The definition of general intelligence is as elusive as its conception. The only point of reference we have for general intelligence is the observed manifestation of biological intelligence in humans and animals, which itself is hard to qualify. We seem to possess an intuitive notion of what intelligent behavior looks like while watching our favorite detective show or raising a child, but when pressed for a precise definition, we find ourselves at a loss for words. This difficulty arises from the fact that general intelligence is not an inherent, standalone property of systems; rather, it _emerges_ from intricate interactions among diverse cognitive processes, neural mechanisms, and the environment. Trying to understand and describe this soup of complexity is a highly ambitious endeavor, particularly considering our current limited understanding of biological intelligence.

A more practical approach would be to try and describe general intelligence as a collection of different emergent capabilities that turn out to be really useful for solving problems in complex environments. I'm going to try and narrow down on capabilities that are both broadly applicable across different problem domains and can be adequately quantified.

<div align="center" markdown="1">### General intelligence abilities
</div>

  <div class="post-card-list">
    <div class="card">
      <span class="header">Task versatility</span>
      <hr />
      <p class="body">
        Task versatility is the ability to perform effectively on a wide range
        of different tasks. The ability can be evaluated by testing the
        system on a diverse set of benchmarks that cover various problem
        domains.
      </p>
    </div>
    <div class="card">
      <span class="header">Learning efficiency</span>
      <hr />
      <p class="body">
        Learning efficiency is the ability to learn effectively and rapidly from
        a given set of data or experiences. It measures how well the system can
        acquire knowledge or skills with minimal resources, such as training
        data, computational power, or time.
      </p>
    </div>
  </div>
  <div class="post-card-list">
    <div class="card">
      <span class="header">Transfer Learning</span>
      <hr />
      <p class="body">
        Transfer learning is the ability to efficiently reuse prior knowledge, aiming
        to reduce the amount of training data, computational power or time required for learning new
        tasks.
      </p>
    </div>
    <div class="card">
      <span class="header">Adaptability</span>
      <hr />
      <p class="body">
        Adaptability is a system's ability to modify its behavior and enhance its performance in response to new data or changing situations. One way to evaluate adaptability is by comparing a system's performance before and after exposure to new data or changing environments.
      </p>
    </div>
  </div>

It's pretty evident that humans are great at all of these abilities. We should strive to create systems that can match a human's performance along these dimensions.

## Interesting approaches

---

Given that we have recently started transitioning from narrow AI to more general AI systems, there hasn't been a lot of emphasis on benchmarking general AI till now. Nevertheless, a few interesting approaches have surfaced, which are worth exploring.

### [The Abstraction and Reasoning Corpus (ARC)](https://lab42.global/arc/)

The ARC dataset, created by [Francois Chollet](#fchollet){:.footnote-link}, is a set of tasks that are intended to serve as a benchmark for measuring learning efficiency. The task format is very simple: There are one or more sample demonstrations in which a grid of colored pixels is transformed into a new grid. The agent has to infer the abstract transformation rule from the demonstrations and apply it to a test input grid.

{% include image.html url='/assets/images/arc.png' description='A sample task where the implicit goal is to find the most common shape in the input grid' %}

Each task contains very few sample demonstrations, which means the agent has to learn the grid transformation rule by looking at a few examples only. According to Chollet, this ability to learn to solve complex tasks from a few demonstrations is a key feature of general intelligence. Since the ARC dataset is fully solvable by humans, Chollet claims that any agent that is able to achieve human-level performance on the benchmark should be able to perform a wide range of tasks of a kind that would normally require human-like fluid intelligence.

### [The Hutter Prize](http://prize.hutter1.net/)

The Hutter Prize is a cash prize funded by [Marcus Hutter](#mhutter){:.footnote-link}, which rewards data compression improvements on a 1GB Wikipedia dataset to encourage research in AI. Hutter believes that a good compressor will intelligently have to find regularities in data which is an intrinsically hard problem.

According to Hutter, for an agent to make optimal predictions in any environment given a set of prior experiences to learn from, it needs to model (compress) the experiences into the [smallest possible summary](#mdl){:.footnote-link}. This principle is akin to Occam's razor which is a problem-solving guideline that recommends selecting the simplest possible explanation for any phenomenon.

Hutter also claims that the best text compression algorithms would be the ones that _understand_ the text in the same way that humans would. The better you understand the data, the more you can delete pieces from it while compressing and reconstruct the missing pieces while decompressing.

For example, consider the missing words in the following sentence:

> _Deep learning <ins>&nbsp;&nbsp;&nbsp;[1]&nbsp;&nbsp;&nbsp;</ins> a subfield of <ins>&nbsp;&nbsp;&nbsp;[2]&nbsp;&nbsp;&nbsp;</ins> learning that involves the use <ins>&nbsp;&nbsp;&nbsp;[3]&nbsp;&nbsp;&nbsp;</ins> artificial neural <ins>&nbsp;&nbsp;&nbsp;[4]&nbsp;&nbsp;&nbsp;</ins> to model and understand complex patterns and representations._

Someone who understands English can easily guess that [1] = **is** and [3] = **of**. Furthermore, an expert on AI would guess that [1] = **machine** and [4] = **networks**. This shows that the better you understand the text, the more you can delete pieces from it without loss. If a compression algorithm matches the reconstruction capabilities of a human, it should be regarded as having the same understanding.

### Simulated environments

Simulated environments have been the de-facto way of testing reinforcement learning algorithms. People have come up with different plans for measuring the generalization power of RL agents in simulated environments - by [procedurally introducing stochasticity](#procedural-envs){:.footnote-link}, [evaluating across a diverse range of environments](#diverse-envs){:.footnote-link}, and modeling environments around [real-world domains](#real-world-envs){:.footnote-link}.

### Crowd-sourced benchmarks

When it comes to quantitatively measuring the generalization power of AI systems, the ability to handle unforeseen tasks becomes a crucial aspect to evaluate. Traditional AI benchmarks, which typically focus on evaluating performance within a static set of skills, are not of much use in this regard.

A better alternative would be crowd-sourced benchmarks such as [BIG Bench](https://github.com/google/BIG-bench) and [OpenAI's evals](https://github.com/openai/evals), which are more diverse and dynamic in nature compared to traditional benchmarks. These benchmarks introduce a wide range of failure modes that challenge the system’s adaptability.

A key factor for the success of crowd-sourced benchmarks is that they have enough people contributing to them regularly with a stream of diverse and high-quality tasks.

### Evolving learning environments

One way of introducing novel tasks for a system to solve is to design dynamic learning environments and problem domains that evolve along with the
the capabilities of the system. These environments and domains continuously generate new tasks of increasing difficulty and complexity, enabling the system to progressively enhance its problem-solving skills. This continual co-evolution of the environment complexity and system creates an open-ended learning process which can lead to surprising developments, much like how Darwinian evolution fostered the development of biological intelligence.

{% include image.html url='/assets/images/coevolution.png' description='Co-evolution of the system and the environment' %}

Various approaches have been explored to foster task evolution in a useful way including [evolutionary algorithms](#ea-envs){:.footnote-link}, [Generative Adversarial Networks](#gan-envs){:.footnote-link}, and [hand-crafted heuristics](#custom-env-evolution){:.footnote-link}.

### Good old Turing Test

The Turing test, one of the earliest experiments devised to evaluate an agent's capacity to exhibit human-level intelligence, while being deceptively straightforward can still be a good test if conducted in the right way.

The premise of the test is as follows - There is a human judge who talks to a machine and a human without knowing which one is which. The judge can ask them questions or have conversations with them through a computer or other communication methods. If the judge cannot tell which one is the machine and which one is the human based on their responses, then the machine is considered to have passed the test.

A comprehensive version of the test, conceived out of a [bet between Mitchell Kapor and Ray Kurzweil](#longbet){:.footnote-link} which involves three judges, three human participants along with the machine, and 24 hours of interviewing, is a good example of how the test should be conducted.

## Conclusion

---

While none of the benchmarks listed above offer definitive solutions for validating the existence of human-level general intelligence in AI systems, they do propose interesting alternatives to the common pitfall of relying solely on the performance of systems in specific, intellectually demanding tasks. As we continue to deploy increasingly capable AI systems to assist human civilization in various domains, we will see more such benchmarks being developed, reflecting the the evolving nature of our understanding and assessment of general intelligence.

<div class="footnotes">
<div markdown="1" id="misleading-tests">
Over the past few decades, there have been a few highly publicized encounters between AI systems and human experts in board games such as [Chess](https://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov) and [Go](https://www.deepmind.com/research/highlighted-research/alphago), as well as video games like [Dota 2](https://openai.com/research/openai-five-defeats-dota-2-world-champions) and [Starcraft](https://www.deepmind.com/blog/alphastar-mastering-the-real-time-strategy-game-starcraft-ii). Despite these remarkable advancements, these systems still fall short when it comes to matching the generalization capabilities exhibited by humans.

</div>
<div markdown="1" id="fchollet">
[François Chollet](https://twitter.com/fchollet) is a artificial intelligence researcher currently working at Google. Chollet is the creator of the Keras deep-learning library, released in 2015, and a main contributor to the TensorFlow machine learning framework.
</div>
<div markdown="1" id="mhutter">
[Marcus Hutter](https://twitter.com/mhutter42) is DeepMind Senior Scientist researching the mathematical foundations of artificial general intelligence.
</div>
<div markdown="1" id="mdl">
This hypothesis is based on the [Minimum Description Length](https://en.wikipedia.org/wiki/Minimum_description_length) principle which states that the best explanation, given a limited set of observed data, is the one that permits the greatest compression of the data.
</div>
<div markdown="1" id="procedural-envs">
**Examples:**
- [Crafter - Benchmarking the Spectrum of Agent Capabilities](https://danijar.com/project/crafter/)
- [Coin Run - Quantifying Transfer in Reinforcement Learning](https://openai.com/research/quantifying-generalization-in-reinforcement-learning)
- [Procgen Benchmark](https://openai.com/research/procgen-benchmark)
</div>
<div markdown="1" id="diverse-envs">
**Examples:**
- [Arcade Learning Environment](https://github.com/mgbellemare/Arcade-Learning-Environment)
- [OpenAI Universe](https://openai.com/research/universe)
</div>
<div markdown="1" id="real-world-envs">
**Examples:**
- [World of Bits - An Open-Domain Platform for Web-Based Agents](https://jimfan.me/publication/world-of-bits/)
- [The AI Economist By Salesforce](https://www.salesforceairesearch.com/projects/the-ai-economist)
- [Project AirSim - Validating autonomous drone systems via simulation](https://www.microsoft.com/en-us/ai/autonomous-systems-project-airsim?)
- [The Balloon Learning Environment - Autonomous navigation of stratospheric balloons](https://ai.googleblog.com/2022/02/the-balloon-learning-environment.html?hl=tr_TR&m=1)
</div>
<div markdown="1" id="ea-envs">
**Examples:**
- [POET - Endlessly Generating Increasingly Complex and Diverse Learning Environments](https://www.uber.com/en-IN/blog/poet-open-ended-deep-learning/)
- [PAIRED - A New Multi-agent Approach for Adversarial Environment Generation](https://ai.googleblog.com/2021/03/paired-new-multi-agent-approach-for.html)
</div>
<div markdown="1" id="gan-envs">
**Examples:**
- [Evolving Mario Levels using GANs](https://arxiv.org/abs/1805.00728)
- [Automatic Goal Generation for Reinforcement Learning Agents](https://arxiv.org/abs/1705.06366)
</div>
<div markdown="1" id="custom-env-evolution">
**Examples:**
- [XLand - Deepmind's Open-ended 3D Environment](https://www.deepmind.com/blog/generally-capable-agents-emerge-from-open-ended-play)
- [POWERPLAY: Training an Increasingly General Problem Solver](https://arxiv.org/abs/1112.5309)
</div>
<div markdown="1" id="longbet">
In 2002, [Ray Kurzweil](https://en.wikipedia.org/wiki/Ray_Kurzweil) and [Mitchell Kapor](https://en.wikipedia.org/wiki/Mitch_Kapor) made a bet about whether a computer would pass the Turing Test by 2029. Kurzweil believed that a computer would pass the Turing Test by 2029, while Kapor believed that it would not happen. The terms of the bet can be found [here](https://longbets.org/1/#adjudication_terms).
</div>
</div>
