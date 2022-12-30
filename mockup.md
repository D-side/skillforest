---
layout: default
permalink: "/mockup"
title: Mockup
---

# Mockup

📝 There is no implementation here _yet_, but to give you an idea what it would look like, here is a "script" (as in "for a performance", there's no code here) of what *should* be happening here.

🖱️ Hints with this icon indicate what the user does. The tutorial relies on clearly telling the user what can be done as well as having nothing else to do in the app until it's complete. That said, not all functions are disabled in order to facilitate **skipping** the tutorial.

## Act 1: first topic

This is a mock-up of what the app's main screen could look like.

<div class="mockup">
    <h3>🗺️ Heading to: <em>Skillforest: Introduction</em></h3>
    <h2 style="text-align: center;">
        <span class="muted" title="past, topics you've already gone through">Past ⏪</span>
        <span style="text-decoration: underline;" title="current, topics you're ready for">Current ⏯</span>
        <span title="future, topics you aren't ready for yet">Future ⏩</span>
    </h2>
    <blockquote><span class="muted" style="display:inline-block;float:right;" title="A button that dismisses the hint">❌</span>💡 Welcome! This is where the app will tell you know what topics you're ready to explore <em>right now</em>. Click the title of the topic to open its page. Once you've explored it, click its checkmark on the right in order to advance.</blockquote>
    <blockquote><a href="/topics/Topic" target="_blank">Skillforest: Topic</a> <a href="#" style="display:inline-block;float:right;" title="A button that marks a source as read/done">✔️</a></blockquote>
</div>

The app detects when it's being opened for the first time and initializes itself with a tutorial goal that explains how to use the app. Unfortunately, this is a chicken-and-egg situation, so a few special nudges are necessary.

🌟 **Topic titles are clickable** and lead to content that's more or less what's meant to be there. The content there **is** a part of the tutorial of course, so for the full experience you'll have to read them as well. It's a decent simulation, as they will open _in the browser_ in the final version too.

Icons aren't clickable, but those that are meant to be buttons are annotated with `title` attributes and display hints on hover. On mobile there is unfortunately currently no way to see them, but they don't contain anything critical.

🖱️ User reads the [Topic](/topics/Topic) page, then comes back to the app, dismisses the hint with a ❌ and clicks the ✔️ on the right.

---

## Act 2: first step

<div class="mockup">
    <h3>🗺️ Heading to: <em>Skillforest: Introduction</em></h3>
    <h2 style="text-align: center;">
        <span title="past, topics you've already gone through">Past ⏪</span>
        <span style="text-decoration: underline;" title="current, topics you're ready for">Current ⏯</span>
        <span title="future, topics you aren't ready for yet">Future ⏩</span>
    </h2>
    <blockquote><a href="/topics/Source" target="_blank">Skillforest: Source</a> <a href="#" style="display:inline-block;float:right;" title="A button that marks a source as read/done">✔️</a></blockquote>
</div>

The hint is gone, and the link list is updated.

Also, the ⏪ button, that opens the list of explored links, is now active, as there is one item on that list now: Topic.

🖱️ The user reads the [Source](/topics/Source) page, then comes back to the app and clicks the ✔️ on the right.

---

## Act 3: first fanout

<div class="mockup">
    <h3>🗺️ Heading to: <em>Skillforest: Introduction</em></h3>
    <h2 style="text-align: center;">
        <span title="past, topics you've already gone through">Past ⏪</span>
        <span style="text-decoration: underline;" title="current, topics you're ready for">Current ⏯</span>
        <span title="future, topics you aren't ready for yet">Future ⏩</span>
    </h2>
    <blockquote><a href="/topics/Requirement" target="_blank">Skillforest: Requirement</a> <a href="#" style="display:inline-block;float:right;" title="A button that marks a source as read/done">✔️</a></blockquote>
    <blockquote><a href="/topics/Result" target="_blank">Skillforest: Result</a> <a href="#" style="display:inline-block;float:right;" title="A button that marks a source as read/done">✔️</a></blockquote>
    <blockquote><a href="/topics/Goal" target="_blank">Skillforest: Goal</a> <a href="#" style="display:inline-block;float:right;" title="A button that marks a source as read/done">✔️</a></blockquote>
</div>

🖱️ The same procedure done before now continues on with three other topics, in no particular order.

## Act 4: first finish line in sight

With the basic topics covered, the goal is in sight, the "Introduction" source.

⏩ is disabled to indicate there are no more sources up ahead.

<div class="mockup">
    <h3>🗺️ Heading to: <em>Skillforest: Introduction</em></h3>
    <h2 style="text-align: center;">
        <span title="past, topics you've already gone through">Past ⏪</span>
        <span style="text-decoration: underline;" title="current, topics you're ready for">Current ⏯</span>
        <span class="muted" title="future, topics you aren't ready for yet">Future ⏩</span>
    </h2>
    <blockquote><a href="/topics/Introduction" target="_blank"><strong>Skillforest: Introduction</strong> 🏁</a> <a href="#" style="display:inline-block;float:right;" title="A button that marks a source as read/done">✔️️</a></blockquote>
</div>

## Act 5: first goal reached

Hitting ✔️️ on the Introduction source, which was the goal of the tutorial, marks the end. Selected goal is dropped and the app explains what happened and what'll happen next.

<div class="mockup">
    <h3>❔ No goal selected</h3>
    <h2 style="text-align: center;">
        <span title="past, topics you've already gone through">Past ⏪</span>
        <span class="muted" style="text-decoration: underline;" title="current, topics you're ready for">Current ⏯</span>
        <span class="muted" title="future, topics you aren't ready for yet">Future ⏩</span>
    </h2>
    <blockquote>
        <p>🏁 All set goals reached!</p>
        <p>💡 If you find something else you'd like to learn, add it as a goal to the app.</p>
        <p>📚 Your learnings from all your past goals are saved, so when tracking other goals in the future, the concepts you've already explored will be skipped.</p>
    </blockquote>
</div>

## Closing thoughts

### More UI elements

A number of elements have been deliberately omitted from the mockups. To name a few:

* Goal selection — the app may be able to track multiple goals at once and switch between them, rebuilding the "current" sources to match
* Topic browser — it's only needed for the more elaborate operations like 

### Media player analogy

In early versions of this "script" I toyed with the idea of using icon-only buttons, even in the "Past", "Current" and "Future" line.

I'm not entirely sure I like the "media player" analogy in the UI in general (aside from randomly disgustingly inconsistent emojis on some systems, that's just the artifact of this quick & dirty demonstration). It certainly ticks a lot of boxes, like succinctly representing "past" and "future" as well how the concept of "media tracks" maps to "SF goals" (⏮️ and ⏭️ for switching between ~~tracks~~ goals).

But at the same time I feel there for whom it's counterintuitive, it'll be **really** counterintuitive.

There does seem to be some potential there though.
