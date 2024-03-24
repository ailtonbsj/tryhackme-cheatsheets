# Active Directory from Windows

```powershell
# Reset password of a user on AD
Set-ADAccountPassword USER -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

# Force change password on logon
Set-ADUser -ChangePasswordAtLogon $true -Identity USER -Verbose

# Update groups policies
gpupdate /force
```