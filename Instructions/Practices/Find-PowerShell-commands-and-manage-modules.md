# Practice: Find PowerShell commands, get help, and manage modules

## Required VMs

* VN1-SRV1
* CL1

## Task

On CL1, find a command to create a new local user and display the help for it. Display the help for the command syntax of PowerShell. Install the PSWindowsUpdate PowerShell module in the Scope of the current user.

## Instructions

Perform these steps on CL1.

1. Logon as **ad\Administrator**.
1. From the context-menu of **Start** (you can press WIN + X), launch **Terminal** as Administrator.
1. Find a command to create a local user.

    ````powershell
    Get-Command -Verb New -Noun *user*
    ````

1. Find other commands to manage local users.

    ````powershell
    Get-Command -Noun LocalUser
    ````

1. Display help for New-LocalUser in a separate window.

    ````powershell
    Get-Help New-LocalUser -ShowWindow
    ````

    Notice, that the help is incomplete, e.g. no examples are provided and the paramters are not explained in detail.

1. Close the separate help window.
1. List all about_ topics in help.

    ````powershell
    Get-Help about_*
    ````

    Notice, that the list is incomplete, e.g. about_command_syntax is missing.

1. Get help about the command syntax.

    ````powershell
    Get-Help about_command_syntax
    ````

    PowerShell will not find this topic.

1. Update the help files.

    ````powershell
    Update-Help
    ````

    Do not wait for the command to complete, instead continue to the next step.

1. In Terminal, click **+** to open a new tab.

1. List the available modules

    ````powershell
    Get-Module -ListAvailable
    ````

1. In PowerShell Gallery, find a module to manage the Windows Update Client.

    ````powershell
    Find-Module *windowsupdate*
    ````

2. If you receive a question to install a certain NuGet provider, type *y*.
3. Install the module **PSWindowsUpdate** from PowerShell Gallery.

    ````powershell
    Install-Module PSWindowsUpdate
    ````

4. If you receive a question about installing modules from an untrusted repository, type *y*.
5. Verify the installation and location of the PSWindowsUpdate module

    ````powershell
    Get-Module PSWindowsUpdate -ListAvailable | Format-List
    ````

    Notice the value of the **Path** property.

6. Uninstall the module **PSWindowsUpdate**.

    ````powershell
    Uninstall-Module PSWindowsUpdate
    ````

7. Verify the removal of the module.

    ````powershell
    Get-Module PSWindowsUpdate -ListAvailable | Format-List
    ````

    You should not receive results.

8. Install the PSWindowsUpdate module for the current user. You do not need to have administrative rights to do that.

    ````powershell
    Install-Module `
        -Name PSWindowsUpdate `
        -Scope CurrentUser `
        -RequiredVersion 2.0.2.2 `
        -Force
    ````

    Notice the double prompt, because you split the command over several lines.

    Note: For testing purposes, we install an older version of the module. Sometimes this is necessary to provide compatibility with older scripts until they are updated.

9.  Verify the installation and location of the PSWindowsUpdate module

    ````powershell
    Get-Module PSWindowsUpdate -ListAvailable | Format-List
    ````

    Notice the value of the **Path** property.

10. List the available commands from the PSWindowsUpdate module.

    ````powershell
    Get-Command -Module PSWindowsUpdate
    ````

11. List the currently loaded modules

    ````powershell
    Get-Module
    ````

    Notice that the **PSWindowsUpdate** module is loaded.

12. Remove the module **PSWindowsUpdate** from memory.

    ````powershell
    Remove-Module PSWindowsUpdate
    ````

13. Verify, that **PSWindowsUpdate** is not loaded anymore.

    ````powershell
    Get-Module
    ````

14. Update the PSWindowsUpdate module to the latest version.

    ````powershell
    Update-Module PSWindowsUpdate -Force
    ````

15. Show the installed versions of the PSWindowsUpdate module

    ````powershell
    Get-Module PSWindowsUpdate -ListAvailable
    ````

    Notice, that two versions are available now.

16. Click the first tab. The help files should have finished downloading.

    Note: If you receive an error that some files could not download, you can safely ignore it for the moment.

17. List all about_ topics in help.

    ````powershell
    Get-Help about_*
    ````

    Notice, that the list is much longer than before.

18. Get help about the command syntax.

    ````powershell
    Get-Help about_command_syntax -ShowWindow
    ````

19. Get help about the **New-LocalUser** command.

    ````powershell
    Get-Help New-LocalUser -ShowWindow
    ````

    Notice that the help is much more detailed now and includes e.g. examples.
