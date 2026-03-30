# Windows File Sharing & NTFS Permissions Lab

## Objective
To practice setting up file sharing and permissions in Windows.

## Tools Used
- HackTheBox Academy (Lab Environment)
- Windows Operating System
- File Explorer
- Computer Management (Local Users and Groups)
- NTFS Permissions (Security Tab)
- SMB Share Permissions (Sharing Tab)
- Advanced Security Settings

## Steps

> I used the Windows GUI to complete the following steps.
## 1. Create a Shared Folder

I created a shared folder called Company Data and enabled sharing.

<img width="1027" height="552" alt="01-enable-sharing" src="https://github.com/user-attachments/assets/03e8b2be-2df7-4d2c-8d96-4fe973e57926" />

## 2. Create a Subfolder

Inside that folder, I created another folder called HR.

<img width="1024" height="627" alt="02-create-subfolder-hr" src="https://github.com/user-attachments/assets/9ad2aaff-0f9b-4df7-b5bc-a9c9457b93f7" />

## 3. Create a User

I created a user named **Jim** in Computer Management.

I also unchecked:
- User must change password at logon
  
<img width="987" height="652" alt="03-computer-management-create-new-user" src="https://github.com/user-attachments/assets/db2bac63-42ca-423b-a886-66efed1ba3f9" />

## 4. Add User to a Group

I added **Jim** to the HR group using Local Users and Groups.

<img width="985" height="707" alt="04-add-jim-to-hr-group" src="https://github.com/user-attachments/assets/b42831cd-efef-4041-b7a5-5592f9117e36" />

## 5. Set Permissions on a Shared Folder (Company Data)

I removed the default group (**Everyone**) from the share permissions.

Then I added the **HR** group and gave it:
- Read
- Change

After that, I configured NTFS permissions in the Security tab and gave HR:

- Modify
- Read & Execute
- List folder contents
- Read
- Write

Now only the HR group can access the shared folder over the network.

<img width="777" height="605" alt="05-hr-group-with-read-and-change-checked" src="https://github.com/user-attachments/assets/48ea5062-2b60-423c-a18f-e9ae6bfc9f28" />

<img width="803" height="581" alt="06-hr-ntfs-permissions" src="https://github.com/user-attachments/assets/86eca8a4-66fb-4f5d-9169-9f2a8b25735a" />

## 6. Set Permissiosn on HR Subfolder

I disabled inheritance on the HR folder and removed any default groups.

Then I added only the **HR** group and gave it:

- Modify
- Read & execute
- List folder contents
- Read
- Write

This makes sure only HR can access sensitive data inside the HR folder.

<img width="847" height="608" alt="07-disable-inheritance" src="https://github.com/user-attachments/assets/7fb4d91f-eb42-4f0c-bcb6-cafd4949e6af" />


## 7. Add the HR Group to the NTFS Permissions List of the HR Subfolder

I did this by opening the HR subfolder properties, going to the security tab, disabling inheritance, adding the HR group, and setting NTFS permissions for HR as:

- modify
- read & execute
- list folder contents
- read
- write

<img width="922" height="636" alt="08-set-hr-ntfs-permissions" src="https://github.com/user-attachments/assets/d06eb732-29a9-46ef-958a-dac30eaa2df1" />

This ensures that only the HR group can access sensitive files inside the HR folder, even if someone can access the main shared folder.

## Overview

In this project, I configured Windows file sharing and NTFS permissions to enforce controlled access to folders. I created users and groups, removed default access, and applied least privilege by disabling inheritance and assigning permissions only to the HR group. This helped me understand how access control works in real environments and how misconfigurations could lead to unauthorized access. 

Misconfigured permissions can allow unauthroized users to access sensitive data. By removing default gruops and disabling inheritence, I made sure that only those groups who needed to access HR group had access. This is important in the real world where sensitive data like employee records must be protected. 
