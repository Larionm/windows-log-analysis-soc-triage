# windows-log-analysis-soc-triage
SOC-style investigation of Windows event logs for suspicious activity

# 🕵️ Windows Log Analysis – SOC Triage

## 🧠 Objective
This project simulates a Tier 1 SOC analyst triaging Windows Security logs for suspicious behavior. The focus is on identifying privilege escalation indicators and documenting findings in an incident report format.

## 🛠 Tools Used
- Windows Event Viewer
- Native Security Event Log (live system)
- Manual investigation techniques

## 🧪 Event Investigated

### 🛡 Privilege Escalation Indicators

- Detected `Event ID 4672`: Special privileges assigned to LocalSystem account
- **Account Name**: Microsoft-Windows-Security-Auditing
- **Privileges Assigned**:
  - SeAssignPrimaryTokenPrivilege
  - SeTcbPrivilege
  - SeSecurityPrivilege
  - SeTakeOwnershipPrivilege
  - SeLoadDriverPrivilege
  - SeBackupPrivilege
  - SeRestorePrivilege
  - SeDebugPrivilege
  - SeAuditPrivilege
  - SeSystemEnvironmentPrivilege
  - SeImpersonatePrivilege
  - SeDelegateSessionUserImpersonatePrivilege
- **Workstation**: X15
- **Date/Time**: 2025-05-13T20:23:13Z

> This event shows the LocalSystem account receiving high-level privileges. While normal for system services, these same privileges can be abused during attacks (e.g., SeDebugPrivilege for process injection, SeImpersonatePrivilege for lateral movement). Analysts should correlate this with related logon and process creation activity.

## 📌 SOC Relevance
- Privilege escalation detection is a core SOC responsibility.
- Event ID 4672 is high-value for correlating with suspicious lateral movement or post-exploitation activity.
- Triaging such events builds practical analyst experience for real-time alert response.

