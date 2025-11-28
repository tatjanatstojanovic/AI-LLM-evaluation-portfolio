# TELCO LLM Evaluation #6 — 5 GHz Wi-Fi Keeps Disappearing  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“My 5 GHz Wi-Fi keeps disappearing randomly. Sometimes I only see the 2.4 GHz network. What is happening?”

---

## Model Output (incorrect example)  
“5 GHz can be unstable in some homes. Try restarting your router or change the Wi-Fi name. If it still disappears, it’s normal — just use 2.4 GHz.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model gives vague consumer-level suggestions and ignores actual 5 GHz technical causes.

Missing technical factors:
- DFS radar events → router forced to leave channel  
- Auto-channel switching → forced reboot of 5 GHz radio  
- Regulatory domain restrictions (EU vs US channels)  
- 160 MHz / 80 MHz channel width instability  
- Transmit power drop after firmware update  
- Band steering bugs → clients forced to 2.4 GHz  
- Hidden SSID bug after reboot  
- Beacon interval changes  
- Temperature throttling of the 5 GHz radio  
- Mesh backhaul stealing 5 GHz band  

The explanation “it’s normal” is incorrect and unsafe.

---

### 2) Completeness — ❌ FAIL  
A proper 5 GHz evaluation must check ALL radio parameters.

Missing critical diagnostics:

- ✔ Check DFS events (weather radar, airport radar)  
- ✔ Check channel (36–48 = stable; 52–140 = DFS)  
- ✔ Check channel width (20/40/80/160 MHz)  
- ✔ Check region/regulatory domain  
- ✔ Verify power level (Tx power limitations)  
- ✔ Check for overheating (router throttles 5 GHz off)  
- ✔ Mesh backhaul using 5 GHz → SSID down  
- ✔ Band steering / Smart Connect bugs  
- ✔ Check if SSID is set to “hidden”  
- ✔ Check if client device supports chosen channel  

The model does not provide any structured troubleshooting.

---

### 3) Safety / Risk — ⚠ Medium  
The model:
- Encourages meaningless restarts  
- Says “it’s normal” → can hide real interference problems  
- Tells user to “just use 2.4 GHz” → bad advice  
- Ignores DFS restrictions → users may break Wi-Fi rules unknowingly  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Clear tone, but dismissive and harmful.

---

### 5) Expected Behavior  

A correct model should follow this checklist:

#### 1. Check radio environment  
- ✔ Identify if router is on DFS channel  
- ✔ Check logs for DFS radar triggers  
- ✔ Recommend switching to CH 36–48  

#### 2. Check channel width  
- ✔ If set to 160 MHz → reduce to 80/40 MHz  
- ✔ Check device compatibility  

#### 3. Check steering / mesh  
- ✔ Disable band steering temporarily  
- ✔ Check if mesh nodes use 5 GHz as backhaul  

#### 4. Check power & firmware  
- ✔ Verify transmit power  
- ✔ Confirm firmware version (DFS bugs common)  
- ✔ Reboot only *after* diagnostics  

#### 5. Check SSID / settings  
- ✔ Ensure 5 GHz SSID is enabled  
- ✔ Ensure SSID is not “hidden”  
- ✔ Confirm naming convention (same SSID possible with steering)  

#### 6. Physical factors  
- ✔ Check overheating of router  
- ✔ Check placement (no enclosed cabinet)  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“My 5 GHz Wi-Fi keeps disappearing. What should I do?”

**Expected Behavior:**  
Provide structured 5 GHz troubleshooting including DFS analysis, channel width checks, regulatory limits, steering/mesh evaluation, SSID status, and power settings.

**Model Output OK?:** No  
**Issues Found:** Incorrect assumptions, dismissive tone, ignores DFS/channel/width/power diagnostics  
**Risk Level:** Medium  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model incorrectly states that disappearing 5 GHz is ‘normal’ and provides shallow advice. It ignores DFS radar events, channel width issues, regulatory limits, firmware bugs, SSID visibility problems, and mesh backhaul interference. The answer is incomplete and not production-ready.”

