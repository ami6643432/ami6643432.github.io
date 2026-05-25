---
title: "A small note on Lyapunov functions, my favourite idea in engineering"
date: 2025-09-15
permalink: /posts/2025/09/lyapunov-functions-favourite-idea/
tags:
  - lyapunov
  - control
  - notes
---

Engineers carry a small bag of ideas around with them that they trust more than anything else they were taught. Different engineers carry different bags. For me, near the top, is the Lyapunov function.

What I love about it is the *posture*. A Lyapunov function does not promise you that the system will reach the goal in five seconds. It does not promise an optimal trajectory. It does not even promise that the path will be sensible. What it promises is something humbler and more honest: "I will name a scalar quantity that, on every trajectory of this system, only goes downhill." Once you have that scalar, you can sleep at night, because you know the system cannot do anything truly unexpected. It might wander, but it will wander downhill.

That posture, finding a quantity that bounds your worst-case behaviour, rather than solving for an optimum you might not trust, feels generalizable in a way most control-theoretic moves are not. I see versions of it everywhere once I started looking:

- Algorithm analysis uses *potential functions* the same way. Amortized cost arguments are Lyapunov arguments wearing a different hat.
- Game theory uses *potential games* the same way. Convergence to equilibrium without anyone solving for it.
- Distributed systems uses *monotonic counters* the same way. State only goes one direction; nobody can lie about the past.

There is something profoundly comforting about the worldview: if you cannot promise optimality, promise monotonicity. If you cannot promise the destination, promise the direction.

I keep a small file of "things I would want a young engineer to actually know." Lyapunov functions are at the top of the list, not because they are the most advanced idea, but because they capture an attitude about uncertainty that I find difficult to teach any other way.
