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
1. Create a Shared Folder

I created a shared folder called Company Data and enabled sharing.

<img width="1027" height="552" alt="01-enable-sharing" src="https://github.com/user-attachments/assets/03e8b2be-2df7-4d2c-8d96-4fe973e57926" />

2. Create a Subfolder

Inside that folder, I created another folder called HR. I did this through the GUI by double-clicking on the Company Data folder on the desktop, right clicking in the folder, and creating a new folder called HR.

<img width="1024" height="627" alt="02-create-subfolder-hr" src="https://github.com/user-attachments/assets/9ad2aaff-0f9b-4df7-b5bc-a9c9457b93f7" />

3. Create a User

I created a user named Jim by opening Computer Management, navigating to "Users", right clicking in the field and selecting "New User", and adding the name "Jim" to the "Username" field.

I also unchecked:
  "User must change password at logon"
  
<img width="987" height="652" alt="03-computer-management-create-new-user" src="https://github.com/user-attachments/assets/db2bac63-42ca-423b-a886-66efed1ba3f9" />

5. Add User to a Group

I added Jim to the HR group by adding a new group called HR in the groups tab under "Local Users and Groups" in Computer Management. Then I right-clicked on HR, then clicked properties, then added Jim to the list of members in HR.

<img width="985" height="707" alt="04-add-jim-to-hr-group" src="https://github.com/user-attachments/assets/b42831cd-efef-4041-b7a5-5592f9117e36" />

6. Set Permissions on a Shared Folder (Company Data)

I removed the default group (Everyone) from the share permissions and then configured NTFS permissions separately in the Security tab by right-clicking on the Company Data folder on the Desktop, clicking on properties, then security, then removed the default group (Everyone).

I added the HR group and gave it Read and Change permissions in the Share settings by clicking "edit" in the security tab, adding HR where it says "enter the object names to select", then OK. Then under the sharing tab, clicking "advanced permissions", and checked "read" and "change" and clicked apply, then OK.

Now HR can access the shared folder over the network.

<img width="777" height="605" alt="05-hr-group-with-read-and-change-checked" src="https://github.com/user-attachments/assets/48ea5062-2b60-423c-a18f-e9ae6bfc9f28" />

Next, I disabled inheritance by going back to properties on the HR subfolder, clicking the security tab, then clicking advanced, and then clicking  disable inheritance. If necessary, I would remove the default group also.

<img width="847" height="608" alt="06-disable-inheritance" src="https://github.com/user-attachments/assets/7c1426a9-cdb0-4084-8650-e65254856c0b" />

Finally, I gave NTFS permissions by checking: 
- modify
- read & execute
- list folder contents
- read
- write
  
<img width="795" height="567" alt="07-ntfs-permissions-company-data" src="https://github.com/user-attachments/assets/e3f24017-f3b8-43e5-959a-e5ee4bffb125" />

7. Add the HR Group to the NTFS Permissions List of the HR Subfolder

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
