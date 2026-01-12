# PowerShell Scripts Repository

Personal collection of PowerShell scripts for Microsoft 365 administration, Exchange Online management, Active Directory automation, and enterprise IT operations.

## 📁 Repository Structure

```
PowerShell-Scripts/
├── Exchange-Online/          # 40 scripts
│   ├── Migration/            # DL migration, mailbox moves, cross-tenant
│   ├── Reporting/            # Mailbox stats, DL reports, ActiveSync
│   └── Management/           # DL maintenance, group sync, DKIM
├── SharePoint-OneDrive/      # 7 scripts - OneDrive provisioning & access
├── ActiveDirectory/          # 17 scripts
│   ├── UserLifecycle/        # User provisioning, cleanup, deprovisioning
│   ├── ComputerLifecycle/    # Stale computer management
│   ├── ServiceAccounts/      # Password notifications, NPS sync
│   └── GroupManagement/      # Security group creation
├── M365-Licensing/           # 3 scripts - License assignment & reporting
├── Reporting/                # 12 scripts - Intune, MFA, permissions
├── Security/                 # 7 scripts - TLS, message class, legal hold
├── Functions/                # 14 scripts - Utilities & connection helpers
├── Templates/                # 2 scripts - Script templates
├── Snippets/                 # Quick reference commands (TBD)
└── Archive/                  # 88 scripts - Legacy & environment-specific
    ├── JAHGlobal-Coleman/    # Previous employer scripts
    ├── Previous-Scripts/     # Old versions
    └── Legacy-DEV/           # Development/test scripts
```

---

## 🔥 Most Used Scripts

### Exchange Online Migration
| Script | Description |
|--------|-------------|
| `Migrate-DistributionGroups.ps1` | Bulk DL migration between tenants |
| `Recreate-DistributionGroup.ps1` | Recreate DLs for cross-tenant moves |
| `AutomatedDLMigration.ps1` | Automated DL migration workflow |
| `Exchange_Mailbox_Discovery_Script.ps1` | Comprehensive mailbox inventory |

### SharePoint/OneDrive
| Script | Description |
|--------|-------------|
| `Remove-OneDriveAccess.ps1` | Remove service account access from OneDrive sites |
| `Validate-OneDriveAccessRemoved.ps1` | Verify access removal |
| `Backout-RestoreOneDriveAccess.ps1` | Rollback access changes |
| `One Drive Provision.ps1` | Pre-provision OneDrive sites |

### Active Directory
| Script | Description |
|--------|-------------|
| `AD_User_Cleanup.ps1` | Disabled user lifecycle management |
| `Disable_Stale_Computers.ps1` | Stale computer object handling |
| `Service_Account_Pass_Notification.ps1` | SVC account password expiry alerts |

### Reporting
| Script | Description |
|--------|-------------|
| `Intune_Device_Report.ps1` | Device compliance reporting |
| `Gett-MFAReport.ps1` | MFA status report |
| `New-PermissionReport.ps1` | Comprehensive permission audit |

---

## ⚠️ Notes

### Credentials
Many scripts contain placeholder or legacy credentials that need updating. Use:
- Azure Key Vault for secrets
- Certificate-based authentication
- `Get-Credential` for interactive prompts

### Deprecated Modules
Some scripts use deprecated modules:
- `MSOnline` → Update to `Microsoft.Graph`
- `AzureRM` → Update to `Az`
- Basic Auth → Modern Auth with MFA

### Microsoft Scripts
For official Microsoft tools, reference the source repos instead of local copies:
- [CSS-Exchange](https://github.com/microsoft/CSS-Exchange) - HealthChecker, CVE scripts, etc.
- [Microsoft365DSC](https://github.com/microsoft/Microsoft365DSC) - M365 config as code

---

## 📚 Quick Reference

### Connect to Exchange Online (Modern Auth)
```powershell
Connect-ExchangeOnline -UserPrincipalName admin@domain.com
```

### Connect to Microsoft Graph
```powershell
Connect-MgGraph -Scopes "User.Read.All","Group.Read.All"
```

### Connect to SharePoint Online
```powershell
Connect-SPOService -Url https://tenant-admin.sharepoint.com
```

### ImmutableID Conversion (Azure AD Connect)
```powershell
# AD GUID to ImmutableID
$guid = (Get-ADUser username).ObjectGuid
$immutableID = [System.Convert]::ToBase64String($guid.ToByteArray())

# ImmutableID to AD GUID  
$bytes = [System.Convert]::FromBase64String($immutableID)
$guid = [Guid]$bytes
```

---

## 📋 Changelog

### January 2026
- Initial repository organization
- Migrated 190 scripts from legacy collection
- Removed 79 obsolete files (VBS, batch, data files, Microsoft scripts)
- Archived 88 legacy/environment-specific scripts
- Organized 102 active scripts into categories

---

## 🔗 External Resources

- [CSS-Exchange Scripts](https://github.com/microsoft/CSS-Exchange)
- [ExchangeOnlineManagement Module](https://www.powershellgallery.com/packages/ExchangeOnlineManagement)
- [Microsoft.Graph Module](https://www.powershellgallery.com/packages/Microsoft.Graph)
- [PnP.PowerShell](https://pnp.github.io/powershell/)
