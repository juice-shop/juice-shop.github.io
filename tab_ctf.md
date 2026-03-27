---
title: CTF
layout: default
---

## Official Multi User Platform

[![MultiJuicer Logo](https://raw.githubusercontent.com/juice-shop/multi-juicer/master/images/multijuicer-with-text.png)](https://github.com/juice-shop/multi-juicer)

Multi User Juice Shop Platform to run separate Juice Shop instances for training or CTF participants on a central Kubernetes cluster. [MultiJuicer](https://github.com/juice-shop/multi-juicer) comes with a built-in leader board and its own dedicated Juice Balancer for instance isolation. It even comes with a sophisticated world globe as a CTF leaderboard for the big screen or projector.

### Architecture

<div class="image-flex">
<img src="https://juice-shop.github.io/juice-shop/assets/JuicyCTF_Architecture.svg" alt="MultiJuicer Architecture" class="architecture-diagram">
</div>

### Screenshots

<div class="image-grid">
  <img src="https://raw.githubusercontent.com/juice-shop/pwning-juice-shop/master/docs/modules/ROOT/assets/images/part4/multi-juicer_register.png" alt="Screenshot 1">
  <img src="https://raw.githubusercontent.com/juice-shop/pwning-juice-shop/master/docs/modules/ROOT/assets/images/part4/multi-juicer_scoreboard.png" alt="Screenshot 2">
  <img src="https://juice-shop.github.io/juice-shop/assets/multi-juicer-ctf-view.jpg" alt="Screenshot 3">
</div>

## CTF Extension

[![GitHub release](https://img.shields.io/github/release/juice-shop/juice-shop-ctf.svg)](https://github.com/juice-shop/juice-shop-ctf/releases/latest)
[![GitHub stars](https://img.shields.io/github/stars/juice-shop/juice-shop-ctf.svg?label=GitHub%20%E2%98%85&style=flat)](https://github.com/juice-shop/juice-shop-ctf)

The Node package
[`juice-shop-ctf-cli`](https://www.npmjs.com/package/juice-shop-ctf-cli)
helps you to prepare
[Capture the Flag](https://en.wikipedia.org/wiki/Capture_the_flag#Computer_security)
events with the OWASP Juice Shop challenges for different popular CTF
frameworks. This interactive utility allows you to populate a CTF game
server in a matter of minutes.

![Juice Shop CLI in Powershell](https://raw.githubusercontent.com/juice-shop/juice-shop-ctf/master/images/juice-shop-ctf-cli.png)

### Supported CTF Frameworks

The following open source CTF frameworks are supported by
`juice-shop-ctf-cli`:

* [CTFd](https://github.com/CTFd/CTFd)
* [FBCTF](https://github.com/facebook/fbctf)
* [RootTheBox](https://github.com/moloch--/RootTheBox)
