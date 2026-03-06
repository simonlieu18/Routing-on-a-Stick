<p align="center">
<img width="50%" height="324" alt="Screenshot 2026-03-06 at 11 49 15 AM" src="https://github.com/user-attachments/assets/eb10a04e-f620-4ced-b76a-bd58df84fa32" />

</p>

<h1>Router on a Stick with inter-VLAN communication</h1>
In this lab, we segment a network into VLANs and enable inter-VLAN routing using a Router on a Stick (ROAS) configuration<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure/Hyper-V (Virtual Machines)
- Remote Desktop
- Group Policy Management Console
- Active Directory Domain Services
- Powershell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows Server 2025

<h2>High-Level Steps</h2>

- Create Shareable Folder
- Configure Desktop Wallpaper policy
- Verify Policy with Different Departments

<h2>Configuration Steps</h2>

<img width="50%" alt="Screenshot 2026-01-05 at 2 08 40 PM" src="https://github.com/user-attachments/assets/457fc520-9a6b-41a0-8f20-0be5ecdc6031" />

<p>
First, a sharable folder needs to be created so that different departments are able to access the correct image for their wallpaper. To do that, a new folder will need to be created in the "C:" drive of the domain controller VM. After that, the folder's properties will need to be adjusted so that it will be shareable. By going into properties, sharing tab, advanced sharing, and then having "Share this folder" checked.
</p>
<br />

<img width="50%" alt="Screenshot 2026-01-05 at 2 15 21 PM" src="https://github.com/user-attachments/assets/06266e8c-e5a1-43ac-b1cf-4f3ed7801a80" />

<p>
Now, on the client VM, sign in as a user to verify that the folder has been shared correctly. To view the folder, open the folder explorer application and input "\\HOSTNAME". In order to find hostname of your DC, open command line/powershell and type in hostname on your DC VM.
</p>
<br />

<img width="50%" alt="Screenshot 2026-01-05 at 2 22 40 PM" src="https://github.com/user-attachments/assets/4e0622a3-76a5-470a-afbe-413004687bfa" />

<p>
Next, input the images into the shareable folder that will be used for the desktop wallpapers.
</p>
<br />

<img width="50%" alt="Screenshot 2026-01-05 at 2 35 44 PM" src="https://github.com/user-attachments/assets/2dfae8f8-bddf-48f2-8067-edc3d43ac443" />

<p>
To configure the newly created GPO, click edit on it, then head to User configuration --> Policies --> Administrative templates --> Desktop --> Desktop --> Desktop wallpaper
</p>
<br />

<img width="372" height="94" alt="Screenshot 2026-01-05 at 2 26 02 PM" src="https://github.com/user-attachments/assets/25a1bec7-59a1-4239-bfb3-c46eee130714" />

<p>
In the Group Policy Management application, locate "Group Policy Objects" and add a new policy called "Desktop Wallpaper Policy" along with the department name if needed.
</p>
<br />

<img width="45%" alt="Screenshot 2026-01-05 at 2 42 47 PM" src="https://github.com/user-attachments/assets/3143b67d-0dbc-4567-a9b0-653b5ded2fcf" />

<p>
From here, you click "Enabled" and then input the file location of the image that you want to use for the wallpaper. The path should be "\\HOSTNAME\FOLDER\FILE", for example my image is a JPG file and the name of the file is "gt-r" so the full path that I would use it "\\dc-1\wallpapers\gt-r.jpg".
</p>
<br />

<img width="375" height="282" alt="Screenshot 2026-01-05 at 3 45 47 PM" src="https://github.com/user-attachments/assets/cb178a79-dc6f-4307-8943-5171c1a2c68c" />

<p>
Now drag and drop the GPO into the correct organizational unit that is correlated to the users/departments.
</p>
<br />

<img width="50%" alt="Screenshot 2026-01-06 at 9 17 11 AM" src="https://github.com/user-attachments/assets/cb47c1a1-4c2e-4e3b-978a-03b988629841" />
<img width="50%" alt="Screenshot 2026-01-06 at 9 43 56 AM" src="https://github.com/user-attachments/assets/1b2f197c-1a7b-43b1-ad6a-7f566fcd8045" />

<p>
Now on the client virtual machine, manually update the Group Policy by opening Powershell and inputting the command "gpudate /force". Then run the command "gpresult /r" to verify that the policy has been applied.
</p>

<img width="75%" alt="Screenshot 2026-01-06 at 9 33 08 AM" src="https://github.com/user-attachments/assets/554cade9-7be9-46eb-b45c-2e7f82e121c0" />

<p>
Log out of the user and log back in, the desktop wallpaper should now be changed. Different users from various departments should also have their own wallpapers if that was configured.
</p>
