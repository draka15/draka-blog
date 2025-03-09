---
title: Self-Hosting Journey - Part 2 - Choosing the Hardware
date: 2024-12-23 13:48:38
author: Draka
comments: true
categories:
  - Self-Hosting
tags:
  - Storage
  - Hardware
  - Mini-PC
  - NAS
  - RAID
  - Redundancy
---
Selecting the hardware for your self-hosted environment is one of the most critical decisions you’ll make. It’s not just about picking components; it’s about creating a setup that aligns with your goals, fits your constraints, and inspires confidence in your system’s reliability. In this post, I’ll walk you through my thought process and share how I made my decision.

<div style="text-align: center; margin: 20px 0; padding: 10px;">
  <img src="/Self-Hosting-Journey-Part-2-Choosing-the-Hardware/self_hosting_2_1.png" alt="A question mark overlapped to some hardware" style="max-width: 60%; height: auto; border-radius: 8px;">
  <p style="color: #f7f7c1; margin-top: 15px; font-style: italic; text-align: center;">How do I choose the Hardware?</p>
</div>

## **Setting the Stage: Goals and Constraints**

Before diving into hardware options, I want to clarify a key concept. There is no **one-size-fits-all** solution; every option has its pros and cons. One solution may be more suitable than another on a specific context, but there isn’t a global winner.

Thus, the first step is to set my goals and constraints.

### **My Goals**

1. **24/7 Availability:** My services must be reliable and always accessible.
2. **Secure Network:** I want to proper structure the LAN dividing it in VLANs, like an enterprise setup.
3. **Privacy and Data Ownership:** I want to move away from Google Drive and store my photos and other archived data on my own hardware, accessing it in a convenient way.
4. **Entertainment and Productivity:** I want to host a streaming service and some other services for meal planning, trip organization, expense tracking and automation tasks.
5. **Future Scalability:** In the long term, I’d like to explore home automation.

### **Constraints**

- **Budget:** I don’t want to spend too much money, both hardware and operational costs (electricity) need to stay reasonable. To achieve this, I also plan to reuse some of the hardware I already have.
- **Space & Noise:** I live in a small apartment, so my setup needs to be small and quiet.

### **My Starting Point: Existing Hardware**

In the past, I already bought these devices that I will include in my self-hosting environment:

- **Raspberry Pi 4 Model B (Pi4B)**
    - **CPU**: ARM v8, SoC quad-core Cortex-A72 64bit running at 1,5GHz, Broadcom BCM2711
    - **RAM**: 2GB LPDDR4
    - **Storage**: 32GB SD card
    - **Network**: 1x Gigabit Ethernet port + 802.11 b/g/n/ac Wireless LAN + Bluetooth 5.0 with BLE
    - **Others**: 2x micro-HDMI ports + 2x USB2 ports + 2x USB3 ports + 1x Raspberry Pi camera port + 1x Raspberry Pi display port + 1x GPIO

- **HP EliteDesk 705 G5 Mini**
    - **CPU**: AMD Ryzen 5 Pro 3400G (4 cores, 8 threads, 3.7GHz up to 4.2GHz turbo, TDP 65W)
    - **GPU**: AMD Radeon Vega 11
    - **RAM**: 64GB Corsair Vengeance SODIMM DDR4 (2x32GB) 2666MHz
    - **Storage**: 2TB SSD SATA III 2.5"
    - **Network**: 1x Gigabit Ethernet port

These two devices could potentially be enough for my infrastructure, but they don't fully meet all my requirements.
The **Raspberry Pi** is optimal for its low power consumption, but it lacks the processing power needed for hosting my environment.
The **EliteDesk**, while excellent in terms of performance, has insufficient storage space and isn't ideal for a 24/7 environment due to its power consumption.

So, I decided to buy a new device that addresses the shortcomings of these two and provides a perfect foundation for my environment.

## **A New Device: Desiderata**

I identified these key criteria for the new device I had decided to buy:

1. **RAM:** I don’t need to host CPU-intensive applications, and I have only two users to serve (myself and my girlfriend), so I don't have high requirements for the CPU. However, I plan to host many applications, so a good amount of RAM is necessary.
2. **Storage:** Archiving all multimedia and documents requires plenty of space.
3. **Disk Redundancy:** Data safety and reliability are non-negotiable; redundancy through RAID is a must.
4. **Compact Size:** It needs to fit into my limited space.
5. **Quiet Operation:** No one wants a noisy setup in their home.
6. **Low Power Consumption:** Essential for 24/7 operation without breaking the bank.
7. **Affordability:** Performance matters, but it must stay within budget.

The first step was to choose a base system compatible with multiple storage solutions. Next, I evaluated several storage options. Below are the three solutions considered for the base system.

### **Option 1: ASRock N100DC-ITX Mini-ITX Board**
The first option I evaluated was building a system based on a mini-ITX motherboard. This involved purchasing a motherboard with an integrated CPU, RAM, a power supply, and a case compatible with redundant storage.

<div style="text-align: center; margin: 20px 0; padding: 10px;">
  <img src="/Self-Hosting-Journey-Part-2-Choosing-the-Hardware/asrock_n100dc.png" alt="An image of the ASRock N100DC-ITX board" style="max-width: 60%; height: auto; border-radius: 8px;">
  <p style="color: #f7f7c1; margin-top: 15px; font-style: italic; text-align: center;">ASRock N100DC-ITX</p>
</div>

Here’s an overview of the components and their costs for this solution:

- **ASRock N100DC-ITX**: €135
- **SO-DIMM DDR5 32GB RAM**: €74.99
- **NAS Case (Jonsbo N2)**: €140 – A compact and stylish case that accommodates HDDs and fits the board perfectly.
- **Corsair SF450 Power Supply**: €100

<div style="text-align: center; margin: 20px 0; padding: 10px;">
  <img src="/Self-Hosting-Journey-Part-2-Choosing-the-Hardware/case_jonsbo_n2.png" alt="An image of the Jonsbo N2 NAS Case" style="max-width: 60%; height: auto; border-radius: 8px;">
  <p style="color: #f7f7c1; margin-top: 15px; font-style: italic; text-align: center;">NAS Case Jonsbo N2</p>
</div>

For powering the system, I chose to use an ATX power supply instead of a traditional picoPSU because the **ASRock N100DC-ITX** can support only **two 3.5-inch HDDs**, due to its **4-pin JST SATA power connector**. The board’s SATA power interface is rated for **2A**, but a typical **7200 RPM 3.5-inch HDD** can draw up to **2.5A during spin-up**. This occurs when the drives are awakened from sleep, which could potentially strain the power supply. Although this is not a frequent event, it presents a risk for a system intended for continuous 24/7 operation.

To create a scalable system that could handle more than two **3.5-inch HDDs**, I found the following solution:

1. Buy a **modular ATX power supply**, such as the **Corsair SF450**, which offers reliable power delivery.
2. Build a custom cable using a **4-pin JST cable** and a **DC jack-to-terminal adapter** to connect the PSU to the board.
3. Manually jump the ATX connector with a wire to turn on the power supply without relying on the motherboard's signal.

Here’s an overview of the final specifics for this solution:

- **Processor:** Intel N100 (12th Gen, 4 cores, 6W TDP)
- **RAM:** Supports up to 32GB SO-DIMM DDR4
- **Storage:** 2x SATA III ports with PCIe Gen 3 expansion
- **Networking:** 1x Gbit Ethernet (GbE) LAN port and 1x PCIe M.2 E-Key slot for a Wi-Fi adapter
- **Price:** ~€450 (fully built with case and PSU)

While this option is very interesting because it offers modern technology and expandability, it requires complex power modifications to support additional HDDs and it is also expensive.

### **Option 2: ZimaBlade 7700 NAS Kit**
The second option I evaluated was a ready-to-use solution based on an excellent x86 board called {% link "ZimaBlade" "https://www.zimaspace.com/products/blade-personal-nas?utm_source=head&utm_medium=menu" %}, with the following specifications:

<div style="text-align: center; margin: 20px 0; padding: 10px;">
  <img src="/Self-Hosting-Journey-Part-2-Choosing-the-Hardware/zima.png" alt="An image of the zimablade board" style="max-width: 60%; height: auto; border-radius: 8px;">
  <p style="color: #f7f7c1; margin-top: 15px; font-style: italic; text-align: center;">Zimablade 7700</p>
</div>

- **Processor:** Intel Celeron N3450 (4 cores, 6W TDP).
- **RAM:** Supports up to 16GB DDR3L.
- **Storage:** 2x SATA III ports with PCIe 2.0 expansion which allows for the addition of up to 4 additional SATA ports.
- **Networking**: 1x Gbit Ethernet (GbE) LAN port.
- **Price:** ~€187 (with taxes).

The price of this solution refers to the NAS kit bundle, which includes 16GB of RAM and a bay rack for up to two 3.5-inch HDDs.
While this solution is the only one ready out-of-the-box, and is both affordable and compact, its older processor and limited scalability do not align with my future needs. Additionally, expanding beyond two HDDs could strain the power adapter, requiring additional power management solutions.

### **Option 3: Mini-PC Based on x86 P5 Board**
This third option is a compact and versatile mini-PC based on the **x86 P5 board** by {% link "CWWK" "https://cwwk.net/" %}. This is an overview of the specification:

<div style="text-align: center; margin: 20px 0; padding: 10px;">
  <img src="/Self-Hosting-Journey-Part-2-Choosing-the-Hardware/cwwk_x86_nas.png" alt="An image of the CWWK x86 Board" style="max-width: 60%; height: auto; border-radius: 8px; ">
  <p style="color: #f7f7c1; margin-top: 15px; font-style: italic; text-align: center;">CWWK x86 P5 Development Board</p>
</div>

- **Processor:** Intel N100 (12th Gen, 4 cores, 6W TDP).
- **RAM:** 1x slot supports up to 48GB SO-DIMM DDR5 4800MHz.
- **Storage:** 1x PCIe 3x4 lane which supports 4x NVMe Gen 3 slots.
- **Networking:** 2x 2.5Gbit Ethernet (GbE) LAN ports and 1x PCIe M.2 E-Key slot for a Wi-Fi adapter.
- **Price:** ~€233  (€158.70 for barebone configuration + €74.99 for 32GB RAM).

This option offers the perfect balance of performance, power efficiency, and expandability. Its compact size (10x10x5.85 cm) and low power consumption make it ideal for my space.

### **Choosing Storage: HDD, SATA SSD, or NVMe SSD?**

When planning a storage solution, one of the most critical decisions is selecting the type of storage. Here’s a quick comparison of the most popular storage technology options:

<div style="width: 100%; line-height: 16px; margin: 20px auto; padding: 0; border-radius: 8px; box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);">
  <table style="width: 100%; border-collapse: collapse; font-family: 'Courier New', monospace; background-color: #333333; border: 1px solid #444444; border-radius: 8px;">
    <colgroup>
      <col style="width: 25%;">
      <col style="width: 25%;">
      <col style="width: 25%;">
      <col style="width: 25%;">
    </colgroup>
    <thead>
      <tr style="background-color: #444444; border-top-left-radius: 8px; border-top-right-radius: 8px;">
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555; border-radius: 8px 8px 0 0;">Type</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Pros</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Cons</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Best Use Case</th>
      </tr>
    </thead>
    <tbody>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: center; border: 1px solid #555555;">HDD</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">High capacity, lower cost per TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">Noisy, high power consumption, slow speed</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">Large, static data (backups)</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: center; border: 1px solid #555555;">SATA SSD</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">Faster, silent</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">Limited capacity, higher cost per TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">Balanced performance/capacity</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: center; border: 1px solid #555555;">NVMe SSD</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">Compact, silent, highest speed</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">Limited capacity, higher cost per TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">High-speed apps and NAS setups</td>
      </tr>
    </tbody>
  </table>
  <p style="text-align: center; color: #e0e0e0; font-weight: 600; margin-top: 20px;">HDD 3.5-inch SATA III Comparison Table</p>
</div>


Here’s a quick comparison of the products I found and their approximate prices at the time I searched:

<div style="margin: 20px auto; line-height: 16px; padding: 0; border-radius: 8px; box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);">
  <table style="width: 100%; border-collapse: collapse; font-family: 'Courier New', monospace; background-color: #333333; border: 1px solid #444444; border-radius: 8px;">
    <colgroup>
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
    </colgroup>
    <thead>
      <tr style="background-color: #444444; border-top-left-radius: 8px; border-top-right-radius: 8px;">
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: left; border: 1px solid #555555; border-radius: 8px 8px 0 0;">Model</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">RPM</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Transfer Rate (MB/s)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Workloads (TB/Year)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Price (€)</th>
      </tr>
    </thead>
    <tbody>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">WD Red Plus 2TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">5400</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">98.00</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">WD Red Plus 4TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">5400</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">185</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">130.00</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Seagate IronWolf 2TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">5900</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">90.00</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Seagate IronWolf 4TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">5900</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">124.00</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Seagate IronWolf Pro 2TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">7200</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">195</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">300</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">116.00</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Seagate IronWolf Pro 4TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">7200</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">214</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">300</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">140.00</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Toshiba N300 4TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">7200</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">204</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">180</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">130.00</td>
      </tr>
    </tbody>
  </table>
  <p style="text-align: center; color: #e0e0e0; font-weight: 600; margin-top: 20px;">HDD 3.5-inch SATA III Comparison</p>
</div>



<div style="margin: 20px auto; line-height: 16px; padding: 0; border-radius: 8px; box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);">
  <table style="width: 100%; border-collapse: collapse; font-family: 'Courier New', monospace; background-color: #333333; border: 1px solid #444444; border-radius: 8px;">
    <colgroup>
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
    </colgroup>
    <thead>
      <tr style="background-color: #444444; border-top-left-radius: 8px; border-top-right-radius: 8px;">
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: left; border: 1px solid #555555; border-radius: 8px 8px 0 0;">Model</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Seq Write Speed (MB/s)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Seq Read Speed (MB/s)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">TBW (TB)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Price (€)</th>
      </tr>
    </thead>
    <tbody>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">WD Red SATA SA500 1TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">530</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">560</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">600</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">110.79</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">WD Red SATA SA500 2TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">530</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">560</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">1,300</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">59.17</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Samsung 870 EVO 1TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">530</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">560</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">600</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">95.88</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Samsung 870 EVO 2TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">530</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">560</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">1,200</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">164.85</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Crucial MX500 1TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">560</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">560</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">700</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">88.95</td>
      </tr>
    </tbody>
  </table>
  <p style="text-align: center; color: #e0e0e0; font-weight: 600; margin-top: 20px;">SSD SATA III Comparison</p>
</div>



<div style="margin: 20px auto; line-height: 16px; padding: 0; border-radius: 8px; box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);">
  <table style="width: 100%; border-collapse: collapse; font-family: 'Courier New', monospace; background-color: #333333; border: 1px solid #444444; border-radius: 8px;">
    <colgroup>
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
      <col style="width: 20%;">
    </colgroup>
    <thead>
      <tr style="background-color: #444444; border-top-left-radius: 8px; border-top-right-radius: 8px;">
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: left; border: 1px solid #555555; border-radius: 8px 8px 0 0;">Model</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Seq Write Speed (MB/s)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Seq Read Speed (MB/s)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">TBW (TB)</th>
        <th style="padding: 14px 20px; color: #e0e0e0; font-weight: 600; text-align: center; border: 1px solid #555555;">Price (€)</th>
      </tr>
    </thead>
    <tbody>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">WD_BLACK SN850 1TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">5300</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">7000</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">600</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">148.99</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Samsung 970 EVO Plus 1TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">3500</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">3500</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">600</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">123.39</td>
      </tr>
      <tr style="color: #e0e0e0; transition: background-color 0.3s ease;">
        <td style="padding: 16px 20px; font-weight: 600; text-align: left; border: 1px solid #555555;">Crucial P5 1TB</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">3400</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">3400</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">600</td>
        <td style="padding: 16px 20px; text-align: center; border: 1px solid #555555;">92.99</td>
      </tr>
    </tbody>
  </table>
  <p style="text-align: center; color: #e0e0e0; font-weight: 600; margin-top: 20px;">SSD NVMe M.2 Comparison</p>
</div>

<style> 
    /* Add hover effect */ 
    tr:hover { 
        background-color: #555555; 
    }
</style>

The **TBW (Terabytes Written)** metric is a critical factor in assessing the durability of SSDs. It indicates the maximum amount of data a drive can write over its lifetime, as declared by the vendor.

## **The Final Decision**

After weighing the pros and cons, I decided on the **Mini-PC x86 P5 with NVMe SSDs**. This setup met all my requirements and stayed within budget. Here’s the breakdown of the costs:

- **Mini-PC (barebone):** €158.70
- **32GB DDR5 RAM:** €74.99
- **3x NVMe SSDs (2TB each):** €207
- **Total Cost:** €440

<div style="text-align: center; margin: 20px 0; padding: 10px;">
  <img src="/Self-Hosting-Journey-Part-2-Choosing-the-Hardware/minipc.png" alt="An image of the mini-pc" style="max-width: 60%; height: auto; border-radius: 8px;">
  <p style="color: #f7f7c1; margin-top: 15px; font-style: italic; text-align: center;">Mini-PC x86 P5</p>
</div>

### Understanding PCIe Lanes and NVMe Connections

A limitation of the setup I chose is that the four NVMe SSD slots share the same single PCIe 3.0 x4 interface.

PCIe (Peripheral Component Interconnect Express) is a high-speed interface that allows devices like NVMe SSDs to communicate with the motherboard and CPU. Each PCIe connection consists of **lanes**, which are individual data pathways made up of one pair of wires for sending data and another for receiving it. The more lanes a device has, the greater its potential bandwidth.

For example, an **NVMe SSD connected via PCIe 3.0 x4** utilizes **four lanes** of PCIe 3.0. Each lane in PCIe 3.0 provides a theoretical bandwidth of **1 GB/s in each direction**, meaning a x4 connection can achieve up to **4 GB/s** of throughput. This makes PCIe 3.0 x4 ideal for high-performance NVMe SSDs, enabling their fast read and write speeds to be fully utilized.

In my configuration, the NVMe SSDs are connected through a single **PCIe 3.0 x4** slot, meaning the available bandwidth is shared among all the connected devices. While PCIe 3.0 x4 can theoretically support up to **4 GB/s** of total throughput, this bandwidth is divided among all drives using the same connection. As a result, the **read and write speeds** of each individual NVMe SSD are lower than their maximum potential speeds due to the shared bandwidth.

### Assembling the Pieces

After purchasing all the necessary components, it's time for a bit of hands-on work to assemble everything. The process is quite simple, and in the following video, you'll see a summary of the assembly phase.

<div style="text-align: center; margin: 20px 0; padding: 10px;">
<video width="500" height="500" controls autoplay loop muted poster="minipc_poster.jpg">
<source src="/Self-Hosting-Journey-Part-2-Choosing-the-Hardware/assembling.mp4" type="video/mp4"> Your browser does not support the video tag.
</video>
  <p style="color: #f7f7c1; margin-top: 15px; font-style: italic; text-align: center;">Assembling the Pieces</p>
</div>


## **Conclusion**

In this blog post, we've explored the **first phase** of planning our self-hosting environment, focusing on **hardware selection**. We discussed the reasoning behind our device choices and learned that the best way to start is by **understanding and defining your goals** and **limitations**. Remember, the perfect setup is the one that works for **you**. In the next post, we'll look at how to design the **physical** and **logical architecture** of our solution.

**Stay tuned! 🚀**

