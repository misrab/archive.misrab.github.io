---
title: Things I Learnt Building a Team
layout: blog
image: /images/organisations/3.png
date: 2018-04-02
excerpt: |
  A preliminary general theory of organisations
---


# Things I Learnt Building a Team

_Posted on April 2nd, 2018_


## Introduction

At [Go-Jek](https://en.wikipedia.org/wiki/GO-JEK), I had the privilege of scaling
a data science team from a few members in one location, to about thirty people across
three countries.

This and past experiences have helped me come to certain preliminary conclusions on how teams best function,
in what I call my "general theory of organisations". This theory represents my own views (i.e. not necessarily
those of any company I've worked with). It's also most definitely a work in progress, and I'm more than happy to be
proven wrong on certain points, and refine these views. It's not meant to be a comprehensive theory, but hopefully contains
a couple nuggets of wisdom.

My favourite characterisations of organisations are "just a bunch of people working together to
create a product or service" [^1], or "information processing systems" [^2]. In other words, there are one
or multiple goals to achieve beyond what a single individual could output, so a group was formed. Simply put,
organisations are a solution to **the scaling problem**. So let's start by talking about how we can scale them optimally
to best address scaling of challenges.

## Scaling

I like to think of scaling as the following picture. Output is typically related to the product or service of the
organisation. It can be represented at different levels of granularity[^3], or relate to different objectives such as low
staff turnover or morale.

![scaling chart]({{ site.url }}/images/organisations/1.png)

I would argue that most organisations encounter diminishing returns to scale, or the "bad" line. Incremental
team members contribute less and less marginal productivity as complexity and communication bottlenecks arise. In fact, even scaling output linearly with respect to team members is probably quite a feat. Hopefully, this feels anecdotally intuitive to you: ever felt the difference between having a 3rd member on a project, versus a 20th?

Imagine however an organisation that was able to achieve increasing returns to scale, labeled "excellent". This team would experience network effects as it grew (presumably within reasonable bounds?); if it were a company, it would leave the competition in the dirt. Think it's only a theoretical proposition? I disagree. I've seen and built teams where adding a novel skillset to a homogeneous group was like rocket fuel for productivity. And it gets better: one can presumably both shift (dashed line) these "excellent" levels of output upwards, and increase their slope, by improving **leverage** - tools and processes that enhance individual productivity, and team communication. More on this in a bit.


## Organisations as a Graph

It helps in many ways to view organisations as graphs, made up of nodes and edges. Typically, nodes would represent
individuals, and edges would represent interfacing/communication between them. It may make sense to view multiple individuals as a node under certain circumstances, for example when communication overhead within that team is genuinely negligible, or when we're modeling at a lower level of granularity.

![scaling graph]({{ site.url }}/images/organisations/2.png)


Remember, organisations are a way to scale output. From a graph perspective, stuff happens at two places in the org: within nodes (1), and at edges, the interface of nodes (2). So these are the two dimensions we can optimise. Let's consider one at a time.

Optimising on the node level (1) is a bit more straightforward, regardless of whether the node is an individual or extremely tightly knit group. It involves things like:

- keeping the individual(s) motivated. This can range from compensation to a holistic [Maslow](https://en.wikipedia.org/wiki/Maslow%27s_hierarchy_of_needs) approach
- tools to be productive e.g. software, non-communication processes
- efficient information dissemination (a whole section on this later)
- career growth and guidance
- clarity of purpose. Output can definitely be low if one is targeting the wrong output!
- self-development: learning skills, design thinking. A lot of this rests on the individual own imperative

There seems to be more literature addressing (1), so I'll spend more time on (2): optimising communication. There are two ways to do this. We could reduce the number of interfaces, or we could improve their quality.

## Edge Scaling

If you're not familiar with [Big O Notation](https://en.wikipedia.org/wiki/Big_O_notation), here's some of the best advice I'll ever give you in life: spend the next ten minutes understanding it. Seriously. It's a way to think about scalability in any field, and the world would benefit tremendously if people in all domains, from politicians to scientists to artists understood it better.

Consider a dense or complete graph. How does the communication overhead (edges) increase as we increase the number n of people (nodes)? In the complete case, you connect the first node to all others. The next node has one less connections to be made, and so on. We calculate the sum:

![scaling edges graph]({{ site.url }}/images/organisations/3.png)

![scaling edges equation]({{ site.url }}/images/organisations/4.png)

For an idea of magnitude, this means 100 individuals end up with on the order (remember this is Big O) of 10,000 communication channels. Think that's unrealistic? Even if divided into teams of 5, we're talking talking 4000 channels. Fancy halving the graph's density? We're still talking 2000 channels. The point is that it scales quadratically. In other words, it does not scale. If you're a business, forget about your competitors committing homicide. You've just committed suicide.

The good this is that alternative organisational designs are completely possible. Take the most common solution approach, for instance: hierarchy. Graphically speaking, this means organising nodes into a k-tree, where k is the number of splits at each level of the tree.

![scaling tree]({{ site.url }}/images/organisations/5.png)

This could represent a CEO, to whom VP's report, to whom team leads report. The good news is that trees with n nodes have at n-1 edges. The problem in this case is that there are downsides to excessive hierarchy, including team isolation, employee dissatisfaction, and communication breakdown itself. The height of a tree with k splits is the number of times you need to multiply k to get number of leaf nodes. For example, if we had 156 individuals (for simplicity), we would have 125 leaves, and a communication depth of at least 3. This is reasonable for smaller organisations, but doesn't scale much further. In fact, I would go so far as to say that any indirect communication across nodes ([Chinese Whispers](https://en.wikipedia.org/wiki/Chinese_whispers)) leads to issues.

Another alternative is to divide people into extremely tightly woven, multi-skilled SWAT teams. 



## Edge Quality

## Information Processing

## The Human Touch


## Conclusion


## Acknowledgements




[^1]: http://www.businessinsider.com/elon-musk-says-theres-no-such-thing-as-a-business-2015-9
[^2]: http://www.dtic.mil/get-tr-doc/pdf?AD=ADA128980
[^3]: For example [OKR](https://en.wikipedia.org/wiki/OKR)s/[KPI](https://en.wikipedia.org/wiki/KPI)s at the team level. N.B. I find these terms extremely corporate. Aesthetics do matter!
