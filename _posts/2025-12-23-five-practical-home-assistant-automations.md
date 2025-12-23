---
title: "Five Practical Home Assistant Automations"
date: 2025-12-23 08:00:00 -0700
categories: [Home Assistant]
tags: [automations, getting-started]
toc: true
comments: true
---

> This post contains affiliate links. If you buy through these links, I may earn a commission at no extra cost to you. Thanks for supporting the blog.
{: .prompt-info }

Home Assistant can do a lot on day one. Here are five simple automations that are easy to set up, genuinely useful, and won’t require advanced hardware. I’ll note where Zigbee/Z‑Wave help, but Wi‑Fi devices work great too.

## 1) Sunset Lighting

Turn on selected lights at sunset and turn them off at bedtime.

- Trigger: Sun → `sunset`
- Conditions: Only if someone is home
- Actions: Turn on living room lights; turn off at 11:30 PM

If you’re starting with Wi‑Fi plugs for lamps, these are reliable:
{% include amazon_link.html product="kasa_smart_plug" %}

## 2) Motion‑Activated Hall Lights

Light up a hallway when motion is detected, then auto‑off after a short delay.

- Trigger: Motion sensor → `on`
- Conditions: Only after sunset
- Actions: Turn on light, wait 2 minutes, turn off

Zigbee sensors have great battery life and low latency:
{% include amazon_link.html product="zigbee_dongle" %}

## 3) “Nobody’s Home” Energy Saver

When all tracked devices leave, turn off non‑essential plugs (office gear, lamps).

- Trigger: `person` → `not_home` (all household)
- Conditions: None
- Actions: Turn off selected switches/plugs

Start simple with a few plugs; expand as you go:
{% include amazon_link.html product="kasa_smart_plug" %}

## 4) Washer/Dryer Done Notifications

Get a mobile alert when the machine finishes based on plug power draw.

- Trigger: Smart plug power drops below threshold for N minutes
- Actions: Send mobile notification

This works with many plugs that report energy usage. If your plug doesn’t, you can still estimate with duration.

## 5) Morning Warm‑Up

Turn on a space heater or coffee machine for a short window when someone wakes up.

- Trigger: Time → 6:30 AM OR first motion in kitchen
- Conditions: Only on weekdays
- Actions: Turn on plug for 20 minutes

## Tips for Reliable Automations

- Prefer local integrations (ZHA/Zigbee2MQTT, Z‑Wave JS) for fast, offline‑friendly control.
- Use `conditions` to prevent automations from firing at the wrong time (e.g., daylight).
- Start with one room; build confidence before expanding.
- Name automations clearly: `Sunset – Living Room Lamps`, `Hall – Motion Nightlight`.

## Recommended Starter Hardware

- Easiest all‑in‑one hardware:
  {% include amazon_link.html product="home_assistant_green" %}
- DIY route:
  {% include amazon_link.html product="raspberry_pi_4_4gb" %} + {% include amazon_link.html product="usb_c_power_supply" %} + {% include amazon_link.html product="microsd_128gb_a2" %}
- Optional upgrades:
  {% include amazon_link.html product="ssd_enclosure_kit" %} for better storage
  {% include amazon_link.html product="zwave_stick" %} if you use Z‑Wave

---

Questions or a favorite automation you use? Drop a comment or email me at <a href="mailto:taylor@oneofthegeeks.com">taylor@oneofthegeeks.com</a>.

Read the full affiliate disclosure on [/disclosure/](/disclosure/).
