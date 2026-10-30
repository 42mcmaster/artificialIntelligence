# ai09: AI in Production — Study Guide

**Course**: Applications of AI (CTE) | **School**: Medina County Career Center
**Instructor**: Ryan McMaster | **Standards**: ITS AI Domain 5 (deploy/production) + Domain 6 (operate/oversight)

> Awareness-level: know the vocabulary and the ideas of taking a model to production, monitoring it,
> and measuring impact. You won't run a data center — but the cert tests these concepts (~1 in 5 questions).

---

## 1. Deploying a model (Domain 5)
A trained model is a file until it's **integrated into an application**:
- **Package** the model so an app can load it.
- **Wrap it in an API** — the app sends inputs, gets predictions back.
- **Application integration** — the model plugs into a real workflow (site, app, tool).
- **Batch vs. real-time** — score a large file on a schedule, or answer one request instantly.
- A **production pipeline** = new data → model → prediction → the app that uses it.

## 2. Drift — why models decay (Domain 5/6)
| Drift type | What changes | Example |
|---|---|---|
| **Data drift** | the incoming data's distribution | new kinds of customers/inputs |
| **Concept drift** | the input→output **relationship** | what counts as "fraud" evolves |

Either way, **accuracy quietly drops in production** — you only see it if you **monitor**.

## 3. The maintenance loop
**Monitor → Alert → Retrain → Redeploy.** Watch live metrics (accuracy, error rate, latency);
alert when a metric crosses a threshold; retrain on **recent** data; redeploy.

## 4. The feedback loop (Domain 6)
Predictions → real outcomes come back → those become **new labels** → retrain. User **corrections**
feed in too. This keeps recommenders and spam filters current.

## 5. Business impact & KPIs (Domain 6.2)
- Translate the business goal into a **KPI** (fewer losses, more sales, faster response).
- **Deploy an MVP** quickly, measure the KPI, iterate.
- **Evaluate on a schedule** — is it still worth running?
- *A 99%-accurate model no one uses has zero business impact.*

---

## Quick vocabulary
**Production pipeline · application integration · API · batch vs. real-time · data drift · concept drift ·
monitoring · alert threshold · retrain/redeploy · feedback loop · user feedback · KPI · MVP · business impact.**

## Study Tips
1. **Deployment = integrating the model into an app** (often via an API), not just having a good model.
2. **Concept drift** = the input→output *relationship* changes; **data drift** = the *inputs* change. Both drop accuracy.
3. **The fix for drift is retraining on recent data** — after **monitoring** catches the drop.
4. **Feedback loop** = real outcomes become new labels to retrain on.
5. **Business impact is measured with KPIs** — accuracy alone isn't success.
