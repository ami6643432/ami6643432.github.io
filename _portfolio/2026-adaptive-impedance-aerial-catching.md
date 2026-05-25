---
title: "Adaptive Impedance Control with Payload-Mass Estimation for Aerial Catching"
excerpt: "A 2R arm on a hovering quadrotor catches a thrown ball; the controller estimates the payload mass on impact while keeping the wrench delivered back to the base under control.<br/><img src='/images/portfolio/catching-compliant-catch.gif' style='max-width:100%;'>"
collection: portfolio
header:
  teaser: portfolio/catching-compliant-catch.gif
---

<figure class="pf-hero">
  <img src="/images/portfolio/catching-compliant-catch.gif" alt="MuJoCo simulation of a 2R arm catching a thrown ball with compliant settling">
  <figcaption class="pf-hero-caption">A lateral catch in MuJoCo with the controller I have been exploring. The arm yields on impact, settles compliantly, and the base stays controllable through the transient.</figcaption>
</figure>

<div class="pf-tldr">
A 2R planar arm on a hovering quadrotor catches a thrown ball. The controller estimates the payload mass during the impact transient, softens the impedance once a payload is detected, and keeps the wrench transmitted back to the base inside what an attitude controller can absorb. Sixteen-controller benchmark, like-for-like comparison.
</div>

## The scenario I keep returning to

Picture a 2R planar arm mounted on a hovering quadrotor. Someone throws a ball into its workspace. The arm has to catch the ball, settle the contact, and do all of that without transmitting a wrench to the base that the attitude controller cannot absorb. Most aerial-manipulation work handles one of those three things well. This thread is my attempt to look at all three together, because in practice they are not separable.

## What the controller is trying to do

Three ideas sit on top of standard impedance control:

1. **Payload-mass estimation** runs in the milliseconds right after impact. The estimate enters the impedance law directly, so the usual stiff-to-soft tradeoff softens once the arm knows what it is holding.
2. **Like-for-like comparison.** The numbers I am willing to publish are the ones that hold up against PD, sliding-mode, and naive-adaptive baselines on identical catching trajectories. The comparison is the experiment, not an afterthought.
3. **A base-wrench audit.** Tip-tracking error gets most of the attention in aerial manipulation papers; the wrench transmitted to the base usually does not. Both are measured here, and the base wrench is treated as a first-class metric rather than a footnote.

## Benchmark snapshots

A sixteen-controller benchmark on a shared catching scene, with identical impact conditions. The cuts are intentionally honest: the controller I am exploring does not win every column. It wins the ones I argue matter most for whether something like this could fly outside a lab.

<div class="pf-grid pf-grid-2">
  <figure class="pf-figure">
    <img src="/images/portfolio/catching-baseline-comparison.png" alt="Tracking and impedance error across baseline controllers">
    <figcaption>Tip tracking and impedance error across baseline controllers on the same catching scene.</figcaption>
  </figure>
  <figure class="pf-figure">
    <img src="/images/portfolio/catching-base-wrench.png" alt="Base wrench norm comparison across controllers">
    <figcaption>Base wrench norm, the quantity most aerial-manipulation comparisons leave out.</figcaption>
  </figure>
</div>

## Video

<figure class="pf-figure">
  <video controls preload="metadata">
    <source src="/files/catching-side-by-side.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption>Side-by-side comparison of the proposed controller against the baselines on the same catching scene, rendered in MuJoCo. Same impact conditions, identical reference, only the controller changes between panels.</figcaption>
</figure>

This is one of the threads I am currently exploring, and a fair illustration of where my research interests sit: contact-rich aerial manipulation, where the controller, the model, and the platform all have to be honest with each other.
