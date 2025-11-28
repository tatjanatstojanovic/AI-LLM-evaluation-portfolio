# TELCO LLM Evaluation #8 — VoIP Phone Flashing Red / Not Registering  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“My VoIP phone is always flashing red and won’t register. What should I do?”

---

## Model Output (incorrect example)  
“Try restarting your router and phone. If the light is still red, check your internet connection or reset your VoIP adapter.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model oversimplifies and misunderstands VoIP registration.

Incorrect or missing:
- VoIP registration is *SIP-level*, not router-level  
- Restarting router rarely fixes SIP registration  
- Suggesting a reset is dangerous (erases SIP credentials)  
- Doesn’t mention SIP error codes (403/404/408/480…)  
- Doesn’t check provisioning status  

Fails to understand typical red-light conditions:
- SIP REGISTER timeout  
- Authentication failure  
- Wrong SIP proxy  
- NAT/SIP ALG issues  
- VLAN or firewall blocks  

Accuracy = fail.

---

### 2) Completeness — ❌ FAIL  

A correct VoIP evaluation must include:

#### ✔ 1) SIP Registration Status  
- Check SIP state: Registered / Not registered  
- Check SIP server reachability  
- Check SIP username / password provisioning  

#### ✔ 2) SIP Error Codes  
Common meanings:  
- **403** Forbidden (wrong credentials)  
- **404** Not Found (line not provisioned)  
- **408** Timeout (server unreachable)  
- **480** Temporarily Unavailable (network/NAT issue)  

Model did not reference ANY of these.

#### ✔ 3) Modem/CPE Provisioning  
- VoIP line must be provisioned via ACS  
- Correct SIP server, outbound proxy, STUN settings  
- Ensure WAN is online  

#### ✔ 4) Physical Layer (if analog phone)  
- Correct FXS port  
- DECT handset paired  
- Cable not damaged  
- Phone not muted or in DND  

#### ✔ 5) Network Layer  
- SIP ALG OFF  
- NAT type symmetric/full-cone issue  
- Firewall blocking SIP or RTP  
- VLAN for VoIP configured  
- DHCP correct  

#### ✔ 6) Avoid dangerous advice  
- DO NOT reset VoIP adapter before SIP diagnostics  
- DO NOT delete SIP credentials  
- DO NOT reboot endlessly

Model failed every part.

---

### 3) Safety / Risk — ❌ High Risk  

Why high risk?
- Resetting can erase SIP credentials → user loses telephony entirely  
- Misleading explanation → user thinks internet is broken  
- No guidance on SIP codes → impossible to troubleshoot  
- No VLAN/SIP ALG warnings → may break VoIP permanently  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

High operational risk.

---

### 4) Tone — ✔ Neutral  
Clear but unhelpful.  
No reassurance, no structure.

---

## 5) Expected Behavior  

A correct model should follow this exact **SIP troubleshooting checklist**:

### ✔ 1. Check VoIP Registration  
- ✔ Is SIP status “registered”?  
- ✔ If “not registered”, read SIP error code  
- ✔ Verify SIP server domain reachable  

### ✔ 2. Validate Provisioning  
- ✔ SIP username/password provisioned via ACS  
- ✔ Correct outbound proxy  
- ✔ Line active in provider system  

### ✔ 3. Network Checks  
- ✔ WAN online  
- ✔ SIP ALG disabled  
- ✔ No firewall blocking UDP 5060/5061 & RTP ports  
- ✔ No double NAT  
- ✔ Correct VLAN assigned  

### ✔ 4. Device Layer  
- ✔ Check FXS port (if analog)  
- ✔ Check DECT registration (if cordless)  
- ✔ Replace phone cable if needed  

### ✔ 5. Avoid risky steps  
- ✔ Reboot only after SIP diagnostics  
- ✔ Reset only as final, warned step  

### ✔ 6. Controlled reset (only as last resort)  
- ✔ Warn user it deletes provisioning  
- ✔ Suggest contacting ISP first  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“My VoIP phone is flashing red and won’t register.”

**Expected Behavior:**  
Explain SIP registration flow, check SIP errors, verify provisioning, confirm FXS port, disable SIP ALG, and avoid suggesting resets without diagnostics.

**Model Output OK?:** No  
**Issues Found:** Missing SIP details, unsafe reset suggestion, incomplete provisioning steps  
**Risk Level:** High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model misunderstands SIP registration and provides unsafe advice such as resetting equipment prematurely. It omits critical diagnostics like SIP codes, provisioning, outbound proxy verification, and network-layer checks. Not suitable for production.”


