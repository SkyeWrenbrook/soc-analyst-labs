# NTFS vs Share Permissions

# Overivew

NTFS and Share Permissions are two primary types of permissions that exist in Windows. Understanding them is crucial for proper security configuration. 

# What I Learned

- NTFS permissions apply locally and over the network
- Share permissions only apply to network access
- SMB is used for file sharing in Windows
- When both are applied, the most restrictive permission wins
  
## One Example

If a user has full control in NTFS but only has Read access on the Share, their access over the network is Read

## One Takeaway

Both NTFS and Share Permissions must be checked together when analyzing access issues or potential security risks
