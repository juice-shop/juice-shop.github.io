---
title: Challenges
layout: default
---

## Challenge Categories

{% assign categories = site.data.challenges | group_by:"category" | sort: "name" %}

The vulnerabilities found in the OWASP Juice Shop are categorized into
several different classes. Most of them cover different risk or
vulnerability types from well-known lists or documents, such as
[OWASP Top 10](https://owasp.org/www-project-top-ten/),
[OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/),
[OWASP Automated Threat Handbook](https://owasp.org/www-project-automated-threats-to-web-applications/)
and
[OWASP API Security Top 10](https://owasp.org/www-project-api-security/)
or MITRE's
[Common Weakness Enumeration](https://cwe.mitre.org/).

<table>
  <tr>
    <th class="col-category">Category</th>
    <th class="col-count">#</th>
    <th>Challenges</th>
  </tr>
  {% for category in categories %}
  <tr>
    <td class="col-category">{{ category.name }}</td>
    <td class="col-count">{{ category.items.size }}</td>
    <td><small>{{ category.items | group_by:"name" | sort: "name" | map: "name" | join: ", " }}</small></td>
  </tr>
  {% endfor %}
  <tr>
    <td><strong>Total Σ</strong></td>
    <td colspan="2">{{ site.data.challenges.size }}</td>
  </tr>
</table>

## Challenge Tags

{% assign tags = site.data.challenges | map: "tags" | uniq | join: "," | replace: ",,", "," | split: "," | sort  %}

Tags do not represent vulnerability categories but serve as additional
meta information for challenges. They mark certain commonalities or
special types of challenges - like those lacking seriousness or ones
that probably need some scripting/automation etc.

<table>
  <tr>
    <th class="col-category">Tag</th>
    <th class="col-count">#</th>
    <th>Challenges</th>
  </tr>
  {% for tag in tags %}
  {% unless tag == "" or tag == nil %}
  {% assign taggedChallenges = site.data.challenges | group_by: "tags" | where_exp:"item", "item.name contains tag" | map: "items" | map: "name" %}
  <tr>
    <td class="col-category">{{ tag }}</td>
    <td class="col-count">
      {{ taggedChallenges.size }}
    </td>
    <td><small>
      {{ taggedChallenges | sort | join: ", " }}
    </small></td>
  </tr>
  {% endunless %}
  {% endfor %}
</table>

