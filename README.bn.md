# বাংলা অনুবাদ · [English](README.md)

> **টেমপ্লেট পরিবারের অংশ** — এটি নিচের দুটির সাথে একসাথে ব্যবহার করুন:
> [`big-software-product-template`](https://github.com/anurag-panda-dev/big-software-product-template) (শুধু সফটওয়্যার) এবং
> [`full-stack-consumer-hardware-products-template`](https://github.com/anurag-panda-dev/full-stack-consumer-hardware-products-template) (হার্ডওয়্যার + সফটওয়্যার)।

<h1 align="center">কনজিউমার হার্ডওয়্যার প্রোডাক্ট টেমপ্লেট</h1>
<p align="center"><i>Consumer Hardware Products Template</i></p>

<p align="center"><b>প্রতিটি ফোল্ডার নিজেকে ব্যাখ্যা করে — মানুষের কাছেও, AI এজেন্টের কাছেও।</b><br>
১০০টি <code>purpose.txt</code> ম্যাপ · ডিসিপ্লিন-প্রথম লেআউট · ADR/RFC সিদ্ধান্ত শৃঙ্খলা</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="MIT License" /></a>
  <a href="https://github.com/anurag-panda-dev/consumer-hardware-products-template/generate"><img src="https://img.shields.io/badge/Use%20this%20template-grey?style=flat-square&logo=github&logoColor=white" alt="Use this template" /></a>
  <a href="https://github.com/anurag-panda-dev/consumer-hardware-products-template"><img src="https://img.shields.io/github/repo-size/anurag-panda-dev/consumer-hardware-products-template?style=flat-square" alt="Repo size" /></a>
</p>

<p align="center">
  <img src="docs/assets/repo-hero.png" alt="GitHub-এ consumer-hardware-products-template রিপোজিটরির বিন্যাস" width="100%">
</p>

```text
products/         স্পেক, ভ্যারিয়েন্ট, রিলিজ ── নিচের ডিসিপ্লিনগুলোর দিকে ইঙ্গিত করে
mechanical/       CAD · এনক্লোজার · CMF
electronics/      PCB · পাওয়ার · RF
firmware/         বুটলোডার · ড্রাইভার · অ্যাপ · OTA এজেন্ট
certification/    BIS · WPC · FCC · CE প্রমাণপত্র
manufacturing/    DFM · অ্যাসেম্বলি · জিগ · ইল্ড
supply-chain/  validation/  packaging/  test-tools/
```

**বাস্তব কনজিউমার প্রোডাক্ট** তৈরির জন্য একটি মনোরিপো টেমপ্লেট — যেখানে সাজানো হয় *ইঞ্জিনিয়ারিং ডিসিপ্লিন* অনুযায়ী (মেকানিক্যাল, ইলেকট্রনিক্স, ফার্মওয়্যার, সার্টিফিকেশন, ম্যানুফ্যাকচারিং), আর `products/`-এ প্রতিটি লাইনের স্পেক থাকে যা সেগুলোর দিকে ইঙ্গিত করে।

স্ট্রাকচারের যুক্তি: `docs/decisions/ADR-0001-Structure.md`।

## অভিজ্ঞতালব্ধ নিয়ম

| যদি এটি হয়… | এটি যাবে… |
|---|---|
| কোনো ডিভাইস প্রোডাক্ট লাইনের স্পেক/ভ্যারিয়েন্ট/রিলিজ | `products/<line>/` |
| CAD, এনক্লোজার, CMF | `mechanical/` |
| স্কিমেটিকস, PCB, পাওয়ার, RF | `electronics/` |
| বুটলোডার, ড্রাইভার, অ্যাপ ফার্মওয়্যার, OTA এজেন্ট | `firmware/` |
| BIS/WPC/FCC/CE প্রমাণপত্র | `certification/` |
| DFM, অ্যাসেম্বলি, টেস্ট জিগ, মান, ইল্ড | `manufacturing/` |
| BOM, সাপ্লায়ার, খরচ | `supply-chain/` |
| নির্ভরযোগ্যতা/তাপ/ব্যাটারি/ড্রপ পরীক্ষা | `validation/` (সফটওয়্যার টেস্টের হার্ডওয়্যার সমকক্ষ) |
| ডাইলাইন, ইনসার্ট, লেবেল | `packaging/` |
| জিগ সফটওয়্যার, ফ্ল্যাশ টুল, ক্যালিব্রেশন | `test-tools/` |
| ব্যবসা ও পরিচালন | `business/` |
| কোড-সংলগ্ন আইনি বিষয় | `legal/` |
| জ্ঞান / সিদ্ধান্ত | `docs/` (গৃহীত) · `rfcs/` (অমীমাংসিত) |
| প্রোটোটাইপ / গবেষণা | `sandbox/` · `labs/` |

**প্রতিটি ফোল্ডারে একটি `purpose.txt` থাকে** — কোনটা ওখানে বসবে এবং কী থাকা উচিত তা বর্ণনা করে। হালনাগাদ রাখুন — এগুলোই মানচিত্র।

## স্ট্রাকচার

```text
products/         প্রতি প্রোডাক্ট লাইনে একটি ফোল্ডার: product.md, requirements/, variants/, release/
mechanical/       cad, industrial-design, enclosure
electronics/      pcb, power, rf, devboards
firmware/         bootloader, drivers, application, boards, ota
certification/    india (BIS/WPC/TEC), international (FCC/CE), emc, safety, environment
manufacturing/    dfm, assembly, test-jigs, quality, yields
supply-chain/     bom, suppliers, costing
validation/       reliability, thermal, battery, drop-vibration, emc-prescan
packaging/        dieline, inserts, labels
test-tools/       jig firmware, flash tools, calibration
business/         product, market-research, marketing, pricing, monetization, finance, metrics, team, support
legal/            compliance, ip, licenses, templates
docs/             architecture, product, strategy, decisions (+ TEMPLATE.md)
rfcs/ labs/ sandbox/ tooling/ (scripts, exporters) security/ .ai/ AGENTS.md
```

## সীমানা নিয়ম (দেখুন PACKAGE.md)

- `products/<line>/`-এ থাকে **স্পেক ও পয়েন্টার** — আর্টিফ্যাক্ট (CAD, gerbers, ফার্মওয়্যার) থাকে ডিসিপ্লিন ফোল্ডারে এবং `product.md` থেকে লিংক করা হয়।
- জেনারেটেড আউটপুট (`tooling/exporters` থেকে এক্সপোর্ট: STEP/STL/Gerber/PDF) **কখনো হাতে সম্পাদনা করা হয় না** — সোর্স থেকে নতুন করে বানান।
- `sandbox/` আর `labs/` সরাসরি প্রোডাকশন ফোল্ডারে ঢোকে না; উত্তোনন একটি সুস্পষ্ট, রিভিউ করা পদক্ষেপ।
- কর্পোরেট ডকুমেন্ট (ইকুইটি, HR, স্বাক্ষরিত চুক্তি, IP ফাইলিং) রাখা হয় একটি **প্রাইভেট company-ops রিপোতে**, কখনো এখানে নয়।

## এই টেমপ্লেট ব্যবহার করা

1. GitHub-এ **এই টেমপ্লেটটি ব্যবহার করুন** (অথবা `gh repo create my-project --template anurag-panda-dev/consumer-hardware-products-template`)
2. **নাম বদলান** — রুট `README.md`, `purpose.txt`, `AGENTS.md` হালনাগাদ করুন
3. **`products/example-device/`** বাদ দিয়ে নিজের প্রকৃত প্রোডাক্ট লাইন বসান (লেআউট রাখুন: `product.md`, `requirements/`, `variants/`, `release/`)
4. **প্রথম সিদ্ধান্তটি লিখে রাখুন** — `docs/decisions/TEMPLATE.md` কপি করে → `ADR-0001-…`; বড় সিদ্ধান্ত (MCU প্ল্যাটফর্ম, এনক্লোজার মেটেরিয়াল, CM পার্টনার) আগে `rfcs/` দিয়ে যায়
5. **খালি স্ক্যাফোল্ডিং আগে থেকে বানাবেন না** — আসল কাজ এলে ফোল্ডার পূরণ হয়
6. `.github/workflows/`-এ ধীরে ধীরে CI যোগ করুন (KiCad DRC, ফার্মওয়্যার বিল্ড, BOM lint এর `purpose.txt`-এ তালিকাভুক্ত)
