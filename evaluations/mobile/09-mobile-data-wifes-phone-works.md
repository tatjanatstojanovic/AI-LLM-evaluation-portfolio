# MOBILE LLM Evaluation #09 — Mobile Data Not Working (Wife’s Phone Works)  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“My mobile data is not working, but my wife’s phone works.”

---

## Model Output (incorrect example)  
“If your mobile data isn’t working but another phone works, restart your phone, reinsert your SIM card, and contact your provider.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model provides generic suggestions unrelated to the most common root causes.

Missing critical areas:
- SIM not selected for data (dual SIM issue — extremely common)  
- Incorrect APN settings  
- Data limit reached  
- Account suspension or data block  
- LTE registration failure  
- eSIM profile corruption  
- Roaming restrictions (if user is abroad)  

Restarting the phone is correct but insufficient.  
Accuracy = partial, but not acceptable → FAIL.

---

### 2) Completeness — ❌ FAIL  

A proper mobile-data evaluation requires checking:

#### ✔ 1) Device-Side Checks  
- ✔ Mobile Data ON  
- ✔ Airplane mode OFF  
- ✔ Correct SIM selected for “Mobile Data” (dual SIM!)  
- ✔ Preferred network mode = 4G/5G, NOT 3G-only  
- ✔ Data saver OFF  
- ✔ Hotspot/Data Sharing OFF  

The model mentions *none* of these.

---

#### ✔ 2) APN Configuration  
Many data issues come from:  
- Wrong APN name  
- Duplicate APNs  
- APN missing  
- Authentication wrong  
- Wrong MCC/MNC  

Model does not reference APN at all → huge omission.

---

#### ✔ 3) Account-Level Checks  
- ✔ No data limit reached  
- ✔ No billing block  
- ✔ No roaming block  
- ✔ Active subscription  
- ✔ IMEI not blacklisted  

Model does not check any of these.

---

#### ✔ 4) Network-Side Checks  
- ✔ LTE registration  
- ✔ IMSI provisioning  
- ✔ Area outage (even if wife’s phone works, could be device-specific)  
- ✔ Check if device supports operator’s LTE/5G bands  

Completely missing.

---

#### ✔ 5) Physical Layer  
- ✔ Check SIM damage  
- ✔ Check eSIM profile download  
- ✔ Firmware update issues  

Also missing.

---

### 3) Safety / Risk — ⚠️ Medium  

Why medium?

- User may factory-reset or replace device unnecessarily  
- Model does not prevent APN misconfiguration (dangerous!)  
- No warning about touching network settings  
- No distinction between device issue vs. provisioning issue  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Tone is fine, but not helpful and not structured.

---

## 5) Expected Behavior  

A correct model should follow this **structured troubleshooting checklist**:

### ✔ 1. Device  
- ✔ Mobile Data ON  
- ✔ Airplane mode OFF  
- ✔ Correct SIM selected for data (dual SIM!)  
- ✔ Preferred network: 4G/5G/Auto  
- ✔ Data saver OFF  

### ✔ 2. APN  
- ✔ Correct APN name  
- ✔ Correct MCC/MNC  
- ✔ No duplicate or deleted APN entries  
- ✔ Authentication type OK  

### ✔ 3. Account  
- ✔ Data plan active  
- ✔ No billing block  
- ✔ No data-limit block  
- ✔ Roaming settings depending on location  

### ✔ 4. Network  
- ✔ LTE/5G registration  
- ✔ Check operator outage  
- ✔ Device supports operator’s LTE bands  

### ✔ 5. Physical  
- ✔ SIM not damaged  
- ✔ eSIM profile valid  
- ✔ Check after OS update  

### ✔ 6. Avoid risky steps  
- ✔ Reset only as final step  
- ✔ Never advise APN deletion without backup  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“My mobile data is not working, but my wife’s phone works.”

**Expected Behavior:**  
Guide user through device checks → APN → SIM selection → data limits → account status → LTE registration → roaming conditions.

**Model Output OK?:** No  
**Issues Found:** Generic advice, missing APN, missing SIM selection, no LTE/IMS verification, no plan checks  
**Risk Level:** Medium  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model skips key diagnostic steps such as APN verification, SIM selection for data, LTE registration, and billing/data-limit checks. Advice is generic and does not help identify the root cause.”


