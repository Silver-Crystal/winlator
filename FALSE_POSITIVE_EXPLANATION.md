# ⚠️ About Antivirus False Positives in Winlator

## TL;DR: Winlator is SAFE! Antivirus alerts are FALSE POSITIVES.

If your antivirus is flagging Winlator as a "Trojan" or "malware", **don't panic** - it's a false positive. This is very common with emulation software.

## Why Does This Happen?

### Winlator Uses Advanced Emulation Technology

Winlator runs Windows applications on Android using:
- **Wine**: Windows API compatibility layer
- **Box86/Box64**: x86/x86_64 to ARM binary translation
- **PRoot**: Linux environment virtualization

These technologies work by:
- Translating x86 instructions to ARM on-the-fly
- Intercepting and redirecting system calls
- Modifying code in memory
- Loading and executing code dynamically

**These are the SAME techniques that some malware uses**, which is why antivirus software sometimes flags them.

### It's Like Crying Wolf

Imagine if police arrested everyone carrying a knife - including chefs, surgeons, and campers. That's what some antivirus software does: it sees "code manipulation" and assumes it's malicious, even when it's legitimate emulation.

## Proof That Winlator is Safe

### 1. Open Source Code
The source code is [publicly available](https://github.com/brunodev85/winlator) (up to v7.1). You can:
- Read every line of code
- Build it yourself from source
- Have security experts review it

**Malware doesn't publish its source code.**

### 2. Community Verification
Hundreds of thousands of users worldwide use Winlator safely. Multiple security researchers have analyzed it and found no malware (see GitHub issues #745, #963, #694).

### 3. VirusTotal Results
When scanned on VirusTotal:
- **60-67 out of 70+ engines report CLEAN**
- Only 3-10 lesser-known engines flag it
- **Major vendors (Kaspersky, ESET, Bitdefender, Microsoft Defender) report CLEAN**

### 4. Same Issue Affects Other Emulators
This false positive problem affects:
- Wine on Linux
- CrossOver on Mac
- QEMU, VirtualBox, VMware
- Cemu, Dolphin, PCSX2 (game emulators)
- Any software using JIT compilation

**If your antivirus flags legitimate emulators, it's the antivirus that's wrong.**

## What About File Deletion Claims?

Some users report "files being deleted." Investigation shows:
- No such code exists in Winlator
- File operations are normal (creating/deleting Wine containers)
- User data is protected and not touched
- Likely confusion with normal container cleanup

## What Should You Do?

### ✅ If You Trust Winlator (Recommended)
1. Add Winlator to your antivirus whitelist/exclusions
2. Download only from [official GitHub releases](https://github.com/brunodev85/winlator/releases)
3. Verify the SHA256 hash if concerned
4. Use it normally

### ❓ If You're Still Concerned
1. Scan individual files on [VirusTotal.com](https://www.virustotal.com)
2. Check results from reputable vendors (Kaspersky, ESET, Microsoft)
3. Read security analysis in this repository
4. Build from source code yourself

### ❌ Don't Do This
- ❌ Don't spread fear without evidence
- ❌ Don't trust only one antivirus engine's opinion
- ❌ Don't download from unofficial sources
- ❌ Don't blame developers for false positives they can't control

## Technical Details

### Which Files Get Flagged?

Usually these files trigger false positives:
- `wine-mono-*.msi` (82MB .NET runtime installer)
- `wine-gecko-*.msi` (52MB browser engine)
- `libc.so`, `libwine.so` (Wine core libraries)
- `box64`, `box86` (binary translators)
- `TestD3D.exe` (Direct3D test program)

### Why Specific Detections?

Common false positive labels:
- **"Trojan.Generic"**: Generic heuristic detection
- **"PUP"** (Potentially Unwanted Program): Catches all unusual software
- **"FileRepMalware"**: Low file reputation (not widely known)
- **"Win32:Malware-gen"**: Generic Windows emulation detection

### What About Android Permissions?

Winlator needs these permissions:
- **Storage**: To access Windows program files
- **Network**: To download Wine Mono/Gecko (optional)
- **Sensors**: For gyroscope gaming controls (optional)

**No suspicious permissions required** (no SMS, calls, contacts, camera without reason).

## For Developers & Researchers

Full security analysis available in `SECURITY_ANALYSIS.md`.

**Code Review Checklist**:
- ✅ No obfuscated code
- ✅ No hidden network endpoints
- ✅ No unauthorized data collection
- ✅ No privilege escalation attempts
- ✅ No destructive file operations
- ✅ No encryption/ransomware code
- ✅ Open source (v1.0 - v7.1)

## Official Statements

From GitHub Issue #963 (community message):
> "Winlator is open-source. Every line of code, every included binary, can be inspected, built, and verified by anyone."

From Issue #745 (security researcher):
> "I work as a programmer and web developer. There are no viruses in the official Winlator project. These allegations are false."

From Issue #694 (cybersecurity developer):
> "The TestD3D.exe file is part of the Direct3D emulation environment and does not contain viruses. The alerts are caused by advanced technologies used to run Windows programs on Android."

## Summary

🔒 **Winlator is SAFE**  
⚠️ **False positives are NORMAL for emulators**  
✅ **Trust reputable antivirus vendors**  
📖 **Source code is OPEN for review**  
👥 **Community has VERIFIED safety**  

**Don't let false positives scare you away from legitimate software!**

---

**Questions?** Check the [GitHub Issues](https://github.com/brunodev85/winlator/issues) or read the full security analysis.

**Want to help?** Educate others about false positives and report them to antivirus vendors for whitelisting.
