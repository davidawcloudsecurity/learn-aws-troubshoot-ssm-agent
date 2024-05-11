## How To Troubleshoot SSM Agent After Clone Snapshot
View the logs first
```ruby
Go to C:\Program Files\Amazon\SSM
Make a copy of the seelog.xml.template file. Change the name of the copy to seelog.xml. The file is located in the following directory.

%PROGRAMFILES%\Amazon\SSM\seelog.xml.template

Edit the seelog.xml file to change the default logging behavior. Change the value of minlevel from info to debug, as shown in the following example.

<seelog type="adaptive" mininterval="2000000" maxinterval="100000000" critmsgcount="500" minlevel="debug">

Locate the following entry.

filename="{{LOCALAPPDATA}}\Amazon\SSM\Logs\{{EXECUTABLENAME}}.log"

Change this entry to use the following path.

filename="C:\ProgramData\Amazon\SSM\Logs\amazon-ssm-agent.log"

Locate the following entry.

filename="{{LOCALAPPDATA}}\Amazon\SSM\Logs\errors.log"

Change this entry to use the following path.

filename="C:\ProgramData\Amazon\SSM\Logs\errors.log"

Restart SSM Agent using the following PowerShell command in Administrator mode.

Restart-Service AmazonSSMAgent
```
```ruby
Import-Module C:\ProgramData\Amazon\EC2-Windows\Launch\Module\Ec2Launch.psm1; Add-Routes
```

## Resource
https://repost.aws/knowledge-center/ec2windows-resolve-ssm-agent-failure

https://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent-status-and-restart.html

https://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent-logs.html
