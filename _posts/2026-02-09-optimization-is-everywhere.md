---
title: "Optimization-plus-modelling is the universal solvent"
date: 2026-02-09
permalink: /posts/2026/02/optimization-is-everywhere/
tags:
  - optimization
  - control
  - cross-domain
  - notes
---

I came into research wanting to build flying robots. The arc I did not expect is how much of the math turned out to be useful far away from anything that flies. The longer I stare at a control problem, the more it looks like the inside of a delivery routing problem, or a recommendation feed, or a traffic light at a busy intersection. The accident of which domain it came from feels less important than the shared structure.

The structure, when I try to write it out, is almost embarrassingly simple:

1. Pick state variables that describe what you care about.
2. Write down how the state evolves, even with a rough model.
3. Write down what "good" means as an objective, plus what "allowed" means as constraints.
4. Solve, repeatedly, as the world supplies new information.

That is it. Once you have those four boxes, you have a recipe that travels.

## Where I have noticed it lately

**Last-mile delivery.** A fleet of vehicles, time windows on the customer side, a depot, fuel constraints, drivers who do not work past a certain hour. State: where each vehicle is, what packages remain. Dynamics: roughly known, partially uncertain. Cost: total distance, lateness penalty, driver overtime. Constraints: package fits in vehicle, time window, legal driving hours. The problem is intractable in the worst case, but the formulation is the same shape as a constrained predictive control problem.

**Traffic signal timing.** State: queue length per approach, vehicle speeds. Dynamics: flow balance plus a saturation model at the stop bar. Cost: total waiting time, emissions, pedestrian delay. Constraints: minimum green, maximum red. People in the traffic community will describe their solver in a different vocabulary, but a controls reader recognizes a receding-horizon optimization on a network.

**Social-media feeds.** This one is more uncomfortable. The state is "what the user has seen and reacted to," the model is some learned predictor of engagement, the cost is a measure of platform value, and the constraints are content policy. The unease about modern feed design is, partly, an unease about *what objective is being optimized for*, but it is still, structurally, an optimization problem with feedback. Naming the feedback loop precisely is, I think, a precondition to disagreeing with it intelligently.

**Power grid balancing, vaccine rollout planning, water-reservoir management.** Same recipe.

## What "modelling" means in this picture

The word "optimization" gets most of the credit, but the load-bearing word in the recipe is *model*. Optimization is a hammer that converges. The model is what decides whether the nail it drives is the right one. A wrong objective, optimized perfectly, gives you exactly the wrong thing, which is, in a sense, the story of every cautionary tale about misaligned incentives in any system.

Control theory's hard-won habits, things like Lyapunov reasoning, robustness margins, observability tests, and "what do we do if the model is wrong," feel like they have something to offer here. Not because they translate cleanly, but because the *posture* of asking those questions transfers. A controls engineer who is suddenly working on traffic timing will, by reflex, ask: what happens if the demand forecast is off by 20%? What is the safe fallback? Which constraints are hard and which are soft? Those are exactly the questions the optimization-only view forgets to ask.

## Why I keep coming back to it

I am, day to day, designing controllers for quadrotors with arms. But the longer I do this, the more I see the same problem shape appearing in places I was not expecting. It is one of the reasons I am reluctant to call myself a "robotics person" too quickly. The math is more ubiquitous than the application domain. Once a year I read something (a paper on opinion dynamics, a course on operations research, a talk on epidemic control) and find that the moves I learned for adaptive control transferred, almost without modification.

This is not a claim to expertise in any of those other fields. It is closer to a thank-you note to whoever decided that constrained optimization with a feedback loop was worth teaching as a general subject. It travels.
