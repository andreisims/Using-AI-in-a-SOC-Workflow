# Using-AI-in-a-SOC-Workflow

### This will be a project that will engineer an automated security orchestration and response (SOAR) workflow deployed on a virtual SOC lab using VMware. 
Splunk with n8n will automate security alert ingestion, enrichment, and workflow execution, reducing manual analyst triage

<h3>First we will open VMware Workstation or you can download it here: https://www.broadcom.com/</h3>
<li>once on the website, click the 'Support Portal' and then register</li>
<img width="1760" height="712" alt="image" src="https://github.com/user-attachments/assets/3677c014-12e9-446f-b4bf-aab6883009eb" />
<li>you may need to disable your VPN in order to log in</li>
<img width="1057" height="346" alt="image" src="https://github.com/user-attachments/assets/42889bbe-a4d0-48c4-b20c-212ab7faf586" />

<li>Once signed in, click 'My Downloads' and you should see the option for VMware Workstation Pro</li>
<img width="1502" height="400" alt="image" src="https://github.com/user-attachments/assets/99cff1e8-654e-404a-87f7-3f52d31c4a01" />
<li>I would also recommend using a notepad/text editor for recording the details for the upcoming installations:</li>
<ul>Windows 10 VM</ul>
<ul>Splunk VM</ul>
<ul>n8n instance</ul>
<ul>Kali linux</ul>
<li>Step1: download a win10 iso file: https://www.microsoft.com/en-us/software-download/windows10</li>
<li>click the download option on 'Create Windows 10 installation media</li>
<img width="1763" height="781" alt="image" src="https://github.com/user-attachments/assets/817c661b-46da-40df-ad2a-05bb58b65a4f" />
<li>save it to your Downloads folder, accept the agreement, select 'Create installation media', then Next</li>
<img width="906" height="576" alt="image" src="https://github.com/user-attachments/assets/75f23728-c7bf-4cb7-b6f3-ab39efa8d79d" />
<li>select Next again to get to the Create installation media (ISO file) option</li>
<img width="906" height="576" alt="image" src="https://github.com/user-attachments/assets/5cd6a519-d185-4f7e-b9b0-a423694276b5" />
<li>save file to Downloads folder. Process may take several minutes</li>
<img width="942" height="500" alt="image" src="https://github.com/user-attachments/assets/c7ba79ee-a743-40e5-bfd6-34d7332e42fd" />
<li>While waiting for that download to complete, let's start on the next installation: Ubuntu https://ubuntu.com/</li>
<li>select Products, Ubuntu Server, and click download</li>
<img width="1117" height="502" alt="image" src="https://github.com/user-attachments/assets/74155db2-9354-42c3-bda6-009dbc9d9629" />
<li>Now download Kali: https://www.kali.org/</li>
<li>once you select download, be sure to choose the Virtual Machines platform</li>
<img width="1012" height="563" alt="image" src="https://github.com/user-attachments/assets/96489f7a-dbef-4348-b935-51937843e8c9" />
<li>click the download arrow on VNware</li>
<img width="1227" height="570" alt="image" src="https://github.com/user-attachments/assets/6fb8af38-9993-48f9-8805-25e0eff659cb" />
<li>Hopefully, the windows 10 vm download is now complete, so click Finish</li>
<img width="860" height="541" alt="image" src="https://github.com/user-attachments/assets/d5a62d7d-b447-45bb-92c8-fa52f93c6904" />
<li>Next, open VMware and select Create a New Virtual Machine</li>
<img width="1481" height="716" alt="image" src="https://github.com/user-attachments/assets/efcce034-5dc0-42ce-be02-c1c4c148b2f7" />
<img width="1080" height="627" alt="image" src="https://github.com/user-attachments/assets/1fd93b3c-73f1-40e9-962b-ca196f34e7ab" />

<li>select Custom, and next to get to the installer disc image option. Browse your Download folder and select the win10 ISO</li>
<img width="992" height="648" alt="image" src="https://github.com/user-attachments/assets/1eb60977-a44b-432c-a759-58dd241a2672" />
<li>click next and give a name to your VM. Then next, next, and next</li>
<li>increase RAM to 4GB, next</li>
<img width="1165" height="692" alt="image" src="https://github.com/user-attachments/assets/be4b499d-2953-46c7-918a-bd6c16e75805" />
<li>NAT is fine, next</li>
<img width="1087" height="608" alt="image" src="https://github.com/user-attachments/assets/97cf6b5c-0af1-4d45-bc0e-0f83001a339f" />
<li>click through the next defaults and then create a new virtual disk</li>
<img width="987" height="636" alt="image" src="https://github.com/user-attachments/assets/809da32e-d817-4036-a5f2-f73216c6d218" />
<li>the default size is fine, next</li>
<img width="985" height="637" alt="image" src="https://github.com/user-attachments/assets/25d59e87-c215-4de2-8fb0-f297b75fc58f" />
<li>next, next, then finish</li>
<img width="1122" height="643" alt="image" src="https://github.com/user-attachments/assets/c21e2688-caaa-45f7-af6e-84e463649fd6" />
<img width="1145" height="706" alt="image" src="https://github.com/user-attachments/assets/24405b34-acbd-4d38-a5cf-fe0de3859a2b" />

<li>Next, let's launch the Ubuntu ISO</li>
<li>this is essentially a repeat process of the windows 10 VM except the image will be the Ubuntu download instead</li>
<img width="1030" height="365" alt="image" src="https://github.com/user-attachments/assets/e2284c25-d997-4a7d-aa2a-3a4e89ae71c9" />
<li>for the name, you might want to include Splunk in the title as this will be where we launch the Splunk instance</li>
<img width="803" height="332" alt="image" src="https://github.com/user-attachments/assets/69ce7427-f6e4-4031-8ede-fc927db55eb8" />
<li>increase RAM to 8GB, and increase disk size to 100GB. Next, next, finish</li>
<img width="825" height="585" alt="image" src="https://github.com/user-attachments/assets/cf988736-cc41-4285-8d48-694fce5cc70e" />

<li>We will repeat the same process for creating a new virtual machine using the same Ubuntu download for our n8n instance</li>
<img width="832" height="585" alt="image" src="https://github.com/user-attachments/assets/68b0f2f5-44c3-4ec9-b161-f3a001a74dca" />
<li>accept the defaults but increase disk size to 50. Next, next, Finish</li>
<img width="920" height="617" alt="image" src="https://github.com/user-attachments/assets/47ad42ef-3e03-4589-99e7-5529c4fb76ab" />

<li>And now, Kali</li>
<li>unzip the Kali download</li>
<li>you want the file with the .vmx extention (enable file name extentions if you don't see it)</li>
<img width="848" height="152" alt="image" src="https://github.com/user-attachments/assets/59da0a42-cf24-426b-ba5b-c731764b44e9" />
<li>double-click it and it should automatically import and launch in VMware</li>
<img width="1483" height="682" alt="image" src="https://github.com/user-attachments/assets/726e91d4-6122-4fd0-a901-9a55b0011940" />

<li>Now let's finish the Win10 VM setup</li>
<li>select next, install now, no product key. next</li>
<img width="970" height="582" alt="image" src="https://github.com/user-attachments/assets/77d07dd5-eeea-4900-aef9-68f488e9742d" />
<li>select Windows 10 Pro, accept the license, custom install, next</li>
<img width="883" height="536" alt="image" src="https://github.com/user-attachments/assets/b631e8e5-5597-43cb-a6fa-c46eeb5cece2" />
<img width="930" height="463" alt="image" src="https://github.com/user-attachments/assets/324dd86d-ccfb-4c98-a9aa-86b4bca85123" />

<li>While that's booting up, let's now tackle the Ubuntu</li>
<img width="1210" height="598" alt="image" src="https://github.com/user-attachments/assets/2aa3fee7-628a-4671-b403-8fbe1e3d6363" />
<li>except all the defaults and select continue on the storage configurations</li>
<img width="1311" height="642" alt="image" src="https://github.com/user-attachments/assets/96b0f6f9-9d32-4451-b253-b73c91ed3fe6" />
<li>complete your profile</li>
<img width="1336" height="412" alt="image" src="https://github.com/user-attachments/assets/b4fea39d-08ca-4bc5-86a2-a224c270b95a" />
<img width="1328" height="420" alt="image" src="https://github.com/user-attachments/assets/0833ec53-63d4-408b-a853-aded78fc2f23" />
<li>Be sure to install the OpenSSH server</li>
<img width="1217" height="362" alt="image" src="https://github.com/user-attachments/assets/6330d8e5-d4f0-4758-9459-69e567ef1d71" />
<li>and reboot</li>
<img width="1395" height="800" alt="image" src="https://github.com/user-attachments/assets/5635106c-7cfe-4b45-93b3-6a4efcd7d72c" />

<li>And we will do the same for the n8n VM</li>
<img width="1365" height="507" alt="image" src="https://github.com/user-attachments/assets/4c483fbf-bcac-4fd9-b7d6-6e6f56978769" />
<img width="1412" height="418" alt="image" src="https://github.com/user-attachments/assets/fc5f1149-6f39-4824-9a1a-b517fd4f6ba9" />

<li>let's finish the win10 setup</li>
<img width="1182" height="687" alt="image" src="https://github.com/user-attachments/assets/fc0cf9cf-bd2e-4160-94fd-0fc104924c5f" />
<img width="1193" height="596" alt="image" src="https://github.com/user-attachments/assets/80354d4a-4e38-47cd-a5da-3346fdda7c60" />

<li>and also Splunk</li>
<img width="1227" height="625" alt="image" src="https://github.com/user-attachments/assets/a2ad222f-7605-4724-835e-3a708d17a36c" />
<li>hopefully, you notated your text editor with your login details</li>
<img width="1352" height="500" alt="image" src="https://github.com/user-attachments/assets/8e5634eb-d35f-4525-85b1-9ea3103da859" />
<li>make note of the VM's ip</li>
<img width="1075" height="300" alt="image" src="https://github.com/user-attachments/assets/69a76b90-fce1-42c0-9e87-9cc49abe2ede" />
<li>now open command prompt on your host pc and SSH into Splunk</li>
<img width="1237" height="443" alt="image" src="https://github.com/user-attachments/assets/7f7b0852-8dca-4ab4-8a00-374476b6ab99" />
<img width="1088" height="492" alt="image" src="https://github.com/user-attachments/assets/2e01f034-2442-4385-a30b-883bd8989c4a" />
<li>now enter 'sudo apt-get update && sudo apt-get upgrade -y'</li>
<img width="1323" height="630" alt="image" src="https://github.com/user-attachments/assets/95d821da-3992-461f-a754-89283c62f0c0" />














































