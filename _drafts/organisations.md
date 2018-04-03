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

This could represent a CEO, to whom VP's report, to whom team leads report. The good news is that trees with n nodes have at n-1 edges. The problem in this case is that there are downsides to excessive hierarchy, including team isolation, employee dissatisfaction, and communication breakdown itself. The height of a tree with k splits is the number of times you need to multiply k to get number of leaf nodes (hence the logarithm). For example, if we had 156 individuals (for simplicity), we would have 125 leaves, and a communication depth of at least 3. This is reasonable for smaller organisations, but doesn't scale much further. In fact, I would go so far as to say that any indirect communication across nodes ([Chinese Whispers](https://en.wikipedia.org/wiki/Chinese_whispers)) leads to issues.

Another alternative is to divide people into extremely tightly woven, multi-skilled SWAT teams. The multidisciplinary nature of such teams, and their small size (e.g. ~5 people) is precisely why we can think of them as independent nodes in the organisation, able to take reasonably sized projects end-to-end. Communication can still build up across teams, so one might choose to limit the degree of any node to, say, 2.

![swat graph]({{ site.url }}/images/organisations/6.png)

The SWAT team structure is in fact a special case of a very common structure: large functional teams like "product", "data science" and "business intelligence". I think the problem with those are threefold:

1. such teams often get too big, meaning the node abstraction doesn't really apply
2. node degree (number of connections to other teams) usually explodes
3. skillsets tend to be relatively homogeneous. This again fails the node abstraction (1), and contributes to (2) as constant cross-team, cross-skill interaction is required

That said, there are benefits to having specialised functional teams. This leads to what I call a heterogeneous SWAT team structure. You have your usual SWAT teams, but certain functional teams or individuals float around as required. These are kept small, but perhaps don't fit into SWAT teams' degree restriction. The kind of nerdy analogy I have in my mind is teams of superheroes/differently skilled characters in a game/military tactical units (pick your favourite or make up a new one) going on quests end-to-end. As multiskilled as these teams are, they sometimes encounter and obstacle that requires a drill team/some artillery. So they call the functional support team in do to some temporary heavy lifting, and carry on.

There is a separate advantage to this approach: individuals' motivation levels. Think about how you would feel going to work with your closely knit squad, versus a large homogeneous amorphous group. It also doens't have to be a permanent situation; there is plenty of scope for occasional rotation of individuals across nodes.

The heterogeneous SWAT team structure is currently the best I can come up with for any organisation of more than 10 people. And I think it scales well. That said, I can imagine all sorts of alterations that might work best in any given environment, albeit with the same underlying principles from this model.


## A Note on Concurrency

Organisations are in many ways distributed systems of human beings, and I would be remiss not to highlight the absolutely crucial point of **concurrency**, as well as point out a common misconception about **parallelism**.

The usual analogy is that of digging a hole. To dig it faster, you could get a bigger spade. This corresponds to making nodes better at what they do, for example with skills mentorship. An alternative would be to get your friends to help you out. At some point you'd probably get in each other's way, so it might make sense to increase your output by each digging an identical hole at the same time. This is the basis of parallelism: doing many similar tasks independently at the same time.

Concurrency is a much broader idea. Now you and your friends are doing different tasks, some you digging, some of you sharpening spades, some of you carrying dirt out of the way. Importantly, different parties will have to interact at certain points, and this can lead to bottlenecks. If you can't shovel anymore because you're waiting for someone to clear the dirt around you, you're stuck idle and unproductive. In fact, we can visualise what happens when an interdependent group has to wait for its slowest member:

![concurrency squiggly]({{ site.url }}/images/organisations/7.png)

There are two mains things we can do to avoid painful idle time. Firstly, we can try and make interactions **asynchronous** (non-blocking) instead of synchronous. We'll describe this more in the section of edge (communication) quality. Secondly, we can limit cross-team dependencies, which is exactly where the SWAT team model comes in. It's worth noting that beyond simply wasting productivity, idleness due to excessive dependencies can be a leading cause of demotivation.


## Edge Quality

Now that we've spoken about managing how communication scales, let's look at how to maintain high standards of
communication quality. This could be translated into our model as edge weights/thickness, denoting the quality or alternatively the cost of a given interaction link (though cost makes more sense in that we could look at metrics like the weighted average of edges in the graph).





## Information Processing

## The Human Touch


## Conclusion


## Acknowledgements




[^1]: http://www.businessinsider.com/elon-musk-says-theres-no-such-thing-as-a-business-2015-9
[^2]: http://www.dtic.mil/get-tr-doc/pdf?AD=ADA128980
[^3]: For example [OKR](https://en.wikipedia.org/wiki/OKR)s/[KPI](https://en.wikipedia.org/wiki/KPI)s at the team level. N.B. I find these terms extremely corporate. Aesthetics do matter!
