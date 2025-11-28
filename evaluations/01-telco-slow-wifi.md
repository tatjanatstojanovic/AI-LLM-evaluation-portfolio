# TELCO LLM Evaluation #1 — Slow Wi-Fi / Router Placement

##  Prompt
“My Wi-Fi is very slow even when I’m close to the router. What should I do?”

##  Model Output (example of incorrect / typical answer)
“Try restarting your router. Slow Wi-Fi is usually caused by too many devices. You can also try moving closer to the router.”

##  Evaluation

### 1) Accuracy — ❌ FAIL
The model oversimplifies the issue and ignores key factors that affect Wi-Fi performance:
- 2.4 GHz vs 5 GHz differences  
- Channel congestion  
- Signal interference (microwaves, Bluetooth, neighbors)  
- Router placement physics  
- Firmware issues  
- ISP throughput vs Wi-Fi throughput  
- Band steering problems

It offers only generic advice (“restart”, “move closer”).

---

### 2) Completeness — ❌ FAIL
Missing critical diagnostics:
- Check if the device is on 2.4 GHz instead of 5 GHz  
- Check channel width (20/40/80 MHz)  
- Verify router placement (height, walls, floor heating)  
- Check for interference sources  
- Check number of connected devices  
- Speedtest via Ethernet to rule out WAN issues  
- Check firmware version  
- Disable/verify band steering

The model doesn’t offer a structured troubleshooting workflow.

---

### 3) Safety / Risk —  Medium
The model:
- May lead users to repeatedly restart their router unnecessarily  
- Does not rule out WAN degradation  
- Can cause users to misdiagnose the root cause  
- Can encourage unnecessary hardware replacement  

Not dangerous, but not reliable.

---

### 4) Tone — ✔️ Neutral
Tone is simple but provides no real guidance, reassurance, or clarity.

---

### 5) Expected Behavior (What a correct model should do)
A correct AI response should:
1. Identify the band (2.4 vs 5 GHz)  
2. Check for interference  
3. Confirm router placement (central, lifted, unobstructed)  
4. Test Ethernet vs Wi-Fi speeds  
5. Check channel congestion  
6. Update firmware  
7. Suggest switching channels or disabling band steering  
8. Restart only as a final controlled step  

---

##  FINAL PASS/FAIL ENTRY

**Prompt:**  
“My Wi-Fi is very slow even when I’m close to the router.”

**Expected Behavior:**  
Provide structured Wi-Fi troubleshooting including band checks, interference analysis, router placement, firmware, and WAN rule-out.

**Model Output OK?:** No  
**Issues found:** Generic advice, missing technical checks, no structure  
**Risk Level:** Medium  
**Pass/Fail:** ❌ FAIL  

**Comment:**  
“The model gives generic suggestions and misses essential Wi-Fi diagnostics such as band identification, interference analysis, channel congestion, and router placement. The answer is incomplete and not production-safe.”

