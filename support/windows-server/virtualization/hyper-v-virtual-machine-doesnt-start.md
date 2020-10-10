---
title: Hyper-V virtual machine doesn't start
description: Describes an issue that triggers an error when you try to start a virtual machine that's running in a Windows Server 2012 R2 Hyper-V environment. Occurs when McAfee VirusScan is installed. A workaround is provided.
ms.date: 09/17/2020
author: Deland-Han 
ms.author: delhan
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: kaushika
ms.prod-support-area-path: Configuration of virtual machine settings
ms.technology: HyperV
---
# Hyper-V virtual machine doesn't start and triggers 0x80070057 error

This article provides a solution to a 0x80070057 error that occurs when you try to start a virtual machine.

_Original product version:_ &nbsp; Windows Server 2012 R2  
_Original KB number:_ &nbsp; 3084322

## Symptoms  

Consider the following scenario:

- You have Hyper-V running on a Windows Server 2012 R2 or Microsoft Hyper-V Server 2012 R2-based server.
- You configure the virtual machines with pass-through disks.
- You install or upgrade to McAfee VirusScan Enterprise (VSE) 8.8 Patch 5.

When you try to start a virtual machine in this scenario, it doesn't start, and the following error is returned:

> [Window Title]  
Hyper-V Manager
>
> [Main Instruction]  
An error occurred while attempting to start the selected virtual machine(s).
>
> [Content]  
'<VM_Name>' failed to start.  
Synthetic SCSI Controller (Instance ID): Failed to Power on with Error 'One or more arguments are invalid'.  
Attachment '\<SCSI ID>' failed to open because of error: 'One or more arguments are invalid'.

If you click **See details in the message window**, the following information is displayed:

> [Expanded Information]  
'\<VM_Name>' failed to start. (Virtual machine ID )
>
> '\<VM_Name>' Synthetic SCSI Controller (Instance ID ): Failed to Power on with Error 'One or more arguments are invalid' (0x80070057). (Virtual machine ID )
>
> '\<VM_Name>': Attachment '\<SCSI ID>' failed to open because of error: 'One or more arguments are invalid' (0x80070057). (Virtual machine ID )
>
> [^] Hide details [Close]

Additionally, you may notice that the following event is logged:

## Cause

This is a known issue in McAfee VirusScan Enterprise 8.8 Patch 5.

## Workaround

> [!WARNING]
>
> - This section contains information about opening or modifying the registry.
> - The following information is intended for system administrators. Registry modifications are irreversible and could cause system failure if done incorrectly.
> - Before you proceed, Intel Security strongly recommends that you back up your registry and understand the restore process. For more information, see [https://support.microsoft.com/kb/256986](https://support.microsoft.com/help/256986).

To work around this issue, disable the mfedisk.sys driver in the registry:

1. Open Registry editor (regedit.exe).
2. Locate the following subkey:

    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\\{4d36e967-e325-11ce-bfc1-08002be10318}

3. Modify the UpperFilters value by deleting "mfedisk" from this string.
4. Restart the computer.

## More information

This issue is documented in the following McAfee KB article: [https://kc.mcafee.com/corporate/index?page=content&id=KB84987](https://kc.mcafee.com/corporate/index?page=content&id=kb84987)  

Third-party information disclaimer
Microsoft provides third-party contact information to help you find technical support. This contact information may change without notice. Microsoft does not guarantee the accuracy of this third-party contact information.