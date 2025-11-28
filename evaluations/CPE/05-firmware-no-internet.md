# TELCO LLM Evaluation #5 — Firmware Update → No Internet  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“I updated my router’s firmware and now I have no internet. What should I do?”

---

## Model Output (incorrect example)  
“Sometimes updates cause bugs. Restart your router or reset it to factory settings. If it still doesn’t work, call your provider.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model gives surface-level advice and ignores all realistic firmware-related failure modes.

Missing technical causes:
- Configuration rollback failure  
- WAN mode reset (PPPoE → DHCP)  
- PPPoE password erased  
- VLAN tag lost after update  
- DNS overwritten with wrong values  
- Band steering disabled  
- Bridge mode disabled after upgrade  
- IPv6 enabled unintentionally causing routing issues  
- Firewall rules reset  
- MAC clone removed (ISP rejects connection)  
- Auto-channel → DFS after firmware (Wi-Fi appears “offline”)  

The model skips all real CPE scenarios.

---

### 2) Completeness — ❌ FAIL  
Firmware-related outages require **full configuration validation**.

Missing diagnostics:

- ✔ Check WAN mode (DHCP / PPPoE / Static)  
- ✔ Check PPP credentials (often wiped after upgrade)  
- ✔ Reapply VLAN tagging  
- ✔ Check DNS settings (manual DNS wiped → no browsing)  
- ✔ Validate MAC binding (ISP expects old MAC)  
- ✔ Confirm bridge/router mode status  
- ✔ Check IPv4/IPv6 routing tables  
- ✔ Inspect logs for “WAN DHCP Discover timeout”  
- ✔ Verify if firmware rollback is available  
- ✔ Reapply Wi-Fi SSID settings (hidden SSID bug common after updates)  

The model does not follow a realistic troubleshooting chain.

---

### 3) Safety / Risk — ⚠ Medium–High  
The model suggests **factory reset** prematurely — dangerous.

Risks:
- User loses entire configuration  
- PPPoE details erased  
- VLAN setup erased  
- Bridge mode broken  
- Static IP configurations lost  
- Wi-Fi settings reset → mesh nodes disconnect  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

---

### 4) Tone — ✔ Neutral  
Clear but not helpful.

---

### 5) Expected Behavior  
A correct model should:

#### 1. Validate WAN configuration  
- ✔ WAN mode correct (PPPoE/DHCP/Static)  
- ✔ PPP username/password still present  
- ✔ VLAN tag still applied  

#### 2. Validate routing  
- ✔ DNS correct  
- ✔ IPv4/IPv6 routing stable  
- ✔ Gateway reachable  

#### 3. Validate interface state  
- ✔ WAN link up  
- ✔ DHCP packets exchanged (Discover/Offer)  
- ✔ PPP logs (CHAP/LCP)  

#### 4. Validate Wi-Fi / LAN  
- ✔ SSID not reset  
- ✔ Mesh nodes still paired  
- ✔ Band steering not disabled  

#### 5. ISP-side validation  
- ✔ MAC address unchanged or rebind  
- ✔ Account still active  

#### 6. Controlled recovery  
- ✔ Reboot ONT/modem first  
- ✔ Reboot router second  
- ✔ Firmware rollback (if supported)  

No factory reset unless final step.

---

## Final PASS/FAIL Entry  

**Prompt:**  
“I updated my router’s firmware and now I have no internet. What should I do?”

**Expected Behavior:**  
Provide structured firmware-diagnostic workflow including WAN config validation, VLAN checks, DNS/routing issues, logs, and MAC binding.

**Model Output OK?:** No  
**Issues Found:** Dangerous reset advice, missing WAN config checks, missing VLAN/DNS/routing diagnostics  
**Risk Level:** Medium–High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model provides oversimplified guidance and prematurely suggests a factory reset. It ignores critical firmware-related failures such as erased PPPoE credentials, missing VLAN tags, incorrect WAN mode, DNS corruption, and MAC-binding issues. The answer is not suitable for production troubleshooting.”
