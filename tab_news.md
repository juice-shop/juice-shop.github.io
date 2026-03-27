---
title: News
layout: default
---

## Upcoming Challenges

The following challenges are planned for release with the next version of OWASP Juice Shop.

{% assign dev_challenges = site.data.challenges_dev %}
{% assign prod_challenges = site.data.challenges %}
{% assign dev_snippets = site.data.snippets_dev.challenges %}
{% assign prod_snippets = site.data.snippets.challenges %}

{% assign prod_categories = "" | split: "," %}
{% assign prod_tags = "" | split: "," %}
{% for prod_ch in prod_challenges %}
  {% assign prod_categories = prod_categories | push: prod_ch.category %}
  {% if prod_ch.tags %}
    {% for tag in prod_ch.tags %}
      {% assign prod_tags = prod_tags | push: tag %}
    {% endfor %}
  {% endif %}
{% endfor %}
{% assign prod_categories = prod_categories | uniq %}
{% assign prod_tags = prod_tags | uniq %}

{% assign upcoming_challenges = "" | split: "," %}

{% for dev_ch in dev_challenges %}
  {% assign is_new_hacking = true %}
  {% for prod_ch in prod_challenges %}
    {% if dev_ch.key == prod_ch.key %}
      {% assign is_new_hacking = false %}
      {% break %}
    {% endif %}
  {% endfor %}

  {% assign is_new_coding = false %}
  {% if dev_snippets contains dev_ch.key %}
    {% unless prod_snippets contains dev_ch.key %}
      {% assign is_new_coding = true %}
    {% endunless %}
  {% endif %}

  {% if is_new_hacking or is_new_coding %}
    {% capture row %}
    <tr>
      <td>{% if is_new_hacking %}<i class="fas fa-certificate" style="color: var(--accent-color);"></i> {% endif %}{{ dev_ch.name }}</td>
      <td style="text-align: center;">
        {% unless prod_categories contains dev_ch.category %}<i class="fas fa-certificate" style="color: var(--accent-color);"></i> {% endunless %}{{ dev_ch.category }}
      </td>
      <td style="text-align: center;">
        {% for i in (1..dev_ch.difficulty) %}<i class="fas fa-star"></i>{% endfor %}
      </td>
      <td style="text-align: center;">
        {% if dev_snippets contains dev_ch.key %}
          {% if is_new_hacking != true and is_new_coding %}<i class="fas fa-certificate" style="color: var(--accent-color);"></i> {% endif %}<i class="fas fa-check"></i>
        {% endif %}
      </td>
      <td style="text-align: center;">
        {% assign tags_with_new_icon = "" | split: "," %}
        {% for tag in dev_ch.tags %}
          {% assign tag_to_display = tag %}
          {% unless prod_tags contains tag %}
            {% capture tag_to_display %}<i class="fas fa-certificate" style="color: var(--accent-color);"></i> {{ tag }}{% endcapture %}
          {% endunless %}
          {% assign tags_with_new_icon = tags_with_new_icon | push: tag_to_display %}
        {% endfor %}
        {{ tags_with_new_icon | join: ", " }}
      </td>
    </tr>
    {% endcapture %}
    {% assign upcoming_challenges = upcoming_challenges | push: row %}
  {% endif %}
{% endfor %}

{% if upcoming_challenges.size > 0 %}
<table>
  <thead>
    <tr>
      <th>Challenge</th>
      <th style="text-align: center;">Category</th>
      <th style="text-align: center;">Difficulty</th>
      <th style="text-align: center;">Coding Challenge</th>
      <th style="text-align: center;">Tags</th>
    </tr>
  </thead>
  <tbody>
    {% for row in upcoming_challenges %}
      {{ row }}
    {% endfor %}
  </tbody>
</table>
{% endif %}

## Latest Releases

[![GitHub release](https://img.shields.io/github/release/juice-shop/juice-shop.svg?style=for-the-badge)](https://github.com/juice-shop/juice-shop/releases/latest)
[![GitHub release](https://img.shields.io/github/downloads/juice-shop/juice-shop/total.svg?style=for-the-badge)](https://github.com/juice-shop/juice-shop/releases/latest)
[![SourceForge](https://img.shields.io/sourceforge/dm/juice-shop?style=for-the-badge&label=sourceforge%20downloads)](https://sourceforge.net/projects/juice-shop/)
[![SourceForge](https://img.shields.io/sourceforge/dt/juice-shop?style=for-the-badge&label=sourceforge%20downloads)](https://sourceforge.net/projects/juice-shop/)
[![Docker Pulls](https://img.shields.io/docker/pulls/bkimminich/juice-shop.svg?style=for-the-badge)](https://hub.docker.com/r/bkimminich/juice-shop)

<!-- next:juice-shop -->
* 2026-03-07T12:17:04Z: juice-shop [`v19.2.1`](https://github.com/juice-shop/juice-shop/releases/tag/v19.2.1)
* 2026-03-07T10:16:27Z: juice-shop [`v19.2.0`](https://github.com/juice-shop/juice-shop/releases/tag/v19.2.0)
* 2025-11-16T14:47:08Z: juice-shop [`v19.1.1`](https://github.com/juice-shop/juice-shop/releases/tag/v19.1.1)

### CTF Extension

[![GitHub release](https://img.shields.io/github/release/juice-shop/juice-shop-ctf.svg?style=for-the-badge)](https://github.com/juice-shop/juice-shop-ctf/releases/latest)
[![npm](https://img.shields.io/npm/dm/juice-shop-ctf-cli.svg?style=for-the-badge)](https://www.npmjs.com/package/juice-shop-ctf-cli)
[![npm](https://img.shields.io/npm/dt/juice-shop-ctf-cli.svg?style=for-the-badge)](https://www.npmjs.com/package/juice-shop-ctf-cli)
[![Docker Pulls](https://img.shields.io/docker/pulls/bkimminich/juice-shop-ctf.svg?style=for-the-badge)](https://hub.docker.com/r/bkimminich/juice-shop-ctf)

<!-- next:juice-shop-ctf -->
* 2025-09-04T06:11:47Z: juice-shop-ctf [`v12.0.0`](https://github.com/juice-shop/juice-shop-ctf/releases/tag/v12.0.0)
* 2025-02-18T11:19:13Z: juice-shop-ctf [`v11.1.0`](https://github.com/juice-shop/juice-shop-ctf/releases/tag/v11.1.0)
* 2024-10-25T14:30:28Z: juice-shop-ctf [`v11.0.0`](https://github.com/juice-shop/juice-shop-ctf/releases/tag/v11.0.0)

### MultiJuicer

[![GitHub release](https://img.shields.io/github/release/juice-shop/multi-juicer.svg?style=for-the-badge)](https://github.com/juice-shop/juice-shop-ctf/releases/latest)

<!-- next:multi-juicer -->
* 2026-02-12T19:50:54Z: multi-juicer [`v9.2.0`](https://github.com/juice-shop/multi-juicer/releases/tag/v9.2.0)
* 2026-01-25T21:15:53Z: multi-juicer [`v9.1.0`](https://github.com/juice-shop/multi-juicer/releases/tag/v9.1.0)
* 2025-11-22T17:39:28Z: multi-juicer [`v9.0.0`](https://github.com/juice-shop/multi-juicer/releases/tag/v9.0.0)

## Roadmap

![GitHub issues by-label](https://img.shields.io/github/issues/juice-shop/juice-shop/help%20wanted.svg?style=for-the-badge)
![GitHub issues by-label](https://img.shields.io/github/issues/juice-shop/juice-shop/good%20first%20issue.svg?style=for-the-badge)

{% assign milestones = site.data.roadmap_milestones %}
{% for milestone in milestones %}
* {{ milestone }}
{% endfor %}
