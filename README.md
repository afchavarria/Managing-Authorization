# File permissions in Linux

## Project description

As part of the research team at my organization, I was tasked with updating the authorizations and permissions of the workers within the projects directory. While investigating, I observed that the permissions did not reflect the level of authorizations given. To update authorizations, I did as follows:

## Checking file and directory details
<img width="1867" alt="Image" src="https://github.com/user-attachments/assets/a8f03094-7d7d-4714-89f6-e3eecef64503" />

The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the projects directory. I used the ls command with the -la option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named drafts, one hidden file named .project_x.txt, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory. 

## Describing the permissions string
The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:
1st character: This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.
2nd-4th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.
5th-7th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.
8th-10th characters: These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.

## Changing file permissions
The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined project_k.txt must have the write access removed for other.

The following code demonstrates how I used Linux commands to do this:
<img width="1866" alt="Image" src="https://github.com/user-attachments/assets/6504e2f8-d2ce-4b3e-bdf8-12992e4fc28b" />

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The chmod command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the project_k.txt file. After this, I used ls -la to review the updates I made.

## Changing file permissions on a hidden file
The research team at my organization recently archived project_x.txt. They do not want anyone to have write access to this project, but the user and group should have read access. 

The following code demonstrates how I used Linux commands to change the permissions:
<img width="1866" alt="Image" src="https://github.com/user-attachments/assets/bbae6fff-5a8a-4432-9a00-2125c3199012" />

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know .project_x.txt is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with u-w. Then, I removed write permissions from the group with g-w, and added read permissions to the group with g+r. 

## Changing directory permissions
My organization only wants the researcher2 user to have access to the drafts directory and its contents. This means that no one other than researcher2 should have execute permissions.

The following code demonstrates how I used Linux commands to change the permissions:
<img width="1864" alt="Image" src="https://github.com/user-attachments/assets/afca20c6-3ec9-4574-8e71-ef7ae675e6b3" />

The output here displays the permission listing for several files and directories. Line 1 indicates the current directory (projects), and line 2 indicates the parent directory (home). Line 3 indicates a regular file titled .project_x.txt. Line 4 is the directory (drafts) with restricted permissions. Here you can see that only researcher2 has execute permissions.  It was previously determined that the group had execute permissions, so I used the chmod command to remove them. The researcher2 user already had execute permissions, so they did not need to be added.

## Summary
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using ls -la to check the permissions for the directory. This informed my decisions in the following steps. I then used the chmod command multiple times to change the permissions on files and directories.





















