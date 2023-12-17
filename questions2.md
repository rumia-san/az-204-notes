231

Question #: 21
Topic #: 5

DRAG DROP -
You develop and deploy an Azure App Service web app. The web app accesses data in an Azure SQL database.
You must update the web app to store frequently used data in a new Azure Cache for Redis Premium instance.
You need to implement the Azure Cache for Redis features.
Which feature should you implement? To answer, drag the appropriate feature to the correct requirements. Each feature may be used once, more than once, or not at all. You may need to drag the split bar between panes or scroll to view content.
NOTE: Each correct selection is worth one point.
Select and Place:

![](./img2/231-1.png)

![](./img2/231-2.png)

This is correct!
https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching

If you look for the right words (related > set | high-performance > channel | recent > list) in documentation, it helps you validate this answer.
Ignore the other comments as it only leads to confusion.

Set（集合）：

解释： Redis 中的 Set 是一个无序的、不包含重复元素的数据结构。你可以使用 Set 存储多个值，但这些值不会有序排列。Set 支持添加、删除和检查元素的操作，是一个用于存储唯一值的有效结构。

List（列表）：

解释： Redis 中的 List 是一个有序的、可以包含重复元素的数据结构。它类似于一个动态数组，支持在两端添加和删除元素。List 常用于实现队列、堆栈等数据结构。

Channel（频道）：

解释： Redis 中的 Channel 是与发布/订阅模式相关的概念。发布/订阅模式允许多个客户端订阅某个频道，当消息发布到频道时，所有订阅该频道的客户端都会接收到该消息。这对于实现消息传递和事件通知非常有用。

---

232

Question #: 22
Topic #: 5

You are developing an ASP.NET Core Web API web service. The web service uses Azure Application Insights for all telemetry and dependency tracking. The web service reads and writes data to a database other than Microsoft SQL Server.
You need to ensure that dependency tracking works for calls to the third-party database.
Which two dependency telemetry properties should you use? Each correct answer presents part of the solution.
NOTE: Each correct selection is worth one point.

	A. Telemetry.Context.Cloud.RoleInstance
	B. Telemetry.Id
	C. Telemetry.Name
	D. Telemetry.Context.Operation.Id
	E. Telemetry.Context.Session.Id


Correct Answer: B and D
message.Properties.Add("ParentId", operation.Telemetry.Id);
message.Properties.Add("RootId", operation.Telemetry.Context.Operation.Id);

Reference:
https://docs.microsoft.com/en-us/azure/azure-monitor/app/custom-operations-tracking#enqueue

---

233

Question #: 23
Topic #: 5

HOTSPOT -
You are using Azure Front Door Service.
You are expecting inbound files to be compressed by using Brotli compression. You discover that inbound XML files are not compressed. The files are 9 megabytes (MB) in size.
You need to determine the root cause for the issue.
To answer, select the appropriate options in the answer area.
NOTE: Each correct selection is worth one point.
Hot Area:

![233-1](./img2/233-1.jpg)

	1.Yes
	2.No Refer - https://docs.microsoft.com/en-us/azure/frontdoor/front-door-caching ,You don’t need to purge the cache assets. Here the issue is that the file size needs to be less than 8MB
	3.Yes

---

234

Question #: 24
Topic #: 5

HOTSPOT -
You are developing an Azure App Service hosted ASP.NET Core web app to deliver video-on-demand streaming media. You enable an Azure Content Delivery
Network (CDN) Standard for the web endpoint. Customer videos are downloaded from the web app by using the following example URL: http://www.contoso.com/ content.mp4?quality=1.
All media content must expire from the cache after one hour. Customer videos with varying quality must be delivered to the closest regional point of presence
(POP) node.
You need to configure Azure CDN caching rules.
Which options should you use? To answer, select the appropriate options in the answer area.
NOTE: Each correct selection is worth one point.
Hot Area:

![234-1](./img2/234-1.jpg)

![234-2](./img2/234-2.jpg)

Box 1: Override
Override: Ignore origin-provided cache duration; use the provided cache duration instead. This will not override cache-control: no-cache.
Set if missing: Honor origin-provided cache-directive headers, if they exist; otherwise, use the provided cache duration.
Bypass cache: Do not cache and ignore origin-provided cache-directive headers.

因为我们要规定1小时，所以要override

Box 2: 1 hour
All media content must expire from the cache after one hour.

题目里说了要1小时

Box 3: Cache every unique URL
Cache every unique URL: In this mode, each request with a unique URL, including the query string, is treated as a unique asset with its own cache. For example, the response from the origin server for a request for example.ashx?q=test1 is cached at the POP node and returned for subsequent caches with the same query string. A request for example.ashx?q=test2 is cached as a separate asset with its own time-to-live setting.

Bypass caching for query strings: In this mode, requests with query strings are not cached at the CDN POP node. The POP node retrieves the asset directly from the origin server and passes it to the requestor with each request.

Ignore query strings: Default mode. In this mode, the CDN point-of-presence (POP) node passes the query strings from the requestor to the origin server on the first request and caches the asset. All subsequent requests for the asset that are served from the POP ignore the query strings until the cached asset expires.

不同质量的视频要有不同的cache，所以每个url都要cache

---

235

Question #: 25
Topic #: 5

HOTSPOT -
You are developing an ASP.NET Core time sheet application that runs as an Azure Web App. Users of the application enter their time sheet information on the first day of every month.
The application uses a third-party web service to validate data.
The application encounters periodic server errors due to errors that result from calling a third-party web server. Each request to the third-party server has the same chance of failure.
You need to configure an Azure Monitor alert to detect server errors unrelated to the third-party service. You must minimize false-positive alerts.
How should you complete the Azure Resource Manager template? To answer, select the appropriate options in the answer area.
NOTE: Each correct selection is worth one point.
Hot Area:

![235-1](./img2/235-1.jpg)

![235-2](./img2/235-2.jpg)

DynamicThresholdCriterion: Dynamic thresholds in metric alerts use advanced machine learning to learn metric
Http5XX, just a name , we are monitoring server errors, so 500 range error reponses
AlertSensitvity : would set is to low. "You must minimize false-positive alerts" 


---

236

Question #: 26
Topic #: 5

You are developing a web application that uses Azure Cache for Redis. You anticipate that the cache will frequently fill and that you will need to evict keys.
You must configure Azure Cache for Redis based on the following predicted usage pattern: A small subset of elements will be accessed much more often than the rest.
You need to configure the Azure Cache for Redis to optimize performance for the predicted usage pattern.
Which two eviction policies will achieve the goal?
NOTE: Each correct selection is worth one point.

A. noeviction
B. allkeys-lru
C. volatile-lru
D. allkeys-random
E. volatile-ttl
F. volatile-random

Suggested Answer: BC


在预测的使用模式中，小部分元素将比其他元素更频繁地访问。为了优化性能，你可以选择以下两个逐出策略：

B. allkeys-lru

说明： 使用最近最少使用（LRU）策略逐出所有键，这意味着最近最少被访问的键将被优先逐出。

C. volatile-lru

说明： 使用LRU策略逐出有过期时间的键，这允许你在键具有过期时间时执行LRU策略，确保对小部分元素的频繁访问。

其他选项的说明：

A. noeviction： 不进行逐出，当内存不足时，将返回错误。这可能导致性能问题，因为没有逐出机制。
D. allkeys-random： 随机逐出所有键，这不太适合小部分元素经常被访问的场景。
E. volatile-ttl： 使用键的过期时间进行逐出。不太适合场景，因为键的过期时间可能不与最近的访问模式对应。
F. volatile-random： 随机逐出有过期时间的键，也不太适合小部分元素经常被访问的场景。
因此，正确的答案是 B. allkeys-lru 和 C. volatile-lru。

---

237

Question #: 27
Topic #: 5

DRAG DROP -
An organization has web apps hosted in Azure.
The organization wants to track events and telemetry data in the web apps by using Application Insights.
You need to configure the web apps for Application Insights.
Which three actions should you perform in sequence? To answer, move the appropriate actions from the list of actions to the answer area and arrange them in the correct order.
Select and Place:

![237-1](./img2/237-1.jpg)

![237-2](./img2/237-2.jpg)

The given answer is correct.
	1. Create an Application Insights resource
	2. Copy the instrumentation key
	3. Install the SDK in your app
https://learn.microsoft.com/en-us/azure/azure-monitor/app/create-new-resource


---

238

Question #: 28
Topic #: 5

An organization hosts web apps in Azure. The organization uses Azure Monitor.
You discover that configuration changes were made to some of the web apps.
You need to identify the configuration changes.
Which Azure Monitor log should you review?

	A. AppServiceAppLogs
	B. AppServiceEnvironmentPlatformlogs
	C. AppServiceConsoleLogs
	D. AppServiceAuditLogs

Suggested Answer: B 

AppServiceEnvironmentPlatformlogs only logs when app services are hosted in an App Service Environment witch is a deployment of Azure App Service into a subnet in your Azure Virtual Network (VNet). It is a Premium service option

The problem is, all other anwers are wrong :
AppServiceAppLogs : logs from inside your app
AppServiceConsoleLogs : logs from the console
AppServiceAuditLogs : logs who are logged in or out.

but...
AppServiceFileAuditLogs will do the job for premium tiers.
https://ruslany.net/2020/01/how-to-monitor-azure-app-service-content-changes-and-publishing-activity/


---

239

Question #: 29
Topic #: 5

You develop and deploy an Azure App Service web app to a production environment. You enable the Always On setting and the Application Insights site extensions.
You deploy a code update and receive multiple failed requests and exceptions in the web app.
You need to validate the performance and failure counts of the web app in near real time.
Which Application Insights tool should you use?

	A. Profiler
	B. Smart Detection
	C. Live Metrics Stream
	D. Application Map
	E. Snapshot Debugger

Suggested Answer: C 

the key is near real time.
https://learn.microsoft.com/en-us/azure/azure-monitor/app/live-stream

---

240

Question #: 30
Topic #: 5

HOTSPOT -
You deploy an ASP.NET web app to Azure App Service.
You must monitor the web app by using Application Insights.
You need to configure Application Insights to meet the requirements.
Which feature should you use? To answer, select the appropriate options in the answer area.
NOTE: Each correct selection is worth one point.
Hot Area:

![240-1](./img2/240-1.png)

![240-2](./img2/240-2.png)

---

241

Question #: 31
Topic #: 5

You are building a web application that performs image analysis on user photos and returns metadata containing objects identified. The image analysis is very costly in terms of time and compute resources. You are planning to use Azure Redis Cache so duplicate uploads do not need to be reprocessed.
In case of an Azure data center outage, metadata loss must be kept to a minimum.
You need to configure the Azure Redis cache instance.
Which two actions should you perform? Each correct answer presents part of the solution.
NOTE: Each correct selection is worth one point.

	A. Configure Azure Redis with AOF persistence.
	B. Configure Azure Redis with RDB persistence.
	C. Configure second storage account for persistence.
	D. Set backup frequency to the minimum value.

The key here is "In case of an Azure data center outage, metadata loss must be kept to a minimum."

So the correct answer is AC.

使用 AOF（Append-Only File）持久性，可以将写命令追加到持久性日志文件中，以便在 Redis 重新启动时重新执行这些命令。这有助于确保在 Azure 数据中心中断的情况下最小化元数据损失。

---

242

Question #: 32
Topic #: 5

You are developing an Azure-based web application. The application goes offline periodically to perform offline data processing. While the application is offline, numerous Azure Monitor alerts fire which result in the on-call developer being paged.
The application must always log when the application is offline for any reason.
You need to ensure that the on-call developer is not paged during offline processing.
What should you do?

	A. Add Azure Monitor alert processing rules to suppress notifications.
	B. Disable Azure Monitor Service Health Alerts during offline processing.
	C. Create an Azure Monitor Metric Alert.
	D. Build an Azure Monitor action group that suppresses the alerts.

A

要确保在离线处理期间不会向在线开发人员发送警报，你可以选择以下操作：

A. 添加 Azure Monitor 警报处理规则以抑制通知。

说明： 通过配置警报处理规则，你可以在离线处理期间抑制通知，防止在此时触发通知。
其他选项的说明：

B. 在离线处理期间禁用 Azure Monitor 服务健康警报： 这样做会禁用与 Azure 服务健康相关的警报，但可能无法直接解决离线处理期间的问题。
C. 创建 Azure Monitor Metric Alert（指标警报）： 指标警报通常用于监视特定指标的变化，而在此场景中，问题是应用程序是否在线，因此指标警报可能不是最合适的选择。
D. 构建一个 Azure Monitor 操作组来抑制警报： 这是正确的思路，但通常使用警报处理规则更为直观和方便。
因此，最合适的答案是 A. 添加 Azure Monitor 警报处理规则以抑制通知。

---

243

Question #: 33
Topic #: 5

You are developing an online game that includes a feature that allows players to interact with other players on the same team within a certain distance. The calculation to determine the players in range occurs when players move and are cached in an Azure Cache for Redis instance.

The system should prioritize players based on how recently they have moved and should not prioritize players who have logged out of the game.

You need to select an eviction policy.

Which eviction policy should you use?

	A. allkeys-Iru
	B. volatile-Iru
	C. allkeys-lfu
	D. volatile-ttl
	
B

Changed my mind;
There must be a way to tell our redis that logged off users must not be prioritized.
Sample: User A moves and then automatically logs-off. With allkeys-lru we can't distinguish this particularity. With volatile-lru we can tell our redis what are good candidates to be removed using different TTL values.


在这种情况下，你应该选择 B. volatile-lru 作为逐出策略。

B. volatile-lru：

说明： 该策略使用最近最少使用（LRU）算法逐出有过期时间的键。这意味着 Redis 会优先逐出最近最少被访问的有过期时间的键，有助于确保离线或不再移动的玩家不会长时间保留在缓存中。因为在游戏中，最近移动的玩家可能更有可能与其他玩家进行交互，所以通过该策略，你可以优化缓存以满足这个要求。
其他选项的说明：

A. allkeys-lru： 使用 LRU 策略逐出所有键，而不仅仅是有过期时间的键。这在不同的场景中可能更适用，但在这个特定的游戏场景中，优先逐出有过期时间的键更有针对性。
C. allkeys-lfu： 使用最不经常使用（LFU）算法逐出所有键。在这个场景中，基于最近的移动更为重要，所以 LRU 可能更合适。
D. volatile-ttl： 使用键的过期时间进行逐出。这可能不是最佳选择，因为过期时间可能不与最近的移动模式直接对应。
因此，正确的答案是 B. volatile-lru。

---

244

Question #: 34
Topic #: 5

You develop an Azure App Service web app and deploy to a production environment. You enable Application Insights for the web app.

The web app is throwing multiple exceptions in the environment.

You need to examine the state of the source code and variables when the exceptions are thrown.

Which Application Insights feature should you configure?

A. Smart detection
B. Profiler
C. Snapshot Debugger
D. Standard test

Suggested Answer: C

---

245

Question #: 35
Topic #: 5

DRAG DROP

You develop and deploy a Java application to Azure. The application has been instrumented by using the Application Insights SDK.

The telemetry data must be enriched and processed before it is sent to the Application Insights service.

You need to modify the telemetry data.

Which Application Insights SDK features should you use? To answer, drag the appropriate features to the correct requirements. Each feature may be used once, more than once, or not at all. You may need to drag the split bar between panes or scroll to view content.

NOTE: Each correct selection is worth one point.

![245-1](./img2/245-1.png)

![245-2](./img2/245-2.png)

Correct answers
Link: https://learn.microsoft.com/en-us/azure/azure-monitor/app/api-filtering-sampling

---

246

Question #: 36
Topic #: 5

HOTSPOT

You develop new functionality in a web application for a company that provides access to seismic data from around the world. The seismic data is stored in Redis Streams within an Azure Cache for Redis instance.

The new functionality includes a real-time display of seismic events as they occur.

You need to implement the Azure Cache for Redis command to receive seismic data.

How should you complete the command? To answer, select the appropriate options in the answer area.

NOTE: Each correct selection is worth one point.

![246-1](./img2/246-1.png)

![246-2](./img2/246-2.png)

Correct.
BLOCK 0 means that we will wait infinitely (timeout 0 means it will never expire) for new items in a stream.
$ ID means that we will receive only new messages, starting from the time we started listening

https://redis.io/docs/data-types/streams-tutorial/#listening-for-new-items-with-xread

---

247

Question #: 37
Topic #: 5

You develop an ASP.NET Core app that uses Azure App Configuration. You also create an App Configuration containing 100 settings.

The app must meet the following requirements:

• Ensure the consistency of all configuration data when changes to individual settings occur.
• Handle configuration data changes dynamically without causing the application to restart.
• Reduce the overall number of requests made to App Configuration APIs.

You must implement dynamic configuration updates in the app.

What are two ways to achieve this goal? Each correct answer presents part of the solution.

NOTE: Each correct selection is worth one point.

	A. Create and register a sentinel key in the App Configuration store. Set the refreshAll parameter of the Register method to true.
	B. Increase the App Configuration cache expiration from the default value.
	C. Decrease the App Configuration cache expiration from the default value.
	D. Create and configure Azure Key Vault. Implement the Azure Key Vault configuration provider.
	E. Register all keys in the App Configuration store. Set the refreshAll parameter of the Register method to false.
	F. Create and implement environment variables for each App Configuration store setting.

AB 不确定

Correct Answers
Link: https://learn.microsoft.com/en-us/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-netfx

Quotes from the reference below:
"A sentinel key is a key that you update after you complete the change of all other keys. Your app monitors the sentinel key. When a change is detected, your app refreshes all configuration values. This approach helps to ensure the consistency of configuration in your app and reduces the overall number of requests made to your App Configuration store, compared to monitoring all keys for changes."

"You can add a call to the refreshOptions.SetCacheExpiration method to specify the minimum time between configuration refreshes. In this example, you use the default value of 30 seconds. Adjust to a higher value if you need to reduce the number of requests made to your App Configuration store."

创建和注册一个 sentinel key（一个特殊的 key），当配置发生更改时，将改变这个 sentinel key 的值，以触发应用程序动态更新。将 refreshAll 参数设置为 true 以确保刷新所有配置，确保一致性。

Reference: https://learn.microsoft.com/en-us/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core?tabs=core6x

---

248

Question #: 38
Topic #: 5

HOTSPOT

You develop and deploy an Azure App Service web app that connects to Azure Cache for Redis as a content cache. All resources have been deployed to the East US 2 region.

The security team requires the following audit information from Azure Cache for Redis:

• The number of Redis client connections from an associated IP address.
• Redis operations completed on the content cache.
• The location (region) in which the Azure Cach3e for Redis instance was accessed.

The audit information must be captured and analyzed by a security team application deployed to the Central US region.

You need to log information on all client connections to the cache.

Which configuration values should you use? To answer, select the appropriate options in the answer area.

NOTE: Each correct selection is worth one point.

![248-1](./img2/248-1.png)

![248-2](./img2/248-2.png)

Correct.
Only Log Analytics supports cross-region logging

Reference: https://learn.microsoft.com/en-us/azure/azure-cache-for-redis/cache-monitor-diagnostic-settings?tabs=basic-standard-premium#enable-connection-logging-using-the-azure-portal

Log Analytics Workspace - used to store log information.
Diagnostic setting - diagnostic logs are streamed to that workspace as soon as new event data is generated

---

249

Question #: 39
Topic #: 5
[All AZ-204 Questions]
You develop and deploy a web app to Azure App Service. The Azure App Service uses a Basic plan in a single region.

Users report that the web app is responding slow. You must capture the complete call stack to help identify performance issues in the code. Call stack data must be correlated across app instances. You must minimize cost and impact to users on the web app.

You need to capture the telemetry.

Which three actions should you perform? Each correct answer presents part of the solution.

NOTE: Each correct selection is worth one point.

	A. Restart all apps in the App Service plan.
	B. Enable Application Insights site extensions.
	C. Upgrade the Azure App Service plan to Premium.
	D. Enable Profiler.
	E. Enable the Always On setting for the app service.
	F. Enable Snapshot debugger.
	G. Enable remote debugging.

BDF 不确定

---

250

Question #: 40
Topic #: 5

You are building an application to track cell towers that are available to phones in near real time. A phone will send information to the application by using the Azure Web PubSub service. The data will be processed by using an Azure Functions app. Traffic will be transmitted by using a content delivery network (CDN).

The Azure function must be protected against misconfigured or unauthorized invocations.

You need to ensure that the CDN allows for the Azure function protection.

Which HTTP header should be on the allowed list?

	A. Authorization
	B. WebHook-Request-Callback
	C. Resource
	D. WebHook-Request-Origin

Suggested Answer: D

https://learn.microsoft.com/en-us/azure/azure-web-pubsub/howto-develop-eventhandler#upstream-and-validation

通过 Azure 门户或 CLI 设置事件处理程序 Webhook 时，服务遵循 CloudEvents 滥用保护措施来验证上游 Webhook。 每个已注册的上游 Webhook URL 都将通过此机制进行验证。 WebHook-Request-Origin 请求头设置为服务域名 xxx.webpubsub.azure.com，它会要求含标头 WebHook-Allowed-Origin 的响应包含此域名或 *。


