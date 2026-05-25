---
title: "The honest cost of \"we tuned the gains by hand\""
date: 2025-07-08
permalink: /posts/2025/07/honest-cost-hand-tuning/
tags:
  - controls
  - notes
  - benchmarking
---

A confession I would like to see in more controls papers: the gains were tuned by hand, on the test cases shown in the figure, by a person who was rooting for the controller.

I am not anti-tuning. Every controller I have ever built has a small forest of gains, and most of them were picked with a mix of physical reasoning and "what looked nice on the plot." The problem is not the tuning. The problem is when the tuning is invisible, and a reader is left to imagine that the gain values fell out of the theorem.

Once I started keeping notes on how much hand-tuning went into the controllers I was comparing against in benchmarks, two things became clear:

1. The "baseline" PID is almost always *somebody else's hand-tuned PID*, on *somebody else's test case*. Running it on a new test case without re-tuning is unfair to the baseline.
2. Re-tuning every controller in a benchmark sounds principled but is itself an act of judgement. Whoever does the re-tuning is, in effect, deciding how much love each controller gets.

The honest version of a comparison table has a column that nobody wants to write: how long, in person-hours, was spent tuning this controller. A method that takes thirty seconds to tune and a method that takes a graduate student a week of evenings are not comparable on the same row, no matter how similar the tracking error is.

In my own work I have started keeping a tuning log. It is embarrassing to write, and useful to read back later. It also turns into a section in the appendix of the paper that I would, in another life, have been too proud to include. I think the appendix is now my favourite part of the paper.

This is not a methodological breakthrough. It is closer to a politeness, naming the human cost of the result. But politeness in engineering tends to compound.
