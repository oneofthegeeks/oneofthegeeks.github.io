---
title: "Getting Started with Home Assistant"
date: 2025-12-23 10:00:00 -0700
categories: [Home Assistant]
tags: [getting-started, hardware, automations, affiliates]
toc: true
comments: true
---

> This post contains affiliate links. If you buy through these links, I may earn a commission at no extra cost to you. Thanks for supporting the blog.
{: .prompt-info }

Home Assistant is a powerful, open‑source home automation platform that runs locally and keeps your data under your control. Here’s a simple, opinionated path to get up and running fast, plus gear I’ve used and recommend.

## What You’ll Need

- A small, always‑on computer (Raspberry Pi or mini PC)
- Storage (microSD or SSD)
- A Zigbee/Z‑Wave radio (optional, but recommended)
- Your home network (Ethernet preferred)

## Recommended Hardware

- Home Assistant Green — easiest official hardware:
  {% include amazon_link.html product="home_assistant_green" %}
- Raspberry Pi 4 (4GB) — DIY starter:
  {% include amazon_link.html product="raspberry_pi_4_4gb" %}
- Power supply for Pi:
  {% include amazon_link.html product="usb_c_power_supply" %}
- microSD card (or use an SSD for longevity):
  {% include amazon_link.html product="microsd_128gb_a2" %}
- Optional SSD kit for Pi:
  {% include amazon_link.html product="ssd_enclosure_kit" %}
- Zigbee USB dongle (for sensors and bulbs):
  {% include amazon_link.html product="zigbee_dongle" %}
- Z‑Wave USB stick (if you have Z‑Wave gear):
  {% include amazon_link.html product="zwave_stick" %}
- Wi‑Fi smart plugs (easy first automation):
  {% include amazon_link.html product="kasa_smart_plug" %}

## Install Home Assistant (HAOS on Raspberry Pi)

1. Download **Home Assistant OS** image for Raspberry Pi from the official docs.
2. Flash the image to your microSD using **Raspberry Pi Imager** or **balenaEtcher**.
3. Insert microSD, connect Ethernet, power on the Pi.
4. Wait ~5–10 minutes, then open `http://homeassistant.local:8123` (or find the Pi’s IP).
5. Create your account and finish onboarding.

## Optional: Install via Docker (on a mini PC)

If you prefer a beefier machine:

- Install Docker and run Home Assistant Container (note: lacks Supervisor/add‑on store).
- Map volumes for persistent config; expose port `8123`.
- Consider **Home Assistant Supervised** only if you know the tradeoffs.

## First Integrations

- Start with built‑ins: **Energy**, **Weather**, **Mobile App**.
- Add cloud devices (Hue, TP‑Link/Kasa, Sonos) via Integrations.
- Pair Zigbee devices using **Zigbee2MQTT** or **ZHA**; Z‑Wave via **Z‑Wave JS**.

## Simple Automations to Try

- Turn lights on at sunset and off at bedtime.
- Motion‑activated lights in hallways.
- Turn off office plug if nobody’s home.
- Notify when washer/dryer finishes (smart plug power draw).

## Securing Your Setup

- Keep HA inside your network; use **Cloudflare Tunnel** or **VPN** for remote access.
- Enable MFA for your account.
- Regular backups (Settings → System → Backups). Store off‑device.

## My Starter Kit (Summary)

- {% include amazon_link.html product="home_assistant_green" %}
- {% include amazon_link.html product="zigbee_dongle" %}
- {% include amazon_link.html product="kasa_smart_plug" %}

---

If you pick up gear through these links, it helps me keep writing. Questions or stuck on setup? Comment below or email me at <a href="mailto:taylor@oneofthegeeks.com">taylor@oneofthegeeks.com</a>.

Read the full affiliate disclosure on [/disclosure/](/disclosure/).
