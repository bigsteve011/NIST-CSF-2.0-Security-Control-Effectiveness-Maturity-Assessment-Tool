# NIST CSF 2.0 Security Control Effectiveness & Maturity Assessment Tool

**A structured control-effectiveness and remediation-governance model that evaluates security maturity through their full lifecycle — assessment, design-maturity scoring, effectiveness-factor measurement, control-gap analysis, and auditable remediation prioritization.**

![Domain](https://img.shields.io/badge/Domain-Control%20Effectiveness%20%26%20Maturity-0b3d5c)
![NIST CSF](https://img.shields.io/badge/NIST%20CSF-2.0-1f6f78)
![ISO 27001](https://img.shields.io/badge/ISO%2FIEC%2027001-2022-1f6f78)
![Methodology](https://img.shields.io/badge/Methodology-Maturity%20%26%20Effectiveness%20Assessment-amber?color=d4a017)
![Status](https://img.shields.io/badge/Type-Control%20Governance%20Assessment-6c757d)

**Bridge the Gap Between "Compliance on Paper" and "Operational Reality"**

An enterprise-grade Python tool that measures security control maturity and effectiveness across the NIST Cybersecurity Framework 2.0, identifying gaps between controls-as-designed and controls-as-implemented, with automated actionable recommendations.

---

## 📋 Table of Contents

1. [Executive Overview](#executive-overview)
2. [The Problem: Compliance Theater](#the-problem-compliance-theater)
3. [NIST CSF 2.0 Framework Explained](#nist-csf-20-framework-explained)
4. [The Maturity Model](#the-maturity-model)
5. [Control Effectiveness Model](#control-effectiveness-model)
6. [Technical Architecture](#technical-architecture)
7. [How to Use](#how-to-use)
8. [Sample Assessment Report](#sample-assessment-report)
9. [Dashboard & Visualization](#dashboard--visualization)
10. [Installation & Dependencies](#installation--dependencies)

---

## Executive Overview

### The Business Problem

Organizations face a **critical credibility gap** in their security posture reporting:

| Question | Traditional Answer | Reality |
|----------|-------------------|---------|
| "Do you have MFA?" | "Yes, we comply with NIST CSF" | 60% of users actually use it |
| "Is your incident response ready?" | "We have an IR plan (ISO 27035 compliant)" | Last test was 2 years ago |
| "Are vulnerabilities managed?" | "We follow CIS Controls" | Patches applied 90 days after release |

**The gap exists because:**
- ✗ Compliance audits verify *existence* of controls, not *effectiveness*
- ✗ Maturity models rate controls on paper, not on actual behavior
- ✗ There's no standard way to bridge the "designed vs. implemented" gap

### The Solution

This tool introduces the **Control Effectiveness Factor (0.0-1.0)** to quantify operational reality:

```
Operational Maturity = Design Maturity × Effectiveness Factor

Example:
  MFA Policy (designed at Level 4 - Managed)
  × 0.60 effectiveness (60% user adoption)
  = 2.4 operational maturity (between Repeatable and Defined)
```

**Result:** A quantified, auditable assessment that bridges compliance and reality.

---

## The Problem: Compliance Theater

### Why Traditional Audits Fail

**ISO 27001 Audit Approach:**
- ✓ Verify policy exists → ✓ Check it's documented → ✓ Sample 10 employees
- Result: "Compliant"
- What's missing: Does the control *actually work under pressure?*

**This Tool's Approach:**
1. What's the designed maturity level? (1-5)
2. What's the actual effectiveness? (0%-100%)
3. What's the operational gap? (designed vs. reality)
4. What's the remediation priority? (quantified impact)

### Real-World Example

**Company: Large Financial Services Firm**
- Claim: "We have a Security Awareness Program (ISO 27001 requirement)"
- Audit Result: ✓ Compliant
- Effective Maturity Assessment:
  - Policy: Level 3 (Defined) ✓
  - Effectiveness: 0.35 (35% of employees complete training) ✗
  - Operational Maturity: 3 × 0.35 = 1.05 (Initial level)
  - Gap: Appears Level 3, actually behaves at Level 1
  - Impact: $0 training effectiveness spending on a 3-level control

**This tool exposes that gap.**

---

## NIST CSF 2.0 Framework Explained

### What is NIST CSF?

The **NIST Cybersecurity Framework 2.0** (released 2024) is a voluntary, industry-led framework providing a common taxonomy of cybersecurity activities, outcomes, and outcomes-related to guidance.

**Three-Tier Structure:**
```
TIER 1: Functions (What to do) → 6 Functions
  └─ TIER 2: Categories (How to do it) → 23 Categories
      └─ TIER 3: Subcategories (Specific actions) → 90+ Controls
```

### The 6 Core Functions (NIST CSF 2.0)

#### 🏛️ **GOVERN (GV)** - Organizational Context & Oversight
*Board-level strategy, risk management, cybersecurity investment decisions*

| Control | Purpose | Maturity Span |
|---------|---------|---------------|
| GV.1: Organizational Context | Define risk appetite, strategic direction | 0-5 |
| GV.2: Governance Structures | CISO role, oversight committees, escalation | 0-5 |
| GV.3: Cybersecurity Policies | Security standards, control baselines | 0-5 |
| GV.4: Resource Allocation | Budget, staffing, vendor management | 0-5 |

**Why it matters:** If Govern is weak, every other function operates without strategic alignment.

---

#### 🔍 **IDENTIFY (ID)** - Asset, Risk, and Dependency Management
*Understand what you need to protect and what threatens it*

| Control | Purpose | Maturity Span |
|---------|---------|---------------|
| ID.1: Asset Management | Inventory hardware/software, criticality rating | 0-5 |
| ID.2: Risk Assessment | Vulnerability assessment, threat modeling | 0-5 |
| ID.3: Business Environment | Suppliers, critical services, dependencies | 0-5 |

**Why it matters:** You can't protect what you don't know you have.

---

#### 🛡️ **PROTECT (PR)** - Access Control, Data Security, Technical Controls
*Implement safeguards to prevent unauthorized access and data loss*

| Control | Purpose | Maturity Span |
|---------|---------|---------------|
| PR.1: Access Control | IAM, MFA, RBAC, PAM | 0-5 |
| PR.2: Data Security | Encryption, key management, classification | 0-5 |
| PR.3: Awareness & Training | Security training, phishing simulations | 0-5 |
| PR.4: System Protection | Firewalls, IPS, segmentation, patching | 0-5 |

**Why it matters:** Prevention is cheaper than response.

---

#### 🚨 **DETECT (DE)** - Monitoring, Logging, Incident Detection
*Monitor for unauthorized activity and anomalies*

| Control | Purpose | Maturity Span |
|---------|---------|---------------|
| DE.1: Monitoring | SIEM, network IDS, anomaly detection | 0-5 |
| DE.2: Investigation | SOC capabilities, forensics, analysis | 0-5 |

**Why it matters:** You can't respond to attacks you don't see.

---

#### 🚒 **RESPOND (RS)** - Incident Response Planning & Execution
*Coordinate and execute incident response activities*

| Control | Purpose | Maturity Span |
|---------|---------|---------------|
| RS.1: Response Planning | IR plan, team structure, communication | 0-5 |
| RS.2: Response Execution | Containment, eradication, remediation | 0-5 |

**Why it matters:** Incident response skill determines business impact.

---

#### 🔄 **RECOVER (RC)** - Business Continuity & Resilience
*Restore systems and services to normal operations*

| Control | Purpose | Maturity Span |
|---------|---------|---------------|
| RC.1: Recovery Planning | DR plan, RTO/RPO, backup strategy | 0-5 |
| RC.2: Recovery Execution | Backup testing, recovery drills | 0-5 |

**Why it matters:** Can you get back to business in acceptable time?

---

## The Maturity Model

### 5-Level Maturity Scale

Each control is rated 0-5 on the following scale:

| Level | Name | Characteristics | Example |
|-------|------|-----------------|---------|
| **0** | Not Implemented | Control doesn't exist | No firewall policy |
| **1** | **Initial** | Ad-hoc, reactive, unpredictable, unstandardized | Firewall rules written by individual engineers, inconsistent |
| **2** | **Repeatable** | Some standardization, documented but not enforced | Firewall rules template exists, mostly followed |
| **3** | **Defined** | Standardized, documented, applied consistently | Firewall rules governed by change control, 95%+ compliance |
| **4** | **Managed** | Measured, monitored, actively managed with metrics | Firewall changes tracked, metrics reported monthly to CISO |
| **5** | **Optimized** | Continuous improvement, automated, predictive | Firewall rules auto-generated from policy, ML-based anomaly detection |

### Mapping to Compliance Standards

| NIST CSF Level | ISO 27001 Level | CIS Controls Tier | SOX Requirement |
|----------------|----------------|--------------------|-----------------|
| 0-1: Initial | Not certified | Not implemented | Non-compliant |
| 2: Repeatable | Audit ready | Tier 1/2 partial | In progress |
| 3: Defined | Certified | Tier 2/3 | Compliant |
| 4: Managed | Certified + advanced | Tier 3 | Optimized |
| 5: Optimized | Advanced + continuous | Best practice | Strategic advantage |

**Note:** Most mature organizations operate at Level 3-4 for critical controls and Level 2-3 for standard controls. Level 5 is aspirational.

---

## Control Effectiveness Model

### Why Effectiveness Matters

A control can be **designed** at one maturity level but **operate** at a lower level due to:

- **Implementation gaps** (not fully deployed)
- **Compliance gaps** (deployed but not followed)
- **Monitoring gaps** (deployed and used but not measured)

### Effectiveness Factor Scoring (0.0-1.0)

Use this guidance to estimate the control effectiveness factor:

```
1.0 = Fully Effective
  • Designed maturity level = operational maturity level
  • 95%+ compliance with control procedures
  • Evidence of testing/monitoring
  • Example: MFA enforced for 98% of employees

0.75-0.99 = Mostly Effective
  • Minor gaps in deployment or compliance (1-5% non-compliance)
  • Some manual exceptions documented
  • Example: MFA enforced for 90% of employees, 10% exemptions

0.5-0.74 = Partially Effective
  • Moderate gaps (10-30% non-compliance)
  • Control inconsistently applied across systems
  • Example: MFA deployed for 70% of critical systems, 30% legacy systems excluded

0.25-0.49 = Minimally Effective
  • Significant gaps (30-60% non-compliance)
  • Control exists but rarely enforced
  • Example: MFA available but only 40% adoption due to poor UX

0.0-0.24 = Ineffective
  • Control doesn't function as designed (>60% non-compliance)
  • Essentially not operationally valuable
  • Example: MFA implemented but 0% adoption due to app incompatibility
```

### How to Determine Effectiveness in Your Organization

**Audit Evidence Collection:**

1. **Review** - Check design documentation (policies, standards)
2. **Observe** - See control in practice (witness employee behavior)
3. **Inquire** - Ask control owners about challenges
4. **Test** - Sample transactions/configurations to verify compliance
5. **Analyze** - Review metrics/monitoring data

**Effectiveness Assessment Checklist:**

- [ ] Is the control actively used by 95%+ of target population?
- [ ] Is there evidence of recent testing or validation?
- [ ] Are there documented exceptions/exemptions? (If yes, reduce effectiveness)
- [ ] Is the control regularly monitored or reported on?
- [ ] Have there been incidents that the control failed to prevent?

**Red Flags (Reducing Effectiveness):**
- ❌ Control hasn't been tested in >1 year
- ❌ Multiple documented exceptions
- ❌ No metrics/KPIs on control performance
- ❌ Staff complaints about control usability
- ❌ Recent incidents bypassed the control

---

## Technical Architecture

### Code Structure

```
nist_assessment.py
├── SecurityControl (dataclass)
│   ├── Control metadata (ID, name, function)
│   ├── Maturity level (0-5)
│   ├── Effectiveness factor (0.0-1.0)
│   └── Adjusted maturity calculation
├── NISTAssessmentQuestionnaire
│   ├── Interactive questionnaire
│   ├── Control inventory
│   └── Results compilation
├── GAPAnalysisEngine
│   ├── Gap scoring algorithm
│   ├── Recommendation generation
│   └── Report formatting
└── Main execution
    ├── Interactive mode (prompts for input)
    └── Demo mode (pre-loaded sample data)
```

### Assessment Logic

```
For each of 17 controls:
  1. Establish DESIGN maturity level (0-5)
  2. Determine EFFECTIVENESS factor (0.0-1.0)
  3. Calculate OPERATIONAL maturity = Design × Effectiveness
  
For each NIST Function:
  4. Average operational maturity across controls
  5. Identify gap vs. target (typically 4-5)
  6. Score gap priority (higher = more urgent)
  
Generate Report:
  7. Rank functions by gap priority
  8. Output actionable recommendations for each function
  9. Save structured JSON results for auditing
```

---

## How to Use

### Option 1: Interactive Mode (Default)

```bash
python nist_assessment.py
```

**This mode:**
- Prompts for organization name
- Walks through each control (17 total)
- Asks for maturity level (0-5) and effectiveness factor (0.0-1.0)
- Allows optional notes on each control
- Generates automated report and saves results

**Expected time:** 30-45 minutes for first assessment

### Option 2: Demo Mode (Pre-Loaded Sample Data)

```bash
python nist_assessment.py --demo
```

**This mode:**
- Uses realistic sample data (Volvo Group Logistics Division)
- Demonstrates full assessment workflow
- Shows report format and gap analysis
- Useful for understanding the tool before running your own assessment

**Expected time:** 2-3 minutes

### Customization Guide

**To adapt controls for your organization:**

Edit the `NIST_CONTROLS` dictionary:

```python
"PR.1": SecurityControl(
    "PR.1", 
    "Access Control & Identity Management",
    "IAM platform, MFA, RBAC, privileged access management",
    "Protect",
    "Access Management"
),
```

Change description to match your environment:
- Large enterprises: Add XACML, fine-grained policy
- SMBs: Focus on basic RBAC, MFA for critical systems
- Public sector: Mention FedRAMP, FISMA requirements

---

## Sample Assessment Report

### Report Structure

Running the assessment generates this formatted report:

```
█████████████████████████████████████████████████████████████████████████████████
█                                                                               █
█  NIST CSF 2.0 SECURITY MATURITY ASSESSMENT REPORT                            █
█  Control Effectiveness & Maturity Analysis                                   █
█                                                                               █
█████████████████████████████████████████████████████████████████████████████████

ASSESSMENT METADATA
═══════════════════════════════════════════════════════════════════════════════

Organization:          Volvo Group Logistics Division
Assessment Date:       2024-12-15
Framework:             NIST Cybersecurity Framework 2.0
Assessment Scope:      6 Core Functions, 17 Key Controls
Controls Evaluated:    17


EXECUTIVE SUMMARY: MATURITY SCORECARD
═══════════════════════════════════════════════════════════════════════════════

Function        │ Maturity Level │ Effectiveness │ Gap Priority │ Status
────────────────┼────────────────┼───────────────┼──────────────┼─────────────
Govern          │ Repeatable (2) │         70%   │         2.48 │ 🟠 High
Identify        │ Repeatable (2) │         60%   │         2.75 │ 🟠 High
Protect         │ Defined (3)    │         75%   │         1.65 │ 🟡 Medium
Detect          │ Repeatable (2) │         48%   │         3.48 │ 🔴 Critical
Respond         │ Initial (1)    │         48%   │         3.67 │ 🔴 Critical
Recover         │ Initial (1)    │         52%   │         3.52 │ 🔴 Critical


DETAILED GAP ANALYSIS & PRIORITIES
═══════════════════════════════════════════════════════════════════════════════

1. RS - RESPOND FUNCTION (CRITICAL)
   ──────────────────────────────────────────────────────────────────────────
   Current Maturity:      1.48 / 5.0 (Initial)
   Control Effectiveness: 48%
   Gap Score:             3.67 (Most urgent)
   Target Maturity:       4.5 / 5.0
   
   Interpretation:
   The Respond function is currently at Level 1.
   However, with an effectiveness factor of 48%, 
   real operational maturity is closer to Level 0.7.
   
   This indicates a CRITICAL gap between "controls-as-designed" 
   and "controls-as-implemented".
   
   Key Recommendations:
   1. Develop incident response plan with defined escalation procedures
   2. Conduct annual incident response tabletop exercises
   3. Establish post-incident review and continuous improvement process

2. DE - DETECT FUNCTION (CRITICAL)
   ...

3. RC - RECOVER FUNCTION (CRITICAL)
   ...


COMPLIANCE VS IMPLEMENTATION BRIDGE
═══════════════════════════════════════════════════════════════════════════════

Traditional compliance approach says:
  ✓ "We have a firewall policy (ISO 27001, CIS Controls) → Compliant"

This assessment adds:
  ✓ "We have a firewall policy (designed at Level 4)"
  ✓ "But only 70% of systems are enforcing it (effectiveness = 0.7)"
  ✓ "Real operational maturity = 4 × 0.7 = 2.8 (below Defined level)"
  
This gap reflects reality: Many organizations are "compliant on paper" but lack
operational rigor. This tool forces the discussion: compliance without 
effectiveness is audit theater.


INVESTMENT PRIORITIZATION FRAMEWORK
═══════════════════════════════════════════════════════════════════════════════

Based on gap priority, recommend investment allocation:

1. MUST-DO (Next 6 months): Address 🔴 Critical gaps
   → Respond (RS): Incident response capability
   → Detect (DE): Security monitoring capability
   → Recover (RC): Business continuity readiness

2. SHOULD-DO (6-12 months): Address 🟠 High gaps
   → Govern (GV): Risk governance structure
   → Identify (ID): Asset and risk management

3. NICE-TO-DO (12+ months): Address 🟡 Medium gaps
   → Protect (PR): Access and data controls


NEXT STEPS
═══════════════════════════════════════════════════════════════════════════════

1. Share this report with:
   - CISO / Chief Information Security Officer
   - CRO / Chief Risk Officer
   - CFO / Budget committee (for investment justification)

2. Translate top 3 gaps into:
   - Project charters
   - Resource requests
   - Timeline milestones
   - Success metrics

3. Re-assess annually to track maturity progression

4. Validate effectiveness factor (0.0-1.0) quarterly:
   - Testing compliance with control procedures
   - Sampling transaction walkthroughs
   - Soliciting feedback from control owners
```

### Key Insights from Sample Report

**Critical Finding:** Three functions (Respond, Detect, Recover) are at **Initial (Level 1)** with only **48-52% effectiveness**. This means:

- Designed as Initial level, operating at ~0.5 (half-implemented)
- Organization would struggle to detect/respond to live attack
- Business continuity capability is weak
- High risk for material loss in incident

**Recommended Action:** Invest in incident response and monitoring infrastructure within 6 months.

---

## Dashboard & Visualization

### Text-Based Executive Dashboard

The tool outputs a professional dashboard for executive presentation:

```
████████████████████████████████████████████████████████████████████████████████

                    NIST CSF 2.0 MATURITY HEATMAP

                Govern    Identify   Protect   Detect   Respond   Recover
        
Maturity      [████░░] [████░░]  [██████░] [███░░░] [██░░░░] [██░░░░]
Level           2.0        2.4       3.6       1.8       1.1       1.2
              Rep.       Rep.       Def.      Init.     Init.     Init.

Effect.        70%        60%        75%       48%       48%       52%
Factor        (0.70)     (0.60)     (0.75)    (0.48)    (0.48)    (0.52)

Gap Score     2.48        2.75       1.65      3.48      3.67      3.52
Priority      HIGH       HIGH      MEDIUM    CRITICAL  CRITICAL  CRITICAL

████████████████████████████████████████████████████████████████████████████████
```

### Generating Further Visualizations

The tool outputs `nist_assessment_results.json` with complete assessment data, enabling:

**Power BI / Tableau Integration:**
```json
{
  "organization": "Volvo Group Logistics Division",
  "assessment_date": "2024-12-15",
  "by_function": {
    "GV": {
      "avg_maturity": 2.25,
      "avg_effectiveness": 0.70,
      "control_count": 4
    },
    ...
  }
}
```

**Excel Analysis:**
- Pivot tables on maturity by function
- Gap analysis trends year-over-year
- Budget allocation vs. risk reduction

---

## Installation & Dependencies

### Requirements

- **Python:** 3.8 or higher
- **Dependencies:** None (uses standard library only)

This tool has **zero external dependencies**, making it highly portable and suitable for secure/air-gapped environments.

### Setup Instructions

```bash
# Clone repository
git clone https://github.com/yourusername/nist-csf-assessment.git
cd nist-csf-assessment

# Run interactive assessment
python nist_assessment.py

# Run demo mode
python nist_assessment.py --demo

# Results saved to: nist_assessment_results.json
```

### Output Files

After assessment:
- `nist_assessment_results.json` - Complete assessment data (structured)
- Console report - Formatted gap analysis and recommendations

---

## Advanced Topics

### Integrating with Other Frameworks

This tool's NIST CSF 2.0 mapping can be extended to:

- **ISO 27001:2022** - Directly maps to Annex A controls
- **CIS Controls v8** - Maps to Safeguards 1-18
- **COBIT 2019** - Maps to Governance, Manage processes
- **SOC 2** - Maps to Trust Service Criteria

### Continuous Assessment Strategy

**Year 1: Establish Baseline**
- Run comprehensive assessment (first time: 45 minutes)
- Identify critical gaps
- Plan remediation projects

**Quarterly: Targeted Re-Assessment**
- Update 2-3 highest-priority functions only (15-20 minutes)
- Track effectiveness improvements
- Adjust remediation priorities

**Annually: Full Re-Assessment**
- Complete reassessment
- Compare vs. baseline (calculate maturity delta)
- Update 3-year roadmap

### Communicating Results to Non-Technical Stakeholders

**Executive Summary (1 page):**
```
Current State: Respond and Detect functions critically underdeveloped
Risk: Organization cannot effectively detect/respond to ransomware attacks
Investment: €500K over 12 months to reach target maturity
ROI: Reduce mean ALE by €1.2M annually
Timeline: Phase 1 (0-6mo), Phase 2 (6-12mo), Phase 3 (12-24mo)
```

**Board Presentation:**
- Show maturity scorecard (which functions lag)
- Map to business risk (which threats go undetected)
- Present investment case (cost vs. risk reduction)
- Timeline for reaching acceptable maturity

---

## References & Further Reading

- **NIST CSF 2.0 Documentation:** https://www.nist.gov/cyberframework
- **NIST CSF Categories & Subcategories:** https://csrc.nist.gov/projects/cybersecurity-framework/
- **ISO 27001:2022 to NIST CSF 2.0 Mapping:** Available from NIST
- **CIS Controls to NIST CSF Mapping:** Available from CIS Benchmarks
- **FAIR Methodology (quantitative risk):** https://www.fairinstitute.org/

---

## License & Attribution

**Author:** Stephen OMOWUMI, (Cybersecurity GRC Professional)  
**Framework:** NIST Cybersecurity Framework 2.0  
**License:** MIT (Open source, use commercially)

---

## Contact & Feedback

Questions about NIST CSF 2.0 assessment?  
Issues implementing maturity models?  
Ideas for extending the tool?

**Open issues, contribute, submit PRs.**

---

**🎯 Key Takeaway:**

*Traditional compliance asks: "Do we have the control?" ✓  
This tool asks: "Does the control actually work?" 🔍  
The difference between audit-ready and attack-ready.*
