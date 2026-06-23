# Linux Access Control Lab

A practical Linux administration project demonstrating user creation, group management, directory ownership, file permissions, ACL configuration, and access verification in a controlled departmental-style environment.

## Overview

This lab simulates a small multi-user Linux environment where access to shared directories is restricted by ownership, group membership, permissions, and ACLs. The objective was to build a secure file structure that separates departmental data and only allows authorized users to access the correct resources.

The project was completed using standard Linux command-line tools and verified through access testing and permission inspection.

## Objectives

- Create and manage Linux users
- Create and manage Linux groups
- Build a structured directory layout for departmental access
- Assign correct ownership and permissions
- Apply the setgid bit to enforce group inheritance
- Configure ACLs for controlled access
- Verify the final configuration using `getfacl`

## Tools Used

- `adduser`
- `addgroup`
- `usermod`
- `mkdir`
- `touch`
- `chown`
- `chmod`
- `setfacl`
- `getfacl`
- `su`
- `ls`
- `cat`

## Lab Summary

The lab began by creating a new user account named `john`. A second user, `jane`, was also created later for testing departmental access.

A working directory named `srv` was created inside the main user’s home directory. Two subdirectories were created inside it:

- `security_directory`
- `finance_directory`

Each directory represented a different department and was assigned to its own group:

- `security_group`
- `finance_group`

Files were created inside each directory to simulate departmental data:

- `logs.txt` inside `security_directory`
- `expenditure.txt` inside `finance_directory`

Ownership and permissions were then configured to restrict access. The setgid bit was applied so that files created inside each directory inherit the correct group ownership. ACLs were also configured to allow approved users to traverse the parent directory and access the correct folders.

## Configuration Details

### Users
- `john`
- `jane`

### Groups
- `security_group`
- `finance_group`

### Directories
- `/home/willyonazure/srv/security_directory`
- `/home/willyonazure/srv/finance_directory`

### Files Created
- `logs.txt`
- `expenditure.txt`

### Access Control Model
- `security_directory` is restricted to `security_group`
- `finance_directory` is restricted to `finance_group`
- Unauthorized access is denied
- ACLs are used where traversal or special access is required

## Results

The lab was successfully completed and tested. The final setup confirmed that:

- Users were created correctly
- Groups were created correctly
- Directory permissions were enforced correctly
- Group-based access worked as intended
- ACLs were properly applied and verified
- Unauthorized directory access was blocked

## Evidence

The repository includes screenshots showing the major stages of the lab, including:

- user creation
- directory creation
- ownership and permission changes
- ACL verification
- permission testing with different users

## Key Skills Demonstrated

- Linux user and group administration
- File and directory permission management
- Ownership control
- ACL configuration
- Security-minded directory design
- Command-line system administration
- Permission verification and troubleshooting

## Repository Structure

```text
linux-access-control-lab/
├── README.md
├── portfolio/
│   ├── Linux_Access_Control_Lab_Portfolio_Final.pdf
│   └── Linux_Access_Control_Lab_Portfolio_Final.odt
├── screenshots/
│   ├── 01-adduser-john.png
│   ├── 02-adduser-jane.png
│   ├── 03-mkdir-srv-subdirs.png
│   ├── 04-chown-chmod.png
│   ├── 05-getfacl-security.png
│   ├── 06-getfacl-finance.png
│   └── 07-testing-permissions.png
└── notes/
    └── command-log.txt