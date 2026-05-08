# Most Common Windows Event IDs to Hunt - Mind Map

Windows Event Logs mindmap provides a simplified view of Windows Event logs and their capacities that enables defenders to enhance visibility for different purposes:
* Log collection (eg: into a SIEM)
* Threat hunting
* Forensic / DFIR
* Troubleshooting

---

## Scheduled Tasks

| Event ID | Description |
| :--- | :--- |
| **4697** | This event generates when new service was installed in the system. |
| **106** | This event is logged when the user registered the Task Scheduler task. |
| **4702** | This event generates when scheduled task was updated. |
| **140** | This event is logged when the time service has stopped advertising as a time source because the local machine is not an Active Directory Domain Controller. |
| **4699** | A scheduled task was deleted. |
| **141** | The time service has stopped advertising as a time source because there are no providers running. |
| **201** | This event is logged when the task scheduler successfully completed the task. |

## Services

| Event ID | Description |
| :--- | :--- |
| **4697** | A service was installed in the system. |
| **7045** | Created when new services are created on the local Windows machine. |
| **7034** | The service terminated unexpectedly. |
| **7036** | The Windows Firewall/Internet Connection Sharing (ICS) service entered the stopped state or, The Print Spooler service entered the running state. |
| **7040** | The start type of the IPSEC services was chnaged from disabled to auto start. |

## Event Log Manipulation

| Event ID | Description |
| :--- | :--- |
| **1102** | Whenever Windows Security audit log is cleared, event ID 1102 is logged. |
| **104** | This event is logged when the log file was cleared. |

## Authentication

| Event ID | Description |
| :--- | :--- |
| **4776** | The domain controller attempted to validate the credentials for an account. |
| **4771** | This event is logged on domain controllers only and only failure instances of this event are logged (Kerberos pre-authentication failed). |
| **4768** | This event is logged on domain controllers only and both success and failure instances of this event are logged (A Kerberos authentication ticket TGT) was requested. |
| **4769** | Windows uses this event ID for both successful and failed service ticket requests (A Kerberos service ticket was requested). |

## Sessions

| Event ID | Description |
| :--- | :--- |
| **4624** | An account was successfully logged on. |
| **4625** | An account failed to log on. |
| **4634 + 4647** | User initiated logoff/An account was logged off |
| **4648** | A logon was attempted using explicit credentials |
| **4672** | Special privileges assigned to new logon |

## Account Management

| Event ID | Description |
| :--- | :--- |
| **4720** | A user account was created |
| **4722** | A user account was enabled |
| **4724** | An attempt was made to reset an accounts password |
| **4728 / 4732 / 4756** | group membership changes. |

## Network Shares

| Event ID | Description |
| :--- | :--- |
| **5140** | A network share object was accessed |
| **5145** | Network share object was checked to see whether client can be granted desired access. |

---
> **Credits:** https://github.com/christophetd/