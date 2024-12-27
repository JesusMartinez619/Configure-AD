<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Creating Virtual network and Virtual machines
- Installing Active Directory (AD)
- Configuring Organizational Unit (OU)
- Adding client-1 to dc-1
- Create Group Policy Object (GPO)

<h2>Deployment and Configuration Steps</h2>

- In this first section I create a virtual network and 2 virtual machines, in the first image I create a virtual network where I will be connecting both virtual machines. In the second image we have 2 virtual machines 1 acting as the domain controller in a server "dc-1" and the other acting as the client in an end-device "client-1".

<img width="445" alt="image" src="https://github.com/user-attachments/assets/988dafa7-0a81-450c-ae9f-1872c746ba2b" />
  <img width="707" alt="image" src="https://github.com/user-attachments/assets/c78e93d4-1f21-4724-aa7f-1de3da348ac2" />

- In this second section I will be in the "Domain controller" and will be adding active directory to the server manager. In the first and second picture it demonstrates how I go into "Add roles and features" where I will be installing "Active Directory Domain Services". In the third picture I configure the deployment to finish up the installment which will require to restart the server and have the server manager updated.

<img width="828" alt="image" src="https://github.com/user-attachments/assets/b1445e3a-870a-489d-b715-821b5108eb8a" /> <img width="355" alt="image" src="https://github.com/user-attachments/assets/b1ec1612-730f-49b9-8799-f650ba557993" /> <img width="345" alt="image" src="https://github.com/user-attachments/assets/f5b9cfc9-bb4c-4f16-acb0-2b0c680cea6a" />


- In this third section I will be creating OUs (Organizational Units) inside the AD (Active Directory), In this first image it demonstrates how I create OUs, I will be creating an OU for "Admins" and for "Employees". In this second image I create a "User" for the "Admins" OU meaning this user will be an admin inside of this domain the admin will use for this example will be "jane". In the third image it shows how I add "jane" to the "domain admins" security group which is a built in administrator group.

<img width="557" alt="image" src="https://github.com/user-attachments/assets/8036e321-e005-451e-ba37-7870bf20181f" /> <img width="653" alt="image" src="https://github.com/user-attachments/assets/cc6e11a0-2105-45d7-852b-245015f8c201" /> <img width="286" alt="image" src="https://github.com/user-attachments/assets/f03278c6-8af3-4ea4-8f33-9661e0f0072f" />

- In this fourth section I configure "client-1" VM (virtual machine) to add it in the AD, in this first picture I am configuring the "client-1" VM to be added as a member of the "dc-1" domain controller. Once the "client-1" is added to the AD I will create an OU for the client named "CLIENTS".

<img width="541" alt="image" src="https://github.com/user-attachments/assets/21eb09cb-582b-4706-8ce7-d30f75716a40" /> <img width="446" alt="image" src="https://github.com/user-attachments/assets/01e54519-f050-4c68-bb86-75137a98b2b4" />

- In this fifth section we will be creating a Group Policy Object (GPO), in this first and second image I open GPO management and create a GPO for "Account Lockout". In the 3rd image it shows the configurations I set for the "Account Lockout" GPO, ( Account lockout duration - 30 min/ Account lockout threshhold - 5 invalid logon attempts/ Reset account lockout counter after - 10 min). In the last image we test the GPO after updating and linking to our OU and account was successfully locked out.


<img width="724" alt="image" src="https://github.com/user-attachments/assets/347b89eb-4548-4f3a-8792-2ebd89f2b9d1" /> <img width="572" alt="image" src="https://github.com/user-attachments/assets/8a648e2a-6114-4cfb-a2b6-05bc396c6419" /> <img width="230" alt="image" src="https://github.com/user-attachments/assets/3a7ecbf7-d6c6-43a2-94f3-18eaefbfe8ef" /> <img width="112" alt="image" src="https://github.com/user-attachments/assets/3308ae19-0e01-40c8-9704-42282a61c5e4" />



