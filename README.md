# cloud server linux: how to pick a plan you won't overpay for, with Sharktech's full price sheet and real annual costs

Searching for "cloud server linux" usually means one of two things: you need a cheap root server to deploy something on, or you're comparing providers and every pricing page looks the same until you hit the fine print. Both come down to the same three questions — what does it cost over a year, what's actually included, and what happens when something goes wrong.

This article answers those questions using Sharktech, a Las Vegas-based hosting company that has been running its own infrastructure since 2003. Its Linux cloud servers start at **$7.95/month** (with annual billing cutting that to **$3.98/month**), and every plan ships with 60Gbps DDoS protection at no extra charge. Below you'll find the full plan table, the real annual totals, the billing quirks that don't show up on the landing page, and the situations where this provider is a bad fit.

> **Quick picks**
> - Most people testing the waters: **SmartVPS entry tier**, $7.95/mo monthly or $3.98/mo on annual billing (billed once a year). 👉 [check current SmartVPS pricing and build your pool](https://bit.ly/SharKtech)
> - Running multiple VMs or need OpenStack features: **Public Cloud Small**, from $39/mo
> - One warning before you click: Sharktech has **no refund policy** — all payments are nonrefundable. Details below.

## What "cloud server linux" actually buys you here

Sharktech sells Linux cloud servers in three shapes, and they behave very differently, so it's worth knowing which one you're looking at before comparing prices.

**SmartVPS** is the main product and the one most people searching this keyword want. It runs on Proxmox clusters with Xeon Gold CPUs and enterprise NVMe storage, gives you full root access, and supports the usual distros: Ubuntu, CentOS, Debian and AlmaLinux. Instead of buying a fixed server, you buy a **resource pool** — one lump of CPU, RAM, storage and bandwidth that you can split across one or many virtual machines, deployed in any of five locations: Los Angeles, Las Vegas, Denver, Chicago or Amsterdam.

**Public Cloud** is the OpenStack-based option. You get the full OpenStack API (Nova, Cinder, Swift, Neutron, Keystone), cloud-init, custom ISO/qcow2 uploads, security groups, load balancers, virtual routers and floating IPs — the primitives you need if you're building something more complex than a single box, or migrating workloads off a hyperscaler.

**Dedicated Cloud** uses the same OpenStack base but with prepaid fixed resources and a predictable monthly bill, in tiers from Tiny up to 3XL.

All three sit on the same network: five self-owned datacenters, a 40G/100G internal backbone, and Sharktech's own ISP network (AS46844, publicly verifiable on bgp.tools and peeringdb) with Tier-1 upstreams including China Telecom, China Mobile, Comcast and GTT.

## SmartVPS plans and pricing

Here is the full SmartVPS lineup. Monthly prices are the standard rates; longer billing cycles apply automatic discounts — **25% off quarterly, 35% off semi-annually, 50% off annually** — with no promo code needed.

| Plan | vCPU / RAM | NVMe | Transfer | Monthly | Annual (per month) |
| --- | --- | --- | --- | --- | --- |
| [Tiny](https://bit.ly/SharKtech) | 1 core / 2 GB | 40 GB | 4 TB | $7.95 | $3.98 |
| [Small](https://bit.ly/SharKtech) | 2 cores / 4 GB | 80 GB | 8 TB | $15.95 | $7.98 |
| [Medium](https://bit.ly/SharKtech) | 4 cores / 8 GB | 160 GB | 16 TB | $31.95 | $15.98 |
| [Large](https://bit.ly/SharKtech) | 8 cores / 16 GB | 320 GB | 32 TB | $63.95 | $31.98 |
| [XL](https://bit.ly/SharKtech) | 16 cores / 32 GB | 640 GB | 64 TB | $127.95 | $63.98 |

One honest caveat on the specs: Sharktech's own configurator currently describes the $7.95 starting point as "2 vCPU + 4 GB RAM," while most third-party price sheets list the entry Tiny tier at 1 vCPU / 2 GB. The prices and the RAM/storage/transfer allocations above are consistent across sources; the exact vCPU count per tier is the one number worth confirming on the order page before you pay. Every plan includes Xeon Gold CPUs, NVMe storage, a 10Gbps port, one IPv4 address, and 60Gbps DDoS protection on every IP.

The pool tops out at 128 vCPU / 256 GB, and you can add storage, bandwidth and extra IPv4s through the customer portal (IPv6 is free; extra IPv4 addresses run $1.50/month each).

## What a year actually costs

The headline discount is 50% off annual billing, but the number that matters is the total leaving your card. Based on the annual rates above:

| Plan | Annual per month | First-year total |
| --- | --- | --- |
| Tiny | $3.98 | $47.76 |
| Small | $7.98 | $95.76 |
| Medium | $15.98 | $191.76 |
| Large | $31.98 | $383.76 |
| XL | $63.98 | $767.76 |

So the cheapest legitimate entry into a DDoS-protected, NVMe-backed Linux VPS here is about **$47.76 for a full year** — less than many shared hosting plans, and this one gives you root on your own kernel with dedicated resources. Note that this discount applies at renewal too, since it's a billing-cycle rate rather than a first-term promo; there's no bait-and-switch from intro price to renewal price, because there's only one price per cycle.

There's no free trial and no refund window, which changes how you should approach the first purchase: if you're unsure about the platform, pay monthly ($7.95) for a month or two before committing to the annual rate. 👉 [open the SmartVPS configurator and pick your billing cycle](https://bit.ly/SharKtech)

## The resource pool: one bill, several Linux VMs

This is the feature most comparisons skip, and it changes the value math once you run more than one server.

You're buying capacity, not boxes. A Medium pool, for example, can run as one 4-core production VM, four 1-core dev VMs, or two 2-core staging machines — same monthly bill. Each VM can live in a different datacenter: a production box in Los Angeles, a database in Chicago, a game server in Amsterdam. Scaling up or down happens through the portal without reinstalling.

For a typical multi-environment setup — production, staging, a couple of dev sandboxes — this undercuts buying four separate VPS plans, because you're not paying four times for the "privilege" of having four machines. It also means the entry plan is genuinely usable as a multi-VM setup rather than a toy.

## Public Cloud: OpenStack when you outgrow a VPS

Public Cloud is the step up when you need real cloud primitives. The fixed-price tiers look like this:

| Tier | vCPU | RAM | Storage | Outbound | Starts at |
| --- | --- | --- | --- | --- | --- |
| Small | 4–16 cores | 8–32 GB | 300 GB | 20 TB | $39/mo |
| Enterprise | 64+ cores | 128+ GB | 5,000 GB | 20 TB | $499/mo |

Medium and Large tiers sit in between with configurable resources. Two things worth knowing before you pick this over SmartVPS:

**Billing above your committed resources is hourly**, with published rates: $0.0025/hr per vCPU core, $0.0035/hr per GB of RAM, and storage from $0.000090/hr per GB (NVMe) down to $0.000020/hr per GB (HDD). The Small-to-Large tiers have hard resource caps so a runaway script can't produce a surprise invoice; only the Enterprise tier is uncapped. Inbound traffic is free and unmetered; outbound beyond your included allocation costs $0.002/GB, and extra public IPv4 addresses are $1.50/month.

**The storage tiers differ meaningfully.** Official reference figures put NVMe at roughly 1.2 GB/s sequential and 18,000 IOPS, SSD at ~350 MB/s and 6,000 IOPS, HDD at ~120 MB/s and 3,000 IOPS. If you're running a database or anything IO-hungry on Linux, the NVMe tier is where your money should go — the price gap is small compared to what slow disk does to query latency.

For deployment, you get weekly-updated official Linux cloud images, cloud-init support, custom ISO uploads, and one-click Kubernetes clusters from the console. If you're leaving AWS or Azure and want OpenStack-style tooling without hyperscaler egress fees, this is the product to look at. 👉 [compare the Public Cloud tiers and hourly rates](https://bit.ly/SharKtech)

## The 60Gbps DDoS question

DDoS protection is included free on every IP across all products, filtering up to 60Gbps automatically at the network level — and given that Sharktech started as a DDoS-mitigation business in 2003, it's their own filtering stack rather than a bolted-on third-party service. Higher mitigation capacity is available; third-party guides cite upgrade paths ranging from 100Gbps to 1Tbps, so confirm current limits with sales if you need more than the standard cap.

Why this matters for the "cloud server linux" search specifically: budget Linux VPS providers are the segment where "DDoS protection" is most often a paid upsell or a suspension trigger. Sharktech's own game-server customers have described this directly — Dingdian Network reported their servers absorbing frequent 3–8Gbps attacks without interruption, and Kill-Streak Gaming has said similar things publicly. If your Linux box is running a game server, a public-facing API, or anything that attracts traffic you didn't ask for, this is the single biggest differentiator versus a generic cheap VPS. Sharktech's own marketing also compares against AWS Shield Advanced, which starts around $3,000/month — take that comparison with the usual vendor-grain of salt, but it gives you the scale of what bundled protection replaces.

## Linux support, Windows, and the add-ons that cost extra

Linux is the first-class citizen here. Ubuntu, CentOS, Debian and AlmaLinux are all available, you get full root access, and on Public Cloud you can upload your own ISO if you run something less common.

The extras, so you're not surprised at checkout:

- **cPanel** on a VPS: $25/month on top of the plan price
- **Windows Server**: supported but needs its own license (yours or purchased through them), installed via ISO yourself
- **Extra IPv4**: $1.50/month each after the first free one; IPv6 is free

## Before you pay: refunds, billing and account verification

The fine print here is short but important.

**There is no money-back guarantee.** Sharktech's terms state that all payments are nonrefundable, including setup fees and monthly charges. Billing disputes must be raised within 30 days of the invoice date, and a dispute resolved in your favor comes back as account credit. Plan your first purchase accordingly — monthly billing exists precisely for this.

**Anti-fraud is strict.** Registration requires your real name, address and contact details, and accounts created with fake information get banned. If you're buying for a company, register under the company's actual details.

**Payment options are unusually broad** for a US provider: credit card, PayPal, wire transfer, Western Union, Alipay, and crypto. The Alipay support is why this provider has a following among Chinese-speaking users, who also get a Chinese-language interface and Chinese pre-sales support.

**Support assumes you know your way around a terminal.** The knowledge base is thin and covers basics; the 24/7 ticket team is responsive (HostAdvice rated support 9.3/10 overall, with the company scoring 9.3 across the board), but nobody is going to configure your nginx for you.

On reputation, the honest picture is mixed-to-good: HostAdvice's technical review praised 6,000+ random IOPS and sub-millisecond network latency ("Sharktech delivers genuine power"), and WHTop users with 3–5 year tenures describe support as fast — while Trustpilot sits at 3.5/5 from a very small sample of 13 reviews. Read both before deciding.

## FAQ

**Which Linux distributions can I run?**
Ubuntu, CentOS, Debian and AlmaLinux on SmartVPS; Public Cloud adds weekly-updated official cloud images, cloud-init support and custom ISO uploads for anything else.

**Can I run Docker and Kubernetes?**
Yes. You have full root access on SmartVPS, so any container runtime works. Public Cloud additionally offers Kubernetes cluster deployment from the console, plus load balancers and security groups.

**Is the annual discount a first-term-only promo?**
No. The 50% off annual (25% quarterly, 35% semi-annual) is the standard billing-cycle rate, applied automatically with no coupon, so renewal costs the same as your first year.

**What happens if my server gets attacked?**
Mitigation up to 60Gbps per IP is automatic and included; the goal is filtering malicious traffic before it touches your machine, rather than null-routing you during an attack.

**Is there a trial or refund?**
Neither. All payments are nonrefundable, so use monthly billing for your first month if you're evaluating.

## Which plan for which reader

Running one or two Linux servers, a blog, a bot, or a small API: the **Tiny or Small** SmartVPS tier covers it, and annual billing at $47.76 or $95.76 a year is hard to argue with — just be comfortable with no-refund terms before choosing the yearly cycle.

Splitting workloads across dev, staging and production: **Medium or Large**, where the resource-pool model lets you carve multiple VMs out of one bill instead of buying separate servers.

Needing OpenStack APIs, Kubernetes, hourly elasticity or custom ISOs: **Public Cloud Small at $39/mo** is the entry point, with the Enterprise tier at $499/mo as the realistic exit ramp from a hyperscaler for compute-heavy workloads.

And if you need hand-holding, a money-back trial period, or locations in Asia — none of which Sharktech offers — you're better off with a provider that does. Everyone else can start cheap and monthly, then lock in the annual rate once the platform proves itself. 👉 [see all Sharktech cloud plans and current pricing](https://bit.ly/SharKtech)
