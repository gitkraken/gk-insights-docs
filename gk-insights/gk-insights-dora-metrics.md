---
title: DORA Metrics in GitKraken Insights
description: Learn about DORA metrics in GitKraken Insights, including Deploy Frequency, Change Lead Time, Mean Time to Repair/Recover, and Defect Rate.
taxonomy:
    category: gk-dev
---
<kbd>Last updated: February 2026</kbd>

DORA (DevOps Research and Assessment) metrics are a standardized set of four key performance indicators: deployment frequency, lead time for changes, change failure rate, and time to restore service.

Developed by a Google Cloud research team, these metrics help organizations measure DevOps performance, identify areas for improvement, and deliver software more efficiently and reliably.

---

## Deploy Frequency

**Definition:** _The total number of deployments, as determined by the rules configured in the **Releases** settings._

This metric shows how often new code is released or deployed to production, measured as the number of deployments per day, week, or other selected timeframe.

<figure>
  <img src="/wp-content/uploads/deploy-frequency.png" srcset="/wp-content/uploads/deploy-frequency@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Shows deployments per day, week or selected timeframe.</figcaption>
</figure>

In addition to the main chart, the following submetrics are displayed when you click the Details button:

- **Deployments per day**
- **Lead time for changes**
- **Average hours to repair (MTTR)**
- **Change failure rate**

<figure>
  <img src="/wp-content/uploads/deployment-frequency-oct-2025.png" srcset="/wp-content/uploads/deployment-frequency-oct-2025@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Click the Details button to get 4 additional metrics.</figcaption>
</figure>

---

## Change Lead Time

**Definition:** _The time between the first commit linked to an issue (such as a Jira ticket) and when the associated code is deployed._

This metric shows how long each pull request within a selected timeframe took to go from the first commit until it was deployed. Values are expressed in **days** and are calculated over a rolling **7-day period**.

<figure>
  <img src="/wp-content/uploads/change-lead-time.png" srcset="/wp-content/uploads/change-lead-time@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Shows how long each PR took from first commit to deployment.</figcaption>
</figure>

---

## Mean Time to Repair/Recover (MTTR)

**Definition:** _Business hours between "defect detected" and "final fix deployed"._

This metric shows how long each pull request within a selected timeframe took to go from the first commit until it was deployed. Values are expressed in **days** and calculated over a rolling **7-day period**. Lower MTTR indicates that teams can respond quickly to incidents and minimize downtime.

---

## Defect Rate

**Definition:** _The percentage of deployments that resolve a critical defect. This metric measures the stability and quality of your deployment process._

This metric shows the number of defects detected over time. Values are expressed as **defects** over a rolling **7-day window**. A lower defect rate indicates a more stable and reliable deployment process.
