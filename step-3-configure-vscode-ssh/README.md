### 🧑‍💻 Remote Coding with Visual Studio Code

Visual Studio Code is a popular code editor that allows developers to work on their code locally or remotely. The "Remote - SSH" extension from Microsoft enables developers to connect to a remote host using the SSH protocol, allowing them to work on their code and run commands directly on the remote host. 

This step will teach you how to configure the extension!

* Make sure the extensions "Remote - SSH" and "Remote - SSH: Editing Configuration Files" is installed in Visual Studio Code.

* Open the Command Palette (Ctrl + Shift + P) and type "Remote-SSH: Open SSH Configuration File" to open the ssh config file.

* Add a new entry for the remote host you want to connect to, using the format "Host [hostname]".

* Under the host entry, add the "User" and "HostName" options, specifying the username and IP or hostname of the remote host.

* Add "IdentityFile" option, specifying the path to your private ssh key that you have genereated in [Step 1: Prerequisites](/step-1-prerequisites/).


* Your final configuration should look something similar:

```bash

Host ec2-workshop
    User ubuntu
    HostName ec2-54-169-196-182.ap-southeast-1.compute.amazonaws.com
    IdentityFile "C:\Users\Hrittik\Desktop\aws-sgp\ssh_workshop"

```

* Once you have your ssh configuration file set up, open the Command Palette again and type "Remote-SSH: Connect to Host" and select the host you want to connect to.

![](https://i.imgur.com/3ToaMyO.png)

* Move forward by clicking on Connect and choosing the system as Linux!

* Once connected, you will be able to open and edit files on the remote host, and run commands on the remote host using the integrated terminal.

Terminal can be accesed from the options to manipulate the file system and carry out operations!


Now you're ready to go to [Step 4!](/step-4-vscode-extras/) 🚀