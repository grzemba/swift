---

copyright:
  years: 2018
lastupdated: "2018-11-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 使用 CLI 建立伺服器端 Swift 應用程式
{: #swift_cli}

{{site.data.keyword.cloud}} 提供解決方案及服務，讓 Swift 開發人員及應用程式可以提供客戶所需的安全性、AI 及價值。有了廣泛的產品組合及 SDK，您可以使用這些服務，並將最頂尖的應用程式快速推向市場。
{: shortdesc}

下列手冊旨在協助您建置、本端執行及部署伺服器端 Swift 應用程式。學習如何使用 {{site.data.keyword.dev_cli_long}}，以利用標準指令來執行這些動作。

您可以使用 {{site.data.keyword.dev_cli_short}}，利用許多指令來管理您的伺服器端應用程式。在 [IBM Cloud Developer Tools CLI](/docs/cli/idt/commands.html) 中，可進一步瞭解 `ibmcloud dev` 指令。

## 步驟 1. 開發人員需求

若要開始使用 {{site.data.keyword.cloud_notm}}，請確定您符合下列需求。

### 作業系統

開發 Swift 應用程式的最佳作法是使用最新的 MacOS 支援硬體，並使用最新的 iOS 版本進行測試。註冊一個 [Apple Developer](https://developer.apple.com/) 帳戶，以在實體裝置上進行測試。

### iOS 及 Xcode
{: #ios_and_xcode}

- [安裝 Xcode 8+（或更新版本）](https://developer.apple.com/xcode/)
- [部署至 iOS 裝置第 8 版（或更新版本）](https://support.apple.com/downloads/ios)
- 將應用程式提交至 Apple 之前，請檢閱 [App Store 提交準則](https://developer.apple.com/app-store/guidelines/)

### SDK 及相依關係管理

下列工具確保您可以安裝原生 SDK，以使用各種 {{site.data.keyword.cloud_notm}} 服務。

- [安裝 CocoaPods（適用於 IBM Cloud SDK）](https://cocoapods.org/)
  ```
  sudo gem install cocoapods
  ```
  {: codeblock}
  
- [安裝 Homebrew 以協助安裝 Carthage](https://brew.sh/)
  ```
  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  ```
  {: codeblock}

- [安裝 Carthage（適用於 Watson SDK）](https://github.com/Carthage/Carthage)
  ```
  brew install carthage
  ```
  {: codeblock}

## 步驟 2. 安裝工具以進行本端開發

{{site.data.keyword.cloud}} 提供本端 CLI 工具，協助您使用各方面的 {{site.data.keyword.cloud_notm}}。如需相關資訊，請參閱 [{{site.data.keyword.dev_cli_long}} 資訊](../cli/index.html)。在雲端部署之前，您可以使用工具來測試本端 Docker 映像檔中的 Swift 後端。

* 若為 MacOS 及 Linux，請執行下列指令：
  ```
  curl -sL http://ibm.biz/idt-installer | bash
  ```
  {: codeblock}

* 若為 Windows 10，請以系統管理員身分執行下列指令：
  ```
  Set-ExecutionPolicy Unrestricted; iex(New-Object Net.WebClient).DownloadString('http://ibm.biz/idt-win-installer')
  ```
  {: codeblock}

  在 Windows PowerShell 圖示上按一下滑鼠右鍵，然後選取**以系統管理員身分執行**。
  {: tip}

## 步驟 3. 建立 Swift 應用程式

1. 從 {{site.data.keyword.dev_cli_short}} CLI 執行 `ibmcloud dev create` 指令，以產生預先配置的入門範本。 
  ```
  ibmcloud dev create
  ```
  {: codeblock}

  請務必以 {{site.data.keyword.cloud_notm}} 帳戶登入，以建立專案。第一次，使用者可以[登錄 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/registration/?cm_sp=dw-bluemix-_-swift-_-devcenter)，取得一個免費帳戶。使用 `ibmcloud login` 指令，即可在指令行上登入。
  {: tip}

2. 系統提示您時，依序選取選項 1、6、2，如下列範例所示：
  ```
  ? Select a resource type:                  
  1. Backend Service / Web App
  2. Mobile Client
  Enter a number> 1

  ? Select a language:
  1. Java - MicroProfile / Java EE
  2. Java - Spring
  3. Node
  4. Python - Django
  5. Python - Flask
  6. Swift
  Enter a number> 6

  ? Select a Starter Kit:
  1. Backend for Frontend - Swift Kitura - A starter for building 
  backend-for-frontend APIs in Swift, using the Kitura framework.
  2. Web App - Create Project
  3. Web App - Swift Kitura Basic - A starter that provides a basic web serving 
  application in Swift, using the Kitura framework.
  Enter a number> 2
  ```
  {: screen}

3. 為您的應用程式提供一個名稱：
  ```
  ? Enter a name for your application> swift_project
  ```
  {: screen}

4. 選擇啟用 OpenAPI 2.0 支援：
  ```
  ? Enable your application based on an OpenAPI 2.0 Specification document? [y/n]> y
  ```
  {: screen}

  如果 OpenAPI 2.0 支援已啟用，您必須提供 OpenAPI 2.0 文件的路徑作為 URL：
  ```
  ? Path to OpenAPI 2.0 document as a url (both yaml and json formats supported)> http://hostname.domain.com/path/to/file.json

  Generating application ...
  ```
  {: screen}

## 步驟 4. 建置、執行及部署應用程式

您現在可以使用 {{site.data.keyword.dev_cli_short}} 來建置、執行及部署您的應用程式。

1. **建置**

  您現在可以建置您的應用程式，這是執行應用程式的必要條件。在應用程式目錄的根目錄中使用下列指令，以建置您的應用程式：
  ```
  ibmcloud dev build
  ```
  {: codeblock}

2. **執行**

  成功建置之後，您可以使用下列指令，在本端容器中執行您的應用程式：
  ```
  ibmcloud dev run
  ```
  {: codeblock}

  如果指令執行成功，則會顯示本端主機及埠，以檢視您應用程式的登入頁面。

3. **部署**

  使用 `deploy` 指令，將您的應用程式部署至 {{site.data.keyword.cloud_notm}}：
  ```
  ibmcloud dev deploy
  ```
  {: codeblock}

## 後續步驟

學習使用 {{site.data.keyword.cloud_notm}} Developer Console for Apple，其可讓開發人員透過各種「入門範本套件」建立應用程式、佈建及連接重要的 {{site.data.keyword.cloud_notm}} 最佳化服務，然後快速下載工作中的程式碼，或針對持續交付進行設定。使用者可以建立、檢視、配置及管理您的應用程式，以及下載您應用程式的程式碼。使用 Developer Console for Apple，您可以快速評估，並以全新的應用程式來測試 {{site.data.keyword.cloud_notm}} 服務。

準備好了嗎？請立即造訪 [{{site.data.keyword.cloud_notm}} Developer Console for Apple](https://console.bluemix.net/developer/appledevelopment/starter-kits)，以開始使用。
{: tip}

如需相關資訊，請參閱[使用入門範本套件來開發 Swift 應用程式](/docs/swift/starter_kit/starter_kits.html)。
