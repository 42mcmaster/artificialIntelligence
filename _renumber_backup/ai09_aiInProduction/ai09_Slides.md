---
marp: true
theme: default
paginate: true
---

# Lesson 09: AI in Production
## Artificial Intelligence
### Medina County Career Center

*(course file: `ai09` — what happens AFTER the model works: deploy, monitor, and improve it)*

---

# The Model Is Only Half the Job

In Lessons 7-12 you **built and evaluated** models. In the real world, a model has to be
**deployed, watched, and maintained** — that's most of an AI project's life. The ITS AI exam
tests this back half (Domains 5 & 6): deploy → operate → oversee.

*This is awareness-level: you should know the vocabulary and the ideas, not run a data center.*

---

<!-- _header: "Sub-Lesson 13a — Deploying a Model" -->

# From Notebook to Product

A trained model is just a file until it's **integrated into an application**:

| Step | What it means |
|---|---|
| **Package the model** | save the trained model so an app can load it |
| **Wrap it in an API** | the app sends inputs, gets predictions back |
| **Application integration** | the model plugs into a real workflow (website, app, tool) |
| **Batch vs. real-time** | score a big file overnight, **or** answer one request instantly |

**A production pipeline** is the whole path: new data → model → prediction → the app that uses it.

---

<!-- _header: "Sub-Lesson 13b — Monitoring & Drift" -->

# Models Get Worse Over Time: Drift

The world changes, so a model trained on old data slowly stops matching reality:

- **Data drift** — the incoming data's distribution shifts (new customers, new inputs)
- **Concept drift** — the **relationship** between inputs and the answer changes over time

Either way, **accuracy quietly drops in production.** You only catch it if you're **monitoring**.

---

<!-- _header: "Sub-Lesson 13b — Monitoring & Drift" -->

# Monitor → Alert → Retrain

The maintenance loop for a live model:

```
  Monitor metrics  -->  Alert on a drop  -->  Retrain on recent data  -->  Redeploy
        ^                                                                     |
        +---------------------------------------------------------------------+
```

- **Monitor** key metrics on live data (accuracy, error rate, latency)
- **Alert** when a metric crosses a threshold (drift detected)
- **Retrain** on more recent data and **redeploy**

---

<!-- _header: "Sub-Lesson 13c — Feedback & Business Impact" -->

# The Feedback Loop

A deployed model can **keep learning** from real outcomes:

- The model makes predictions → real results come back → those become **new labels** → the model is **retrained**
- User **corrections** ("this was wrong") feed back in too

This is how a recommender or spam filter stays current. Handling this **user feedback** well is a Domain 6 skill.

---

<!-- _header: "Sub-Lesson 13c — Feedback & Business Impact" -->

# Did It Actually Help? KPIs

A model's real success is **business impact**, not just accuracy:

- Translate the business goal into a **KPI** (key performance indicator): fewer fraud losses, more sales, faster response
- **Deploy an MVP** quickly, measure the KPI, and iterate
- **Evaluate on a regular schedule** — is it still worth running?

**A 99%-accurate model that no one uses has zero business impact.**

---

# Key Takeaways

| Concept | What it means |
|---|---|
| **Production pipeline** | new data → model → prediction → app that uses it |
| **Application integration** | wiring the model into a real workflow (often via an API) |
| **Data / concept drift** | the world changes, so accuracy drops over time |
| **Monitoring** | watch live metrics to catch drift |
| **Feedback loop** | real outcomes become new labels to retrain on |
| **KPIs / business impact** | measure whether it actually helped |

---

# Learning Objectives (ITS AI Domains 5 & 6)

✓ Describe how a model is deployed and integrated into an application
✓ Explain data drift vs. concept drift and why accuracy drops in production
✓ Describe the monitor → alert → retrain → redeploy loop
✓ Explain the feedback loop and handling user feedback
✓ Connect a model to business impact via KPIs and regular evaluation

---
