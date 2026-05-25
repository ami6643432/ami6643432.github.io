---
title: "Coming across Lean: when a proof assistant turned into a research tool"
date: 2026-04-18
permalink: /posts/2026/04/coming-across-lean/
tags:
  - lean
  - formal-verification
  - control
  - notes
---

I first heard about Lean the way most engineers do: as something mathematicians used to formalize the Liquid Tensor Experiment, or to mechanize a kilometre of group theory in `mathlib4`. It looked like a museum exhibit: beautiful, far away, and not for me.

What changed my mind was a Lyapunov derivative that I could not get past myself.

## The setup

I was reworking an adaptive control proof where a parameter update law had to cancel a cross-term in `V̇`. The algebra on paper looked clean. The simulation was unstable. I worked the chalkboard for two days. Then a friend, half joking, said: "If you do not trust the algebra, why don't you let a machine check it?"

I did not want to do that. Mechanizing a proof felt like building a cathedral around a doorbell.

## What happened anyway

The first time I tried to write the controller's Lyapunov function in Lean 4, I discovered that I had the sign of one term wrong. Not the proof. The *definition*. The proof I had been carrying in my head was correct for a Lyapunov function I had never actually written down. On paper, the sign was just a transcription typo that I had read past for two days. Lean could not read past it, because Lean has no eyes.

That single experience flipped my prior on formal verification. The interesting feature of a proof assistant, for someone like me, is not that it gives you a certificate at the end. It is that the work of *stating* the theorem in a language with no slack forces you to find out what you actually mean.

## What it is good at, what it is not

After a few months of part-time work, my honest take:

- **Where it earns its keep.** Algebraic identities I keep mis-copying, sign conventions across coordinate frames, "obvious" inequalities that turn out to have a hidden assumption, and the bookkeeping at the boundary of a Lyapunov argument. The kind of mistakes that pass a chalkboard review and fail in a simulation.
- **Where it does not.** It does not pick a Lyapunov candidate for you. It will not tell you that your controller is silly. It will not survey the literature. If your modelling assumption is wrong, the proof will be impeccably correct about the wrong system, and you will not learn anything until the hardware tells you.

## The mental shift

I used to think proofs and code were two different artefacts: one for the paper, one for the robot. Lean dissolved that distinction for me. The proof *is* a program; the program's type signature *is* the theorem. When I now write a derivation on paper, I find myself trying to phrase each step so that I could, if I had to, type it into Lean tomorrow. That habit alone has improved the papers I am writing, whether or not the Lean file gets attached.

It is also a useful reminder of how much of "I understand this" was really "I have not yet been forced to be precise about this."

## Where I am now

I keep small Lean files alongside the simulation directories for the controllers I work on. Most of them are not finished proofs. They are scaffolds, with `sorry` placeholders that mark the spots where I still owe myself an argument. The placeholders are honest in a way that informal notes never quite are: I cannot pretend I have closed an argument when the file refuses to compile.

If you are an engineer who has avoided proof assistants because they look like a different career path, I would gently push back. You do not have to become a logician. You just have to be willing to type your assumptions, in order, in a language that will not nod along.
