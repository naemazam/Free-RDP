# Free-RDP
Make your Own Free RDP using GitHub 



### Create a Github Reposatory

you can name it any name 

### Goto Settings 

1. Go to > Secrets and Variables > Select "Action"
2. Go to your Ngrock Profile > Copy Your Auth Code 
3. Click "New Repository Secrets" > Type Name "NGROK_AUTH_TOKEN" > Copy your Ngrock Profile your Ngrock Profile

 





## Run Locally

Clone the project

```bash
  name: CI


on: [push, workflow_dispatch]


jobs:

  build:


    runs-on: windows-latest


    steps:

    - name: Download

      run: Invoke-WebRequest https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows-amd64.zip -OutFile ngrok.zip

    - name: Extract

      run: Expand-Archive ngrok.zip

    - name: Auth

      run: .\ngrok\ngrok.exe authtoken $Env:NGROK_AUTH_TOKEN

      env:

        NGROK_AUTH_TOKEN: ${{ secrets.NGROK_AUTH_TOKEN }}

    - name: Enable TS

      run: Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0

    - run: Enable-NetFirewallRule -DisplayGroup "Remote Desktop"

    - run: Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1

    - run: Set-LocalUser -Name "runneradmin" -Password (ConvertTo-SecureString -AsPlainText "P@ssw0rd!" -Force)

    - name: Create Tunnel

      run: .\ngrok\ngrok.exe tcp 3389




```

### Go To Action 

1. Click "Setup Workflow" 
2. Click "Create main.yml" , click "Build"
3. ## User & Password 

Username: 

Password: 
## Run RDP

Download "Remote Desktop "

