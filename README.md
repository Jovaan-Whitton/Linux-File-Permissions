# File Permissions in Linux – Portfolio Activity

## Project Description

Linux commands allow users to communicate and control the OS.  
As a security professional, I have been tasked with examining existing file permissions on the file system to ensure the appropriate users on the research team are authorized with the correct permissions.  
If permissions do not match the users’ authorization, they will be modified to authorize appropriate users and remove any unauthorized access.

---

[View Full Portfolio Document](file-permissions-linux-portfolio.docx)

---

## Check File and Directory Details

To check the file and directory details within the `projects` directory, I used the command:

```bash
ls -la
```

- `ls`: Lists all contents within a directory or file.
- `-l`: Displays a list of permissions for files and sub-directories.
- `-a`: Displays hidden files.

This command shows all file and directory permissions, including hidden files.

---

## Describe the Permission String

The output from `ls -la` shows permissions granted for files and directories.  
For example, the 10-character permission string for the file `project_k.txt` is read as follows:

```text
-rw-rw-rw-
```

- `-`: Indicates a file (if it were a directory, it would be `d`)
- `rw-`: User has read and write permissions; lacks execute
- `rw-`: Group has read and write permissions; lacks execute
- `rw-`: Others have read and write permissions (**should be corrected**)

---

## Change File Permissions

Our company doesn't allow the "others" owner type to have write permissions.  
To remove write permission for others from `projects_k.txt`, use:

```bash
chmod o-w projects_k.txt
```

---

## Change File Permissions on a Hidden File

The research team archived `.project_x.txt`, making it a hidden file.  
This file should **not** grant any owner type write permissions.  
Only the user and group should have read access.

Set permissions with:

```bash
chmod u=r,g=r .project_x.txt
```

Explanation:
- `chmod`: Command to change permissions
- `u=r`: Set user to read-only
- `g=r`: Set group to read-only

Alternative command:

```bash
chmod u-w,g-w+r .project_x.txt
```

- `-`: Removes a permission
- `+`: Adds a permission

---

## Change Directory Permissions

Files and directories belong to **Researcher 2**, who should be the only one with execute access to the `drafts` directory.

Remove group execute permission with:

```bash
chmod g-x drafts
```

- `g-x`: Removes execute from the group for the `drafts` directory

---

## Summary

The commands used:

- Allowed me to audit and secure the Linux file system
- Ensured only authorized users have appropriate permissions
- Removed unnecessary or risky permissions

This approach aligns with best practices in Linux file security and role-based access.

---
