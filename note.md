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

# Scale

## autoscale

https://learn.microsoft.com/zh-cn/azure/azure-monitor/autoscale/autoscale-get-started?toc=%2Fazure%2Fapp-service%2Ftoc.json

Azure 应用服务计划（App Service Plan）提供了自动缩放的功能，允许根据应用程序的负载和需求动态调整应用服务的规模。以下是配置 App Service Plan 自动缩放的一般步骤：

选择应用服务计划： 进入 Azure 门户，导航到你的 App Service 计划。在左侧菜单中选择“缩放”。

配置缩放规则： 在缩放选项卡中，你可以配置自动缩放规则。主要的配置包括：

指标（Metric）： 选择一个或多个性能指标，例如 CPU 使用率、内存使用率、请求数等，作为触发自动缩放的依据。
操作符和阈值： 定义触发缩放的条件。例如，你可以设置 CPU 使用率大于某个阈值时触发扩展。
缩放方向： 选择“扩展”（Scale Out）或“缩减”（Scale In）。
实例计数： 指定在触发缩放时应添加或删除的实例数。
高级配置（可选）： 在高级配置中，你可以进一步定义缩放的行为，例如冷却期间（Cooldown），即在上一次缩放操作完成后的等待时间，以避免频繁的缩放。

保存并应用： 配置完缩放规则后，记得点击“保存”并在需要时点击“应用”以使更改生效。

# stage environment

https://learn.microsoft.com/zh-cn/azure/app-service/deploy-staging-slots?tabs=portal

## Staging Environment

"Staging Environment"（暂存环境）是软件开发和部署过程中的一个特定环境，用于进行测试和验证，以确保新代码或应用程序版本在发布到生产环境之前是稳定和可靠的。Staging 环境通常是在开发环境和生产环境之间的一个中间阶段，具有一些特定的特征：

测试新功能： Staging 环境是用于测试新功能、代码或应用程序版本的地方。开发团队通常会在这个环境中模拟生产环境，以确保新功能的正确性和性能。

性能测试： 在 Staging 环境中进行性能测试，以确保应用程序在真实负载情况下仍然能够正常运行。这包括测试应用程序的响应时间、吞吐量和资源利用率。

回归测试： 在 Staging 环境中进行回归测试，以确保新功能的引入不会破坏现有功能。这有助于捕获可能在新版本中引入的潜在问题。

集成测试： 将所有组件整合在 Staging 环境中进行测试，以确保它们在协同工作时没有冲突或问题。

与生产环境相似： Staging 环境通常被配置得与生产环境尽可能相似，包括硬件、网络配置和其他环境参数。这有助于确保在切换到生产环境时不会出现意外的问题。

版本管理： 使用 Staging 环境进行版本管理，确保部署到生产环境的代码或应用程序版本是经过充分测试和验证的。

蓝绿部署： 有时，Staging 环境用于执行蓝绿部署（Blue-Green Deployment），在两个环境之间切换以减少服务中断，并确保新版本的平稳部署。

故障排除： 如果在 Staging 环境中发现问题，团队可以在影响生产环境之前对其进行修复和调试。

总的来说，Staging 环境在软件开发和部署流程中扮演着关键的角色，帮助团队在将新功能或版本部署到生产环境之前发现和解决潜在问题。

## deployment slot

在 Azure 应用服务中，"Deployment Slot"（部署槽）是一项用于实现持续部署和应用程序版本管理的功能。Deployment Slot 允许你在同一 Azure 应用服务实例中运行多个独立的环境（槽），每个槽都可以包含不同版本的应用程序。

以下是 Deployment Slot 的一些关键概念：

主槽（Main Slot）： 每个 Azure 应用服务都有一个主槽，通常用于托管生产环境。生产环境中运行的是你应用的主要版本。

部署槽（Deployment Slot）： 除了主槽之外，你可以创建多个自定义的部署槽，每个槽都有独立的配置和设置。这些部署槽可以用于测试、预发布、演示等不同目的。

环境切换： 你可以将部署槽中的应用程序版本与主槽中的版本进行交换，从而实现零停机时间的部署。这样，你可以在不中断生产流量的情况下将新版本的应用程序推送到生产环境。

独立配置： 每个部署槽都可以有独立的应用程序配置、环境变量、连接字符串等设置。这允许你在不同的槽中测试不同的配置，而无需影响其他槽或生产环境。

持续部署： 部署槽通常与持续集成和持续部署（CI/CD）工作流结合使用。你可以在每次新版本构建时自动部署到一个或多个部署槽中，然后通过环境交换来更新生产环境。

应用性能监控： 每个部署槽都有独立的应用性能监控，可以帮助你监测和分析每个环境的性能指标。

通过使用 Deployment Slot，你可以更加安全和可控地进行应用程序的部署和测试，同时最小化对生产环境的影响。这是一种强大的功能，特别适用于需要频繁部署和测试的现代应用程序开发流程。

# Azure Functions

类似于aws lambda

https://learn.microsoft.com/zh-cn/azure/azure-functions/functions-overview?pivots=programming-language-csharp

##  hosting plan

https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale

### Consumption plan

Scale automatically and only pay for compute resources when your functions are running.

On the Consumption plan, instances of the Functions host are dynamically added and removed based on the number of incoming events.

✔ Default hosting plan.
✔ Pay only when your functions are running.
✔ Scales automatically, even during periods of high load.

### Premium plan

Automatically scales based on demand using pre-warmed workers, which run applications with no delay after being idle, runs on more powerful instances, and connects to virtual networks.

Consider the Azure Functions Premium plan in the following situations:

✔ Your function apps run continuously, or nearly continuously.
✔ You have a high number of small executions and a high execution bill, but low GB seconds in the Consumption plan.
✔ You need more CPU or memory options than what is provided by the Consumption plan.
✔ Your code needs to run longer than the maximum execution time allowed on the Consumption plan.
✔ You require features that aren't available on the Consumption plan, such as virtual network connectivity.
✔ You want to provide a custom Linux image on which to run your functions.

### Dedicated plan

Run your functions within an App Service plan at regular App Service plan rates.

Best for long-running scenarios where Durable Functions can't be used. Consider an App Service plan in the following situations:

✔ You have existing, underutilized VMs that are already running other App Service instances.
✔ Predictive scaling and costs are required.

## trigger and binding

https://learn.microsoft.com/zh-cn/azure/azure-functions/functions-triggers-bindings?tabs=isolated-process%2Cpython-v2&pivots=programming-language-csharp

触发器会导致函数运行。 触发器定义函数的调用方式，一个函数必须刚好有一个触发器。 触发器具有关联的数据，这些数据通常作为函数的有效负载提供。

绑定到函数是以声明方式将另一个资源连接到该函数的一种方式；绑定可以输入绑定和/或输出绑定的形式进行连接。 绑定中的数据作为参数提供给函数。

可根据需要，混合搭配不同的绑定。 绑定是可选的，一个函数可以有一个或多个输入绑定和/或输出绑定。

使用触发器和绑定可以避免对其他服务进行硬编码访问。 函数接收函数参数中的数据（例如，队列消息内容）。 使用函数的返回值发送数据（例如，用于创建队列消息）。

## Durable Functions

https://learn.microsoft.com/zh-cn/azure/azure-functions/durable/durable-functions-overview?tabs=in-process%2Cnodejs-v3%2Cv1-model&pivots=csharp

https://learn.microsoft.com/en-us/azure/azure-functions/durable/durable-functions-types-features-overview

Durable Functions 是 Azure Functions 的一个扩展，用于简化编写和管理具有状态的、长时间运行的工作流和异步操作。传统的 Azure Functions 是无状态的，它们通常设计为执行短期的计算任务。而 Durable Functions 则允许你编写能够保持状态并在长时间内执行的工作流。

以下是 Durable Functions 的一些关键特点：

状态保持： Durable Functions 允许你在函数之间保持状态。这使得你可以创建复杂的工作流，其中的每个步骤都能够访问和修改共享的状态。

长时间执行： 传统的 Azure Functions 有时间限制，通常是数分钟。而 Durable Functions 允许你执行长时间运行的操作，可以是数小时、数天，甚至更长。

决策： 你可以在 Durable Functions 中使用决策（orchestration）来定义工作流的逻辑。决策是一个编排函数的概念，它控制工作流中的执行流程，包括函数的调用、等待、分支和循环等。

定时器： Durable Functions 支持使用定时器，以便在特定时间触发工作流中的操作。这对于执行定期任务或超时处理非常有用。

Human Interaction： Durable Functions 支持与人类交互的能力，通过等待外部事件，比如等待用户输入或等待外部系统的响应。

失败处理： Durable Functions 提供了用于处理故障和重试的内置机制。你可以配置工作流的失败和重试策略。

监控： Durable Functions 集成了 Azure Monitor 和 Application Insights，可以提供对工作流执行的监控和诊断信息。

通过使用 Durable Functions，你可以更轻松地开发和维护复杂的分布式工作流，而无需担心状态管理、超时、重试等问题。这使得 Durable Functions 成为处理异步、长时间运行的任务和工作流的强大工具。

## Pattern #1: Function chaining

在函数链接模式中，将按特定顺序执行一系列函数。 在此模式中，一个函数的输出将应用到另一函数的输入。 每个函数之间的队列的使用可确保系统保持持久且可缩放，即使存在从一个函数到下一个函数的控制流也是如此。

## Pattern #2: Fan out/fan in

在扇出/扇入模式中，将会并行执行多个函数，然后等待所有函数完成。 通常会对这些函数返回的结果执行一些聚合操作。

## Pattern #3: Async HTTP APIs

异步 HTTP API 模式解决了使用外部客户端协调长时间运行的操作的状态时出现的问题。 实现此模式的一种常用方式是让 HTTP 终结点触发长时间运行的操作。 然后，将客户端重定向到某个状态终结点，客户端可轮询该终结点，以了解操作是何时完成的。

Durable Functions 原生支持此模式，可以简化甚至消除为了与长时间运行的函数执行进行交互而需要编写的代码。 例如，Durable Functions 快速入门示例（C#、JavaScript、TypeScript、Python、PowerShell 和 Java）演示了可用于启动新业务流程协调程序函数实例的简单 REST 命令。 启动实例后，该扩展会公开 Webhook HTTP API 用于查询业务流程协调程序函数的状态。

## Pattern #4: Monitor

监视模式是指工作流中的灵活重复进程。 例如，轮询到满足特定的条件为止。 可以使用常规计时器触发器解决简单方案（例如定期清理作业），但该方案的间隔是静态的，并且管理实例生存期会变得复杂。 可以使用 Durable Functions 创建灵活的重复间隔、管理任务生存期，以及从单个业务流程创建多个监视进程。

监视模式的一个例子是反转前面所述的异步 HTTP API 方案。 监视模式不会公开终结点供外部客户端监视长时间运行的操作，而是让长时间运行的监视器使用外部终结点，然后等待某个状态发生更改。

只需编写少量的代码行，即可使用 Durable Functions 创建多个监视器来观察任意终结点。 监视器在满足某个条件时可以结束执行，或者，另一函数可以使用持久业务流程客户端来终止监视器。 可以根据特定的条件（例如指数退避）更改监视器的 wait 间隔。

## Pattern #5: Human interaction

许多自动化过程涉及到某种人机交互。 自动化过程中涉及的人机交互非常棘手，因为人的可用性和响应能力不如云服务那样高。 自动化过程允许使用超时和补偿逻辑来实现这种交互。

审批过程就是涉及到人机交互的业务过程的一个例子。 例如，某份超出特定金额的开支报表需要经理的审批。 如果经理未在 72 小时内审批该开支报表（经理可能正在度假），则会启动上报过程，以便其他人（可能是经理的经理）进行审批。

## Pattern #6: Aggregator (stateful entities)

第六种模式涉及到将一段时间的事件数据聚合到单个可寻址的实体。 在此模式中，要聚合的数据可来自多个源、可分批传送，也可以分散在较长的时间段。 聚合器可能需要在事件数据到达时对其执行操作，而外部客户端可能需要查询聚合数据。

使用普通无状态函数尝试实现此模式的棘手之处在于，并发控制会成为一项巨大的挑战。 你不仅需要考虑到多个线程会同时修改相同的数据，而还要考虑如何确保聚合器每次仅在一个 VM 上运行。

可以使用持久实体轻松地将此模式实现为单一函数。

# Blob Storage

https://learn.microsoft.com/zh-cn/azure/storage/blobs/storage-blobs-introduction

Azure Blob 存储是 Microsoft 提供的适用于云的对象存储解决方案。 Blob 存储最适合存储巨量的非结构化数据。 非结构化数据是不遵循特定数据模型或定义的数据（如文本或二进制数据）。

## 层次

存储帐户
存储帐户中的容器
容器中的 Blob

存储帐户在 Azure 中为数据提供唯一的命名空间。 存储在 Azure 存储中的每个对象都有一个地址，其中包含唯一的帐户名称。 帐户名称与 Blob 存储终结点的组合构成了存储帐户中对象的基址。

例如，如果存储帐户名为 mystorageaccount，则 Blob 存储的默认终结点为：
http://mystorageaccount.blob.core.windows.net

容器对一组 blob 进行组织，类似于文件系统中的目录。 一个存储帐户可以包含无限数量的容器，一个容器可以存储无限数量的 Blob。

## Blob 类型

Azure 存储支持三种类型的 Blob：

* 块 Blob 存储文本和二进制数据。块 Blob 由可以分别管理的数据块构成。 块 blob 最多可存储约 190.7 TiB。
* 与块 Blob 一样，追加 Blob 也由块构成，但针对追加操作进行了优化。 追加 Blob 非常适用于诸如记录来自虚拟机的数据之类的场景。
* 页 Blob 用于存储最大 8 TiB 的随机访问文件。 页 blob 存储虚拟硬盘 (VHD) 文件并作为 Azure 虚拟机的磁盘。 有关页 Blob 的更多信息，请参阅 Azure 页 Blob 概述

## 冗余 Redundancy

https://learn.microsoft.com/zh-cn/azure/storage/common/storage-redundancy#locally-redundant-storage

* 本地冗余存储 (LRS) 在主要区域中的单个物理位置同步复制数据三次。 LRS 是成本最低的复制选项，但不建议对需要高可用性或持续性的应用程序使用此选项。
* 区域冗余存储 (ZRS) 跨主要区域中的三个 Azure 可用性区域同步复制数据。 对于需要高可用性的应用程序，Microsoft 建议在主要区域中使用 ZRS，并复制到次要区域。
* Geo-redundant storage
异地冗余存储 (GRS) 使用 LRS 在主要区域中的单个物理位置内同步复制数据三次。 然后，它将数据异步复制到距离主要区域数百英里以外的次要区域中的单个物理位置。 GRS 在一年中提供至少 99.99999999999999%（16 个 9）的存储资源持久性。
* Geo-zone-redundant storage
地域区域冗余存储 (GZRS) 将冗余跨可用性区域提供的高可用性与异地复制提供的区域中断保护相结合。 将跨主要区域中的三个 Azure 可用性区域复制 GZRS 存储帐户中的数据，并将其复制到次要地理区域，以防御区域灾难。 Microsoft 建议对需要最大程度的一致性、耐用性和可用性、卓越性能和灾难恢复复原能力的应用程序使用 GZRS。
* 启用 RA-GRS 或 RA-GZRS 后，次要区域可用于读取访问，因此你可以预先测试应用程序，以确保在发生服务中断时可以从次要区域正确读取数据。 
