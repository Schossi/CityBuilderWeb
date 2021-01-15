---
permalink: /manual/risks
title: "Risks"
sidebar:
  title: "Manual"
  nav: manual
---

Risks are values on Buildings that increase over time and cause some event when full. RiskWalkers roam around reducing the Risk values of RiskRecipients they pass.
>fire, collapse, disease

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-15T18:45:09.071Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;HZyLZJtNiXjE51AI7cPx\&quot; version=\&quot;14.2.3\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;s3Ydoy8WXJicPXpNoJ6Y\&quot; name=\&quot;Risks\&quot;&gt;7ZldU6MwFIZ/TS/tAAGKl7Z1XWfWmR0dx+sUDpA1JWxILfXXb5BQyoe2uK2l6k0b3iQn4cnJxwkDNJmnVxzH4Q3zgA4MzUsHaDowDHNkyt9MWOWCYVu5EHDi5ZJeCnfkGZSoKXVBPEgqBQVjVJC4KrosisAVFQ1zzpbVYj6j1VZjHEBDuHMxbaoPxBNhrjqWVuo/gQRh0bKuqZw5LgorIQmxx5YbErocoAlnTOSpeToBmrFbczEBXyaBE92nzr0+Wd7/wfZZbuxHlyrrV+AQif2aNnLTT5guFC/1rmJVAORsEXmQGdEGaLwMiYC7GLtZ7lJ6jNRCMafySZdJZQ64gLTGf0vn9TVR6YnA5iD4StZTVlAxCKva87IcU1NJ4cZwFhpWXhSsLZekZELB6gAOnQo4u2fgzBMBZ2o9A2edCjizZ+DsUwHn9AzcqAWcTWWr4yTGUYWg/XeRbYNjn0XiLHk5BFzIAroWp2WmTAXZ//UtSR4LU7JnubU8r5Bn/P3299PLW3BJTIbD4as9/R8n8gmlE0YZf6mLPAyO72Z9Fpw9wkaO7Tow8z9whzCcI7ud8+12X8Dt6vvr0d3u/NvtvoLbmcdzu19ecGPr0+fpFb59vh6T+TQ2VdD25ulEBp5xlvQppBdZSCz5QOSp5NSlOEmI23ZIAa8RHL+P3gYdq4VOoXGgWJCnapttyFQLvxmRvSm3IseqnoDQ+dBBVSsJW3AXVMXNcLdmy7S32xKYByAatl7Gcf3y719R9ObYbq4F2aTPJ9cDpo/AG+MumyBxAp2nl++D7bZOL290PtO0Txo1tU4vffv0Klcy/Yhx+qi2LqEmOOONmbd3cJ1uhnYAV/dRx4V2H505lmkd0kcbqEe7odYPhbrTXdIRfdTUe+ajna5EjgnO6hm4TlciJzW5G6jN3VAfbANqXqJc1w8Bezizf+zhPOud+tKjH3SlNnp2WG+7mujjgoNQzxactuD6cyw4DdT2bqiN7qjlY/m1MQ9Syk+26PIf&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

CCBK comes with Risks that add Addons to Buildings or replace the Building with other structures or Buildings.  
To add Risks that execute other actions simply inherit from Risk and implement the Execute and Resolve methods.