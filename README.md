# Skillforest

Skillforest is a tool for tracking skillsets and ways to improve them. A "skilltree", a well-known concept in role-playing games (RPGs), is a set of skills with some depending on the others. Skillforest is an environment where individual skilltrees grow and interact. Hence, **skillforest**.

This project is currently in the **design phase**, implementation hasn't even begun. Since this project will likely involve federation-like interaction between servers, specifying that interaction as formally as possible is important on early stages so multiple implementations of this spec can grow and highlight the inconsistencies.

## The idea

The process of tracking skills revolves around the user's ability to **mark** and **unmark** skills.

Having a certain skill **marked** is a claim of having mastered it. The tool is not intended to check whether it's actually true, it's intended to *guide* self-improvement and it relies on the user being honest with himself. However, the intention is *to not restrict implementations from performing such checks* on an attempt to mark a skill. It just doesn't seem feasible at the time, but may be very well possible within certain education systems.

## Goals

TBD

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

* [Initial concept (in Russian)](http://meta.ru.stackoverflow.com/a/2793/181100).

  [1]: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)
  [2]: https://en.wikipedia.org/wiki/Vacuous_truth
