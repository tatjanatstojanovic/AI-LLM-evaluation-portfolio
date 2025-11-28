# TELCO LLM Evaluation #4 — PPPoE Error 651  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“I am getting *PPPoE Error 651*. My internet won’t connect. What should I do?”

---

## Model Output (incorrect example)  
“Error 651 usually means the modem is disconnected. Restart your router and check the cable. If the issue continues, contact your ISP.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model gives only generic steps and completely ignores real PPPoE failure causes.

Missing critical PPPoE root causes:  
- Wrong PPPoE username/password  
- Account suspended / quota exceeded  
- VLAN tagging missing or incorrect  
- Wrong WAN mode (DHCP instead of PPPoE)  
- ISP RADIUS server unreachable  
- PPP session limit reached (duplicate sessions)  
- ONT/Modem link-down event before PPP negotiation  
- MTU/MRU mismatch (common cause of PPPoE failure)  
- Misconfigured MAC binding  
- CPE bug after firmware upgrade  

The answer oversimplifies and does not reflect actual troubleshooting.

---

### 2) Completeness — ❌ FAIL  
A correct PPPoE evaluation requires multiple validation layers.

Missing diagnostics:

- ✔ Verify PPPoE credentials (case-sensitive, full username format)  
- ✔ Check if account is active at ISP (RADIUS reject)  
- ✔ Check VLAN tagging (PPPoE requires specific VLAN)  
- ✔ Ensure WAN is set to PPPoE (not DHCP/Static)  
- ✔ Check for duplicate session (session already active)  
- ✔ Review PPP logs (LCP/CHAP failures)  
- ✔ Test WAN physical link (LOS/LOF if on fiber)  
- ✔ Validate MTU (1492 standard)  
- ✔ Reboot ONT/Modem *before* router reconnect  
- ✔ Verify MAC binding with ISP if required  

The model does not follow any structured PPPoE troubleshooting sequence.

---

### 3) Safety / Risk — Medium–High  
The model:  
- Suggests reboots without verifying authentication  
- Does not warn about account suspension (common cause)  
- Does not check for duplicate PPP sessions → user cannot reconnect  
- Could cause unnecessary resets of modem/router  
- Misses VLAN misconfiguration → user can lose more connectivity  
- Does not check logs → user stays offline for hours  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Clear but shallow and not technically helpful.

---

### 5) Expected Behavior  
A correct model should:

1. Validate PPPoE user credentials  
   - ✔ Correct username/password  
   - ✔ Account active; no RADIUS reject  

2. Check WAN mode & config  
   - ✔ WAN set to PPPoE  
   - ✔ Correct VLAN tag  
   - ✔ MTU 1492  

3. Review logs  
   - ✔ LCP timeout  
   - ✔ CHAP authentication reject  
   - ✔ PPP session already active  

4. Validate WAN physical link  
   - ✔ ONT/Modem LOS/LOF  
   - ✔ Ethernet link status  

5. Check ISP-side issues  
   - ✔ PPP server downtime  
   - ✔ RADIUS failure  
   - ✔ Duplicate session  

6. Only then suggest controlled reboot  
   - ✔ Restart ONT first  
   - ✔ Then restart router  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“I am getting *PPPoE Error 651*. My internet won’t connect. What should I do?”

**Expected Behavior:**  
Provide structured PPPoE troubleshooting including credential validation, VLAN tag checks, WAN-mode configuration, PPP logs, duplicate sessions, and physical link verification.

**Model Output OK?:** No  
**Issues Found:** Missing authentication checks, missing VLAN checks, missing logs, no MTU validation  
**Risk Level:** Medium–High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model oversimplifies PPPoE troubleshooting and misses essential steps such as validating credentials, confirming VLAN tags, checking PPP logs, and ruling out RADIUS and duplicate-session issues. The answer is incomplete and not reliable for production use.”

