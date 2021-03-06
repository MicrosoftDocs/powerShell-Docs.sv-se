---
title: Installera PowerShell Core på arm
description: Installera PowerShell Core på ARM-baserade system
ms.date: 11/11/2020
ms.openlocfilehash: 1477b99767c19d24f8540714942f63c8347550e9
ms.sourcegitcommit: ef25c8bc95df12697725958c9814f0e187cfc683
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/12/2021
ms.locfileid: "98130147"
---
# <a name="powershell-core-on-arm"></a>PowerShell Core på arm

Stöd för PowerShell på arm baseras på de **.net Core-principer som stöds av OS-livscykeln**.

PowerShell 7,0 baseras på den [operativ system livs cykel princip för .net Core 3,1 som stöds](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) och har stöd för följande plattformar:

|         Operativsystem          |          Version           | Arkitekturer |          Livscykel           |
| ------------------- | -------------------------- | ------------- | ---------------------------- |
| Windows Nano Server | Version 1803 +              | Arm32         | [Windows][Windows-lifecycle] |
| Alpine Linux        | 3.10 +                      | Arm64         | [Alpina][Alpine-lifecycle]   |
| Debian              | 9 +                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu              | 20,10, 20,04, 18,04, 16,04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

PowerShell 7,1 baseras på principen för [OS-livscykel som stöds i .net 5,0](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) och stöder följande plattformar:

|        Operativsystem         |          Version           | Arkitekturer |          Livscykel           |
| ----------------- | -------------------------- | ------------- | ---------------------------- |
| Windows 10-klient | Version 1709 +              | Arm64         | [Windows][Windows-lifecycle] |
| Alpine Linux      | 3.11 +                      | Arm64         | [Alpina][Alpine-lifecycle]   |
| Debian            | 9 +                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu            | 20,10, 20,04, 18,04, 16,04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

[Windows-lifecycle]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Alpine-lifecycle]: https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases
[Debian-lifecycle]: https://wiki.debian.org/DebianReleases
[Ubuntu-lifecycle]: https://wiki.ubuntu.com/Releases

Installations anvisningar finns i följande artiklar:

- [Windows 10 på arm](installing-powershell-core-on-windows.md#installing-the-zip-package)
- [Windows 10 IoT Enterprise](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-enterprise)
- [Windows 10 IoT Core](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-core)
- [Raspbian](installing-powershell-core-on-linux.md#raspbian)
