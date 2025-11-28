
# MOBILE LLM Evaluation #10 — Not Receiving Calls  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“I’m not receiving calls even though everything looks fine.”

---

## Model Output (incorrect example)  
“Try restarting your phone or checking airplane mode.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model provides incorrect and dangerously incomplete advice.

It completely ignores the **#1 real cause** of missing calls:
- ✔ Call Forwarding (CFU / CFB / CFNRy) accidentally enabled  
- ✔ Especially common after SIM/eSIM changes, travel, Teams/WhatsApp interference  

Missing critical mobile voice requirements:
- IMS Registration  
- VoLTE provisioning  
- Call barring  
- Dual SIM conflicts  
- DND (Do Not Disturb)  
- SIM provisioning  

Because of these omissions → Accuracy FAIL.

---

### 2) Completeness — ❌ FAIL  

A proper inbound-call troubleshooting must include:

#### ✔ 1) Call Forwarding (CRITICAL)
- CFU — unconditional forwarding  
- CFB — busy forwarding  
- CFNR — no reply  
- CFNRy — unreachable  

### Without checking CF, 80% of cases remain unsolved.  
Model does not mention CF at all.

---

#### ✔ 2) Device-Side Checks  
- ✔ DND OFF  
- ✔ Airplane mode OFF  
- ✔ VoLTE ON  
- ✔ Network mode = 4G/5G preferred  
- ✔ Allow 4G calling  
- ✔ App-level call permissions (Teams, WhatsApp, Viber)  

Missing.

---

#### ✔ 3) SIM & Account  
- ✔ SIM active, not barred  
- ✔ eSIM provisioning valid  
- ✔ No incoming call barring activated  
- ✔ Correct SIM selected for calls (dual SIM!)  

Missing.

---

#### ✔ 4) Network / IMS  
- ✔ IMS Registration status  
- ✔ VoLTE profile active  
- ✔ Operator-side provisioning  
- ✔ Local cell fallback issues (common during 3G shutdown)  

Missing entirely.

---

### 3) Safety / Risk — ⚠️ HIGH  

Why high?

- User may remain unreachable for hours or days  
- Calls can silently fail due to IMS/VoLTE issues  
- Model does not warn about call barring  
- Restart-only advice is misleading  
- Incorrect CF settings can break emergency call routing  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Tone is fine, but content is not helpful and lacks structure.

---

## 5) Expected Behavior  

A correct AI model should follow this structured checklist:

### ✔ 1. Call Forwarding (first mandatory step)
- ✔ Check CFU (must be OFF)  
- ✔ Check CFB  
- ✔ Check CFNR / CFNRy  
- ✔ Remove all forwarding rules  

### ✔ 2. Device  
- ✔ DND OFF  
- ✔ Airplane mode OFF  
- ✔ VoLTE ON  
- ✔ Network mode 4G/5G  
- ✔ App-level call permissions  

### ✔ 3. SIM / Account  
- ✔ SIM active  
- ✔ Correct SIM selected for calls (dual SIM)  
- ✔ No call barring  
- ✔ eSIM profile not corrupted  

### ✔ 4. Network / IMS  
- ✔ IMS Registered = Yes  
- ✔ VoLTE provisioned  
- ✔ Operator-side barring  
- ✔ Local network fallback issues  

### ✔ 5. Avoid unsafe advice  
- ✔ No random resets  
- ✔ No SIM reinsertion unless needed  
- ✔ No factory reset  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“I’m not receiving calls even though everything looks fine.”

**Expected Behavior:**  
Start with Call Forwarding → DND → VoLTE/IMS → SIM/account → network provisioning.

**Model Output OK?:** No  
**Issues Found:** Skips CF, IMS, VoLTE, call barring, SIM conflicts  
**Risk Level:** High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model provides generic advice and omits the essential first step (checking Call Forwarding). It also ignores IMS registration, VoLTE provisioning, and call barring. This can leave users unreachable and is unsafe in real-world scenarios.”

