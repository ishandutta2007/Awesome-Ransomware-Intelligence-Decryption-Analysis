# Awesome-Ransomware-Intelligence-Decryption-Analysis

# Top Ransomware Intelligence & Decryption Analysis Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Threat Intelligence, Free Decryptors & Self-Hosted Analysis Tooling*  
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Ransomware Intelligence & Decryption Analysis**. These tools enable defenders to identify ransomware strains, assess threat actor activity, locate free decryption tools, and recover encrypted data without paying—turning a ransomware event from a guaranteed loss into a manageable incident.

**Examples** include CrowdStrike Falcon Ransomware Lookup, Recorded Future, Mandiant Threat Intelligence, Flashpoint, Malwarebytes Threat Intelligence, Sophos Ransomware Protection, Trend Micro Ransomware File Decryptor, Bitdefender Ransomware Remediation, Coveware by TeleSign, and Halcyon (the category leaders).

**Open-source emphasis**: Ransomware Intelligence & Decryption Analysis is a domain where open-source tooling is **genuinely valuable for decryption analysis but fragmented and strain-specific**. The strongest active project is **lockbit-rescue**—a toolkit that exploits a **keystream-reuse weakness in LockBit 3.0** to recover files without the ransom, using known-plaintext from long filenames to reconstruct the Salsa20 keystream . **No Ransom (Kaspersky)** and **Avast** provide free, legitimate decryptors for dozens of ransomware families—including TeslaCrypt, Yanluowang, and newer STOP/Djvu variants when offline keys are available . The critical caveat: **no open-source project provides a unified, real-time ransomware intelligence platform**—commercial tools like Recorded Future and Halcyon aggregate dark web intel, victimology, and TTPs across the entire threat landscape . For specific decryption analysis, open-source tools are **strain-specific and require the right conditions** (e.g., LockBit rescue requires a long-named oracle file in the same encryption batch) .

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[CrowdStrike Falcon Ransomware Lookup](https://www.crowdstrike.com/)**  
  Ransomware identification and intelligence within the Falcon platform; leverages Falcon Sandbox (the same technology behind Hybrid Analysis) for automated malware analysis, threat scoring, and IOC extraction to identify ransomware families and their behaviors .

- **[Recorded Future](https://www.recordedfuture.com/)**  
  Threat intelligence platform with a dedicated **ransomware risk profile** combining dark web extortion site monitoring, victimology insights, threat actor breakdowns, and TTP filtering . Features AI-generated audience-specific ransomware intelligence reports and automated remediation workflows. **Best for organizations wanting proactive ransomware intelligence** across the attack lifecycle—but it is intelligence, not a decryption tool.

- **[Mandiant Threat Intelligence](https://www.mandiant.com/)**  
  Frontline intelligence from Mandiant incident response; **M-Trends 2026** highlights that prior compromise doubled to 30% of initial infection vectors, driven by Initial Access Brokers (IABs) . Provides adversary tracking, IOC feeds, and ransomware group profiles.

- **[Flashpoint](https://flashpoint.io/)**  
  Primary-source threat intelligence with deep dark web and criminal community coverage; monitors ransomware leak sites and affiliate activity.

- **[Malwarebytes Threat Intelligence](https://www.malwarebytes.com/)**  
  Threat intelligence from Malwarebytes research; provides ransomware family identification and IOC context alongside endpoint protection.

- **[Sophos Ransomware Protection](https://www.sophos.com/)**  
  Endpoint protection with **CryptoGuard** anti-ransomware technology in Intercept X; protects document files against malicious encryption and can terminate or isolate ransomware processes . **Best for Sophos customers** wanting integrated prevention—not a decryption tool.

- **[Trend Micro Ransomware File Decryptor](https://success.trendmicro.com/)**  
  Free decryption tool for specific ransomware families: **TeslaCrypt V1/V2, CryptXXX, LeChiffre, DXXD, Teamxrat/Xpan, Crysis, WannaCry, Petya, and others** . **Critical caveats**: CryptXXX V3 decryption is partial only (no archive files, no files >13MB); LeChiffre requires the original infected machine; WannaCry decryption only works on an infected machine with the ransomware process still active . **Best for victims of these specific legacy families**—coverage does not extend to modern ransomware.

- **[Bitdefender Ransomware Remediation](https://www.bitdefender.com/)**  
  **Ransomware Mitigation** feature in GravityZone monitors file entropy during write attempts; when abnormal encryption is detected, a temporary backup is created in memory and the original file is restored after the process is blocked . **Does not rely on Volume Shadow Copy** (which attackers delete), providing mitigation against previously unseen variants. Recovery can be on-demand (within 30 days) or automatic . **Best for Bitdefender customers** wanting rollback without ransom payment.

- **[Coveware by TeleSign](https://www.coveware.com/)**  
  Ransomware incident response and negotiation firm; **checks whether a free decryptor exists before discussing payment** as part of its recovery decision tree . Maintains detailed profiles of decryptor reliability, negotiation patterns, and recovery outcomes. Joined the **No More Ransom** partner organization in 2018 . **Best for organizations needing expert incident response**—not a self-service tool.

- **[Halcyon](https://www.halcyon.ai/)**  
  Ransomware-specific security platform with the **world's first Ransomware Operations Center (ROC)**—a 24/7 team of ransomware specialists included at no extra charge for all customers . Features **key material capture and decryption capabilities** to restore encrypted data without paying, behavioral detection focused on ransomware TTPs (not generic malware), and automated rollback . **Best for organizations wanting dedicated ransomware defense** with guaranteed recovery—but it is a premium enterprise platform.

## Open-Source GitHub Projects

### Decryption Analysis Toolkits (Strain-Specific)

- **[lockbit-rescue](https://github.com/saddytech/lockbit-rescue)**  
  The most technically sophisticated open-source **ransomware decryption analysis toolkit** available (May 2026) . Exploits a **keystream-reuse vulnerability in LockBit 3.0 ("Black")**: files in the same encryption batch share the same Salsa20 keystream; by identifying a file with a **long original filename** (the "oracle"), the known plaintext (compressed filename + footer metadata) reveals enough keystream to decrypt other files in the same group . **Requirements**: Linux x86_64, the encrypted files, and at least one long-named file per batch. **Limitations**: files outside groups with a long-named oracle remain unrecoverable; resumable if interrupted . **Best for LockBit 3.0 victims** wanting a free recovery path—but it is strain-specific and condition-dependent.

### Free Decryptor Collections

- **[No Ransom (Kaspersky)](https://noransom.kaspersky.com/)**  
  Kaspersky's **free decryption tool portal** covering dozens of ransomware families. Tools include **RakhniDecryptor** (covers TeslaCrypt, Chimera, Crysis, Dharma, Maze, Sekhmet, Egregor, Conti, and more) . For **Yanluowang**, Kaspersky released a dedicated decryptor that works if the victim has **one or more original files** to use as known plaintext . **Best for victims of covered families**—check the tool list before assuming your strain is supported.

- **[Avast Free Ransomware Decryption Tools](https://www.avast.com/ransomware-decryption-tools)**  
  Avast's collection of free decryptors covering families including **Alcatraz, Apocalypse, AtomSilo/LockFile, Babuk, BadBlock, Bart, Globe, HermeticRansom, HiddenTear, Jigsaw, and more** . Each tool is family-specific; the page lists file extensions and ransom note filenames to help identify the strain.

- **[Emsisoft Decryptor (STOP/Djvu)](https://www.emsisoft.com/ransomware-decryption-tools/)**  
  Emsisoft provides free decryptors for **STOP (Djvu)** variants when an **offline key** is available . **Critical caveat**: newer STOP variants using **online keys cannot be decrypted** by Emsisoft—there is no way to retrieve the key from the attacker's server without paying . If the decryptor indicates an online ID under the Results tab, recovery without payment is not possible for that variant.

### Additional Strong Open-Source Options

- **FUCKFBI Decryptor** — Open-source Python decryptor for a specific ransomware family that uses a **32-byte repeating-key XOR** and writes the key to disk (`decryption_key.fuckfbi`) before encryption . If the key file is present, recovery is trivial; if missing, known-plaintext recovery works for files ≥32 bytes with predictable headers (PDF, PNG, JPG, DOCX, ZIP) . **Niche**—for this specific family only, but demonstrates the XOR key-recovery pattern.
- **lockbit-v3-linux-decryptor (yohanes)** — The underlying C implementation (`stream-reuse.c`) that lockbit-rescue drives; contains the core keystream-recovery logic . **Reference implementation** for researchers.
- **No More Ransom** — The **EU-backed portal** (founded by Europol, Kaspersky, and McAfee) aggregating **59+ free decryption tools** covering 91+ ransomware families; has assisted over 72,000 victims . Not a GitHub project—it is a curated directory of legitimate decryptors.

**Frameworks for building custom systems**: For **LockBit 3.0 recovery**, lockbit-rescue provides the only open-source analysis toolkit . For **legacy family decryption**, check **No Ransom** and **Avast** tool lists first . For **STOP/Djvu**, Emsisoft's decryptor handles offline keys only . **No open-source project provides real-time ransomware intelligence** comparable to Recorded Future's dark web monitoring or Halcyon's dedicated ROC team —those are commercial intelligence and response platforms.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Ransomware decryption tools should only be used on systems you are authorized to recover; **always isolate infected systems and preserve evidence** before attempting decryption. Decryption can be slow, partial, or destructive—test on copies where possible.
- **Open-source ransomware decryption is strain-specific and condition-dependent**—lockbit-rescue requires a long-named oracle file per batch , Emsisoft's STOP/Djvu decryptor only works with offline keys , and Trend Micro's tool covers only specific legacy families with significant limitations . **No open-source project provides real-time ransomware intelligence or guaranteed decryption**—organizations facing active ransomware attacks should engage incident response professionals (Coveware, Halcyon) or law enforcement rather than relying solely on self-service tools.
- Verify license terms for commercial use; lockbit-rescue is open-source (check repository), and No Ransom / Avast / Emsisoft tools are free for victim use.

---

**Made for incident responders, threat analysts, and organizations recovering from ransomware attacks.**  
Let's make ransomware decryption analysis more open, but with clear eyes about the strain-specificity and condition-dependence that define what open-source tools can and cannot recover.
