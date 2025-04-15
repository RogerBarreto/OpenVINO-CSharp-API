## Setting up OpenVINO™ C# Development Environment on Linux

- [Setting up OpenVINO™ C# Development Environment on Linux](#setting-up-openvino-c-development-environment-on-linux)
  - [🧩 Introduction](#-introduction)
  - [🔮 Installing .NET Runtime Environment](#-installing-net-runtime-environment)
    - [Step 1: Installing .NET 6.0 SDK](#step-1-installing-net-60-sdk)
    - [Step 2: Installing .NET 6.0 Runtime](#step-2-installing-net-60-runtime)
  - [🎈 Configuring C# Development Environment](#-configuring-c-development-environment)
  - [🎨 Creating and Configuring C# Project](#-creating-and-configuring-c-project)
    - [Step 1: Creating an OpenVINO™ C# Project](#step-1-creating-an-openvino-c-project)
    - [Step 2: Adding Project Dependencies](#step-2-adding-project-dependencies)
    - [Step 3: Installing Other OpenVINO Dependencies](#step-3-installing-other-openvino-dependencies)
  - [🎁 Testing OpenVINO™ C# Project](#-testing-openvino-c-project)
  - [🎯 Summary](#-summary)



### 🧩 Introduction

This article will detail the process of setting up an **OpenVINO™ CSharp** development environment from scratch on **Linux (Ubuntu 22.04)**, and perform a simple test of the **OpenVINO™ CSharp API** environment.

### 🔮 Installing .NET Runtime Environment

**[.NET](https://learn.microsoft.com/en-us/dotnet/)** is a free, cross-platform, open-source developer platform created by **Microsoft**. It allows you to write code in C#, F#, or Visual Basic to build various types of applications that can run on any compatible operating system (Windows, Linux, Mac OS, etc.).

Microsoft officially provides detailed installation procedures for the **.NET** environment. You can refer to the following article for installation: [Install .NET on Linux](https://learn.microsoft.com/en-us/dotnet/core/install/linux).

Since there are many Linux distributions available, the following demonstration will be based on installing **.NET 6.0** on **Linux (Ubuntu 20.04)**.

#### Step 1: Installing .NET 6.0 SDK

Open a Terminal and enter the following command to install **.NET 6.0 SDK**.

```shell
sudo apt-get install -y dotnet-sdk-6.0
```

<div align=center><img src="https://s2.loli.net/2024/01/08/yq7jt1FCTw8paRY.png" width=500></div>

#### Step 2: Installing .NET 6.0 Runtime

Generally, the **.NET 6.0 SDK** installation already includes the **.NET 6.0 Runtime**. However, if the versions are inconsistent, it may not work properly. Therefore, users can enter the following command to install **.NET 6.0 Runtime** separately.

```shell
sudo apt-get install -y dotnet-runtime-6.0
```

<div align=center><img src="https://s2.loli.net/2024/01/08/S5DBkfa2yeR9hzK.png" width=500></div>

### 🎈 Configuring C# Development Environment

In a Linux environment, we can use the following combination for C# code development:

- Code building tool: **dotnet**
- Code editing tool: **Visual Studio Code**

We have already installed the **dotnet** tool when installing **.NET 6.0 SDK** above. **Visual Studio Code** is a powerful code editor that supports many third-party plugins and C# code development. Installing **Visual Studio Code** is quite simple - just download the installation file from the [VS Code official website](https://code.visualstudio.com/) and complete the installation with the default options.

Then configure the C# editing environment by searching for C# in the extension marketplace and installing the C# extension, as shown in the image below.

<div align=center><img src="https://s2.loli.net/2024/01/08/1QY8UR4IEPrZvaf.png" width=800></div>

### 🎨 Creating and Configuring C# Project

#### Step 1: Creating an OpenVINO™ C# Project

Use **dotnet** to create a test project. Enter the following command in the Terminal to create the project:

```shell
dotnet new console -o test_openvino_csharp --framework net6.0
```

<div align=center><img src="https://s2.loli.net/2024/01/08/6bjKwRMHoW9uOsC.png" width=500></div>

#### Step 2: Adding Project Dependencies

Next, enter the following commands in sequence to open the project file with **Visual Studio Code**:

```shell
cd test_openvino_csharp
code .
```

Then, in the terminal window at the bottom of **Visual Studio Code**, enter the following commands to add the ``OpenVINO.CSharp.API`` and ``OpenVINO.runtime.ubuntu.22-x86_64`` project dependency packages. The output is shown in the image below:

```shell
dotnet add package OpenVINO.CSharp.API
dotnet add package OpenVINO.runtime.ubuntu.22-x86_64
```

- **OpenVINO.CSharp.API**: Core assembly for the OpenVINO™ CSharp API project.
- **OpenVINO.runtime.ubuntu.22-x86_64**: Dependencies required for OpenVINO™ to run on Ubuntu 22.04 platform.

<div align=center><img src="https://s2.loli.net/2024/01/08/EPQ4RGdTr1saCuJ.png" width=800></div>

If users are using other Linux environments, they need to install OpenVINO™ runtime dependencies for other platforms. The currently released OpenVINO CSharp API corresponding Linux runtime dependency packages are shown in the table below. Users can install them according to their system requirements.

| Package                               | Description                          | Link                                                         |
| ------------------------------------- | ------------------------------------ | ------------------------------------------------------------ |
| **OpenVINO.runtime.ubuntu.22-x86_64** | Native bindings for ubuntu.22-x86_64 | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.ubuntu.22-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.ubuntu.22-x86_64/) |
| **OpenVINO.runtime.ubuntu.20-x86_64** | Native bindings for ubuntu.20-x86_64 | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.ubuntu.20-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.ubuntu.20-x86_64/) |
| **OpenVINO.runtime.ubuntu.18-x86_64** | Native bindings for ubuntu.18-x86_64 | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.ubuntu.18-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.ubuntu.18-x86_64/) |
| **OpenVINO.runtime.debian9-arm64**    | Native bindings for debian9-arm64    | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.win.svg)](https://www.nuget.org/packages/OpenVINO.runtime.win/) |
| **OpenVINO.runtime.debian9-armhf**    | Native bindings for debian9-armhf    | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.debian9-armhf.svg)](https://www.nuget.org/packages/OpenVINO.runtime.debian9-armhf/) |
| **OpenVINO.runtime.centos7-x86_64**   | Native bindings for centos7-x86_64   | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.centos7-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.centos7-x86_64/) |
| **OpenVINO.runtime.rhel8-x86_64**     | Native bindings for rhel8-x86_64     | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.rhel8-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.rhel8-x86_64/) |



#### Step 3: Installing Other OpenVINO Dependencies

If users have not previously installed OpenVINO C++ on their host machine and are using OpenVINO™ for the first time, they need to install other dependencies.

First, enter ``dotnet run`` to run the project, then open the ``[Project File]/bin/Debug/net6.0/runtimes/ubuntu.22-x86_64/native`` directory, find the ``install_openvino_dependencies.sh`` file, then open a terminal in that directory and enter the following command:

```shell
sudo -E install_openvino_dependencies.sh
```

The output after running is shown in the image below:

<div align=center><img src="https://s2.loli.net/2024/01/08/K7UDMkdT1PEqOzj.png" width=600></div>

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

After creating and configuring the project, you can run it directly. First, add a temporary environment variable to set the dependency path for ``OpenVINO.runtime.ubuntu.22-x86_64``:

```shell
export LD_LIBRARY_PATH=[Project File]/bin/Debug/net6.0/runtimes/ubuntu.22-x86_64/native
```

Then enter ``dotnet run`` in the terminal to run the program. The result is shown in the image below:

<div align=center><img src="https://s2.loli.net/2024/01/08/yQZCTrdSXGpFKLn.png" width=800></div>

This primarily outputs the OpenVINO version information. If you see the results above, it indicates that the environment has been successfully configured.

### 🎯 Summary

At this point, we have completed setting up the OpenVINO™ C# development environment on Linux. We welcome everyone to use it. For more information, you can refer to the following resources:

- [OpenVINO™](https://github.com/openvinotoolkit/openvino)
- [OpenVINO CSharp API](https://github.com/guojin-yan/OpenVINO-CSharp-API)
- [OpenVINO CSharp API Samples](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples)
