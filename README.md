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


## Real-World Application

This lab mirrors a common enterprise scenario where multiple departments share the same server infrastructure but require strict data separation. In a real organization, HR, Finance, and Security teams often store sensitive files on shared systems, and improperly configured permissions are one of the most common causes of internal data breaches. This setup demonstrates how proper user/group segregation, ownership control, and ACLs can enforce least-privilege access, ensuring users only see what they're authorized to see, regardless of how the directory structure grows.

## Lessons Learned

- Group inheritance isn't automatic — Initially, new files created inside `security_directory` weren't inheriting the correct group ownership. This led me to research and apply the `setgid` bit on the directory, which solved the issue by ensuring all new files automatically inherit the parent directory's group.
- Standard permissions have limits - Traditional `chmod`/`chown` worked well for the two main departmental groups, but fell short when a user needed to traverse a parent directory without being granted full access to sibling folders. This is where ACLs (`setfacl`) became necessary, they allowed precise, additive permissions without loosening the overall security model.
- Verification is not optional — Running `getfacl` after every major change became a habit rather than a final step. Assuming a configuration worked without checking it directly led to a couple of false positives early on, reinforcing that in real environments, you verify access control changes the same way you'd verify a firewall rule, trust nothing until it's tested.

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