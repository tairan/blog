---
layout: post
title: .Net 全球通用应用程序开发(一)
tags:
- .NET
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
开发全球化的软件，毫无疑问，Microsoft是很有发言权的。在.NET环境中我们如何开发全球化的软件呢？首先来看看一些来自MSDN的建议，自己在这些建议中加上自己的理解。
<a href="http://msdn.microsoft.com/zh-cn/library/w7x1y988.aspx" target="_blank">http://msdn.microsoft.com/zh-cn/library/w7x1y988.aspx</a>

<strong> 全球化最佳做法</strong>

   1.  在内部使应用程序代码成为 Unicode。
<em style="color:#996633">【Daniel】现在很多程序都使用UTF-8来编码，程序体积的增大已经不能构成什么影响了。</em>

   2.  使用 System.Globalization 命名空间提供的区域性识别类来操作和格式化数据。
          * 对于排序，使用 SortKey 类和 CompareInfo 类。
          * 对于字符串比较，使用 CompareInfo 类。
          * 对于日期和时间格式化，使用 DateTimeFormatInfo 类。
          * 对于数字格式化，使用 NumberFormatInfo 类。
          * 对于公历和非公历，使用 Calendar 类或特定的 Calendar 实现之一。
<em style="color:#996633">【Daniel】全球化带来的问题就是文化相关的冲突，如日历，日期显示的格式，钱币的符号，数字的格式化等。所以对这些文化相关的资源进行操作时就要使用上面提到的特有的操作。</em>

   3.   在适当的情况下，使用 System.Globalization.CultureInfo 类提供的区域性属性设置。使用 CultureInfo.CurrentCulture 属性来执行格式化任务，如日期和时间或数字的格式化。使用 CultureInfo.CurrentUICulture 属性来检索资源。请注意，CurrentCulture 和 CurrentUICulture 属性可以基于每个线程来设置。

   4.   通过使用 System.Text 命名空间中的编码类，使应用程序能够与各种编码相互进行数据读写。不要采用 ASCII 数据。假定在用户可以输入文本的任何位置都将提供国际字符。例如，在服务器名、目录、文件名、用户名和 URL 中接受国际字符。
<em style="color:#996633">【Daniel】ASCII 已经过时啦，UTF-8是向下兼容的。</em>

   5.   使用 UTF8Encoding 类时，出于安全原因，建议您使用此类提供的错误检测功能。要打开错误检测功能，请使用带有 throwOnInvalidBytes 参数的构造函数创建该类的实例，并将 throwOnInvalidBytes 的值设置为 true。
<em style="color:#996633">【Daniel】UTF-8也有BOM和非BOM之分。</em>

   6.    尽可能将字符串按整个字符串处理，而不是按一系列个别字符处理。这在排序或搜索子字符串时尤为重要。这可以防止与分析组合字符有关的问题。

   7.    使用 System.Drawing 命名空间提供的类来显示文本。
<em style="color:#996633">【Daniel】用Drawing的方式就不存在字符显示的问题了。</em>

   8.    为保持操作系统间的一致性，不要允许用户设置重写 CultureInfo。使用接受 useUserOverride 参数的 CultureInfo 构造函数，并将该参数设置为 false。

   9.    在国际操作系统版本上使用国际数据来测试应用程序功能。
<em style="color:#996633">【Daniel】也就是用模拟真实环境来进行测试。</em>

  10.    如果安全决策基于字符串比较或大小写更改操作的结果，请通过显式指定 CultureInfo.InvariantCulture 属性来执行不区分区域性的操作。这种做法确保结果不会受 CultureInfo.CurrentCulture 的值的影响。有关说明不区分区域性的字符串比较如何产生不一致结果的示例，请参见自定义大小写映射和排序规则。

<strong> 本地化最佳做法</strong>

   1.  将所有可本地化的资源移动到单独的纯资源 DLL 中。可本地化的资源包括用户界面元素，如字符串、错误信息、对话框、菜单以及嵌入的对象资源。
<em style="color:#996633">【Daniel】模块化。</em>

   2.  不要对字符串或用户界面资源进行硬编码。
<em style="color:#996633">【Daniel】硬编码是一时之爽，高潮过后，随之而来的是生孩子的痛苦。</em>

   3.  不要将不可本地化的资源放在纯资源 DLL 中。否则会使翻译人员产生困惑。
<em style="color:#996633">【Daniel】于人方便就是于己方便。</em>

   4.  不要使用在运行时从串联词组生成的复合字符串。复合字符串难以本地化，因为它们往往采用英语语法顺序，而此顺序并不适用于所有语言。
<em style="color:#996633">【Daniel】带来的是界面显示的问题，本来界面上字符的位置和大小是固定的，如果动态生成的组合词，翻译后位置和大小发生变化咋办？</em>

   5.  避免不明确的构造，如“Empty Folder”，因为根据字符串组成部分的语法规则，这些字符串可能产生不同的翻译。例如，“empty”既可以是一个动词，也可以是一个形容词，因此在诸如意大利语或法语等语言中就可能导致不同的翻译。
<em style="color:#996633">【Daniel】用词要精确，专业精神。</em>

   6.  避免在应用程序中使用包含文本的图像和图标。本地化这些图像和图标的成本是很大的。

   7.  允许在用户界面中为字符串长度的扩展保留足够的空间。在某些语言中，词组可能另外需要百分之五十到百分之七十五的空间。
<em style="color:#996633">【Daniel】未雨绸缪。</em>

   8.  使用 System.Resources.ResourceManager 类来根据区域性检索资源。

   9.  使用 Microsoft Visual Studio 2005 创建 Windows 窗体对话框，以便可以使用 Windows 窗体资源编辑器 (Winres.exe) 对它们进行本地化。不要对 Windows 窗体对话框进行手动编码。

  10. 安排进行专业本地化工作（翻译）。

  11. 有关创建并本地化资源的完整说明，请参见“应用程序中的资源”。

 <strong>ASP.NET 应用程序的全球化最佳做法</strong>

   1.  在应用程序中显式设置 CurrentUICulture 和 CurrentCulture 属性。不要依赖于默认设置。

   2.  请注意，ASP.NET 应用程序是托管应用程序，因此可以使用与其他托管应用程序相同的类，以根据区域性检索、显示和操作信息。

   3.  注意在 ASP.NET 中可以指定以下三种编码类型：
          *  requestEncoding 指定从客户端浏览器接收的编码。
          *  responseEncoding 指定要发送到客户端浏览器的编码。在大多数情形下，这应与 requestEncoding 是相同的。
          *  fileEncoding 指定用于 .aspx、.asmx 和 .asax 文件分析的默认编码。

   4.  在 ASP.NET 应用程序中的以下三个位置指定 requestEncoding、responseEncoding、fileEncoding、culture 和 uiCulture 属性的值：
          *  在 Web.config 文件的全球化一节中。此文件是 ASP.NET 应用程序的外部文件。有关更多信息，请参见 &lt;globalization&gt; 元素。
          *  在页面指令中。请注意，当应用程序在页面中时，文件已经被读取。因此，指定 fileEncoding 和 requestEncoding 为时已晚。只有 uiCulture、Culture 和 responseEncoding 可以在页面指令中指定。
          *  在应用程序代码中以编程方式指定。该设置可能随请求的不同而不同。同页面指令一样，到打开应用程序代码时，指定 fileEncoding 和 requestEncoding 为时已晚。只有 uiCulture、Culture 和 responseEncoding 可以在应用程序代码中指定。

   5.  请注意，uiCulture 可以设置为浏览器接受语言。
