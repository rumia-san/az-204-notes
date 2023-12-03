这些笔记来自chatgpt和官方文档。
我看的视频是https://youtu.be/tB_tBPfQJMI?si=1krligK_YuJim-9M
视频作者为A Guide To Cloud

# subscription

## subscription是什么

在 Microsoft Azure 中，一个 "subscription" 是对 Azure 服务的一种付费订阅。当你注册 Azure 账户时，你需要创建一个 Azure 订阅。这个订阅是与你的 Azure 账户相关联的，它允许你使用和管理 Azure 中的各种云服务。通过 Azure 订阅，你可以创建、部署和管理虚拟机、存储、数据库、Web 应用等各种云资源。

一些关键概念：

资源组（Resource Group）： 在一个订阅中，你可以创建一个或多个资源组，用于组织和管理相关的云资源。资源组是一种逻辑容器，方便你对资源进行组织和管理。

计费： 订阅是与计费紧密关联的，你将根据你的订阅使用情况来支付费用。Azure 提供不同类型的订阅，包括免费试用、付费订阅等，每种类型都有不同的计费模型。

权限和角色： 订阅中的资源的访问权限可以通过 Azure Active Directory（AAD）中的身份验证和授权来管理。Azure 使用基于角色的访问控制（RBAC）来控制用户对资源的访问权限。

管理工具： 你可以使用 Azure 门户、Azure CLI、PowerShell 等工具来管理和操作你的订阅中的资源。

在 Azure 中，每个订阅都有一个唯一的标识符（Subscription ID），用于在 Azure 服务中唯一标识该订阅。订阅是组织和管理 Azure 资源的核心概念，它为用户提供了一个框架，使其能够有效地利用 Azure 云服务。

## 和AWS中什么概念最接近

在AWS中，与Azure中的订阅（subscription）概念最接近的是AWS中的"账户"（Account）。

在AWS中，一个账户代表一个独立的、完全独立计费的实体。当你注册AWS账户时，你会创建一个唯一的AWS账户，该账户有一个唯一的12位数字的账户ID。AWS账户用于组织和管理AWS资源，以及在AWS中进行计费。

# azure app service plans

## azure app service plans是什么

Azure App Service Plans 是 Azure 中用于托管 Web 应用程序的一种服务计划。它提供了一种方式来分配资源、调整规模并管理运行应用程序的环境。下面是一些关键概念：

App Service Plan： 这是一个逻辑容器，用于定义一组共享相同计算资源和配置设置的 App Service Web 应用。App Service Plan 包括计算资源（例如虚拟机实例）、操作系统、网络资源等。一个 App Service Plan 可以托管一个或多个 Web 应用、API 应用、移动应用或后端服务。

Scale Up/Down： 通过更改 App Service Plan 的大小，你可以垂直缩放应用程序。这意味着你可以根据应用程序的需求调整计算资源的大小，例如，从共享层（Shared）升级到基本层（Basic）、标准层（Standard）、高级层（Premium）等。

Scale Out/In： 通过更改实例数，你可以水平缩放应用程序。这意味着你可以增加或减少运行应用程序的虚拟机实例的数量，以应对流量和负载的变化。

定价模型： App Service Plans 有不同的定价层，每个层次都提供不同的计算资源和功能。共享层适用于低流量的开发和测试，而标准、高级和高级加强层适用于更大规模的生产应用程序。

特定区域和可用性： App Service Plan 可以在特定的 Azure 区域中创建，以确保应用程序的高可用性和降低延迟。

总体而言，Azure App Service Plans 提供了一种方便的方式来管理和调整计算资源，以满足你的应用程序的性能和可伸缩性需求。通过使用 App Service Plans，你可以根据应用程序的需求有效地管理资源，同时最大程度地减少维护和配置的复杂性。


## 这个和aws的云服务中什么东西比较接近

在 AWS 中，与 Azure App Service Plans 相对应的服务主要是 AWS Elastic Beanstalk 和 AWS App Runner。这两个服务都提供了一种简化和自动化的方式来托管和部署 Web 应用程序，类似于 Azure App Service 的功能。

AWS Elastic Beanstalk： 这是一项完全托管的服务，允许你轻松部署、运行和扩展应用程序。类似于 Azure App Service Plan，Elastic Beanstalk 提供了环境的概念，你可以选择环境的规模、实例类型等。它支持多种语言和框架，并自动处理底层基础设施的管理。

AWS App Runner： 这是一个全托管的服务，专注于快速构建、部署和扩展容器化的应用程序。你只需提供你的应用程序代码和配置，App Runner 将处理底层的容器和基础设施管理。这使得它非常适合于开发人员快速部署应用程序而无需关心底层的运维细节。

虽然 Azure App Service Plans、AWS Elastic Beanstalk 和 AWS App Runner 在某些方面相似，但也有一些区别。选择其中一个服务通常取决于你的特定需求、技术栈和偏好。在比较这些服务时，你可能需要考虑到每个云提供商的特定功能、价格模型、集成选项以及支持的语言和框架。

## 文档

https://learn.microsoft.com/zh-cn/azure/app-service/overview-hosting-plans

应用服务计划的定价层确定了所提供的应用服务功能和计划费用。 应用服务计划可用的定价层取决于创建时选择的操作系统。 定价层包括以下：

* 共享计算：“免费”和“共享”，这两个基本层在其他应用服务应用（包括其他客户的应用）所在的同一个 Azure VM 上运行应用。 这些层将 CPU 配额分配给在共享资源上运行的每个应用，并且资源无法横向扩展。这些层仅用于开发和测试目的。
* 专用计算：“基本”、“标准”、“高级”、“高级 V2”和“高级 V3”层在专用的 Azure VM 上运行应用。 只有同一应用服务计划中的应用可以共享相同的计算资源。 层越高，可用于横向扩展的 VM 实例就越多。
* 独立：“独立”层和“独立 V2”层在专用的 Azure 虚拟网络中运行专用的 Azure VM。 它在计算隔离的基础上为应用提供了网络隔离。 此层提供最大的横向扩展能力。

* Shared compute: Free and Shared, the two base tiers, runs an app on the same Azure VM as other App Service apps, including apps of other customers. These tiers allocate CPU quotas to each app that runs on the shared resources, and the resources cannot scale out. These tiers are intended to be used only for development and testing purposes.
* Dedicated compute: The Basic, Standard, Premium, PremiumV2, and PremiumV3 tiers run apps on dedicated Azure VMs. Only apps in the same App Service plan share the same compute resources. The higher the tier, the more VM instances are available to you for scale-out.
* Isolated: The Isolated and IsolatedV2 tiers run dedicated Azure VMs on dedicated Azure Virtual Networks. It provides network isolation on top of compute isolation to your apps. It provides the maximum scale-out capabilities.

应用如何运行和缩放？

在“免费”和“共享”层中，应用遵循共享 VM 实例上的 CPU 分钟配额，且不能横向扩展。 在其他层中，应用按如下所述运行和缩放。

在应用服务中创建某个应用时，该应用会成为应用服务计划的一部分。 该应用运行时，将在应用服务计划中配置的所有 VM 实例上运行。 如果同一应用服务计划中包含多个应用，这些应用将共享相同的 VM 实例。 如果对某个应用使用多个部署槽位，所有部署槽位也在相同的 VM 实例上运行。 如果启用诊断日志、执行备份或运行 WebJob，它们也会使用这些 VM 实例上的 CPU 周期和内存。

于是，应用服务计划便成了应用服务应用的缩放单元。 如果将计划配置为运行五个 VM 实例，该计划中的所有应用将在所有五个实例上运行。 如果为计划配置了自动缩放，该计划中的所有应用将会根据自动缩放设置一起横向扩展。

# Configure App Service

https://learn.microsoft.com/zh-cn/azure/app-service/configure-common?tabs=portal

## Application Settings

环境变量： 在 Application Settings 中，你可以设置应用程序的环境变量。这些变量可以在你的应用程序代码中动态获取，以便根据不同环境配置不同的参数，如数据库连接字符串、API密钥等。

连接字符串： 如果你的应用程序需要连接到数据库或其他服务，你可以在 Application Settings 中设置连接字符串。这样，你可以在应用程序中引用这些连接字符串，而无需硬编码到代码中。

应用程序密钥： 对于需要进行身份验证的应用程序，你可以在 Application Settings 中设置应用程序密钥或密码。这些信息通常用于访问受保护的 API、服务或资源。

调整配置： Application Settings 允许你在 Azure 门户或通过 Azure CLI、PowerShell 等工具中动态调整你的应用程序配置，而无需重新部署整个应用。

多环境支持： 使用 Application Settings 可以更轻松地在不同的环境（如开发、测试、生产）中配置不同的设置，从而避免了在代码中硬编码这些配置。

## default document

此设置仅适用于 Windows 应用。

默认文档是在应用服务应用的根 URL 中显示的网页。 使用列表中第一个匹配文件。 如果应用使用的模块基于 URL 进行路由而不是提供静态内容，则无需使用默认文档。

## Path mapping

### 将 URL 路径映射到目录

默认情况下，应用服务从应用代码的根目录启动应用。 但某些 Web 框架不在根目录下启动。 例如，Laravel 在 public 子目录中启动。 例如，可在 http://contoso.com/public 中访问此类应用，但你通常需要改为将 http://contoso.com 定向到 public 目录。 如果应用的启动文件位于其他文件夹中，或者存储库包含多个应用程序，你可以编辑或添加虚拟应用程序和目录。

### 配置处理程序映射

对于 Windows 应用，可以自定义 IIS 处理程序映射和虚拟应用程序与目录。 使用处理程序映射可以添加自定义脚本处理程序用于处理特定文件扩展名的请求。

# inbound and outbound IP address

https://learn.microsoft.com/zh-cn/azure/app-service/overview-inbound-outbound-ips

在 Azure App Service 中，入站和出站 IP 地址与你的应用程序与外部通信时使用的 IP 地址相关。这些 IP 地址与特定的 App Service 实例关联，而且可能会因为应用服务计划（App Service Plan）的规模和配置而变化。

## 入站 IP 地址
概念： 入站 IP 地址是指外部请求到达你的应用程序时使用的 IP 地址。这主要与应用服务的 HTTP 请求相关。

## 出站 IP 地址
概念： 出站 IP 地址是指你的应用程序用于发起对外部服务的网络请求时使用的 IP 地址。
