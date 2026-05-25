---
title: "Payload Feasibility Certificate for Energy-Based Safety Filters"
excerpt: "A pre-flight test that asks whether an aerial manipulator can safely lift a given payload, paired with a closed-form bound and a Lean 4 proof script.<br/><img src='/images/portfolio/payload-cert-delta-envelope.png' style='max-width:100%;'>"
collection: portfolio
header:
  teaser: portfolio/payload-cert-delta-envelope.png
---

<figure class="pf-hero">
  <img src="/images/portfolio/payload-cert-delta-envelope.png" alt="Feasibility envelope across the workspace, heat-mapped over joint configurations">
  <figcaption class="pf-hero-caption">Feasibility envelope across the workspace. Lighter regions admit heavier payloads; darker regions are where the binding constraint kicks in.</figcaption>
</figure>

<div class="pf-tldr">
A scalar pre-flight test for whether an aerial manipulator can safely lift an uncharacterized payload. One closed-form bound from CAD plus torque limits. Supporting lemmas mechanized in Lean 4, where the act of typing the proof caught a sign error two months of paper review had read past.
</div>

## The question I keep coming back to

A quadrotor with an arm picks up a payload nobody measured. The onboard safety filter is supposed to keep the joint dynamics inside a known energy envelope no matter what that payload does. The question I started exploring was simple, and harder than it looked: *before* the controller closes the loop, can we hand the operator one number that says whether the payload is safe to lift?

This page is about how that one number takes shape, why it needed a closed-form bound to be useful in the field, and why I ended up reaching for a proof assistant to finish the argument.

## The idea I am exploring

The certificate takes three things you already have, namely the nominal CAD model of the arm, the actuator torque limit, and a candidate payload mass. It returns a scalar that I call `δ`. When `δ < 1`, the energy-based safety filter remains feasible at every joint configuration inside the workspace slice you care about. From there, a short calculation gives a conservative upper bound on payload mass, no online optimization required, and you can read it off a table before powering anything up.

## What the simulations look like

The two figures below are the ones I find most useful for explaining the work to a new reader. The left plot shows the system's kinetic energy under controllers with and without the proposed safety filter: the filter respects the energy barrier; the baseline drifts past it. The right plot reconstructs the same scenario using the true energy quantity rather than its measurable proxy, which is the question reviewers ask most often.

<div class="pf-grid pf-grid-2">
  <figure class="pf-figure">
    <img src="/images/portfolio/payload-cert-energy-trace.png" alt="Kinetic energy trace with and without the safety filter">
    <figcaption>Kinetic energy under three controllers. The proposed filter respects the barrier; the baselines do not.</figcaption>
  </figure>
  <figure class="pf-figure">
    <img src="/images/portfolio/payload-cert-true-vs-proxy.png" alt="True vs proxy kinetic energy under the safety filter">
    <figcaption>True energy quantity versus its measurable proxy under the same filter, the comparison reviewers ask for most often.</figcaption>
  </figure>
</div>

## Why I reached for a proof assistant

A handful of supporting lemmas hold the certificate together. Writing them down in Lean 4 was not a stylistic flourish: the act of typing the dissipation term in a language with no slack caught a sign error that two months of paper review had read past. Lean has no eyes. That, I have come to think, is the feature.

This work is one of the threads I am actively exploring, and a representative slice of what I find interesting in aerial manipulation, namely making the safety story explicit and verifiable rather than something the controller "should" be doing in the background.
