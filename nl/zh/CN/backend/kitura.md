---

copyright:
  years: 2018
lastupdated: "2018-08-17"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 使用 Kitura 创建应用程序
{: #kitura}

[Kitura](http://www.kitura.io) 是一种服务器端 Swift 框架，用于构建 iOS 后端和 Web 应用程序。此框架使用 Kitura 本身提供的 URLSession SDK（例如，Alamofire、RestKit 或 [KituraKit](https://github.com/ibm-swift/kiturakit) SDK）来创建可从 iOS 应用程序调用的 REST API。

Kitura 能够与 {{site.data.keyword.cloud}} 提供的所有服务和功能相集成，包括 {{site.data.keyword. appid_short}}、{{site.data.keyword.mobilepushshort}} 和 {{site.data.keyword.mobileanalytics_short}} 以及数据库、机器学习和其他服务。然后，可以使用 {{site.data.keyword.cloud}} 中的 Cloud Foundry 或 Docker（基于 Kubernetes）平台来部署和自动扩展 Kitura。

Kitura 提供了 `kitura` [命令行界面 (CLI)](http://www.kitura.io/en/starter/gettingstarted.html)，用于简化创建、构建、测试和部署 Kitura 应用程序。使用 Kitura CLI 构建的应用程序包括完全支持部署到任何支持 Cloud Foundry、Docker 和 Kubernetes 技术的云。但是，如果要专门针对 {{site.data.keyword.cloud}} 进行构建，建议您在浏览器中使用 IBM Apple Development Console 或使用 {{site.data.keyword.dev_cli_notm}}。此外，虽然这两种方法都共享底层技术，但 Apple Development Console 和 IBM Developer Tools 会创建托管的项目和部署管道，以及供应应用程序所需的服务。

## 开始之前

首先，请确保您已准备好以下必备软件：  

* iOS 11.0+  
* Xcode 9.0  
* Swift 4.0+  
* Cocoapods  

## 步骤 1. 使用浏览器创建 Kitura 项目

1. 转至 Apple Development Console 的“入门模板工具包”部分。选择预定义的入门模板，例如“Swift - 服务于前端的后端 API”，或者使用**创建项目**磁贴来创建定制项目。单击**创建项目**。
2. 为项目提供名称并选择要部署项目的位置。如果不确定要部署应用程序的位置，请使用缺省值，因为日后可以更改这些值。
3. 选择 Swift 语言。这将创建服务器端 Swift 项目。还会显示“主机”和“域”选项，这些选项构成应用程序的 URL。如果不确定，请使用缺省值，您还可以通过应用程序将位于其中的域提供者来提供自己的定制域。
4. 可以为要构建的 REST API 提供 OpenAPI（也称为 Swagger）定义。如果您有此类定义，那么将创建包含 Kitura 中相应处理程序函数的 REST API。如果您没有 OpenAPI 定义，也不必担心，因为通过 Kitura，您可以轻松地使用其路由器 API 来手动创建 REST API。
5. 单击**创建项目**。

这将创建项目，但该项目尚未使用其他任何服务或功能。可以使用**添加资源**按钮来添加服务，或单击**下载代码**按钮以获取项目的代码。您还可以轻松地将服务添加到现有项目。

## 步骤 2. 添加服务

1. 单击**添加资源**按钮以添加服务。这将显示服务类别的面板。例如，选择**数据**以查看可用数据库，然后选择 **Cloudant NoSQL DB**。
2. 选择服务的定价套餐（如轻量），然后单击**创建**。

这将创建服务的实例，其中会提供应用程序的服务凭证，在某些情况下，还会将必要的代码添加到项目，以包含与服务的正确连接。现在，可以使用**添加资源**按钮来添加服务，或单击**下载代码**按钮以获取项目的代码。

下载项目后，可以开始使用应用程序。

## 步骤 3. 使用 Xcode 开发应用程序
下载项目后，可以使用 Xcode 来修改和开发项目，然后上传修改的应用程序以部署到云。

1. 创建 Xcode 项目。  
  在 Xcode 中使用项目之前，必须使用 Swift Package Manager 命令创建 Xcode 项目文件。从已下载项目的根目录（包含 `Package.swift` 文件）运行以下命令：
  ```
  swift package generate-xcodeproj
  ```
  {: codeblock}

  这将在同一目录中创建 Xcode 项目，随后您可以打开该项目。

2. 设置项目的 Xcode 目标。  
  要运行 Kitura 服务器，必须通过单击工具栏上的 **project_name-Package** 部分并从菜单中选择 **project_name** 目标来编辑方案。请检查目标设备是否设置为**我的 Mac**。

3. 本地运行 Kitura 服务器  
  单击**运行**按钮或使用 `⌘+R` 快捷键来启动 Kitura 服务器。启动服务器后，可以检查以下标准 Kitura URL 是否在运行：
  * Kitura 监视：[http://localhost:8080/swiftmetrics-dash/]()
  * Kitura 运行状况检查：[http://localhost:8080/health]()

## 步骤 5. 添加 REST API
框架 Kitura 服务器已创建，但并未提供 iOS 应用程序可以使用的任何 REST API。在 Kitura 中添加具有最少编码的 REST API。以下步骤显示了如何添加 REST API 以对 `/meals` 发出 `GET` 请求，该请求旨在返回 Kitura 服务器存储的 `Meal` 对象。

1. 将 `Meal` 结构添加到 `Sources/Application/Application.swift` 文件：  
  在声明 App 类之前，添加以下内容以创建符合可编码协议的 Meal 结构：  
  ```swift
	struct Meal: Codable {    
	    var name: String
	    var photo: Data
	    var rating: Int
	}
  ```
  {: codeblock}

2. 通过将 `let cloudEnv = CloudEnv()` 添加到以下代码部分，将字典添加到 `Sources/Application/Application.swift` 文件以存储 `Meal` 对象：
 
  ```swift
  private var mealStore: [String: Meal] = [:]
  ```
  {: codeblock}

3. 通过将以下代码添加到 `postInit()` 函数中，将用于处理对 `/meals` 发出的 `GET` 请求的处理程序添加到 `Sources/Application/Application.swift` 文件：  

  ```swift
  router.get("/meals", handler: loadHandler)
  ```
  {: codeblock}

4. 通过将以下代码作为另一个函数添加到 `App` 类中，将 loadHandler 函数实现到 `Sources/Application/Application.swift` 文件：  

  ```swift
  func loadHandler(completion: ([Meal]?, RequestError?) -> Void ) {
      let meals: [Meal] = self.mealStore.map({ $0.value })
    completion(meals, nil)
  }
  ```
  {: codeblock"}

现在，您拥有 REST API 用于对 `/meals` 发出 `GET` 请求，这些请求使用 ` Meals` 数组或错误进行响应。

5. 运行项目。  
  按**运行**按钮或使用 `⌘+R` 快捷键。如果出现提示，请选择**允许入局网络连接**。

6. 测试 REST API。通过使用 `GET` 请求（与 Web 浏览器从服务器请求数据的方式一致），可以使用以下 URL 来测试 REST API：  
  ```
  * `GET /meals`:	[http://localhost:8080/meals]()
  ```

  返回了空数组 `[]`，因为 `mealStore` 中当前没有存储任何 `Meal` 对象。 

可以使用 [FoodTrackerBackend](https://github.com/IBM/FoodTrackerBackend) 教程，该教程可帮助您构建一组 REST API，用于存储、访存和删除 iOS 应用程序中的 `Meal` 对象，包括将数据存储在数据库中。
{: tip}

## 步骤 6. 将 KituraKit 安装到 iOS 应用程序中
使用 Kitura 服务器构建的 REST API 是标准 Web API，可通过任何应用程序使用，与使用的客户端库或编写客户端的语言无关。这意味着您可以使用 Alamofire、RestKit 或 URLSession 建立与服务器的连接。Kitura 还提供了一个 KituraKit 形式的经过优化的定制客户端连接器，以简化从 iOS 调用其 REST API 的过程。 

KituraKit 提供了 Kitura 中使用的路由器处理程序 API 的镜像映像，使其能够在客户端与服务器之间共享 Swift 类型，几乎不需其他工作。通过此功能，无需对服务器发送或接收的数据执行 JSON 编码和解码。

以下步骤说明如何将 KituraKit 安装到 iOS 应用程序中，并将其用于调用使用 Kitura 创建的 `GET /meals` REST API：

1. 如果在 iOS 应用程序目录的根目录中没有 pod 文件，请创建 pod 文件：
  ```
  pod init
  ```
  {: codeblock}

2. 编辑 pod 文件，为项目设置 iOS 11 的全局平台，方法是将以下行：
  ```
  # platform :ios, '9.0'
  ```
  {: codeblock}

  替换为以下代码：
	```
  platform :ios, '11.0'
  ```
  {: codeblock}

3. 通过在 `# Pods for <application name>` 下添加以下内容，将 KituraKit 添加到 pod 文件：
  ```
  pod 'KituraKit', :git => 'https://github.com/IBM-Swift/KituraKit.git', :branch => 'pod'
  ```
  {: codeblock}

4. 保存 pod 文件并使用以下命令安装 KituraKit：
  ```
  pod install
  ```
  {: codeblock}

5. 通过打开工作空间（而非项目）来重新在 Xcode 中打开应用程序。现在，可以向 Kitura 服务器中使用的 iOS 应用程序添加相同的 `Meal` 定义：
  ```swift
  struct Meal: Codable {    
      var name: String
      var photo: Data
      var rating: Int
  }
  ```
  {: codeblock}

  然后，使用以下代码来建立与 Kitura 服务器的连接：

  ```swift
  import KituraKit
  
  // 在 http://localhost:8080 上连接到 Kitura 服务器
  guard let client = KituraKit(baseURL: "http://localhost:8080") else {
      print("Error creating KituraKit client")
      return
  }
  
  // 发出请求 `GET /meals`，应该会返回 [Meal] 或 RequestError
  client.get("/meals") { (meals: [Meal]?, error: RequestError?) in
      // 检查是否有错误
      guard error == nil else {
          print("Error saving meal to Kitura: \(error!)")
          return
      }
      // 检查是否有 meals
      guard let meals = meals else {
          print("Received Meals!")
          return
      }
  }
  ```
  {: codeblock}

使用 `client.get("/meals")` 通过与 Kitura 的完成处理程序中的参数相匹配的回调来调用 Kitura 服务器。

可以使用 [FoodTrackerBackend](https://github.com/IBM/FoodTrackerBackend) 教程，该教程可帮助您构建一组 REST API，用于存储、访存和删除 iOS 应用程序中的 `Meal` 对象，包括将数据存储在数据库中。
{: tip}
## 后续步骤
现在，您已拥有 Kitura 服务器（提供可由 iOS 应用程序调用的 REST API），可随时将服务器部署到 {{site.data.keyword.cloud_notm}}。部署可以通过将 Containers 与 Kubernetes、Secure Containers 或 Cloud Foundry 配合使用来完成。