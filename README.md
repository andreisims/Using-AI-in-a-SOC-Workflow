# Using AI in a SOC Workflow

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

<li>Back to the windows installation</li>
<img width="1207" height="655" alt="image" src="https://github.com/user-attachments/assets/4c67241d-590b-45b3-9a05-eea7b46933af" />
<li>select the personal use option, then offline account, and then limited experience</li>
<img width="1102" height="512" alt="image" src="https://github.com/user-attachments/assets/960a9baa-2d2b-49c5-a62b-408d4fffbac5" />
<img width="1145" height="713" alt="image" src="https://github.com/user-attachments/assets/2552ebd9-a35a-460c-affd-2244d2e4cc16" />
<li>create your personal profile, details can be fictional but remember/write down the password</li>
<img width="1127" height="710" alt="image" src="https://github.com/user-attachments/assets/c3de7b26-7803-4f2a-931b-c105d84761b9" />
<img width="1155" height="652" alt="image" src="https://github.com/user-attachments/assets/1d01a526-500e-4909-a968-acd1e5f3f26c" />
<li>skip the customization and Cortana options</li>
<img width="1121" height="658" alt="image" src="https://github.com/user-attachments/assets/3f325959-5fd0-479f-995c-597a7c0f35ce" />
<img width="1192" height="753" alt="image" src="https://github.com/user-attachments/assets/f25e4865-c858-4bd1-ac8f-e6587c8fc217" />

<li>Let's check on the n8n server (Ubuntu)</li>
<img width="1531" height="576" alt="image" src="https://github.com/user-attachments/assets/c9a6c18d-0d73-4129-a43c-b5478410d6ac" />
<li>Ater logging in, we will enter the same 'sudo apt-get update && sudo apt-get upgrade -y' commands</li>
<img width="1195" height="388" alt="image" src="https://github.com/user-attachments/assets/299023f0-1553-4811-8ed8-1e1b65801790" />
<li>Our n8n server is now up to date</li>

<li>Back on windows, go to the remote desktop settings</li>
<img width="1132" height="518" alt="image" src="https://github.com/user-attachments/assets/69e3ab32-d75e-4855-8f9e-d55ecc30c66f" />
<li>enable the remote desktop setting</li>
<img width="963" height="487" alt="image" src="https://github.com/user-attachments/assets/c6fca97b-3088-4696-9df1-9ce77f2686c1" />
<li>open the command prompt (cmd)</li>
<img width="1221" height="812" alt="image" src="https://github.com/user-attachments/assets/ebd9e491-2707-455d-b6df-44e73e6fd7cc" />
<li>type ipconfig to obtain the win10 IP address</li>
<img width="943" height="380" alt="image" src="https://github.com/user-attachments/assets/c2e1030d-ddf7-4937-a149-976fe6cdfeba" />
<li>notate it and enter ifconfig on the n8n server to get it's IP</li>
<img width="710" height="197" alt="image" src="https://github.com/user-attachments/assets/1c1b31a2-17be-4cce-9f1c-ec706cb5fc53" />
<li>PERSONAL PREFERENCE: you can either use RDP to connect to the windows machine or work directly in the VM. I'm using RDP on my host machie to connect it</li>
<li>enter the vm's IP and then log in</li>
<img width="716" height="340" alt="image" src="https://github.com/user-attachments/assets/b0b08d62-c0ac-49f8-809a-9da24ab68be5" />
<img width="626" height="461" alt="image" src="https://github.com/user-attachments/assets/8e0d7658-0ac0-4327-b109-b0cedd70b456" />
<img width="536" height="507" alt="image" src="https://github.com/user-attachments/assets/d32e245d-50a8-493b-995b-98c5862f5e9e" />

<li>Let's take a snapshot of the working devices</li>
<li>select 'VM', Snapshot, Take snapshot</li>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9d626851-82b7-454c-84ea-0f07f47efcd7" />
<li>provide a name for the snapshot, and select take snapshot</li>
<img width="887" height="455" alt="image" src="https://github.com/user-attachments/assets/27d20e0a-8595-4385-8481-8dd935ada51b" />

<li>now let's SSH into splunk VM from the command line (CMD) so that we can download and install splunk https://www.splunk.com/</li>
<img width="1157" height="621" alt="image" src="https://github.com/user-attachments/assets/b92c4b33-767e-4e3f-a678-157eae00388e" />
<li>sign in or create an account</li>
<img width="1202" height="487" alt="image" src="https://github.com/user-attachments/assets/1bb223fd-874c-4a84-ba3d-ceef14e51aff" />
<li>go to Trials and Downloads> Splunk Enterprise> start trial</li>
<img width="1147" height="522" alt="image" src="https://github.com/user-attachments/assets/dd7e9109-a7b0-4884-bd3e-6ab3c2e45777" />
<li>select the Linux package (.deb file) using the wget link</li>
<img width="1297" height="421" alt="image" src="https://github.com/user-attachments/assets/fe2bcb53-8310-4701-8526-c10304e6bf59" />
<li>copy and paste it into the command line</li>
<img width="1513" height="175" alt="image" src="https://github.com/user-attachments/assets/f6d3b49d-44a5-40cc-b180-a2d5a23d708c" />
<img width="1465" height="318" alt="image" src="https://github.com/user-attachments/assets/2d379cf9-1ff3-4b7e-a12a-1adfbb555f0a" />
<li>Success!</li>
<img width="1092" height="242" alt="image" src="https://github.com/user-attachments/assets/f6ab74d7-2f41-477a-b067-7ab08fb918d9" />
<li>now that it's downloaded, let's install it: sudo dpkg -i splunk-10.0.2-e2d18b4767e9-linux-amd64.deb</li>
<img width="1222" height="218" alt="image" src="https://github.com/user-attachments/assets/a7e5e7b8-4a37-443c-9982-edd773bf8c08" />
<li>we can resolve this error</li>
<img width="1073" height="76" alt="image" src="https://github.com/user-attachments/assets/9f7d3857-2c07-4ac8-8dd1-4aa60a1ae08b" />
<li>go to the splunk directory (cd /opt/splunk/) and the 'll'</li>
<img width="1305" height="521" alt="image" src="https://github.com/user-attachments/assets/35d7bea2-5ae9-4f02-8397-3907afd0bcc5" />
<li>we need to change the user from splunk (sudo -u splunk bash), then change back to the splunk directory (cd /opt/splunk/), then to the bin directory (cd bin), and then 'ls' </li>
<img width="1525" height="766" alt="image" src="https://github.com/user-attachments/assets/31deb881-ae39-4853-b477-875dc6fa16e4" />
<li>now type: ./splunk start</li>
<img width="1295" height="672" alt="image" src="https://github.com/user-attachments/assets/12d4e010-3dbc-48b9-a180-2076eb6360c5" />
<li>hold the space key until you get to the end of the file and select 'y' for yes</li>
<img width="1002" height="307" alt="image" src="https://github.com/user-attachments/assets/42116767-bcb8-4592-919c-f894fce5c872" />
<li>we will use the same username and password, for simplicity</li>
<img width="1053" height="156" alt="image" src="https://github.com/user-attachments/assets/fbe54c78-eab7-45f7-81df-877b987c3694" />
<img width="1202" height="627" alt="image" src="https://github.com/user-attachments/assets/62242199-34d8-40a8-b218-de617d24e549" />
<li>the last option we need to address is to ensure that splunk starts on reboot. Type 'cd bin' then 'ls'</li>
<img width="1436" height="752" alt="image" src="https://github.com/user-attachments/assets/74b319d5-1bb6-4fe9-9937-394c8fec341b" />
<li>type 'sudo ./splunk enable boot-start -user splunk'</li>
<img width="1210" height="148" alt="image" src="https://github.com/user-attachments/assets/82df6d25-1c1e-45bf-a9fb-4d2026516bde" />
<li>with that, splunk should now start whenever the VM is started. We should also be able to access the GUI using splunk's IP and the default port of 8000. Viola!</li>
<img width="1766" height="780" alt="image" src="https://github.com/user-attachments/assets/ec1243c8-580a-446d-af29-72e6ebf97a8c" />
<li>Now sign in with your Splunk username and password</li>
<img width="1873" height="817" alt="image" src="https://github.com/user-attachments/assets/eda36d89-7ad7-443a-80b9-a267242e4a35" />
<li>Let's make some configuration changes: Settings> Forwarding and Receiving> Configure Receiving> New Receiving Port> and enter the default port of 9997. click save</li>
<img width="1075" height="311" alt="image" src="https://github.com/user-attachments/assets/91ce9751-7e89-4912-a5bd-e543cdee92ed" />
<img width="1676" height="233" alt="image" src="https://github.com/user-attachments/assets/51b11bbe-8aa2-4d40-b776-06bc183bc179" />
<li>now Settings> Indexes> click got it> New Index</li>
<img width="850" height="816" alt="image" src="https://github.com/user-attachments/assets/d92769dd-104f-4abb-adf3-48d7db7ac47d" />
<li>Name it, then save it</li>
<img width="886" height="826" alt="image" src="https://github.com/user-attachments/assets/81f56a92-a455-4dca-a85d-a2c7b26c0160" />
<li>Lastly: Apps> Find More Apps> then search for Windows Events</li>
<img width="1611" height="581" alt="image" src="https://github.com/user-attachments/assets/4e4b5526-a0bd-49c4-a904-19cd539d1906" />
<li>select install for the Splunk Add-on for Microsoft Windows and then sign in with your Splunk account details (the one used to download Splunk from its website)</li>
<img width="785" height="337" alt="image" src="https://github.com/user-attachments/assets/5687a636-4e3a-4d3d-a840-7da77efca38a" />
<li>with the updates completed, take a snapshot for the Splunk VM (VM> Snapshot> take snapshot)</li>

<li>Next, let's configure the Windows VM to send its telemetry to Splunk. Open Remote Desktop on your host PC, connect to the Windows VM, and then ping the Splunk VM (success! Windows can reach Splunk)</li>
<img width="1295" height="507" alt="image" src="https://github.com/user-attachments/assets/fec384b3-88c1-44d5-b088-e8a5bece5a0e" />
<li>From the splunk.com site> Trials and Downloads> Universal Forwarder> start download</li>
<img width="1386" height="532" alt="image" src="https://github.com/user-attachments/assets/78ff4c52-be63-4a8e-a262-b6610b1eb375" />
<li>select 'Windows 10, 11
Windows Server 2019, 2022, 2025'</li>
<li>Download now</li>
<img width="1337" height="526" alt="image" src="https://github.com/user-attachments/assets/de403799-474b-4c0b-89e1-e7012350e336" />
<li>copy download from your host PC and paste it in the Windows VM</li>
<img width="1004" height="141" alt="image" src="https://github.com/user-attachments/assets/b5111c99-0ade-456b-9eed-0c10fa9cfe43" />
<img width="1287" height="487" alt="image" src="https://github.com/user-attachments/assets/b4595eac-f73b-44f7-9986-39d35fbe5f94" />
<li>open the forwarder and check the license agreement and make sure the 'on-premise' instance is selected. Next</li>
<img width="1108" height="557" alt="image" src="https://github.com/user-attachments/assets/4290feeb-e953-420d-8666-455f7c9bb3d3" />
<li>uncheck the 'random password' option and then create a profile. Next</li>
<img width="991" height="512" alt="image" src="https://github.com/user-attachments/assets/3d08fefe-a349-44a2-9a46-7767ed0adbf4" />
<li>click next for the Deployment Server (we dont have one). Enter the Splunk VM IP address for the Receiver Indexer and the default port of 9997. Next, then install, and Finish</li>
<img width="1002" height="517" alt="image" src="https://github.com/user-attachments/assets/b4271d02-21c8-42b1-9e0b-70ce3345825d" />
<img width="1137" height="543" alt="image" src="https://github.com/user-attachments/assets/fa46ad92-4329-40fc-b457-48d19c6593d1" />
<li>on the Windows VM, go to This PC> the C: drive> Program Files> Splunk Universal Forwarder> Continue> etc> system> local</li>
<img width="1463" height="365" alt="image" src="https://github.com/user-attachments/assets/59160b7b-bfe2-4a19-8614-c17a8aa4ce38" />
<li>We currently do not have an inputs.conf file (which is needed for the windows VM to send telemetry to Splunk)</li>
<li>link to the configurations file: https://drive.google.com/file/d/1-qYp4oCrT1BqhG1oaprQfkFhgFIHiWEm/view. It can also be viewed below</li>
<img width="906" height="618" alt="image" src="https://github.com/user-attachments/assets/951afced-4621-4b5f-b6d2-8e9b7795288b" />
<li>be sure to use your index name everywhere you see 'index = mydfir-project', then paste into the local directory</li>
<img width="1540" height="440" alt="image" src="https://github.com/user-attachments/assets/cb811f81-f7bd-4b34-bbf1-d958ce5fd9b3" />
<li>also on the Windows VM: go to Services> run as administratior> SplunkForwarder</li>
<img width="1561" height="537" alt="image" src="https://github.com/user-attachments/assets/cb995398-7ca7-4468-a519-f77195d3a2cf" />
<li>double-click> 'Log on' tab, the select 'Local System account'. Apply, then OK</li>
<img width="1106" height="463" alt="image" src="https://github.com/user-attachments/assets/1bd2e936-ea8c-4245-812a-67baebd2bed5" />
<li>now right-click and restart the SplunkForwarder</li>
<img width="1207" height="413" alt="image" src="https://github.com/user-attachments/assets/5e8a9ddf-684e-48de-b114-a27d9da55591" />

<li>Let's confirm if the Windows VM is now sending telemetry to Splunk. go to the splunk dashboard> Apps> Search and Reporting> skip the Welcome message> then type 'index= (your index name here)'. keep the 24hr time range option and click magnifying glass</li>
<img width="1906" height="206" alt="image" src="https://github.com/user-attachments/assets/3e543b68-6de0-41d8-903f-b224f0b61d4c" />
<li>Viola! Telemetry</li>
<img width="1783" height="767" alt="image" src="https://github.com/user-attachments/assets/4661c6b4-283a-41fd-8738-994a154461d9" />

<li>Now for the part you have all been waiting for: n8n</li>
<li>SSH into the n8n/Ubuntu server</li>
<img width="1160" height="741" alt="image" src="https://github.com/user-attachments/assets/90222020-267b-4b0f-8669-ef245d0ff320" />
<li>to install it, we'll be using Docker. Type 'sudo apt install docker.io', and enter 'y'</li>
<img width="1171" height="386" alt="image" src="https://github.com/user-attachments/assets/c3b0c965-221f-4bc5-a995-8ab731d39675" />
<img width="1281" height="565" alt="image" src="https://github.com/user-attachments/assets/8dab4e89-2561-4e94-a0fc-d2776ec51efd" />
<li>and just to be safe, let's do 'sudo apt-get update && sudo apt-get upgrade -y'. Then 'sudo apt install docker-compose'</li>
<img width="1521" height="350" alt="image" src="https://github.com/user-attachments/assets/98b01a18-10a9-4327-9319-5c591844e4c9" />
<li>now we can install n8n. Make a new directory: mkdir n8n-compose. Then change into the new directory: cd n8n-compose</li>
<img width="1342" height="192" alt="image" src="https://github.com/user-attachments/assets/577a702d-63bc-4615-aa38-13cae9ec1225" />
<li>now create the docker-compose file: sudo nano docker-compose.yaml</li>
<img width="1091" height="463" alt="image" src="https://github.com/user-attachments/assets/77bf5117-c6a8-4dec-bc91-27b47e323b52" />
<li>be sure to enter the IP address for your n8n/Ubuntu VM, and that the tabs are aligned. Save and exit nano</li>
<li>now let's pull a docker image for n8n: sudo docker-compose pull</li>
<img width="1002" height="278" alt="image" src="https://github.com/user-attachments/assets/e534a615-9387-499e-95d8-7a50ba4d9140" />
<li>and now: 'sudo docker-compose up -d', so that we can access our n8n instance</li>
<img width="1001" height="145" alt="image" src="https://github.com/user-attachments/assets/180e82ea-fb19-45a0-9515-ec3f11771966" />
<li>in a new browser, type your n8n IP address followed by port 5678</li>
<li>FAILURE TO LAUNCH!</li>
<img width="1480" height="772" alt="image" src="https://github.com/user-attachments/assets/dca02942-7534-4e56-a309-1b836b4fd125" />
<li>So let's do some troubleshooting.</li>
<li>Is there a firewall blocking access? Type: sudo ufw status</li>
<img width="938" height="132" alt="image" src="https://github.com/user-attachments/assets/b5bc8515-8664-43e9-bf17-40958004c97d" />
<li>files and permissions check. Type: ll</li>
<img width="1206" height="212" alt="image" src="https://github.com/user-attachments/assets/be46379f-9751-4001-82f3-b032afc4fd5c" />
<li>The permissions for the n8n.data file is under root. So we'll change that. Type: sudo chown -R 1000:1000 n8n_data/</li>
<img width="1097" height="203" alt="image" src="https://github.com/user-attachments/assets/6043d11b-ab32-4182-8880-943b0ecfb710" />
<li>now let's essentially restart it. Type: sudo docker-compose down. Then sudo docker-compose up -d</li>
<img width="1012" height="183" alt="image" src="https://github.com/user-attachments/assets/10823225-f35a-4109-8e51-5d9e62d4d268" />
<li>and reload the page.....GOOOOOAAAAAAAALLLLL!</li>
<img width="1760" height="860" alt="image" src="https://github.com/user-attachments/assets/14cf3357-c08a-4759-a24b-c9a664a962f9" />
<li>complete the form and all the information can be fictional. Just remember the password</li>
<img width="902" height="640" alt="image" src="https://github.com/user-attachments/assets/784be2eb-c643-42d9-b3d7-f832686d90d1" />
<li>and again, enter anything that you like</li>
<img width="891" height="655" alt="image" src="https://github.com/user-attachments/assets/fc9781fd-08cc-43fc-9c77-a8999d847506" />
<img width="963" height="911" alt="image" src="https://github.com/user-attachments/assets/5d9946ad-eba9-4c63-bc15-6e9b5f1629e1" />

### Create an Alert in Splunk that the n8n Webhook Can Catch
<li>Rollback protocol first, take a snapshot of n8n</li>
<img width="1372" height="605" alt="image" src="https://github.com/user-attachments/assets/e8bae620-0d66-4f05-b9f5-ac21d7a1c481" />
<li>now let's create the alert. Go to the Splunk dashboard and create an alert for Brute Force attempts</li>
<li>create a new search by adding EventID=4625 to the existing search and click the magnifying glass</li>
<li>no results</li>
<img width="1907" height="317" alt="image" src="https://github.com/user-attachments/assets/fdb539aa-3d22-4dbd-9bef-2e1900c67adc" />
<li>Troubleshooting: either we have not generated any brute force attempts yet or the fieldname is incorrect</li>
<li>Test the fieldname: 4624 (successful logon) should generate data but no results within the last 24 hours</li>
<img width="1900" height="323" alt="image" src="https://github.com/user-attachments/assets/27bed893-dcca-4b7c-8ce1-f3d21326b981" />
<li>Let's do a deep dive: remove the EventID and press enter. We are now getting event details</li>
<img width="1897" height="785" alt="image" src="https://github.com/user-attachments/assets/9f12b741-4943-44ff-8289-821fff1fb82a" />
<li>Let's expand the first event to see the details and fields</li>
<img width="1637" height="810" alt="image" src="https://github.com/user-attachments/assets/28867505-c129-4944-bf51-919b791dec35" />
<li>we're looking for the field that contains the event codes. VIOLA! It's EventCode and not EventID</li>
<img width="1475" height="478" alt="image" src="https://github.com/user-attachments/assets/68a22e05-86da-45ea-a167-efa1a46bb90c" />
<li>now update the search using EventCode=4625, and it is case-sensitive. And VIOLA!!</li>
<img width="1887" height="852" alt="image" src="https://github.com/user-attachments/assets/bf22b0c0-32a2-45e1-bbfc-28e405aa609c" />
<li>And let's double check by generating some failed login attemps via RDP (4 times). I was considering using Kali Linux but that might be too resource intensive right now. We can always use it later for additional tasks</li>
<img width="828" height="455" alt="image" src="https://github.com/user-attachments/assets/3b868441-22a1-4317-9ad8-2e4fefd5b92a" />
<li>and here are those brute force attempts</li>
<img width="1681" height="770" alt="image" src="https://github.com/user-attachments/assets/f4ef9e67-d9a8-4535-8e44-a5c18131347c" />
<li>now let's clean up the visualization by entering the following in the search field. And this will only work after installing the Splunk Add-on for Microsoft Windows app</li>
<img width="1671" height="576" alt="image" src="https://github.com/user-attachments/assets/9e39f63c-cd65-4dc5-a227-3c1f2205c021" />
<li>Now save this alert. Click Save As> Alert> provide a name for it. You can keep all the defaults but set the schedule to run on chron. Replace the Expression (0 6 * * 1) to all asterisks (* * * * *) so that it'll every minute. Under Trigger Actions, select Add to Triggered Alerts and Webhook. For the webhook URL, use the n8n. To do so, go to n8n dashboard and click 'Start from Scratch', Add First Step, then search for Webhook</li>
<img width="1817" height="576" alt="image" src="https://github.com/user-attachments/assets/3fc1f12a-73b1-4225-a52d-da3b6a2a6462" />
<li>select Webhook (starts the workflow...). Change the http method from GET to POST, then copy and paste the URL into Splunk Alert</li>
<img width="1566" height="763" alt="image" src="https://github.com/user-attachments/assets/6832bf91-051a-46e6-adbc-a40e4609ded5" />
<img width="1066" height="842" alt="image" src="https://github.com/user-attachments/assets/bae9d4f0-e2e0-4b98-bac8-d70e047292e5" />
<li>click Save and View Alert</li>
<img width="1292" height="295" alt="image" src="https://github.com/user-attachments/assets/61f1c6c6-ed7d-4b5b-b75f-bd6188dea832" />
<li>back to n8n and click Listen for Test Event......and TOUCHDOWN!!</li>
<img width="1805" height="685" alt="image" src="https://github.com/user-attachments/assets/073061e0-fa31-4d9b-8ae1-bb668042b306" />

### Now Let's Build The Automation in n8n
<li>ALERT: credits are needed for OpenAI</li>
<li>First: let's disable the alert for now in Splunk</li>
<img width="937" height="272" alt="image" src="https://github.com/user-attachments/assets/834c411d-d59f-4b1e-9043-623072c0a77f" />
<li>On n8n, the workflow has been pinned so that we can continue to use so that we don't have to retrigger the workflow</li>
<img width="1188" height="465" alt="image" src="https://github.com/user-attachments/assets/ec02dbb4-9dcd-479f-bbab-74cdf6be48cb" />
<li>In the upper-right corner, click the + and search for chatgpt</li>
<img width="1797" height="666" alt="image" src="https://github.com/user-attachments/assets/053067a7-58e0-457a-b038-aaa7c33fb5b0" />
<li>click openAI> message a model> create new credential</li>
<img width="1346" height="615" alt="image" src="https://github.com/user-attachments/assets/026b9ac0-eb46-4708-9600-028be8a5d77f" />
<li>For that, go to https://openai.com/ and API Platform. Then sign-in or sign-up</li>
<img width="1760" height="704" alt="image" src="https://github.com/user-attachments/assets/eca8c38b-5d56-4595-b021-fb11d0749d43" />
<img width="1895" height="891" alt="image" src="https://github.com/user-attachments/assets/4e588b46-be37-4927-a771-f4817e159214" />





























































































































































