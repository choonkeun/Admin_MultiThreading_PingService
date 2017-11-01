# MultiThreading_PingService
"PingService" as Windows Service to check all site is working


Version 2.4
-----------

1. Go to "D:\Sample Source\PingService2.3\PingService Setup\PingService Setup\Express\DVD-5\DiskImages\DISK1"

2. Run "PingService Setup.msi"  (you can use "setup.exe" also) to install
   - you can use this to uninstall

3. It will installed into C:\PingService folder
 and the folder will have below files
 - pingservice.exe
---

When program installed, 
if type is "exe" then
    program will registered into Windows Service and run programs that listed at app.config right away
    and PingService.exe will continue to check the program list and they are running or not by every 10 seconds
    and write into the log file(PingService.log) by every 60 minutes
    if one of program of listed at app.config is gone then PingService.exe will restart it.

if type is "http" then
    PingService will connect and download http page and check the result is exist or 404 error
    This is no process execute but only check the results

---
<MonitorServices>
    <ServicesNames>
        <add Name="Ping"       Type="exe"  Interval="60" Path="D:\Sample Source\Ping2.2\Ping\bin\Debug\Ping.exe" />
        <add Name="ftpmonitor" Type="exe"  Interval="60" Path="D:\Sample Source\SFTP-Monitor-V2.5\FTPMonitor\bin\Debug\ftpmonitor.exe" />
        <add Name="homepage"   Type="http" Interval="60" Path="http://192.168.6.49" />
    </ServicesNames>
</MonitorServices>
