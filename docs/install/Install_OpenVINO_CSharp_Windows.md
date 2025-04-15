## Setting up OpenVINO™ C# Development Environment on Windows

- [Setting up OpenVINO™ C# Development Environment on Windows](#setting-up-openvino-c-development-environment-on-windows)
  - [🧩 Introduction](#-introduction)
  - [🔮 Installing .NET Runtime Environment](#-installing-net-runtime-environment)
  - [🎈 Configuring C# Development Environment](#-configuring-c-development-environment)
  - [🎨 Creating and Configuring C# Project](#-creating-and-configuring-c-project)
    - [Step 1: Creating an OpenVINO™ C# Project](#step-1-creating-an-openvino-c-project)
    - [Step 2: Adding Project Dependencies](#step-2-adding-project-dependencies)
  - [🎁 Testing OpenVINO™ C# Project](#-testing-openvino-c-project)
  - [🎯 Summary](#-summary)

### 🧩 Introduction

This article will detail the process of setting up an **OpenVINO™ CSharp** development environment from scratch on **Windows 10/11**, and perform a simple test of the **OpenVINO™ CSharp API** environment.

### 🔮 Installing .NET Runtime Environment

**[.NET](https://learn.microsoft.com/en-us/dotnet/)** is a free, cross-platform, open-source developer platform created by **Microsoft**. It allows you to write code in C#, F#, or Visual Basic to build various types of applications that can run on any compatible operating system (Windows, Linux, Mac OS, etc.).

Microsoft officially provides detailed installation procedures for the **.NET** environment. You can refer to the following article for installation: [Install .NET on Windows](https://learn.microsoft.com/en-us/dotnet/core/install/windows).

### 🎈 Configuring C# Development Environment

There are several platforms available for creating and compiling C# code on Windows. The easiest and simplest option is to use **Visual Studio IDE**, but **Visual Studio IDE** currently only supports Windows environments. If you want cross-platform compatibility, the best combination is:

- Code building tool: **dotnet**
- Code editing tool: **Visual Studio Code**

Therefore, in this article, we will explain how to compile and run projects using **Visual Studio IDE** for Windows, while the combination of **dotnet & Visual Studio Code** will be explained for Linux and MacOS systems. For **Visual Studio IDE** installation, you can refer to the installation tutorials provided by Microsoft:

- [Visual Studio 2022 IDE](https://visualstudio.microsoft.com/vs/)
- [Install .NET on Windows](https://learn.microsoft.com/en-us/dotnet/core/install/windows)

### 🎨 Creating and Configuring C# Project

#### Step 1: Creating an OpenVINO™ C# Project

Use **Visual Studio 2022 IDE** to create an OpenVINO™ C# test project. Follow the process shown in the image below.

<div align=center><img src="https://s2.loli.net/2024/01/08/kInKFwbhU5tRPXp.png" width=800></div>

#### Step 2: Adding Project Dependencies

For the dependencies required by the OpenVINO™ C# project, you can install all necessary assemblies using NuGet Package. The installation process is shown in the image below:

<div align=center><img src="https://s2.loli.net/2024/01/08/m5In3luJe1H9PFt.png" width=800></div>

Here, you mainly need to install two types of NuGet packages:

- **OpenVINO CSharp API**
  - **OpenVINO.CSharp.API**: Core assembly for the OpenVINO CSharp API project.
  - **OpenVINO.runtime.win**: Dependencies required for OpenVINO to run on Windows platform.
- **OpenCvSharp**
  - **OpenCvSharp4**: Core assembly for the OpenCvSharp4 project.
  - **OpenCvSharp4.runtime.win**: Dependencies required for OpenCvSharp4 to run on Windows platform.

Among these, **OpenVINO CSharp API** is the project we are focusing on, while **OpenCvSharp** is an open-source vision processing library used in C#.

### 🎁 Testing OpenVINO™ C# Project

First, add the test code. Users can directly replace the content of the **Program.cs** file in the project created above with the following code:

```csharp
using OpenCvSharp;
using OpenVinoSharp;
namespace test_openvino_csharp
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

            // -------- Testing OpenCvSharp Installation --------
            //Create a 300*300 three-channel color image with green color
            Mat img = new Mat(300, 300, MatType.CV_8UC3, new Scalar(255, 0, 0));
            Cv2.ImShow("img", img);
            Cv2.WaitKey(0);
        }
    }
}
```

After creating and configuring the project, you can run it directly. With **Visual Studio 2022 IDE**, you can click the run button to execute the program. The output after running the program is shown below:

<div align=center><img src="https://s2.loli.net/2024/01/08/zCWDTHmpG74A2rO.png" width=800></div>

This primarily outputs the OpenVINO version information and uses OpenCvSharp to draw a blue image. If you see the results above, it indicates that the environment has been successfully configured.

### 🎯 Summary

At this point, we have completed setting up the OpenVINO™ C# development environment on Windows. We welcome everyone to use it. For more information, you can refer to the following resources:

- [OpenVINO™](https://github.com/openvinotoolkit/openvino)
- [OpenVINO CSharp API](https://github.com/guojin-yan/OpenVINO-CSharp-API)
- [OpenVINO CSharp API Samples](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples)
