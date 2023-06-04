## Setup


### Install
Install Postman with Choco in an admin panel
```bash
choco install postman
```

### Install Postman CLI
```bash
powershell.exe -NoProfile -InputFormat None -ExecutionPolicy AllSigned -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://dl-cli.pstmn.io/install/win64.ps1'))"
```

### Install Newman
```bash
npm install -g newman
```