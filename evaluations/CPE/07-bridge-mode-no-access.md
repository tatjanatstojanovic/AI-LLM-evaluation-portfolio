# TELCO LLM Evaluation #7 — Bridge Mode Enabled, Cannot Access Modem  
LLM Tested: ChatGPT v5.x (simulation)

---

## Prompt  
“I put my modem into bridge mode and now I lost access to its interface. How can I get back in?”

---

## Model Output (incorrect example)  
“When you enable bridge mode, you sometimes lose access. Just restart the modem or change the IP address of your router. If nothing works, reset the modem.”

---

## Evaluation  

### 1) Accuracy — ❌ FAIL  
The model misunderstands bridge mode behavior.

Incorrect assumptions:
- Suggests changing router IP (irrelevant)  
- Suggests random resets (dangerous)  
- Claims “sometimes you lose access” → incomplete explanation  

Missing core principles:
- Bridge mode disables router functions  
- Management IP changes  
- NAT/DHCP disabled  
- LAN ports behavior may change  
- Access requires direct connection, not via router  

The model fails to describe *why* GUI becomes unreachable.

---

### 2) Completeness — ❌ FAIL  
Bridge mode troubleshooting requires specific procedural checks.

Missing critical steps:

#### ✔ Management IP  
- Many modems use a *special management IP* (e.g., 192.168.100.1)  
- This IP works only if directly connected via LAN

#### ✔ Connection Method  
- Must connect PC → LAN port 1 (often only port with MGMT access)  
- Router must be bypassed  

#### ✔ PC Network Configuration  
- MAY need static IP inside management subnet  
- Example:  
  - IP: 192.168.100.10  
  - Mask: 255.255.255.0  
  - Gateway: 192.168.100.1  

#### ✔ DHCP Disabled  
- Bridge mode disables DHCP → PC needs manual IP if modem doesn’t provide one  

#### ✔ WAN vs LAN Differences  
- LAN ports may switch roles  
- Some ports become WAN passthrough only  

#### ✔ Reset as *last resort*  
- Only if management IP fails via direct connection  

The model mentions *none* of these.

---

### 3) Safety / Risk — ⚠ High  
The model suggests:
- Factory reset too early → user loses ISP credentials  
- Changing router IP → can break user network  
- No explanation of DHCP loss → user stuck offline  

**Ne pružanje diferenciranih dijagnostičkih koraka može voditi do nepotrebnih poziva tehničkoj podršci, što povećava troškove korisničkog servisa.**

High risk due to potential total service loss.

---

### 4) Tone — ✔ Neutral  
Clear but unhelpful.

---

## 5) Expected Behavior  

A correct model should follow this exact checklist:

### 1. Understand bridge mode effects  
- ✔ DHCP disabled  
- ✔ NAT disabled  
- ✔ Modem becomes Layer 2 passthrough  
- ✔ Only *management IP* stays active  

### 2. Provide correct access method  
- ✔ Connect a laptop directly to LAN1  
- ✔ Disconnect router  
- ✔ Try management IP (common: 192.168.100.1)  

### 3. Check IP assignment  
- ✔ If no IP → set static PC IP in mgmt subnet  
  - ✔ IP: 192.168.100.10  
  - ✔ Mask: /24  
  - ✔ Gateway: 192.168.100.1  

### 4. Validate cables / LAN behavior  
- ✔ Ensure using correct LAN port  
- ✔ Avoid WAN port of router  

### 5. Only then: controlled reboot  
- ✔ Restart modem *after* diagnostics  

### 6. Reset = only last resort  
- ✔ Warn user it will erase ISP provisioning  
- ✔ Should be avoided when possible  

---

## Final PASS/FAIL Entry  

**Prompt:**  
“I enabled bridge mode and now I can't access my modem interface.”

**Expected Behavior:**  
Explain bridge mode architecture (no DHCP/NAT), guide user to management IP via direct LAN, instruct static IP setup if needed, and avoid dangerous resets.

**Model Output OK?:** No  
**Issues Found:** Missing mgmt IP explanation, missing DHCP implications, unsafe reset suggestion  
**Risk Level:** High  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model fails to explain how bridge mode works, omits the management IP concept, and provides unsafe reset advice. It does not guide the user through the correct direct-LAN access method or static IP configuration.”


