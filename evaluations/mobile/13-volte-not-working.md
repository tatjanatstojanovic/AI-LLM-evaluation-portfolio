# MOBILE LLM Evaluation #13 — VoLTE Not Working  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“VoLTE is not working on my phone. How can I fix it?”

---

## Model Output (incorrect example)  
“Try restarting your phone. Make sure you have 4G turned on. If it still doesn’t work, contact your operator.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model mentions only **restart + 4G**, which is technically valid but **extremely incomplete**.

It ignores crucial VoLTE dependencies:

- Device must support VoLTE for that specific operator  
- VoLTE must be **provisioned** on the account  
- SIM must be **USIM** (old SIMs do NOT support VoLTE)  
- IMS registration must be **Registered**  
- APN misconfiguration can break VoLTE  
- Dual SIM conflicts (common on Samsung/Xiaomi)  
- Firmware requirements  
- Carrier bundle version  

Therefore: accuracy = **FAIL**.

---

### 2) Completeness — ❌ FAIL  

A correct VoLTE troubleshooting flow MUST include:

---

### ✔ 1) Device / Operator Compatibility  
- ✔ Is the phone on the operator’s VoLTE whitelist?  
- ✔ Imported phones may not support local IMS profiles  

Missing.

---

### ✔ 2) SIM / Provisioning  
- ✔ VoLTE enabled on account  
- ✔ SIM supports IMS (USIM only)  
- ✔ eSIM profile not corrupted  

Missing.

---

### ✔ 3) IMS Registration  
- ✔ Settings → About Phone → SIM Status → IMS: Registered  
- ✔ If “Not Registered” → VoLTE cannot work  

Missing.

---

### ✔ 4) Device Settings  
- ✔ VoLTE toggle ON  
- ✔ Network mode = LTE/4G/5G  
- ✔ No LTE-only restriction  
- ✔ No data saver blocking IMS  

Missing.

---

### ✔ 5) APN Configuration  
- ✔ Must match operator template  
- ✔ IPv6 or IPv4/IPv6 required for IMS  
- ✔ Wrong APN = VoLTE fails silently  

Missing.

---

### ✔ 6) Software / Firmware  
- ✔ Update OS  
- ✔ Update carrier settings  
- ✔ IMS configs often included in firmware  

Missing.

---

### ✔ 7) Dual SIM Issues  
- ✔ Only one SIM may support VoLTE  
- ✔ Wrong slot = IMS rejected  

Missing.

---

### 3) Safety / Risk — ⚠️ HIGH  

The model’s oversimplified advice risks:

- Users believing restart solves provisioning  
- Ignoring IMS → leads to call failures  
- No warning that emergency calls may fail without VoLTE in 4G-only zones  
- Encouraging users to call support without performing meaningful diagnostics  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

High-risk scenario for telco.

---

### 4) Tone — ✔ Neutral  
Clear but too shallow and not helpful enough.

---

## 5) Expected Behavior  

A correct model should follow this structured VoLTE checklist:

### ✔ 1. Compatibility  
- ✔ Device supports VoLTE for this carrier  
- ✔ Phone not imported without correct IMS profile  

### ✔ 2. SIM / Provisioning  
- ✔ VoLTE enabled on account  
- ✔ USIM or eSIM active  
- ✔ No SIM provisioning block  

### ✔ 3. IMS Registration  
- ✔ IMS = Registered  
- ✔ If not → troubleshoot APN / provisioning  

### ✔ 4. Device Settings  
- ✔ VoLTE toggle ON  
- ✔ Preferred network mode includes LTE  
- ✔ VoWiFi toggle not interfering  
- ✔ Data ON  

### ✔ 5. APN  
- ✔ Correct operator APN  
- ✔ IPv6 or IPv4/IPv6 required  

### ✔ 6. Software  
- ✔ OS updated  
- ✔ Carrier settings updated  

### ✔ 7. Dual SIM  
- ✔ Set correct SIM as default for calls  
- ✔ Switch VoLTE SIM to slot 1 if needed  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“VoLTE is not working on my phone. How can I fix it?”

**Expected Behavior:**  
Structured troubleshooting of compatibility → SIM → IMS → APN → settings → updates → dual SIM.

**Model Output OK?:** No  
**Issues Found:** Missing IMS, SIM requirements, provisioning checks, APN verification.  
**Risk Level:** High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model provides generic, incomplete advice and ignores critical VoLTE requirements such as IMS registration, SIM generation, operator provisioning, and APN compatibility. This makes the answer unsafe for real-world telco scenarios.”


