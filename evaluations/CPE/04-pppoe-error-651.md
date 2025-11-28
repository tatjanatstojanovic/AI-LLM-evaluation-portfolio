# TELCO LLM Evaluation #4 — PPPoE Error 651  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“PPPoE keeps failing with error 651. What should I do?”

---

## Model Output (incorrect example)  
“Error 651 usually means the line is busy. Try rebooting your router or reinstalling your broadband driver. If that doesn’t help, call your ISP.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model output is incorrect and mixes **Windows driver issues** with **router-level PPPoE authentication**, which is misleading.

What the model misses:  
- Incorrect PPPoE username/password  
- Missing VLAN tagging (very common failure)  
- PPPoE server unreachable  
- MAC binding mismatch at ISP  
- Incorrect WAN mode (DHCP instead of PPPoE)  
- Authentication timeout  
- DSL/ONT link not established  
- PPP session limit reached  
- MTU mismatch (common cause of PPPoE drops)  

The explanation is technically inaccurate.

---

### 2) Completeness — ❌ FAIL  
Missing critical PPPoE troubleshooting:

- ✔ Verify correct PPPoE credentials  
- ✔ Check VLAN ID configuration (CH/DE/AT often require VLAN 10 or 100)  
- ✔ Check physical link (WAN port up/down, ONT/DSL sync)  
- ✔ Verify WAN mode set to PPPoE (not DHCP, not static)  
- ✔ Check router logs (PPPoE PADT, PADI timeout, authentication failure)  
- ✔ Check MTU (1492 recommended for PPPoE)  
- ✔ Confirm ISP MAC binding / CPE registration  
- ✔ Check if multiple PPP sessions are limited to 1  
- ✔ Check for maintenance window / ISP-side PPP outage  

Model does not present structured PPPoE diagnostics — only generic “restart”.

---

### 3) Safety / Risk — Medium  
The model:  
- Suggests reinstalling “broadband driver” — irrelevant for routers  
- Does not guide the user to check credentials → may cause long outages  
- Does not check if ONT is offline  
- Encourages resets without context  
- Can cause user frustration and unnecessary ISP escalations  

**Ne pružanje diferenciranih dijagnostičkih koraka može povećati broj poziva tehničkoj podršci i troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Neutral tone but technically unhelpful.

---

### 5) Expected Behavior  
A correct model should:

1. Validate WAN link  
   - ✔ ONT/DSL sync OK  
   - ✔ WAN port link-up  

2. Verify PPPoE credentials  
   - ✔ Username  
   - ✔ Password  
   - ✔ Typo check  

3. Check configuration  
   - ✔ WAN mode set to PPPoE  
   - ✔ VLAN tag configured if required  
   - ✔ MTU = 1492  

4. Review router logs  
   - ✔ Authentication failure  
   - ✔ Timeouts  
   - ✔ PADT events  

5. Check ISP provisioning  
   - ✔ MAC binding  
   - ✔ PPP session limit  

6. Restart only after validated diagnostics  
   - ✔ Avoid factory reset unless instructed  
   - ✔ Do NOT reinstall drivers (not applicable)  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“PPPoE keeps failing with error 651. What should I do?”

**Expected Behavior:**  
Provide structured PPPoE troubleshooting including credential validation, VLAN tags, WAN link analysis, PPP logs, and MTU configuration.

**Model Output OK?:** No  
**Issues Found:** Inaccurate assumptions, incorrect PC-related advice, missing PPPoE diagnostics  
**Risk Level:** Medium  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model incorrectly suggests PC driver actions for a router scenario and ignores core PPPoE troubleshooting steps such as verifying credentials, VLAN tagging, MTU configuration, and PPP logs. The response is technically inaccurate and not production-ready.”
