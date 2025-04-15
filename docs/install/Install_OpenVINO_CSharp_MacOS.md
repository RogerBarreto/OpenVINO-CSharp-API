## Setting up OpenVINO™ C# Development Environment on MacOS

- [Setting up OpenVINO™ C# Development Environment on MacOS](#setting-up-openvino-c-development-environment-on-macos)
  - [🧩 Introduction](#-introduction)
  - [🔮 Installing .NET Runtime Environment](#-installing-net-runtime-environment)
  - [🎈 Configuring C# Development Environment](#-configuring-c-development-environment)
  - [🎨 Creating and Configuring C# Project](#-creating-and-configuring-c-project)
    - [Step 1: Creating an OpenVINO™ C# Project](#step-1-creating-an-openvino-c-project)
    - [Step 2: Adding Project Dependencies](#step-2-adding-project-dependencies)
  - [🎁 Testing OpenVINO™ C# Project](#-testing-openvino-c-project)
  - [🎯 Summary](#-summary)

### 🧩 Introduction

Currently, MacOS systems are divided into two major versions: one is the Apple system before 2020, which uses Intel series CPUs, and the other is the system with Apple M series chips introduced after 2020. This tutorial will detail the process of setting up an **OpenVINO™ CSharp** development environment from scratch on **MacOS (M2)**, and perform a simple test of the **OpenVINO™ CSharp API** environment.

### 🔮 Installing .NET Runtime Environment

**[.NET](https://learn.microsoft.com/en-us/dotnet/)** is a free, cross-platform, open-source developer platform created by **Microsoft**. It allows you to write code in C#, F#, or Visual Basic to build various types of applications that can run on any compatible operating system (Windows, Linux, Mac OS, etc.).

Microsoft officially provides detailed installation procedures for the **.NET** environment. You can refer to the following article for installation: [Install .NET on macOS](https://learn.microsoft.com/en-us/dotnet/core/install/macos).

First, visit the website [Download .NET](https://dotnet.microsoft.com/en-us/download). The specific download selection is shown below:

<div align=center><img src="https://s2.loli.net/2024/01/08/n2wVCSYoFm8JgzP.png" width=500></div>

After downloading the file, install the environment by double-clicking the installation file:

<div align=center><img src="https://s2.loli.net/2024/01/08/De5XQlPk4Fxr1Ly.png" width=500></div>

After opening the installation file, as shown in the image below, there is no need to set other configurations. Just follow the default steps to complete the installation.

<div align=center><img src="https://s2.loli.net/2024/01/08/S17VTvHwnOPhxt8.png" width=400></div>

### 🎈 Configuring C# Development Environment

In the MacOS environment, we can use the following combination for C# code development:

- Code building tool: **dotnet**
- Code editing tool: **Visual Studio Code**

We have already installed the **dotnet** tool when installing **.NET** above. **Visual Studio Code** is a powerful code editor that supports many third-party plugins and C# code development. Installing **Visual Studio Code** is quite simple - just download the installation file from the [VS Code official website](https://code.visualstudio.com/) and complete the installation with the default options.

Then configure the C# editing environment by searching for C# in the extension marketplace and installing the C# extension, as shown in the image below.

<div align=center><img src="https://s2.loli.net/2024/01/08/to9sSw2vGbchJIZ.png" width=800></div>

### 🎨 Creating and Configuring C# Project

#### Step 1: Creating an OpenVINO™ C# Project

Use **dotnet** to create a test project. Enter the following command in the Terminal to create the project:

```shell
dotnet new console -o test_openvino_csharp --framework net6.0
```

<div align=center><img src="https://s2.loli.net/2024/01/08/ZbmSRdEDVA7yK8w.png" width=500></div>

#### Step 2: Adding Project Dependencies

Next, use **Visual Studio Code** to open the project file. In the terminal window at the bottom of **Visual Studio Code**, enter the following commands to add the ``OpenVINO.CSharp.API`` and ``OpenVINO.runtime.macos-arm64`` project dependency packages. The output is shown in the image below:

```shell
dotnet add package OpenVINO.CSharp.API
dotnet add package OpenVINO.runtime.macos-arm64
```

- **OpenVINO.CSharp.API**: Core assembly for the OpenVINO™ CSharp API project.
- **OpenVINO.runtime.macos-arm64**: Dependencies required for OpenVINO™ to run on MacOS M series platforms.
- **OpenVINO.runtime.macos-x86_64**: Dependencies required for OpenVINO™ to run on MacOS Intel CPU series platforms.

<div align=center><img src="https://s2.loli.net/2024/01/08/KBy74UngiFkIDuM.png" width=800></div>

### 🎁 Testing OpenVINO™ C# Project

First, add the test code. Users can directly replace the content of the **Program.cs** file in the project created above with the following code:

```csharp
using OpenVinoSharp;
namespace test_openvino_csharp // Note: actual namespace depends on the project name.
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // -------- Testing OpenVINO CSharp API Installation --------
            OpenVinoSharp.Version version = Ov.get_openvino_version();
            Console.WriteLine("---- OpenVINO INFO----");
            Console.WriteLine("Description : " + version.description);
            Console.WriteLine("Build number: " + version.buildNumber);
        }
    }
}
```

After creating and configuring the project, enter ``dotnet run`` in the terminal to run the program. The result is shown in the image below:

<div align=center><img src="https://s2.loli.net/2024/01/08/cIXCWJLrgjVOZT2.png" width=800></div>

This primarily outputs the OpenVINO version information. If you see the results above, it indicates that the environment has been successfully configured.

### 🎯 Summary

At this point, we have completed setting up the OpenVINO™ C# development environment on MacOS. We welcome everyone to use it. For more information, you can refer to the following resources:

- [OpenVINO™](https://github.com/openvinotoolkit/openvino)
- [OpenVINO CSharp API](https://github.com/guojin-yan/OpenVINO-CSharp-API)
- [OpenVINO CSharp API Samples](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples)
