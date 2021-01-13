# Azure AD Application Proxy Connector - Data Collector Script

The purpose of the Data Collector Script is to collect all the data that might be required to troubleshoot the issue you reported to the Microsoft Support on an efficient way. This Data Collector Script collects the following information:

- Registry keys (SCHANNEL, WinHTTP)
- Azure AD Application Proxy service trace
- Network Capture, information about the network configuration like IPCONFIG /ALL etc.
- MSInfo32
- Extended Traces (WinHttp, Schannel, DCLoc, Kerberos/Ntlm)
- Eventlogs (System, Security, Application, Azure AD Application Proxy related logs, CAPI)
- List of certificates in the certificate stores
- Group policy result
- Information about the patch level of the server
- Adding the -ServiceTraceOn parameter, the service trace will be collected. This restarts the service!

If you have any concerns or would like to know more details about the data the script collects, please don't hesitate to contact us and don't start the data collection.

1. Download the AADAP_DataCollectorv9.zip file and create a folder on the machine(s) where the connector is running. Example: C:\tracing
2. Copy the file to that folder on the server(s). Decompress the file. You should see the files: AAD-AP-tracingV9.ps1, AppProxyTrace.cmd, tracelog.exe, AgentConstants.ps1,   ConfigureAgentLogging.ps1.

Note: The script will capture multiple traces in circular buffers. It will use a temporary folder under the path you provide (Example: C:\tracing\temporary). The temporary folder will be compressed and .zip file left in the path file you selected. Please ensure that you have at least 5 GB free space on the hard drive where the tracing folder stored. Please don't kill or force the script to stop. If something went wrong, please wait until the script has finished, close the Powershell window and start the steps from the beginning.

3. Open a PowerShell console with elevated privileges in all the machines which is running AAD-AP, navigate to the C:\tracing folder, and execute .\AAD-AP-tracingV9.ps1. Important: Provide an absolute Path to the script (like "C:\tracing" and not just "tracing" or ".\tracing")
4. The script will prepare itself to start capturing. When you have the script in this prompt in all the servers, just hit any key to start collecting data in all of them. It will then display another message to inform you that it's collecting data. It will wait for another key to be pressed to stop the capture.
5. Perform the steps to REPRODUCE THE ISSUE. Please do this as quickly as you can.
6. When reproduced, hit any key to stop the capture. It will take several minutes and some popup windows will appear.
7. After the scripts finish, please upload the data to the workspace.
