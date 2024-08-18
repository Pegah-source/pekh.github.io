---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
redirect_from:
  - /projects
---

{% include base_path %}

### [Adversarial corner case generation for motion planning](https://github.com/pegah-kh/kinematic_adversary_agents/blob/main/report.pdf)
  
[Code](https://github.com/pegah-kh/kinematic_adversary_agents)
[Report](https://github.com/pegah-kh/kinematic_adversary_agents/blob/main/report.pdf)

We attempted to develop a framework to stress-test vehicle planners by generating safety-critical driving scenarios. Recognizing that real-world scenarios are rare and costly, we used a realistic simulator, [nuPlan](https://www.nuscenes.org/nuplan) to create scenarios aimed at exposing potential collision risks. Building on the method introduced by [Han et al., 2022](https://arxiv.org/abs/2204.13683), we adapted it to a more complex environment with a wider range of agents and behaviors.

![Codebook Image](images/induced_collisions.png)
