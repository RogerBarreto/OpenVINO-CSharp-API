# Detailed Introduction to OpenVINO™ C# API Latest Version

> Preface
>
> Since its creation, the OpenVINO™ C# API project has been continuously maintained and updated. With in-depth research on this project, it has now formed fixed API interfaces and a relatively stable running version. In previous versions, the project implementation was mainly through custom encapsulation of fixed interfaces. After OpenVINO™ officially released the extended C API, OpenVINO™ C# API also synchronously updated to version 3.0, making its interface more flexible.
>
> Currently, the project has completed the upgrade to version 3.1, which adds many new features on the basis of 3.0, fixes issues that appeared in the 3.0 code, and supports more platforms and use cases.
> 

## Project Introduction
&emsp;    [OpenVINO™](www.openvino.ai) is an open-source toolkit for optimizing and deploying AI inference.

- Enhance deep learning performance in computer vision, automatic speech recognition, natural language processing, and other common tasks
- Use models trained with popular frameworks such as TensorFlow, PyTorch, etc.
- Reduce resource requirements and efficiently deploy on a range of Intel® platforms from edge to cloud

&emsp;    OpenVINO™ C# API is a .Net wrapper for OpenVINO™, developed using the latest OpenVINO™ libraries. It implements .Net calls to OpenVINO™ Runtime through OpenVINO™ C API, with usage habits consistent with OpenVINO™ C++ API. Since OpenVINO™ C# API is based on OpenVINO™, the supported platforms are completely consistent with OpenVINO™. For specific information, please refer to OpenVINO™. By using OpenVINO™ C# API, you can use C# language under .NET, .NET Framework, and other frameworks to implement deep learning model inference acceleration on specified platforms.

## Project Features
- **OpenVINO™ C# API supports all C API functions and encapsulates them using C# features, making them easier to use;**
  - 1. The project implementation principle is to implement .Net calls to OpenVINO™ Runtime through OpenVINO™ C API, so the project implements all OpenVINO™ C API;
  - 2. Based on the object-oriented features of C# language, the converted API has been encapsulated at a higher level, and the interface features of OpenVINO™ C++ API have been referenced to further define and encapsulate the interfaces, which is very friendly to users who have been in contact with C++ API;

- **The project encapsulation fully adopts C# features, and all conversions are implemented using C# top-level interfaces, avoiding the use of unsafe code mode;**
  - Pointers are not safe types, so when encapsulating the project involving pointer operations, C# top-level interfaces were used as much as possible to operate pointers, avoiding the use of unsafe programming. And unmanaged memory is managed to prevent memory leaks.

- **Supports Windows 10/11, Linux, Mac OS three major platforms, supports Nuget Package one-click deployment, making it more convenient to use;**
  - 1. The current version has completed testing on different platforms and supports the most common systems such as Windows 10/11, Linux, Mac OS;
  - 2. Provides OpenVINO™ Runtime Nuget Package for different platforms, enabling one-click deployment on Windows 10/11, Linux, Mac OS three major platforms, making it more convenient to use.

- **Implemented complete interface testing**
  - The current version provides unit tests for core assembly interfaces, and has completed testing of 99% of interfaces, ensuring the stability of interface usage.
  
- **Added commonly used extension interfaces, and supports using ``OpenCvSharp`` and ``Emgu.CV`` for image data processing;**
  - 1. Encapsulated commonly used interface methods in model deployment, such as common image data preprocessing, inference result output and drawing interfaces;
  - 2. Encapsulated common model deployment process methods, such as Yolov8, PP-Yoloe, RT-DETR, PP-OCR and other models, allowing developers to implement local deployment of models with just a few lines of code.
  - 3. During encapsulation, both ``OpenCvSharp`` and ``Emgu.CV`` were used for development, giving users more choices.

- **Provides more complete project examples, supporting more common model deployment cases;**
  - Developed more comprehensive model deployment cases using the latest version of OpenVINO™ C# API, and equipped with more comprehensive project development documentation, allowing more novice developers to quickly get started.

## Nuget Package

NuGet is a free, open-source package management development tool that focuses on installing third-party component libraries during .NET application development. Therefore, the current project has been packaged as a Nuget Package, allowing users to quickly install the current project through Nuget Package.

In this project, the following four types of Nuget Packages are mainly encapsulated:

- **Core Managed Libraries**

  **OpenVINO.CSharp.API** is the core assembly of this project, mainly encapsulating the [OpenVINOCSharpAPI](https://github.com/guojin-yan/OpenVINO-CSharp-API/tree/csharp3.1/src/CSharpAPI) assembly, which is a must-install assembly when using the project.

| Package                                        | Description                                               | Link                                                         |
| ---------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| **OpenVINO.CSharp.API**                        | OpenVINO C# API core libraries                            | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.CSharp.API.svg)](https://www.nuget.org/packages/OpenVINO.CSharp.API/) |


- **Native Runtime Libraries**

**Native Runtime Libraries** packages the assembly files of different platforms released by OpenVINO™ officially, which mainly include OpenVINO™ Runtime dynamic link libraries and dynamic link library files of third-party dependencies used. Users can install according to the platform type used. Up to now, support for **Windows (10/11)**, **Linux (Ubuntu/Centos/Debain/Rhel)**, **MacOS (x64/Arm64)** and other platforms has been implemented.
| Package                               | Description                          | Link                                                         |
| ------------------------------------- | ------------------------------------ | ------------------------------------------------------------ |
| **OpenVINO.runtime.win**              | Native bindings for Windows          | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.win.svg)](https://www.nuget.org/packages/OpenVINO.runtime.win/) |
| **OpenVINO.runtime.ubuntu.22-x86_64** | Native bindings for ubuntu.22-x86_64 | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.ubuntu.22-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.ubuntu.22-x86_64/) |
| **OpenVINO.runtime.ubuntu.20-x86_64** | Native bindings for ubuntu.20-x86_64 | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.ubuntu.20-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.ubuntu.20-x86_64/) |
| **OpenVINO.runtime.ubuntu.18-x86_64** | Native bindings for ubuntu.18-x86_64 | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.ubuntu.18-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.ubuntu.18-x86_64/) |
| **OpenVINO.runtime.debian9-arm64**    | Native bindings for debian9-arm64    | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.win.svg)](https://www.nuget.org/packages/OpenVINO.runtime.win/) |
| **OpenVINO.runtime.debian9-armhf**   | Native bindings for debian9-armhf    | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.debian9-armhf.svg)](https://www.nuget.org/packages/OpenVINO.runtime.debian9-armhf/) |
| **OpenVINO.runtime.centos7-x86_64**   | Native bindings for centos7-x86_64   | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.centos7-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.centos7-x86_64/) |
| **OpenVINO.runtime.rhel8-x86_64**     | Native bindings for rhel8-x86_64     | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.rhel8-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.rhel8-x86_64/) |
| **OpenVINO.runtime.macos-x86_64**     | Native bindings for macos-x86_64     | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.macos-x86_64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.macos-x86_64/) |
| **OpenVINO.runtime.macos-arm64**      | Native bindings for macos-arm64      | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.runtime.macos-arm64.svg)](https://www.nuget.org/packages/OpenVINO.runtime.macos-arm64/) |


- **Core Extensions Managed Libraries**

**Core Extensions Managed Libraries** is an extension of the core assembly of this project, mainly encapsulating [OpenVINOCSharpAPI.Extensions](https://github.com/guojin-yan/OpenVINO-CSharp-API/tree/csharp3.1/src/CSharpAPI.Extensions), [OpenVINOCSharpAPI.Extensions.OpenCvSharp](https://github.com/guojin-yan/OpenVINO-CSharp-API/tree/csharp3.1/src/CSharp.API.Extensions.OpenCvSharp), [OpenVINOCSharpAPI.API.Extensions.EmguCV](https://github.com/guojin-yan/OpenVINO-CSharp-API/tree/csharp3.1/src/CSharpAPI.Extensions.EmguCV) assemblies, which users can install according to their usage needs.
| Package                                        | Description                                               | Link                                                         |
| ---------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| **OpenVINO.CSharp.API.Extensions**             | OpenVINO C# API core extensions libraries                 | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.CSharp.API.Extensions.svg)](https://www.nuget.org/packages/OpenVINO.CSharp.API.Extensions/) |
| **OpenVINO.CSharp.API.Extensions.OpenCvSharp** | OpenVINO C# API core extensions libraries use OpenCvSharp | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.CSharp.API.Extensions.OpenCvSharp.svg)](https://www.nuget.org/packages/OpenVINO.CSharp.API.Extensions.OpenCvSharp/) |
| **OpenVINO.CSharp.API.Extensions.EmguCV**      | OpenVINO C# API core extensions libraries use EmguCV      | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.CSharp.API.Extensions.EmguCV.svg)](https://www.nuget.org/packages/OpenVINO.CSharp.API.Extensions.EmguCV/) |

- **Integration Library**

  This assembly mainly encapsulates integration packages for different platforms. Currently, the Windows platform integration package has been distributed, which mainly includes the ``OpenVINO.CSharp.API`` and ``OpenVINO.runtime.win`` assemblies, making it convenient for users to use.

| Package                     | Description                    | Link                                                         |
| --------------------------- | ------------------------------ | ------------------------------------------------------------ |
| **OpenVINO.CSharp.Windows** | All-in-one package for Windows | [![NuGet Gallery ](https://badge.fury.io/nu/OpenVINO.CSharp.Windows.svg)](https://www.nuget.org/packages/OpenVINO.CSharp.Windows/) |


## Assembly Introduction

### Core Assembly

In OpenVINO™ C# API, the following namespaces are mainly included:
```csharp
// Contains OpenVINO™ C# API core assembly
using OpenVinoSharp;
// Contains OpenVINO™ data types
using OpenVinoSharp.element;
// Contains OpenVINO™ C# API model processing methods
using OpenVinoSharp.preprocess;
```
Among them, under the ``OpenVinoSharp`` namespace, it contains the main objects of OpenVINO™ for deploying deep learning models. During encapsulation, the C++ API interface definition method was mainly referenced, so its usage is basically the same as the C++ API, as shown in the following table:
|Class|C++ API|C# API|Description|
| ----------- | ------------ | ------------- | -------------- |
| Core class | ov::Core | Core| OpenVINO™ runtime core entity class |
| Model class | ov::Model | Model | User-defined model class |
| CompiledModel class | ov::CompiledModel|CompiledModel|Compiled model class|
| Node class | ov::Node | Node | Model node entity class |
| Output class | ov::Output | Output | Model output node entity class |
| Input class | ov::Input | Input | Model input node entity class |
| InferRequest class | ov::InferRequest | InferRequest| Model inference request class |
| Tensor class | ov::Tensor | Tensor| Inference request node tensor |
| Shape class | ov::Shape | Shape| Node tensor shape class |
| PartialShape class | ov::PartialShape | PartialShape | Node tensor dynamic shape class |

### Core Extension Assembly

The OpenVINO™ C# API core extension assembly mainly encapsulates some commonly used function methods and model deployment interfaces for common models, mainly including image data processing methods, result objects and inference methods for Yolov8, PP-Yoloe, RT-DETR, PP-OCR and other models. At the same time, the way of processing image data was fully considered during encapsulation, using both **OpenCvSharp** and **Emgu.CV** open-source libraries.

This extension assembly mainly includes the following namespaces:

```csharp
// Contains extension programs encapsulated using OpenVINO™ C# API
using OpenVinoSharp.Extensions;
// Contains some custom extension methods
using OpenVinoSharp.Extensions.utility;
// Contains common model deployment interfaces encapsulated using OpenVINO™ C# API
using OpenVinoSharp.Extensions.model;
// Contains common image processing interfaces encapsulated using OpenCvSharp or Emgu.CV
using OpenVinoSharp.Extensions.process;
// Contains common model result classes encapsulated using OpenCvSharp or Emgu.CV
using OpenVinoSharp.Extensions.result;
```

Here is a brief introduction to the main objects under the ``OpenVinoSharp`` namespace. For detailed introduction, please refer to the following articles: [《OpenVINO™ C# API Detailed Explanation and Demonstration (Basic Interfaces)》](), [《OpenVINO™ C# API Detailed Explanation and Demonstration (Preprocessing Interfaces)》](), [《OpenVINO™ C# API Detailed Explanation and Demonstration (Extension Interfaces)》]().

## Usage Examples

To help everyone get started with this project more quickly, a case repository has been specially created in this project: [OpenVINO C# API Samples](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples), which has already updated some common model deployment cases:

### Regular Object Detection Cases

| Case Name                                | Running Effect                                                     | Link                                                         |
| --------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Deploy Yolov5-det model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/01/DhRioXwzYEMyUfI.png" width="200">  <img src="https://s2.loli.net/2024/02/01/ljRezkToBU37cAN.png" width="300"> | Project Link: [yolov5_det_opencvsharp](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov5/yolov5_det_opencvsharp), [yolov5_det_emgucv](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov5/yolov5_det_emgucv)<br>Model Link: [yolov5](https://github.com/ultralytics/yolov5)<br>Blog Link: [Deploy Yolov5 on MacOS using OpenVINO™ C# API](https://blog.csdn.net/grape_yan/article/details/136053953) |
| Deploy Yolov6-det model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/07/tTJRKOgieI9fBpy.png" width="200"><img src="https://s2.loli.net/2024/02/07/pZfRKq6IDXBzsxb.png" width="300"> | [yolov6_det_opencvsharp](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov6/yolov6_det_opencvsharp)<br>[yolov6_det_emgucv](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov6/yolov6_det_emgucv) |
| Deploy Yolov7-det model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/07/bjefx3WpPgVwhry.png" width="200"><img src="https://s2.loli.net/2024/02/07/RnEYv3bCGuOZilz.png" width="300"> | [yolov7_det_opencvsharp](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov7/yolov7_det_opencvsharp)<br>[yolov7_det_emgucv](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov7/yolov7_det_emgucv) |
| Deploy Yolov8-det model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/07/IrPzpqMwYgnkvcV.png" width="200"><img src="https://s2.loli.net/2024/02/07/qRiSnjg65WXVLZp.png" width="300"> | [yolov8_det_opencvsharp](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov8/yolov8_det_opencvsharp)<br>[yolov8_det_emgucv](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov8/yolov8_det_emgucv) |
| Deploy PP-YOLOE model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/07/znksi2m8lfKF4We.png" width="200"><img src="https://s2.loli.net/2024/02/07/avXK9WQ8noSNETd.png" width="300"> | [yolov8_det_opencvsharp]()<br/>[yolov8_det_emgucv]()         |
| Deploy RT-DETR model using OpenVINO™ C# API  | <img src="https://s2.loli.net/2024/02/07/XLQinEmgZ4U1AB3.png" width="200"><img src="https://s2.loli.net/2024/02/07/bMeElhfoRxpSzrI.png" width="300"> | [yolov8_det_opencvsharp]()<br/>[yolov8_det_emgucv]()         |



### Rotated Object Detection Cases

| Case Name                                  | Running Effect                                                     | Link                                                         |
| ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Deploy Yolov8-obb model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/10/DMQ1IWhRHjo7pEA.png" width="200"><img src="https://s2.loli.net/2024/02/10/WqhYaVNtDIrC9jy.jpg" width="300"> | [yolov8_obb_opencvsharp](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov8/yolov8_obb_opencvsharp)<br/>[yolov8_obb_emgucv](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/yolov8/yolov8_obb_emgucv) |
| Deploy PP-YOLOE-R model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/10/Glp97SaQRKM5ZqH.png" width="200"><img src="https://s2.loli.net/2024/02/10/ZUR6k5i4ouBN7LV.jpg" width="300"> | [ppyoloe_r_opencvsharp](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/ppyoloe/ppyoloe_r_opencvsharp) |



### Face Recognition Cases

| Case Name                                  | Running Effect                                                     | Link                                                         |
| ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Deploy Blaze Face model using OpenVINO™ C# API | <img src="https://s2.loli.net/2024/02/10/Lvoj8wGSCps2zD3.png" width="200"><img src="https://s2.loli.net/2024/02/10/SnW7qzC568hvfLD.png" width="300"> | [blazeface_opencvsharp](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/face_detection/blazeface_opencvsharp)<br/>[blazeface_emgucv](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples/tree/master/model_samples/face_detection/blazeface_emgucv) |
|                                           |                                                              |                                                              |



### OCR Text Recognition Cases

| Case Name                                  | Running Effect                                                     | Link                                                         |
| ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Deploy Paddle OCR model using OpenVINO™ C# API | <img src="https://s2.loli.net/2023/12/23/pJBGrle9AFDjOEP.png" width="600"><img src="https://s2.loli.net/2023/12/22/ESbjL24Ydxq1ePH.png" width=400 /> | [PaddleOCR-OpenVINO-CSharp](https://github.com/guojin-yan/PaddleOCR-OpenVINO-CSharp) |
|                                           |                                                              |                                                              |






## Contribution
Currently, this project is still in the development stage and has basically completed the encapsulation of the C API currently officially encapsulated by OpenVINO™, but currently OpenVINO™ C API has not fully implemented C++ API. Therefore, if you are interested, you can submit issues or PRs to OpenVINO™ official source code's C API to continue enriching the official C API. For contributing to OpenVINO™, please refer to the following article: [CONTRIBUTING](https://github.com/openvinotoolkit/openvino/blob/master/CONTRIBUTING.md)

In addition, if you are interested in this project, you can also submit contributions to this project, such as optimizing the current project code, improving interface testing, adding extension interfaces, etc. For contributing to OpenVINO™ C# API, please refer to the following article: [Contributing to OpenVINO™ C# API](https://github.com/guojin-yan/OpenVINO-CSharp-API/blob/csharp3.1/CONTRIBUTING.md)


## Contact
If you have any questions during use, you can solve them by submitting issues. Due to my limited energy, I may not be able to reply in time. You can get more information or add my contact information through the following ways:

<div align=center><img src="https://s2.loli.net/2024/01/29/VIPU1MSwjEh2QAY.png" width=800></div>


## References
For more information, please refer to:
- [OpenVINO GitHub](https://github.com/openvinotoolkit/openvino)

- [OpenVINO Document](https://docs.openvino.ai/)

- [OpenVINO™ C# API](https://github.com/guojin-yan/OpenVINO-CSharp-API)

- [OpenVINO™ C# API Samples](https://github.com/guojin-yan/OpenVINO-CSharp-API-Samples)
