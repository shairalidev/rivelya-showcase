<div align="center">

<a href="https://www.rivelya.com"><img src="assets/rivelya.jpg" alt="Rivelya: A pay-per-minute expert consultation marketplace with live chat, voice and video." width="100%"/></a>

# Rivelya

**A pay-per-minute expert consultation marketplace with live chat, voice and video.**

[![Live site](https://img.shields.io/badge/Live-rivelya.com-7c6cff?style=for-the-badge&logo=googlechrome&logoColor=white)](https://www.rivelya.com) [![Case study](https://img.shields.io/badge/Case_study-shairali.com-111?style=for-the-badge)](https://shairali.com/work/rivelya)

Marketplace · Rivelya · Italy · Nov 2025 – Apr 2026

</div>

> [!NOTE]
> This repository is a **showcase**. The source code is private and belongs to the client, so this page documents what I built, how it works and the stack behind it. Screenshots are from the live product.

<p align="center"><img src="assets/tour.gif" alt="Rivelya product tour" width="100%"/></p>

## Overview

An Italian marketplace where clients top up a wallet and consult verified experts by chat, voice or video, billed by the minute, booked ahead or started on demand.

| | |
|---|---|
| **Role** | Solo full-stack developer: product, frontend, backend, infrastructure & DevOps |
| **Client** | Rivelya · Italy |
| **Timeline** | Nov 2025 – Apr 2026 |
| **Live** | [rivelya.com](https://www.rivelya.com) |

## At a glance

<table><tr>
<td align="center" width="25%"><h3>1,250+</h3><sub>Commits, all mine</sub></td>
<td align="center" width="25%"><h3>180+</h3><sub>API endpoints</sub></td>
<td align="center" width="25%"><h3>29</h3><sub>Data models</sub></td>
<td align="center" width="25%"><h3>3</h3><sub>Live channels: chat, voice, video</sub></td>
</tr></table>

## The challenge

Minute-based consultations are a high-volume, trust-sensitive business. The client needed a platform that could match clients with available experts instantly, meter every session precisely, collect payment upfront, hold and settle expert earnings and do all of it reliably in real time, without anyone reconciling balances by hand.

## What I built

I built Rivelya from scratch as a one-developer product: a React app for clients, experts and admins; an Express and Socket.io backend; self-hosted LiveKit for WebRTC voice and video; and a billing engine on MongoDB transactions that the server controls. The server starts, meters and closes every session, so the money is always right, even when a browser tab isn't.

## Key features

### Instant or scheduled sessions

Expert presence updates live. Clients can start a session immediately (the expert has 30 seconds to accept) or book a slot from the expert's availability calendar. A scheduler auto-starts booked sessions on time, in the Europe/Rome timezone.

<img src="assets/experts.webp" alt="Rivelya expert directory with online status, ratings and channels" width="100%"/>

### Chat, voice and video in one place

Socket.io powers chat, typing indicators, presence and call signalling. Voice and video run on a self-hosted LiveKit server with a TURN relay, with Twilio as a phone fallback. A live countdown shows each client exactly how much time is left.

<img src="assets/expert-profile.webp" alt="Rivelya expert profile with Start now button, reviews and channel options" width="100%"/>

### Wallet and per-minute billing that can't drift

Stripe Payment Intents with verified webhooks top up a prepaid wallet held in integer cents. Every balance change runs in an atomic MongoDB transaction with idempotent payment handling, and negative balances are blocked. Expert earnings sit on a 7-day hold before they become withdrawable.

<img src="assets/journey-10.webp" alt="Rivelya booking management showing a confirmed €19 session" width="100%"/>

### Expert and admin consoles

Invite-only expert onboarding with availability, rates, earnings and withdrawal requests. The admin console has an OTP login and covers commission per expert, payouts, CMS and blog, testimonials and promotional email campaigns.

<img src="assets/journey-12.webp" alt="Rivelya live session room with conversation list and timer" width="100%"/>

## User journey

A client's path from landing page to a rated session, step by step.

<table>
<tr>
<td width="33%" valign="top"><img src="assets/journey-01.webp" alt="Start a consultation" width="100%"/><br/><sub><b>1. Start a consultation</b><br/>Start right away or book a time. The flow guides the client step by step.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-02.webp" alt="Sign in" width="100%"/><br/><sub><b>2. Sign in</b><br/>Email and password, or Google sign-in, with phone verification before the first booking.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-03.webp" alt="Open the expert directory" width="100%"/><br/><sub><b>3. Open the expert directory</b><br/>The Experts menu lists everyone who is available right now.</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><img src="assets/journey-04.webp" alt="Choose an expert" width="100%"/><br/><sub><b>4. Choose an expert</b><br/>Clients compare ratings, specialities and channels, then open the profile.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-05.webp" alt="Start now" width="100%"/><br/><sub><b>5. Start now</b><br/>One click on Start now. It's the fastest way to talk to an online expert.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-06.webp" alt="Or pick a day and time" width="100%"/><br/><sub><b>6. Or pick a day and time</b><br/>Date, time slot and channel. Price and duration are calculated live.</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><img src="assets/journey-07.webp" alt="Booking sent" width="100%"/><br/><sub><b>7. Booking sent</b><br/>The request goes to the expert, and the amount is charged upfront.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-08.webp" alt="Track the booking" width="100%"/><br/><sub><b>8. Track the booking</b><br/>Booking management shows whether the expert has accepted.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-09.webp" alt="Awaiting confirmation" width="100%"/><br/><sub><b>9. Awaiting confirmation</b><br/>If the expert rejects, the client is refunded automatically.</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><img src="assets/journey-10.webp" alt="Booking confirmed" width="100%"/><br/><sub><b>10. Booking confirmed</b><br/>A real-time notification arrives as soon as the expert accepts.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-11.webp" alt="Join the session" width="100%"/><br/><sub><b>11. Join the session</b><br/>At the scheduled time, the client joins by chat, chat and voice, call or video.</sub></td>
<td width="33%" valign="top"><img src="assets/journey-12.webp" alt="Session in progress" width="100%"/><br/><sub><b>12. Session in progress</b><br/>A server-controlled countdown shows the time remaining.</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><img src="assets/journey-13.webp" alt="Rate the session" width="100%"/><br/><sub><b>13. Rate the session</b><br/>After the session, the client leaves a rating that feeds the expert's stats.</sub></td>
</tr>
</table>

## Architecture

```mermaid
flowchart LR
  subgraph L0["Client"]
    direction TB
    L0_0["React SPA for clients, experts and admins"]
    L0_1["Socket.io client"]
    L0_2["LiveKit client"]
    L0_3["Stripe Elements"]
  end
  subgraph L1["Edge"]
    direction TB
    L1_0["Nginx on AWS EC2"]
    L1_1["HTTPS"]
    L1_2["Static build + /api & websocket proxy"]
  end
  subgraph L2["Application"]
    direction TB
    L2_0["Express REST API"]
    L2_1["Socket.io realtime hub"]
    L2_2["Cron session scheduler & metering"]
    L2_3["PM2 process manager"]
  end
  subgraph L3["Data & services"]
    direction TB
    L3_0["MongoDB Atlas (transactions)"]
    L3_1["AWS S3 media"]
    L3_2["Stripe"]
    L3_3["LiveKit SFU + TURN"]
    L3_4["Twilio Verify"]
    L3_5["Resend email"]
    L3_6["Groq / Gemini assistant"]
  end
  L0 --> L1
  L1 --> L2
  L2 --> L3
```

## Engineering highlights

- The server is the source of truth for billing: cron jobs start, meter and end sessions, and timers in the browser are display-only.
- Payments are protected against duplicates with a unique index on the payment intent, a check before processing and atomic transactions.
- Security: Helmet headers, rate limiting, verified Stripe webhooks, OTP admin sessions, KYC middleware and no direct S3 URLs.
- GDPR: cookie consent, account deletion with OTP confirmation, and media served through an authenticated proxy with WebP conversion.
- Push-to-deploy CI/CD with GitHub Actions: SSH, install, build and restart PM2 with no downtime.
- Built-in AI support assistant using Groq Llama 3.1, with Gemini as a fallback.

## Tech stack

| Area | Technologies |
|---|---|
| **Frontend** | ![React 18](https://img.shields.io/badge/React%2018-20232A?style=flat-square&logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white) ![TanStack Query](https://img.shields.io/badge/TanStack%20Query-FF4154?style=flat-square&logo=reactquery&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) ![Socket.io client](https://img.shields.io/badge/Socket.io%20client-010101?style=flat-square&logo=socketdotio&logoColor=white) ![LiveKit client](https://img.shields.io/badge/LiveKit%20client-333333?style=flat-square&logo=webrtc&logoColor=white) |
| **Backend** | ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white) ![Socket.io](https://img.shields.io/badge/Socket.io-010101?style=flat-square&logo=socketdotio&logoColor=white) ![node-cron](https://img.shields.io/badge/node--cron-555?style=flat-square) ![Joi](https://img.shields.io/badge/Joi-555?style=flat-square) |
| **Data** | ![MongoDB Atlas](https://img.shields.io/badge/MongoDB%20Atlas-47A248?style=flat-square&logo=mongodb&logoColor=white) ![Mongoose](https://img.shields.io/badge/Mongoose-880000?style=flat-square&logo=mongoose&logoColor=white) ![AWS S3](https://img.shields.io/badge/AWS%20S3-569A31?style=flat-square&logo=amazons3&logoColor=white) |
| **Integrations** | ![Stripe](https://img.shields.io/badge/Stripe-635BFF?style=flat-square&logo=stripe&logoColor=white) ![LiveKit (WebRTC)](https://img.shields.io/badge/LiveKit%20(WebRTC)-333333?style=flat-square&logo=webrtc&logoColor=white) ![Twilio](https://img.shields.io/badge/Twilio-F22F46?style=flat-square&logo=twilio&logoColor=white) ![Resend](https://img.shields.io/badge/Resend-000000?style=flat-square&logo=resend&logoColor=white) ![Google OAuth](https://img.shields.io/badge/Google%20OAuth-4285F4?style=flat-square&logo=google&logoColor=white) ![Groq / Gemini](https://img.shields.io/badge/Groq%20%2F%20Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white) |
| **Infrastructure** | ![AWS EC2](https://img.shields.io/badge/AWS%20EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white) ![PM2](https://img.shields.io/badge/PM2-2B037A?style=flat-square&logo=pm2&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white) |

## About the developer

Designed, built and deployed by **[Shair Ali](https://shairali.com)**, a full-stack developer who owns products end to end: architecture, interface, API, data, payments, servers and CI/CD.

[![Portfolio](https://img.shields.io/badge/Portfolio-shairali.com-111?style=flat-square)](https://shairali.com) [![Fiverr](https://img.shields.io/badge/Fiverr-devshair-1DBF73?style=flat-square&logo=fiverr&logoColor=white)](https://www.fiverr.com/sellers/devshair) [![LinkedIn](https://img.shields.io/badge/LinkedIn-shairali2-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shairali2) [![GitHub](https://img.shields.io/badge/GitHub-shairalidev-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/shairalidev)

<sub>Have a similar project? [Get in touch](https://shairali.com/contact).</sub>
