# Cloud Server Cost: What You'll Pay per Month, Why Two Quotes Differ by 20x, and How to Pick a Tier (With a First-Year Cost Breakdown)

A basic cloud server costs **$5–$20 a month**. A standard box with 2–4 vCPU and 4–8 GB of RAM lands at **$20–$80**. Anything with 8+ vCPU, 16 GB+ of memory, advanced networking and backups starts around **$100 and runs past $500**. Behind those brackets sit the global average unit rates across providers and regions: **$11.40 per vCPU per month, $2.90 per GB of RAM per month, and $0.07 per GB of outbound traffic**, up 9.8%, 7.2% and 5.5% year over year respectively.

That averages across every resource type, region and provider, so your quote will land somewhere inside a wide range. The useful question isn't "what does a cloud server cost" in the abstract, but which line items move the number and which ones show up only after the first invoice. Both are covered below, including a worked first-year total you can recompute with your own figures.

> **Quick pick:** price a **2 vCPU / 4 GB** instance first. It covers a small production site, a staging environment or a self-hosted app for one team, and it sits where the price-to-capability ratio is best across published tiers. Anything with 1 vCPU and 1 GB is a dev box, not a production plan. Pull the live plan list and current prices before you commit: 👉 [See Spin Servers' current cloud server plans and prices](https://bit.ly/Spinservers)

## The three price bands, and what separates them

| Band | Typical specs | Monthly price | What you're paying for |
| --- | --- | --- | --- |
| Basic | 1 vCPU, 1–2 GB RAM, 20–40 GB SSD | $5–$20 | Entry hardware, shared or burst capacity, minimal support |
| Standard | 2–4 vCPU, 4–8 GB RAM | $20–$80 | Current-gen CPUs, predictable single-core performance, room for a real workload |
| High performance | 8+ vCPU, 16 GB+, advanced networking, backups | $100–$500+ | Dedicated cores or GPU, high-IOPS storage, redundancy, SLA-backed support |

The jump from band one to band two buys more than extra cores. Low-end tiers commonly run previous-generation CPUs, standard SSD and bandwidth capped somewhere between 250 and 500 Mbit/s, while the higher bands add current-generation silicon, faster storage classes and network headroom. Two plans with identical vCPU and RAM counts can therefore differ by a factor of three on real throughput.

Hourly and per-second billing exist for short-lived workloads, and they're worth using when a job runs for hours rather than weeks. For anything that stays up, a monthly plan is almost always cheaper per hour.

## Where the money actually goes

Compute dominates. vCPU plus RAM is roughly **70% of a cloud server's price**, which is why the vCPU and memory line items are the only ones worth negotiating hard on.

| Resource | Unit | Published range |
| --- | --- | --- |
| vCPU | 1 core/month | $7–$20 |
| RAM | 1 GB/month | $1.50–$5 |
| Block storage (SSD) | 1 GB/month | $0.05–$0.12 |
| Object storage | 1 GB/month | $0.015–$0.03 |
| Egress bandwidth | 1 GB | $0.01–$0.09 |

Memory-optimized instances sit at the top of the RAM range. Storage type matters as much as storage volume: one provider prices in-house high-IOPS block storage at €0.220/GB/month against €0.085/GB/month for standard and €0.056/GB/month for archive, so a 100 GB volume costs €22, €8.50 or €5.60 depending on the tier. The performance gap is real (up to 100,000 read IOPS on the fast tier versus roughly 10,000 on standard and 600 on archive), but most web workloads never touch the ceiling of the standard tier.

Location shifts the total too. Central US is the cheapest region in current market data, with prices about 6% above baseline, while APAC Singapore is the most expensive at roughly 14% above. Same machine, different rack, different invoice.

## Why the same 2 vCPU / 4 GB costs €12 at one provider and $35 at another

Run the average unit rates against a 2 vCPU / 4 GB spec and the compute alone works out to about **$34.40 a month** (2 × $11.40 plus 4 × $2.90). Starter-tier plans sell the same vCPU and RAM count for €12 a month. Different currencies, so don't read that as a direct ratio, but the direction is clear: the gap comes from four things.

**CPU generation and storage class.** Entry tiers typically use previous-generation AMD or Intel parts with standard SSD. Newer silicon is genuinely faster per core; one vendor's fifth-generation EPYC nodes benchmarked over 37% higher than the prior configuration at 2 vCPU / 4 GB. You're buying fewer, faster cores versus more, slower ones.

**Billing model.** Fixed plans are billed 24/7/365 until you delete the server, with a round monthly price. Pay-as-you-go plans bill CPU and memory only while the machine is powered on, but storage and IP addresses keep billing continuously because the allocation persists. A server you run eight hours a day is not 67% cheaper on the second model; it's cheaper on compute and full price on everything attached to it.

**Managed versus unmanaged.** A managed control panel, patching and support staff add cost that has nothing to do with the hardware spec.

**Region and redundancy.** Distributed virtual server architecture spreads instances across physical hosts, which is what buys you failover when a node dies. That redundancy is priced in.

## The costs that only appear on invoice two

Egress is the classic one. At the $0.07/GB average, **1 TB of outbound traffic adds about $71.68 a month**, more than many servers cost on their own. Some providers charge nothing for it (one European provider lists €0.00/GiB outbound and inbound), and that single policy can outweigh a €10 difference in plan price if you serve video, run an API with heavy responses, or host a download mirror.

Backups are the second. One provider's tiered backup add-on is priced as a percentage of the server plan: **+10% for 24-hour daily retention, +20% for 7 days, +40% for a month, +60% for a year**. On a €12 plan that's €1.20 to €7.20 a month; on a €300 plan it's €30 to €180. Others treat daily backups as a paid option rather than an inclusion, and only some plan families ship a 24-hour snapshot at no charge. Ask what retention you get before you assume anything: 👉 [Check what each Spin Servers plan includes before you add backups](https://bit.ly/Spinservers)

IPv4 addresses are the third. Extra public IPv4 runs **€3.47/month** at one provider and **$3.65/month** at another. IPv6 is usually free. If you're running multiple services behind separate addresses, this line adds up quietly.

Then come the pricing structures that look like savings. Committed-use discounts and free credits tie you to a term or an account, and the discount is calculated against list prices that can change mid-term. Higher SLA tiers and paid support are worth the premium for production systems where an hour of downtime costs more than the annual fee, and a waste of money for a staging box.

## A first-year total you can recompute

Take a 4 GB / 2 core / 30 GB plan at **€12/month** with 500 Mbit/s bandwidth, billed monthly. Add the day-retention backup at +10% (€1.20) and one extra public IPv4 at €3.47. Egress is €0.00/GiB, so heavy traffic adds nothing.

| Line item | Monthly | First year |
| --- | --- | --- |
| Plan | €12.00 | €144.00 |
| Backup (day, +10%) | €1.20 | €14.40 |
| Extra IPv4 | €3.47 | €41.64 |
| Egress (assume 1 TB/mo) | €0.00 | €0.00 |
| **Total** | **€16.67** | **€200.04** |

Swap the backup to month retention (+40%, €4.80) and the total becomes €20.27/month, or €243.24 for the year. Same server, 21% more.

Now the same arithmetic with a metered egress rate. If that 1 TB were billed at the $0.07/GB average instead of zero, you'd add $71.68/month, or $860.16 across the year, and the server itself becomes the small part of the bill. Currency matters here: €200.04 and $860.16 aren't comparable, and you shouldn't add them. The point is the ratio inside each currency. Run your own volume through the same three lines before you compare two quotes: 👉 [Run the same math against Spin Servers' live price list](https://bit.ly/Spinservers)

## Check the effective date before you trust a number

Prices on a pricing page can carry a future effective date. One provider has published an adjustment to its previous-generation Cloud Server plans, Standard and Archive block storage, and Windows Server licensing that **takes effect on November 16, 2026**, and states that its new Starter plans replace the older Developer line at an average of about 25% less while keeping the same 99.99% SLA.

That's nine days from now, which makes the current page a snapshot rather than a commitment. Before you budget on any number, look for an effective date or a changelog link on the pricing page. If the page shows a promotional rate, find the renewal rate too; the second one is what you'll actually pay for most of the contract.

## Which tier fits your workload

**Personal projects, dev and test environments:** 1 vCPU / 1–2 GB, 10–30 GB storage, the cheapest plan on the page. Expect previous-generation CPU and standard SSD and don't plan on heavy concurrent traffic. Total should stay under €10/month.

**A growing site or a small app with real users:** 2 vCPU / 4 GB minimum, 30–50 GB storage, and check the bandwidth cap. This is the tier where a few euros separates a plan that holds up under a traffic spike from one that doesn't. Budget $20–$40.

**Production with paying customers:** 4+ vCPU, 8 GB+, high-IOPS storage if you run a database, backups with at least week-long retention, and an SLA you've read. Budget $80–$200 with backups and monitoring included, and price a second instance for failover before you need it.

**Anything memory-bound (caches, analytics, JVM services):** buy RAM, not cores. The memory-optimized band costs more per vCPU but far less than running three standard instances to get the same heap.

## What to confirm before you order

1. **Renewal price versus intro price**, and any announced change with an effective date.
2. **Egress policy**: included volume, overage rate, and whether inbound counts.
3. **Backup cost and retention**, including whether a daily snapshot is bundled with the plan you picked.
4. **IP count**: how many public IPv4 addresses are included, and the monthly cost of extras.
5. **Billing granularity**: whether storage and IPs bill while the server is powered off.
6. **Storage tier**: standard versus high-IOPS, and the per-GB rate of each.
7. **Cancellation and refund terms**, plus whether a trial exists.

## FAQ

**Will my price go up at renewal?** Often, yes. Promotional first-term pricing is common, and published adjustments can land mid-contract for new billing periods. Compare the renewal rate, not the headline rate.

**Is hourly billing cheaper than monthly?** Only for short-lived machines. Hourly compute stops when the server is off; attached storage and IP addresses usually keep billing.

**How is bandwidth counted?** Most providers meter outbound traffic only, at $0.01–$0.09/GB, with some charging nothing. Inbound is usually free. 1 TB at the average rate is roughly $71.68 a month, so it's worth checking before you pick a region.

**Can I get a refund if it doesn't work out?** Policies vary widely and trials are not universal. Confirm the terms in writing before the first payment rather than after.

The rule that survives all of this: pick the smallest plan whose **bandwidth cap, storage tier and backup retention** you can live with, then compare totals for twelve months rather than the monthly sticker. A €12 plan with metered egress and a +40% backup can cost more than a €20 plan with both included. 👉 [Start from Spin Servers' current plan list and price each one for a full year](https://bit.ly/Spinservers)
