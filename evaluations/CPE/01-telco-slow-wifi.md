# TELCO LLM Evaluation #1 — Slow Wi-Fi / Router Placement
LLM Tested: ChatGPT v5.x (simulation)

## Prompt
“My Wi-Fi is very slow even when I’m close to the router. What should I do?”

## Model Output (incorrect example)
“Try restarting your router. Slow Wi-Fi is usually caused by too many devices. You can also try moving closer to the router.”

## Evaluation

### 1) Accuracy — ❌ FAIL
The model oversimplifies the issue and ignores key factors:
- 2.4 GHz vs 5 GHz differences
- Channel congestion
- Nearby interference (microwave, Bluetooth, neighbors)
- Router placement physics
- Firmware issues
- ISP throughput vs Wi-Fi throughput
- Band steering problems

Only generic advice (“restart”, “move closer”).

### 2) Completeness — ❌ FAIL
Missing essential diagnostics:
- ✔ Check if device is on 2.4 GHz instead of 5 GHz
- ✔ Verify channel width (20/40/80 MHz)
- ✔ Check router placement (height, walls, floor heating)
- ✔ Identify interference sources
- ✔ Check number of connected devices
- ✔ Ethernet speed test to rule out WAN issues
- ✔ Firmware version
- ✔ Check or disable band steering

No structured troubleshooting flow.

### 3) Safety / Risk — Medium
- Encourages unnecessary restarts
- WAN degradation not ruled out
- Possible misdiagnosis → hardware replacement
- Can increase calls to tech support
- Lack of detailed steps increases operational cost

### 4) Tone — ✔ Neutral
Clear but lacks reassurance, structure, and depth.

### 5) Expected Behavior
A correct response should:
1. Identify Wi-Fi band (2.4 vs 5 GHz)
2. Check interference
3. Verify router placement
4. Compare Ethernet vs Wi-Fi speeds
5. Check channel congestion
6. Verify firmware
7. Suggest channel change / band steering adjustments
8. Use restart as final controlled step

## Final PASS/FAIL Entry
**Prompt:** “My Wi-Fi is very slow even when I’m close to the router.”  
**Expected Behavior:** Structured troubleshooting: band checks, interference, placement, congestion, firmware, WAN rule-out.  
**Model Output OK?:** No  
**Issues Found:** Generic advice, missing technical steps, no structured workflow.  
**Risk Level:** Medium  
**Pass/Fail:** ❌ FAIL  
**Comment:** “The model provides generic suggestions and lacks essential Wi-Fi diagnostics such as band identification, interference analysis, channel congestion, and WAN comparison. The answer is incomplete and not production-safe.”
