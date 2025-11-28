# TELCO LLM Evaluation #2 — Nokia Beacon Disconnecting
LLM Tested: ChatGPT v5.x (simulation)

## Prompt
“My Nokia Beacon keeps disconnecting every few minutes. What should I do?”

## Model Output (incorrect example)
“Try restarting the Beacon and place it closer to your modem. It usually disconnects because of weak signal.”

## Evaluation

### 1) Accuracy — ❌ FAIL
The model ignores real technical causes of Beacon disconnect issues:
- Mesh backhaul issues (Ethernet vs Wi-Fi backhaul)
- DFS channel switching (very common Beacon cause)
- Auto-channel instability
- Interference from radar/weather stations on 5 GHz
- Firmware bugs (common in early Beacon builds)
- Beacon–Gateway distance matrix (placement rules)
- Incorrect topology (Beacon behind another router → double NAT)

The answer is oversimplified and partially incorrect.

---

### 2) Completeness — ❌ FAIL
Missing critical diagnostics:
- ✔ Check if Beacon uses Ethernet backhaul (preferred)
- ✔ Verify mesh signal quality (RSSI, mesh hop count)
- ✔ Check DFS channel events (causes periodic drops)
- ✔ Check auto-channel → switch to manual stable channel
- ✔ Confirm firmware version on both Beacon and main gateway
- ✔ Check topology (no double NAT, no cascade router)
- ✔ Check if Beacon is too close or too far (optimal 6–10 m)
- ✔ Check for overlapping Wi-Fi networks

The model doesn’t present a structured troubleshooting flow.

---

### 3) Safety / Risk — Medium–High
The model:
- Encourages meaningless restarts  
- Ignores mesh instability → user keeps experiencing drops  
- Hides root cause (DFS) → very common in EU apartments  
- Doesn’t rule out topology conflicts  
- Can lead to unnecessary device replacement

Lack of accurate diagnostics may increase support calls and user frustration.

---

### 4) Tone — ✔ Neutral
Clear tone but not technically helpful and lacks context.

---

### 5) Expected Behavior
A correct model should:
1. Check if the Beacon is using Ethernet or Wi-Fi backhaul  
2. Verify signal strength between main unit and Beacon  
3. Check DFS/auto-channel logs  
4. Suggest switching to a stable non-DFS 5 GHz channel  
5. Confirm firmware updates  
6. Verify correct placement (not in corners, behind TV, or near metal)  
7. Check network topology (no double NAT, no unmanaged switches)  
8. Reboot mesh only *after* diagnostics

---

## Final PASS/FAIL Entry

**Prompt:**  
“My Nokia Beacon keeps disconnecting every few minutes.”

**Expected Behavior:**  
Provide structured mesh troubleshooting: backhaul verification, DFS issues, firmware, placement rules, topology validation, and channel analysis.

**Model Output OK?:** No  
**Issues Found:** Oversimplified advice, missing Beacon-specific diagnostics, misleading root cause assumption.  
**Risk Level:** Medium–High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model provides generic suggestions and ignores key factors for Nokia Beacon mesh stability such as DFS channel switching, backhaul verification, firmware issues, and topology conflicts. The response is incomplete and not suitable for production troubleshooting.”

