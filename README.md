<h1>Splunk Installation and API Configuration Lab</h1>


<h2>Description</h2>
In this lab, my first goal was to install and configure Splunk Enterprise and Universal Forwarder on a Windows 10 Virtual Machine. Following this setup, I downloaded a dataset named BotsV3, consisting of millions of diverse logs from various sources, to analyze within Splunk. Focusing specifically on IP traffic, I aimed to identify potentially malicious activity. Beginning with fine-tuning a Search Processing Language (SPL) query, I generated a table showing the top IP addresses making connections. However, a significant portion of the traffic originated from private IP addresses, indicating a brute force probing attack targeting hosts with open ports. To enhance visualization and make it more understandable, I saved the search to a dashboard. Seeking additional information about the IPs, I turned to the AbuseIPDB website, which has a catalog of IPs associated with online malicious activities, along with location data for further identification. AbuseIPDB had a Splunk app whcih I integrated into my account with Splunk via an API token, enabling seamless access to the AbuseIPDB through Splunk's search and processing functions. Upon confirming the successful installation of the app, I modified my previous search to include the AbuseIPDB database, enriching the log data further. The analysis revealed that the majority of malicious traffic originated from China. I exported the search that showed the top countries where the malicious IPs originated from to the same dashboard as earlier. Lastly, I refined my SPL query to exclusively display traffic originating from China and set up an alert to run hourly, notifying me via email of any Chinese-originated traffic detected in Splunk. This prepared me for potential future analysis in a Security Operations Center (SOC) Analyst role.
<br />


<h2>Utilities Used</h2>

- <b>Splunk</b> 
- <b>Oracle Virtual Box (VM)</b>
- <b>AbuseIPDB</b>


<h2>Environments Used </h2>

- <b>Windows 10</b> 

<h2>Lab Overview:</h2>

<p align="center">
"I began by creating a Splunk account, followed by downloading Splunk Enterprise and then Splunk Universal Forwarder. This allowed my host machine to examine logs and forward them to Splunk. I set up the default listening port and confirmed the hostname that Splunk had found was correct.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/b49e3a4e-a154-4bff-8e7f-e645334e601e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/69830ac7-bec3-4e6e-a4b7-1ab5c74e966f"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/6f1cee97-8071-40f8-b62f-2be8b1744c05"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/5a43a5c5-5b39-4628-97d2-2df36db1f5e7"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/3ff8bd55-e479-4272-a025-d7f4b3118d35"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/bd04788d-8944-483e-9c08-48c7e56ec9f7"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
I then downloaded a popular dataset (sample logs) from Splunk called: Botsv3. Once it was downlaoded and unpacked, I moved the files into "C:\Program Files\Splunk\etc\apps". I chose to do this because this dataset has a considerable amount of various logs both benign and malicious to examine compared to generating them on my host machine which I have done in other labs.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/c02832d8-3513-491e-b92f-5c051abe7798"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/6a0ba3f5-4286-4d2d-b628-2f77febfc165"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/e12ce2ee-95c4-4228-b267-4436bd02c927"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
For this excercise I focused on IP traffic. I wanted to transform the raw data in the logs to something more visual and quickly understandable. So I began fine tuning a Search Processing Language (SPL) query that would provide the approprioate context on the given IP addresses in the logs and their connections.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/ac4a0fc7-5faf-422a-9d1b-e7c375f74211"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/3e28b01c-4f51-4db4-8a1c-35a1a6a16dcd"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/059ddb41-d605-48a9-8deb-0d5b10f47ac3"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/de46b6a0-c1ed-468c-bd85-5a13de6a279e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
Once I was satisfied with the query, I then created a dashboard and exported the search to the dashboard to visualize the data.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/271a9936-b9b4-4704-9ab5-306950dc52e5"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/d554771f-874e-4034-a3cf-71544bfab56e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
The logs now reveal that certain IP addresses appear to be malicious/suspicioius due to the amount of traffic generated from them. However, it would be even more optimal if we could obtain further information about the IPs for potentional defensive strategies With this in mind, I used AbuseIPDB which helps to"...identify IP addresses that have been associated with malicious activity online", as well provide more information about the IP such as location and coooridnates. Splunk has an AbuseIPDB app that when configured with an API token linking both accounts, AbuseIPDB's database can be accessed through SPL in Splunk.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/b3ab81f1-69ed-47fc-85ac-7345783df775"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/319e5250-2b0f-4028-bdbc-1eba72b23d2f"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/faad2143-8a2a-4b1f-ade2-bd8a04f43e4f"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
I included the newly installed app into the search as well as removed all IPv6 and private IP addresses because they are non-unique and irrelevant to block as you may block proper intranet traffic; leaving only public IPv4 addresses. The serach confirms that the App and API were correctly installed and configured. I then made sure that the data being shown in Splunk was accurate so I went to AbuseIPDB's website and another website "whois" which is very similar in functionality and it confirms that the data is the same. <br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/0b6f16fc-69ad-4c3b-b41c-61f13516852e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/ae2fb2e3-8a5f-4b45-bea4-23ecf265b507"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
  <img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/83bb842f-e9c7-45c0-bcfa-82e2960b6746"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
I modified the SPL query slightly to output the count of the country, saved it to the same dashboard and modified the previous dashboard I made to remove the private IP addresses. The dashboard now contains the top 20 IP addresses that made the most connections and those IP addresses filtered by country.<br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/bbc41906-09b2-421c-9018-ebc6e8d048ce"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/bc18a3a6-64c8-460f-a22f-69a6dce54960"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/7d019d56-678d-4388-81a2-10dc016f011e"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />
Lastly, due to the data showing that traffic from China was the significant part of the malicious traffic, in this scenario I knew that the there would be no reason for traffic originating from China. I again modified the search slightly to only show traffic from China with AbuseIPDB and created an alert for it that would send me an email if traffic matched the alert appeared in the Splunk logs so I could further investigate whether it to be malicious as a SOC Analyst. <br/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/5b763418-9772-4a26-a408-83ca98efb69a"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/1d09dd6e-2a06-49eb-b438-57e2bbb553a4"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<img src="https://github.com/KirkDJohnson/Setting-Up-Splunk-with-API-Integration-Lab/assets/164972007/fef8945d-9529-4d2c-9f04-ef69310b9da7"  height="80%" width="80%" alt="Splunk Installation and Configuration Lab"/>
<br />
<br />



<h2>Thoughts</h2>
This lab proved highly beneficial as it offered me hands-on experience in a part of Splunk I hadn't previously explored: downloading and installing apps within Splunk. While I had configured Splunk in the past, this exercise served as valuable practice, improving my proficiency with the process. The lab also increased my proficiency in Search Processing Language (SPL), Splunk's search language, is advantageous given its popularity as a Security Information and Event Management (SIEM) solution. Moreoceer, I discovered a new search command, distinct_count, which efficiently calculates the number of unique values for fields. Unlike my previous methods using deduplicate and count, this new command is more straightforward, resulting in faster search response times. However, the primary takeaway from this lab was the experience with the configuration of a Splunk app using an API token and effectively utilizing it within the search function. After reviewing the README for the AbuseIPDB app I installed, the process became clear and streamlined. Overall, this lab significantly expanded my comprehension and familiarity with Splunk, proving to be a valuable learning experience.


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
