---
title: "UX Patterns for Nostr Apps"
description: "Evidence-informed patterns for building Nostr apps people actually use"
layout: hextra-home
---

<div class="hx:mt-6 hx:mb-6">
{{< hextra/hero-headline >}}
  UX Patterns for&nbsp;<br class="hx:sm:block hx:hidden" />Nostr Apps
{{< /hextra/hero-headline >}}
</div>

<div class="hx:mb-12">
{{< hextra/hero-subtitle >}}
  Evidence-informed patterns for building Nostr apps people actually use
{{< /hextra/hero-subtitle >}}
</div>

<div class="hx:mb-6">
{{< hextra/hero-button text="Get Started" link="docs/introduction/" >}}
</div>

<div class="hx:mt-6"></div>

{{< hextra/feature-grid >}}
  {{< hextra/feature-card
    title="Validation Framework"
    subtitle="A 3-question filter for every feature decision."
    class="hx:aspect-auto hx:md:aspect-[1.1/1] hx:max-md:min-h-[340px]"
    image="images/validation.png"
    imageClass="hx:top-[40%] hx:left-[24px] hx:w-[110%] hx:sm:w-[110%] hx:dark:opacity-80"
  >}}
  {{< hextra/feature-card
    title="Quick Wins"
    subtitle="18 high-impact, low-effort improvements by pattern area."
    class="hx:aspect-auto hx:md:aspect-[1.1/1] hx:max-lg:min-h-[340px]"
    image="images/quick-wins.png"
    imageClass="hx:top-[40%] hx:left-[36px] hx:w-[110%] hx:sm:w-[110%] hx:dark:opacity-80"
  >}}
  {{< hextra/feature-card
    title="Implementation Guide"
    subtitle="Practical guidance: which pattern first, how to measure, what to avoid."
    class="hx:aspect-auto hx:md:aspect-[1.1/1] hx:max-md:min-h-[340px]"
    image="images/implementation.png"
    imageClass="hx:top-[40%] hx:left-[36px] hx:w-[110%] hx:sm:w-[110%] hx:dark:opacity-80"
  >}}
{{< /hextra/feature-grid >}}

<div class="hx:mt-8"></div>

{{< hextra/feature-grid cols="3" >}}
  {{< hextra/feature-card
    title="Onboarding"
    subtitle="Minimize time-to-first-value during setup and first run."
    icon="user-add"
  >}}
  {{< hextra/feature-card
    title="Content Discovery"
    subtitle="Smart defaults and discovery mechanisms for the cold start problem."
    icon="sparkles"
  >}}
  {{< hextra/feature-card
    title="Core Interactions"
    subtitle="Reliable interactions with optimistic UI and error handling."
    icon="cursor-click"
  >}}
  {{< hextra/feature-card
    title="Performance"
    subtitle="Skeleton screens, caching, and perceived performance strategies."
    icon="lightning-bolt"
  >}}
  {{< hextra/feature-card
    title="Progressive Complexity"
    subtitle="Progressive disclosure patterns for managing complexity."
    icon="adjustments"
  >}}
  {{< hextra/feature-card
    title="Cross-Client Consistency"
    subtitle="Multi-relay write strategies and data integrity patterns."
    icon="shield-check"
  >}}
{{< /hextra/feature-grid >}}
