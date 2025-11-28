# TELCO LLM Evaluation #3 — WAN Disconnected / No Internet  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“My router says *WAN Disconnected*. What should I do?”

---

## Model Output (incorrect example)  
“Restart your router and check if the cable is properly plugged in. If it doesn’t work, contact your internet provider.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model gives only superficial steps and ignores technical WAN-layer diagnostics.

It misses critical telco causes:  
- Incorrect PPPoE credentials  
- ONT/Modem link down  
- GPON LOS/LOF alarms  
- DHCP lease failure  
- VLAN provisioning issues  
- Ethernet WAN cable link-status (speed/duplex errors)  
- MAC binding / MAC mismatch  
- ISP maintenance windows  
- Optical power out of range (fiber)  
- CPE bringing WAN down after firmware crash  

The answer is oversimplified and technically incomplete.

---

### 2) Completeness — ❌ FAIL  
Missing required WAN troubleshooting steps:

- ✔ Check physical WAN link (LED status, link-up/link-down)  
- ✔ Verify Ethernet cable (CAT5e/CAT6, no damage)  
- ✔ Verify WAN port vs LAN port mis-patch  
- ✔ Check Optical Signal Levels (for fiber)  
- ✔ Check modem/ONT status (LOS/LOF, update-in-progress)  
- ✔ Verify VLAN tagging (common WAN failure in CH/DE)  
- ✔ Check DHCP lease or PPPoE authentication  
- ✔ Check MAC cloning / MAC registration  
- ✔ Confirm no double NAT or wrong WAN mode  
- ✔ Check router logs for PPP drop, DHCP fail, WAN lost  

Model does not give a structured WAN troubleshooting workflow.

---

### 3) Safety / Risk — Medium  
The model:  
- Encourages meaningless reboots  
- Misses LOS/LOF optical issues (critical for fiber)  
- Does not rule out VLAN/PPPoE misconfiguration  
- Could lead user to reset modem unnecessarily  
- May cause long outages if WAN authentication is the root cause  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Tone is simple, but not helpful for real WAN troubleshooting.

---

### 5) Expected Behavior  
A correct model should:

1. Identify WAN technology  
   - ✔ Fiber (GPON/XPON)  
   - ✔ DSL (VDSL/ADSL)  
   - ✔ Cable (DOCSIS)  
   - ✔ Ethernet/DHCP  

2. Check physical link  
   - ✔ WAN LED status  
   - ✔ ONT/Modem LOS/LOF indicators  
   - ✔ Cable seating & port correctness  

3. Check provisioning  
   - ✔ VLAN tags  
   - ✔ PPPoE username/password  
   - ✔ ISP MAC binding  

4. Review logs  
   - ✔ PPP authentication failures  
   - ✔ DHCP renewal errors  
   - ✔ WAN drop events  

5. Validate configuration  
   - ✔ Correct WAN mode  
   - ✔ No double NAT or wrong bridge/router mode  

6. Suggest restart only after diagnostics  
   - ✔ Avoid factory reset unless last step  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“My router says *WAN Disconnected*. What should I do?”

**Expected Behavior:**  
Provide structured WAN troubleshooting including physical link checks, PPPoE/DHCP validation, VLAN tagging, ONT/Modem status, and WAN-mode configuration.

**Model Output OK?:** No  
**Issues Found:** Oversimplified advice, missing WAN diagnostics, no provisioning checks  
**Risk Level:** Medium  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model gives generic suggestions and ignores essential WAN-layer diagnostics such as PPPoE credentials, DHCP lease issues, VLAN provisioning, ONT alarms, and physical link verification. The response is incomplete and not suitable for production troubleshooting.”
