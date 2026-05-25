---
title: "Two things aerial manipulation papers under-report: base forces and impedance error"
date: 2025-11-22
permalink: /posts/2025/11/base-forces-impedance-error/
tags:
  - aerial-manipulation
  - impedance-control
  - notes
---

If you read enough aerial manipulation papers, two omissions start to feel structural. The first is the wrench transmitted to the base of the quadrotor during contact. The second is the impedance-tracking error during the transient, not the steady-state error, but the few hundred milliseconds when the arm first touches the world. I want to argue, gently, that both of these deserve a row in every comparison table.

## Why the base wrench matters

A grounded manipulator absorbs reaction forces through its mount. A quadrotor mount is a hovering vehicle. Every newton-metre the arm transmits to its base is a newton-metre the attitude controller has to fight off, in a regime where authority is finite and the position controller is already busy.

When a paper reports only tip-tracking error, it is implicitly assuming the base controller will absorb whatever shows up. That is fine for desktop experiments and unfair to anyone who has tried to fly the controller. The cost of *not* reporting it is that two papers with identical tip-tracking curves can have wildly different real-world behaviour. The one with smaller base wrench will fly; the other will tumble.

I think of the base wrench norm the same way an automotive engineer thinks of unsprung mass: invisible in the brochure, dominant in the ride.

## Why the impedance error in the *transient* matters

Steady-state impedance error is the wrong place to look. By the time the contact has settled, any reasonable controller will get the error small. The interesting moment is the impact: how much does the desired stiffness `K_d` get violated in the first few hundred milliseconds, and by how much?

Two controllers can both pass a steady-state check while behaving completely differently on impact. One is stiff during the transient and soft after; the other is soft during the transient and stiff after. The papers report the same number. The robots are doing different things.

Reporting the *transient* error, that is the peak deviation from the desired impedance during the first overshoot, is almost free, and it separates controllers that *behave* like impedance controllers from ones that *settle* like impedance controllers.

## What I have been doing about it

In the catching benchmark I am writing up, the table has columns for tip tracking, transient impedance error, and base wrench norm. The third column has been the most argued-over, internally, of any number in the paper. That is, I think, evidence it should have been there in the literature all along.

None of this is a deep theoretical observation. It is closer to a measurement hygiene complaint. But measurement hygiene complaints, in my limited experience, tend to be where the actual progress of a field lives.

## A short checklist for myself

When I review an aerial manipulation paper now, I look for:

1. Is the base wrench reported, or is the arm implicitly assumed to be grounded?
2. Is the impedance error during the contact *transient* shown, not just the steady state?
3. Is the reference trajectory feasible for the actuator limits, or is the actuator saturating in a way the figure does not show?

If two of those three are missing, I am usually looking at a controller that works in the figure and surprises everyone in the lab.
