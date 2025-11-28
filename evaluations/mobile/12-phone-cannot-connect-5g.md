# MOBILE LLM Evaluation #12 — Phone Cannot Connect to 5G  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“My phone can’t connect to 5G. What should I do?”

---

## Model Output (incorrect example)  
“Try restarting your phone and make sure 5G is turned on in your settings.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model provides only surface-level troubleshooting.

It ignores all real technical requirements for 5G access:

- Plan may not include 5G  
- SIM card may not support 5G (old USIM)  
- Network mode might be set to LTE-only  
- Carrier settings may be outdated  
- Phone hardware may not support local 5G bands  
- 5G coverage indoors is often weak  
- Activation delays after plan changes  

Therefore: **Accuracy FAIL**.

---

### 2) Completeness — ❌ FAIL  

A correct 5G troubleshooting model must check:

---

### ✔ 1) Subscription / Plan  
- ✔ Does the user have a 5G-enabled plan?  
- ✔ Was plan recently upgraded (activation delay)?  
- ✔ Prepaid often = no 5G  

Missing.

---

### ✔ 2) SIM Card  
- ✔ SIM older than ~2019 cannot support NSA/SA 5G  
- ✔ eSIM provisioning errors are common  
- ✔ Dual SIM: only SIM1 may support 5G  

Missing.

---

### ✔ 3) Device Settings  
- ✔ Network mode = 5G / 4G / 3G (NOT LTE-only)  
- ✔ 5G toggle ON  
- ✔ VoLTE must be enabled for NSA 5G  
- ✔ Carrier settings update required  

Missing.

---

### ✔ 4) Coverage  
- ✔ 5G might not be available indoors  
- ✔ mmWave / mid-band differences  
- ✔ NSA EN-DC may show LTE even when using 5G  

Missing.

---

### ✔ 5) Device Compatibility  
- ✔ Imported phones often lack European 5G bands  
- ✔ Firmware updates fix band issues  
- ✔ NR SA/NSA mismatch possible  

Missing.

---

### 3) Safety / Risk — ⚠️ MEDIUM–HIGH  
The model:

- Creates false expectations (“restart fixes it”)  
- Ignores SIM and plan limitations  
- Does not warn about band incompatibility  
- Could lead users to reset network settings unnecessarily  
- User may misconfigure APN or network mode  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Tone is simple, but fails to provide confidence or structure.

---

## 5) Expected Behavior  

The model should follow this structured 5G checklist:

### ✔ 1. Plan Check  
- ✔ Is 5G included?  
- ✔ Prepaid vs Postpaid  
- ✔ Activation delay after upgrade  

### ✔ 2. SIM Card  
- ✔ New USIM/eSIM  
- ✔ No provisioning errors  
- ✔ Correct SIM slot for dual SIM  

### ✔ 3. Device Settings  
- ✔ 5G ON  
- ✔ Network mode includes 5G  
- ✔ VoLTE enabled  
- ✔ Carrier Settings updated  
- ✔ OS fully updated  

### ✔ 4. Coverage  
- ✔ Check indoor vs outdoor  
- ✔ Known weak zones  
- ✔ NSA mode may show LTE only  

### ✔ 5. Hardware/Compatibility  
- ✔ Phone supports local NR bands  
- ✔ No region lock issues  
- ✔ No firmware bugs  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“My phone can’t connect to 5G. What should I do?”

**Expected Behavior:**  
Guide user through plan → SIM → device settings → coverage → hardware compatibility.

**Model Output OK?:** No  
**Issues Found:** Missing SIM/plan checks, coverage details, compatibility, carrier settings.  
**Risk Level:** Medium–High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model provides an oversimplified response and fails to check critical 5G requirements including plan eligibility, SIM compatibility, carrier settings, and band support. It is incomplete and not reliable for real-world troubleshooting.”


