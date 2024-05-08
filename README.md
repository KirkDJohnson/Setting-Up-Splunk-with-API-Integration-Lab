<h1>Nessus Vulnerability Scanner Lab </h1>


<h2>Description</h2>
Text
<br />


<h2>Utilities Used</h2>

- <b>Splunk</b> 
- <b>Oracle Virtual Box (VM)</b>
- <b>AbuseIpdb</b>


<h2>Environments Used </h2>

- <b>Windows 10</b> 

<h2>Lab Overview:</h2>

<p align="center">
I began by first creating a Splunk account and downloaded Splunk Enterprise then Splunk Universal Forwarder so my host computer could examine logs and forward them to Splunk. I set up the default listening port and confirmed the hostname on that Splunk has correct hostname.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/b49e3a4e-a154-4bff-8e7f-e645334e601e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/69830ac7-bec3-4e6e-a4b7-1ab5c74e966f"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/6f1cee97-8071-40f8-b62f-2be8b1744c05"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/5a43a5c5-5b39-4628-97d2-2df36db1f5e7"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/3ff8bd55-e479-4272-a025-d7f4b3118d35"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/bd04788d-8944-483e-9c08-48c7e56ec9f7"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
I then downloaded a popular dataset (sample logs) from Splunk Botsv3, and moved the files into the "C:\Program Files\Splunk\etc\apps" have a considerable amount of various logs both benign and malicious to examine.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/c02832d8-3513-491e-b92f-5c051abe7798"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/6a0ba3f5-4286-4d2d-b628-2f77febfc165"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/e12ce2ee-95c4-4228-b267-4436bd02c927"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
For this excersise I focused on IP traffic, seeing how the raw data log, I wanted to enrich the data in a dashboard for easier viewing. So i began fine tuning a Search Processling Language (SPL) query that would provide the appro[rioate context.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/ac4a0fc7-5faf-422a-9d1b-e7c375f74211"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/3e28b01c-4f51-4db4-8a1c-35a1a6a16dcd"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/059ddb41-d605-48a9-8deb-0d5b10f47ac3"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/de46b6a0-c1ed-468c-bd85-5a13de6a279e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
I then created a bashboard and exported the search to the dashboard to visualize the data.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/271a9936-b9b4-4704-9ab5-306950dc52e5"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/d554771f-874e-4034-a3cf-71544bfab56e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
Now that I have data that certain IPs in the logs appear to be malicious/suspicioius due to the amount of traffic generating from them, it would be even better if we can obtain more infoarmtion about the IPs for potentional defensive stragegies. With this in mind, I used AbuseIPDB which helps to"...identify IP addresses that have been associated with malicious activity online", as well provide more information about the IP such as location adn coooridnates. Splunk has an app tht allows API AbuseIPDB to parse the data from the logs once you download it, create an acocunt, and set the API key between the two accounts. <br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/b3ab81f1-69ed-47fc-85ac-7345783df775"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/319e5250-2b0f-4028-bdbc-1eba72b23d2f"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/faad2143-8a2a-4b1f-ade2-bd8a04f43e4f"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
I included the newly installed app into the search as well as removed all IPv6 and private IP andaddresse because they are non-unique and irrelevant to block as you may block proper intranet traffic, so what is left was all public IPv4 addresses. The serach demonstrtares that the App and API were correclty installed and configured and to double check that the data being shown in Splunk was accurate I went to AbuseIPDB's website and another website whois which is very similar in functionality and it confrims taht the data is the same. <br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/0b6f16fc-69ad-4c3b-b41c-61f13516852e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/ae2fb2e3-8a5f-4b45-bea4-23ecf265b507"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/83bb842f-e9c7-45c0-bcfa-82e2960b6746"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
I modified the SPL a little to outpt the count of the country, saved it to the same dashboard and modified the previous dashboard I made to remove the private IP addresses because they were squwling the resuilts and as mentioned before irrelvelnt to block and analyze compraraerd to public IP addresses. And the finished dashboard with the two searches<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/bbc41906-09b2-421c-9018-ebc6e8d048ce"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/bc18a3a6-64c8-460f-a22f-69a6dce54960"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/7d019d56-678d-4388-81a2-10dc016f011e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
Lastly, due to the data showing that traffic from China was the significant part of the malicious traffic, in this scenerio I knew that the there would be no reason from traffic originatibg from China, I made a search just fror Chian traffic with AbuseIPDB and created an alert for it that would send me an emial if traffic origination from China appeared in the Splunk logs so I could further ivestigate whether it to be malicous or not as a SOC Analyst. <br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/5b763418-9772-4a26-a408-83ca98efb69a"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/1d09dd6e-2a06-49eb-b438-57e2bbb553a4"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/fef8945d-9529-4d2c-9f04-ef69310b9da7"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />



<h2>Thoughts</h2>
Text


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
