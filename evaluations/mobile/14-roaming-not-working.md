# MOBILE LLM Evaluation #14 — Roaming Not Working  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“My roaming is not working. What should I do?”

---

## Model Output (incorrect example)  
“Turn roaming on in your phone settings. Restart your phone. If it still doesn’t work, contact your carrier.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The advice is **oversimplified** and only covers the most basic surface steps.

Missing critical roaming requirements:

- Roaming must be **enabled on the account** (carrier-side)
- User must have an **active roaming package/plan**
- Billing issues can BLOCK roaming
- APN misconfiguration prevents data roaming
- Manual network selection required in many countries
- SIM must support international roaming
- Some destinations require LTE-only or 3G fallback
- eSIM provisioning may fail abroad

Therefore, accuracy = **FAIL**.

---

### 2) Completeness — ❌ FAIL  

A correct roaming diagnostic flow MUST include:

---

### ✔ 1) Carrier-Side Provisioning  
- ✔ Roaming enabled on the account  
- ✔ No unpaid bills  
- ✔ Prepaid limits (many prepaid plans block roaming)  
- ✔ Zone-specific roaming rules (EU vs. non-EU)  

Missing.

---

### ✔ 2) Device Settings  
- ✔ Data Roaming ON  
- ✔ Preferred network mode (LTE/3G/2G depending on country)  
- ✔ No “5G only” lock  
- ✔ Disable Data Saver mode  

Missing.

---

### ✔ 3) Network Selection  
- ✔ Try manual selection  
- ✔ Choose partner network  
- ✔ Avoid networks without a roaming agreement  

Missing.

---

### ✔ 4) APN Verification  
APN MUST be correct.  
Wrong APN = NO data abroad.

Missing.

---

### ✔ 5) SIM / eSIM  
- ✔ Old SIM may not support roaming  
- ✔ eSIM could fail to download roaming profile  
- ✔ Dual SIM device may use wrong SIM for data  

Missing.

---

### ✔ 6) Country-Specific Issues  
- ✔ Some countries shut down 3G → roam only on LTE  
- ✔ Some require 3G fallback because LTE VoLTE roaming not supported  

Missing.

---

### 3) Safety / Risk — ⚠️ HIGH  

Why high risk?

- User may remain without mobile network abroad  
- Emergency calls may fail if phone stays on a non-roaming network  
- APN changes without guidance may break internet entirely  
- Users may waste time rebooting instead of fixing provisioning  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Clear but too shallow, not supportive for a high-stress situation (traveling).

---

## 5) Expected Behavior  

A correct model should follow this roaming checklist:

---

### ✔ 1. Carrier Provisioning  
- ✔ Roaming active on account  
- ✔ No payment issues  
- ✔ Plan supports roaming  
- ✔ Prepaid limits checked  

### ✔ 2. Device Settings  
- ✔ Data Roaming ON  
- ✔ Network mode = LTE/3G/2G  
- ✔ Data Saver OFF  

### ✔ 3. Network Selection  
- ✔ Try manual network selection  
- ✔ Connect to an approved partner network  

### ✔ 4. APN  
- ✔ APN matches operator template  
- ✔ No duplicated custom APNs  

### ✔ 5. SIM  
- ✔ USIM or valid eSIM  
- ✔ Correct SIM selected for data (dual SIM phones)  

### ✔ 6. Software  
- ✔ Latest OS  
- ✔ Latest carrier settings  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“My roaming is not working. What should I do?”

**Expected Behavior:**  
Comprehensive roaming diagnostics including account provisioning, APN, manual network selection, SIM, device settings, and country-specific connectivity.

**Model Output OK?:** No  
**Issues Found:** Missing provisioning checks, APN validation, manual network selection, billing issues, dual-SIM logic.  
**Risk Level:** High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model provides oversimplified advice and misses critical roaming diagnostics such as operator provisioning, APN validation, network selection, and SIM compatibility. This can leave the user without service abroad and is unsafe for real-world support scenarios.”


