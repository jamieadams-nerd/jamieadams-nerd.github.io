---
layout: page
---

Welcome.

I am a Software Engineer, security nerd, and longtime builder of high-assurance MLS/CDS systems. This site is a public notebook for engineering work and design reasoning, with a focus on high-assurance Linux systems and tooling. It's not ALL serious though -- you'll find some Easter eggs, some fun programming techniques, and other gems. 

## Projects
<img src="/assets/images/umrs-logo-1024px.png" align="right" width=200>
My primary project is the [UNCLASSIFIED MLS Reference System Project](https://github.com/jamieadams-nerd/umrs-project/blob/main/UMRS-PROJECT.md).
<p>UMRS is a hands-on, high-assurance engineering project built on Red Hat Enterprise Linux 10 in FIPS mode. It demonstrates how a real organization can design, implement, and operate a hardened Linux system using SELinux MLS and a complete unclassified label hierarchy for Controlled Unclassified Information (CUI), aligned with frameworks such as NIST SP 800-53 and the Cybersecurity Maturity Model Certification (CMMC).</p>

Beyond system configuration, UMRS develops high-assurance tools that are intentionally designed to be observable, reviewable, and auditable. These tools apply procedural controls, configuration isolation, and cryptographic techniques to help administrators and auditors examine system state, intent, and behavior from a high-assurance perspective—treating tooling itself as part of the assurance boundary.

Rather than describing security in theory, UMRS shows how commercial Linux can be deliberately tailored, locked down, and extended to meet concrete security and operational requirements.


Long-form documentation lives in project repositories. This site is for context, rationale, and ongoing work.


## Recent Posts

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }})  
  <span style="color:#999;">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

[All posts →](/posts/)
