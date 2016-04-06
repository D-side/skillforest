# Skillforest

Skillforest is a tool for tracking skillsets and ways to improve them. A "skilltree", a well-known concept in role-playing games (RPGs), is a set of skills with some depending on the others. Skillforest is an environment where individual skilltrees grow and interact. Hence, **skillforest**.

This project is currently in the **design phase**, implementation hasn't even begun. Since this project will likely involve federation-like interaction between servers, specifying that interaction as formally as possible is important on early stages so multiple implementations of this spec can grow and highlight the inconsistencies.

## Rationale

Many attempts have been made to "gamify" the process of gaining technical skills. Most of them are fairly direct translations of in-game concepts to real-world skills: achievements, levels, etc. But applying the same concepts to actual skills are a **big simplification**. So big that it doesn't look right in many ways.

The birth of this concept was "triggered" by a suggestion on [meta.ru.StackOverflow][3] to gather community-maintained "lists of skills and knowledge", loosely divided into levels of "beginner", "intermediate" and "advanced", with relevant materials available for every point.

The community has currently settled for "reading lists", consisting of community-maintained answers with lists of books on topic specified by a question. But this doesn't really answer the question of "what should I know to be hired". Questions like these are a bad fit for StackOverflow anyway, but they still come up from time to time and need to be answered, at least somewhere else. Of course, **there is no single answer**, there are choices to make.

## The idea

Just a list of skills divided into categories doesn't really work:

* A list implies order, at least order of appearance, even though it has no real significance
* Levels such as "beginner", "intermediate" and "advanced" are arbitrary and subjective
* Skills don't fit into a linear structure, some of them depend on the others

We tackle these points by using a [**graph**][1] instead. Skills are **nodes** of this graph, connected with **requirements**. The process of tracking skills revolves around the user's ability to **mark** and **unmark** skills. Having a certain skill **marked** is a claim of having mastered it.

The tool is not intended to check whether it's actually true, it's intended to *guide* self-improvement and it relies on the user being honest with himself. However, the intention is *to not restrict implementations from performing such checks* on an attempt to mark a skill. It just doesn't seem feasible at the time, but may be very well possible within certain education systems.

Skillforests are meant to be **federated**, in that a single user might be using **multiple skillforests** at once in this workflow, possibly located on *different servers* (hence, a *federation* of servers), and **skillforests can reference other skillforests**, in which case clients have to load and use the dependent skillforests as well.

> This tool assumes that the learner and the maintainer of skillforest are different. Still, constructing the skillforest while progressing through it at the same time may be possible for advanced self-learners. Whether this could work needs to be tested.

## Example

### Background

* There is a public UI client that anyone can open witha  web browser.
* Bob maintains a Ruby skillforest.
* Jack maintains a Rails skillforest
  - Some of the Rails skillforest's skills require some Ruby skills, so Jack referenced Bob's Ruby skillforest in some places

### Action

* Paul wants to learn Rails.
* Paul stumbles upon "this whole skillforest thing" and decides to use it to guide his path.
* Paul finds a link that starts the skillforest client with Rails skillforest.
* Paul's browser loads the client, sees the Rails skillforest in URL and downloads a skillforest
* *(Lazy/eager?)* Paul's browser, seeing that some of the Rails skills require some Ruby skills, downloads Bob's Ruby skillforest too
* Point of entry: the skillforest client starts, showing only the nodes with **no requirements**
  - This should probably be *"I want to learn X!"* for every skillforest (best practice? allow multiple entry points?)
  - Given that 2 skillforests are loaded at the same time and none of them is the **main** one (is that necessary?), there have to be multiple entry points: one for Ruby, one for Rails, but Paul knows what he wants
* Paul marks the Rails entry point, "I want to learn Rails!"
  - This node contains the references to learn about **what Rails is** and by marking it, Paul claims to know that
  - UI displays the possible next steps
* *(Main loop)* Paul picks a node and studies the materials it references until he feels confident that he knows everything what this node is about
* After a bit of practice (and marked nodes as well!), Paul stumbles upon a Rails skill which requires a Ruby skill from the branch he hasn't even started; UI shows a path to all the skills required for that, until it hits nodes that can be marked (Ruby entry point in this case)
* Willing to progress, he marks "I want to learn Ruby!" and receives materials on the matter
  - In practice that will probably happen pretty fast if not right away: to **run** Rails, one has to set up a Ruby environment first
* After a bit of practice with Ruby, he achieves the level of understanding necessary to go on with Rails, but likes Ruby and decides to progress further into Ruby skillforest instead
* ???

> The example is simplified, of course. E. g. it doesn't mention an OS shell.

## Goals

* Describe the abstractions behind the skillforest
* Develop non-interactive example skillforests for several related technologies
* Design a file format (possibly more than one?) for transmission of skillforests
  - Start with autonomous skillforests, add cross-references when ready
* Outline the process and best practices of maintaining a graph
  - Graphs change, clients either need to remember the version they're tracking or need to adapt to changes
    + Determine behaviour in case of structural conflicts of user-defined state and new version of the graph
    + Cache policy (cache once in use, upgrade explicitly?)
    + Bind user-defined state to specific version and let implementations decide on migration?
    + Determine whether update notification mechanisms are necessary and whether an optional mechanism is possible
  - Develop a linting tool
    + Check general structure (schema? JSON schema?)
    + Check acyclicity
* Develop a proof-of-concept UI
  - Don't bother with multiple versions initially
* Mobile app? (Kidding or not?)
* State migration between clients? (File? Permalink?)
* Determine the use of URLs (relative, absolute?)
* Think over the implications of having multiple disjoint skillforests in a single session
* Extension policy: what extra fields are allowed? How to deal with conflicts?

## Philosophy

* **Don't overwhelm. Motivate to learn** by showing that "it's not **that** hard".
  - Don't show too much information at once. Introduce new information only when the user is ready to digest it.
  - ...but don't get in the way. If the user wans to see "the whole picture" it's his own choice.
  - Continuing analogy with Rails, you won't need *too much* of Ruby to work with Rails, and a full-fledged Ruby book might seem a bit intimidating (making a *first step* may be the hardest challenge).
* **Leave choices.** If hitting a particular level opens up multiple learning possibilities, leave choice to the user.
  - This is particularly different from learning "by the book" in the order imposed "by the book" and allows the user to keep learning even if he's stuck in a certain direction. He can just choose a different one and come back later.
  - "A Well-Grounded Rubyist" by David Black discusses topics about Ruby in breadth-first order; it's mentioned in the book itself; this is a case when a piece of knowledge being a book may be a limiting factor (an exaggeration, perhaps)
* **Stay on-topic.** If learning one technology requires to learn another one, consider extracting it into a separate skillforest.
  - Using a skillforest maintained by a 3rd party may be a good idea, it could open new horizons even for the maintainer of related skillforest!
  - A skillforest for that separate technology might be needed for some other technology. Like, Ruby shouldn't be **embedded** into Rails, since... Well, Chef uses Ruby too. Calabash as well. And many others!

## Uses

* Tracking self-improvement, obviously
* A concise way to show your skills to those that are interested: "details available on-demand, a lot of them"

## Theory

The main abstraction is a **skill**. The **skillforest** is defined as an oriented acyclic [graph][1], where nodes (vertices) are **skills** and connections (edges) are **requirements**. For every user every node can either be **marked** or **unmarked**. Every **skill** can be in one of the following states, defined in terms of being **marked**/**unmarked** and its surroundings:

* Mastered -- "the edge" of mastered skills in a certain direction that hasn't yet been built upon
  - **Marked**
  - All the skills that are required for it are **unmarked**
* Known -- skills for which all the requirements have been mastered, as such, these skills can now be mastered too
  - **Unmarked**
  - All the skills that are required for it (possibly *none*, via [vacuous truth][2]) are **marked**
* Unknown -- skill that is so far from the current skillset that may not even be known yet
  - **Unmarked**
  - There is *at least one* **unmarked** skill required for it
* Active -- actively used in that other skills have been mastered that require it
  - Marked
  - There is *at least one* **marked** skill that requires it

> Being a "requirement" is a property of edges. Whether we need other forms of dependency, such as "discovery", when marking any given skill's discovery-dependent node *discovers* that skill, is undecided; use cases are needed for that.

---

#### To be continued...

## References

* [Initial concept (in Russian)][3].

  [1]: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)
  [2]: https://en.wikipedia.org/wiki/Vacuous_truth
  [3]: http://meta.ru.stackoverflow.com/a/2793/181100
