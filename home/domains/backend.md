---
description: Comprehensive directory of modern backend development topics, frameworks, and architecture patterns.
icon: server
layout:
width: wide
title:
visible: true
description:
visible: true
tableOfContents:
visible: false
outline:
visible: false
pagination:
visible: false
metadata:
visible: false
tags:
visible: true
actions:
visible: true
anchors:
visible: false
---

⚙️ Backend Engineering Hub

Ask Backend AI...



Express & Node.js
Auth & Security
Real-Time Sync

Core Concepts & Modules

Explore our structured modules to build robust, scalable, production-ready server applications.

🌐 Core Web Servers & APIs

🔐 Auth, Async & Cloud Storage

{% columns %}
{% column width="50%" %}

Interactive Code Examples

Each concept in the directory comes paired with step-by-step code walkthroughs. Learn how to write secure middleware, process background queues, and manage active connections.

{% hint style="info" icon="sparkle" %}
Building your first production backend?

Ask AI to generate a complete setup template tailored to your tech stack.

Generate Boilerplate...
{% endhint %}

{% hint style="warning" icon="life-ring" %}
Common Architecture Questions

Direct file uploads bypass Express workers, hogging memory and I/O. Presigned URLs let users upload directly to AWS S3 or Cloudflare R2, keeping your backend fast and responsive.

Use BullMQ for any heavy or slow task that shouldn't block the HTTP request-response cycle—such as sending emails, processing videos, generating PDFs, or calling external APIs.

Ask architectural question...
{% endhint %}

{% endcolumn %}

{% column width="50%" %}
{% stepper %}
{% step %}

Select a Module

Choose from Web Servers, Auth, Caching & Queues, WebSockets, or Object Storage.
{% endstep %}

{% step %}

Test Code Snippets

Explore ready-to-run implementation examples for your services.

{% tabs %}
{% tab title="Express & Auth" %}
{% code overflow="wrap" %}

import express from "express";
import jwt from "jsonwebtoken";

const app = express();
app.use(express.json());

app.get("/api/protected", (req, res) => {
  const token = req.headers.authorization?.split(" ")[1];
  if (!token) return res.status(401).json({ error: "Unauthorized" });

  const payload = jwt.verify(token, process.env.JWT_SECRET!);
  res.json({ message: "Access granted", user: payload });
});


{% endcode %}
{% endtab %}

{% tab title="BullMQ Worker" %}
{% code overflow="wrap" %}

import { Worker } from "bullmq";

const worker = new Worker("email-queue", async (job) => {
  console.log(`Sending email to ${job.data.email}`);
  // Execute async email transport
}, { connection: { host: "localhost", port: 6379 } });


{% endcode %}
{% endtab %}

{% tab title="WebSocket Server" %}
{% code overflow="wrap" expandable="true" %}

import { WebSocketServer } from "ws";

const wss = new WebSocketServer({ port: 8080 });

wss.on("connection", (ws) => {
  ws.on("message", (data) => {
    ws.send(`Echo response: ${data}`);
  });
});


{% endcode %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}

Deploy & Scale

Follow our deployment guides to push your code onto Docker, AWS, or Render with full CI/CD.
{% endstep %}
{% endstepper %}
{% endcolumn %}
{% endcolumns %}