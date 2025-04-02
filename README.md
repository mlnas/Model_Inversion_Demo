# Model Inversion Attack Demo — Executive Overview

##  What This Project Demonstrates

This interactive demo shows how a machine learning model — even when exposed *only as an API* — can leak sensitive patterns from the data it was trained on. It simulates a **Model Inversion Attack**, where an adversary attempts to **reconstruct private input data** (e.g., customer behavior) by manipulating the model’s output.

The project also shows how to defend against this risk using **AI security tools** like the **Adversarial Robustness Toolbox (ART)** and **SecML**, and compares the attack effectiveness before and after defenses are applied.

---

##  What Is a Model Inversion Attack?

A model inversion attack is when an attacker **reconstructs inputs** (like images or financial records) by probing a machine learning model repeatedly.

###  Business Threat:
Even if your data isn’t shared, **your model can leak information** about the people, behaviors, or patterns it was trained on.

###  Real-World Targets in a Business:
- A competitor could reconstruct **fraud patterns** or **high-risk customer profiles**
- An attacker might recreate **training samples** that resemble actual customers
- A malicious insider could extract sensitive features by querying internal APIs

---

##  Attack Flow (Simplified)

1. **Attacker chooses a target label**  
   E.g., “Reconstruct a sample of a high-risk customer.”

2. **Starts with random noise**

3. **Uses model feedback (e.g., prediction confidence)**  
   Adjusts input step by step to make the model say “Yes, that’s it.”

4. **Ends up with an input that the model believes represents the target class**  
   That input may look **alarmingly similar to real data** the model was trained on.

---

##  Business Impact of a Successful Attack

-  Re-identification of real individuals (privacy breach)
-  Regulatory non-compliance (e.g., GDPR, CCPA, PCI-DSS)
-  Leakage of proprietary logic (e.g., fraud scoring logic)
-  Reputational and trust damage from exposed data
-  Potential legal, audit, or partner fallout

---

##  How We Defend Against It

We secure your models using:
-  **ART & SecML** to simulate, test, and benchmark threats
-  **Model hardening techniques** like:
  - Dropout & regularization
  - Output obfuscation (e.g., logits clipping)
  - Differential privacy (optional)
-  Before/after risk reporting
-  Integration into your **CI/CD and MLOps** workflows

---

##  What the Demo Includes

This demo lets you interactively test a model with and without defenses.

###  Target Digit Selector
Choose which digit (0–9) the attack will try to reconstruct.  
In a real system, this could represent:
- A customer category
- A transaction risk score
- A segmentation label

---

###  Image Panels

| Panel | What It Shows |
|-------|----------------|
| **Original Sample** | A real data point from the test set |
| **Baseline Inversion** | What an attacker reconstructs from the unprotected model |
| **Defended Inversion** | What the attacker gets after model defenses are applied |

You’ll see that defended reconstructions are **blurred, noisy, or inaccurate** — showing the effectiveness of the privacy hardening.

---

###  Inversion Loss Chart

This chart shows **how easily an attacker can reconstruct data**.

- Baseline model → fast convergence = vulnerable
- Defended model → slower/lower convergence = safer

---

###  “Train Models” Button

Retrains both baseline and hardened models from scratch.  
You can test again to compare performance before and after defenses are applied.

---
