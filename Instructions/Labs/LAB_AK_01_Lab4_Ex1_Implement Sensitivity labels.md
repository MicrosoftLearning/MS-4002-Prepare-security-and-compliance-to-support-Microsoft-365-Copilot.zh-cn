# 学习路径 1 - 实验室 4 - 练习 1 - 使用 Microsoft Entra ID 保护实现敏感度标签

你扮演 Adatum 的新 Microsoft 365 管理员 Holly Dickson，已将 Microsoft 365 部署到虚拟化实验室环境中。 随着 Microsoft 365 试点项目的推进，后续步骤是在 Adatum 中使用 Microsoft Purview 信息保护实现敏感度标签。 在本实验室中，你将创建和发布标签，并测试已发布的标签。 但是，不用测试你在本实验室中创建的标签， 你将测试其他标签。

**重要提示：** 发布新的敏感度标签和标签策略时，可能需要最多 24 小时才能通过 Microsoft 365 传播。 因此，你无法测试你在本实验室中创建的标签， 而是测试名为 Project - Falcon 的已有的敏感度标签****。 这个预先存在的标签与你将创建的标签几乎相同，因此，如果能够测试你创建的标签，你将会看到基本相同的结果。 


### 任务 1 – 安装 Microsoft Purview 信息保护客户端

若要在 Adatum 的试点项目中实现敏感度标签，必须先从 Microsoft 下载中心安装 **Microsoft Purview 信息保护客户端**。

1. 在上一个实验室结束时，你使用的是 LON-CL2。 请切换到 LON-CL1****。  <br/>

    你仍应以 **adatum\administrator** 帐户的身份登录到 LON-CL1，并且在 Edge 浏览器中，你仍应以 **Holly Dickson** 身份登录到 Microsoft 365。 

2. 在“Microsoft Edge”**** 中打开一个新标签页，然后在地址栏中输入（或复制粘贴）以下 URL：**https://www.microsoft.com/download/details.aspx?id=53018** <br/>

    此时将开始下载 **Microsoft Purview 信息保护客户端**。

3. 在页面右上角显示的“下载”窗口中，你将看到正在下载 PurviewInfoProtection.exe 文件********。 文件下载完成后，选择文件名下方显示的“打开文件”链接****。

4. 系统会打开“Microsoft Azure 信息保护”向导****。 如果向导未显示在桌面上，请选择任务栏上的向导图标以显示向导。

5. 在向导中出现的“**安装 Microsoft Purview 信息保护客户端**”窗口中，选中“**我确认将卸载 Office 的 AIP 加载项(必需)**”复选框，并清除（取消选中）“**通过将使用情况发送至 Microsoft 来帮助改进 Microsoft Purview 信息保护**”复选框。 然后，选择“我同意”按钮****。

6. 安装完成后，选择“关闭”。

你已成功在 LON-CL1 VM 上安装了 **Microsoft Purview 信息保护客户端**。


### 任务 2 – 在 SharePoint 和 OneDrive 中为文件启用敏感度标签

在本练习中，你将在 SharePoint 和 OneDrive 中为受支持的 Office 文件和 PDF 文件启用敏感度标签。 启用此功能后，用户会在功能区上看到“敏感度”按钮，以便他们可以应用标签****。 它们还会在状态栏上看到任何应用的标签名称。 对于 SharePoint，用户还可以从详细信息窗格中查看和应用敏感度标签。

启用此功能还会使 SharePoint 和 OneDrive 能够处理 Office 文件和使用敏感度标签加密的 PDF 文档（可选）的内容。 标签可在 Office 网页版或 Office 桌面应用中应用，并在 SharePoint 和 OneDrive 中上传或保存。 在启用此功能之前，这些服务无法处理加密的文件，这意味着共同创作、电子数据展示、数据丢失防护、搜索和其他协作功能不适用于这些文件。

首先，为存储在 SharePoint 和 OneDrive 中的 Office 联机文件启用敏感度标签。 然后，你将启用对 PDF 的支持。

**注意：** 与 SharePoint 和 OneDrive 的所有租户级配置更改一样，更改需要大约 15 分钟才能生效。

1. 在 LON-CL1 上的 Edge 浏览器中，你仍以“Holly Dickson”身份登录到 Microsoft 365****。

2. 在 Edge 浏览器中，你仍为“Microsoft 365 管理中心”打开一个标签页****。 如果未打开，请打开一个新标签页并输入以下 URL：**https://admin.microsoft.com**。

3. 在 Microsoft 365 管理中心中，根据需要在导航窗格中选择******全部显示**。 在“管理中心”组下选择“合规性”********。 这会在新选项卡中打开 Microsoft Purview 门户。

4. 首先，为存储在 SharePoint 和 OneDrive 中的 Office 联机文件启用敏感度标签。 <br/>

    在 **Microsoft Purview** 门户导航窗格的“**解决方案**”部分下，选择“**信息保护**”，然后选择“**敏感度标签**”。

5. 在“**敏感度标签**”页上，页面中间应显示以下消息：**你的组织尚未启用处理已应用加密敏感度标签且存储在 OneDrive 和 SharePoint 中的 Office 联机文件内容的功能。你可以在此处启用该功能，但请注意，多地理位置环境需要其他配置。** <br/>

    此消息下方是“立即启用”按钮****。 选择本按钮。  <br/>

    **注意：** 该命令会立即运行，下次刷新页面时，将不再看到该消息或按钮。

6. 现在，你将为 SharePoint 和 OneDrive 中的文件启用 PDF 保护。 <br/>

    在 Microsoft Purview 门户的导航窗格的“信息保护”下，选择“标签”************。

7. 在“自动标记”页上，应会在页面中间看到“使用自动标记保护 PDF”横幅********。 选择“使用自动标记保护 PDF”标题，以为 SharePoint 和 OneDrive 中的文件启用 PDF 保护****。 

8. 在显示的“**自动标记策略**”对话框中，选择“**确认**”，以确认你要为 SharePoint 和 OneDrive 中的文件启用 PDF 保护。 

    **注意：** 该命令会立即运行，下次刷新页面时，将不再看到“使用自动标记保护 PDF”横幅****。

9. 让 Edge 浏览器与所有选项卡一起保持打开状态。 


### 任务 3 - 创建敏感度标签

在本练习中，你将创建一个敏感度标签并将其添加到默认策略中，使其对 Adatum 租户的所有用户有效。

1. 在 LON-CL1 上的 Edge 浏览器中，你仍以“Holly Dickson”身份登录到 Microsoft 365****。

2. 在 Microsoft Edge 浏览器中，仍应为上一任务中的 Microsoft Purview 门户打开一个标签页****。 在 **Microsoft Purview** 门户中，选择导航窗格中“**信息保护**”下的“**敏感度标签**”。 

3. 在“**敏感度标签**”页上，选择屏幕中间菜单栏上显示的“**+创建标签**”选项。 此时会启动“新建敏感度标签”向导****。

4. 在“新建敏感度标签”向导中，在“提供此标签的基本详细信息”页上输入以下信息********：

    - 名称：PII****
    
    - 显示名称：PII****

    - 针对用户的说明：PII 的文档、文件和电子邮件****

    - 针对管理员的说明：PII 的文档、文件和电子邮件****

    - 标签颜色：选择一种要分配给敏感度标签的颜色

5. 选择**下一步**。

6. 在“**定义此标签的范围**”页上，确认已选中了“**项目**”复选框，以及其下方的“**文件**”、“**电子邮件**”和“**会议**”复选框（如有必要，现在选中所有这四个复选框）。 通过这些复选框，可以定义此敏感度标签的使用位置，以便能够配置适用的保护设置。 选择**下一步**。

7. 在“**为所选项目类型选择保护设置**”页上，可以开始使用加密设置来限制对将应用此标签的内容的访问。 当文档、电子邮件或会议邀请被加密时，对内容的访问将会受到限制，因此它：  <br/>

    - 只能由标签的加密设置授权的用户对其进行解密。
    - 无论文档或电子邮件位于何处（组织内部或外部），即使文件已重命名，也保持加密状态。
    - 在静态（例如在 OneDrive 帐户中）和传输过程中（例如，在 Internet 上传输电子邮件）都会被加密。

   Holly 希望配置加密设置，因此，在“**为所选项目类型选择保护设置**”上，选中“**控制访问**”复选框。 此外，选中“**应用内容标记**”复选框，以便稍后可以配置页眉、页脚和水印设置。 选择**下一步**。

8. 由于在上一页中选择了“**控制访问**”选项，因此现在会显示“**访问控制**”页。 通过此页面，可以配置标签如何应用加密。 可以选择下述操作之一：  <br/>

    - **如果已应用于项，请移除访问控制设置：** 选择此选项时，应用标签会移除现有加密，即使它是独立于敏感度标签应用的。 请务必了解，如果用户没有足够的权限移除现有加密，此设置可能会导致他们无法应用敏感度标签。  
    - **配置访问控制设置：** 此选项可启用带权限管理的加密。 它还使以下设置可见： <br/>
        - 立即分配权限或让用户自行决定？
        - 用户对内容的访问权限过期
        - 允许脱机访问

    **备注：** 一种常见的配置策略是，首先将敏感度标签配置为不应用加密，然后再编辑某些现有标签以应用加密。 这是 Holly 希望采用的方法。 <br/>

    因此，选择“**如果已应用于项目，则删除访问控制设置**”选项，然后选择“**下一步**”。

9. 由于在之前的页面上选择了“**应用内容标记**”选项，因此现在会显示“**内容标记**”页。 将“**内容标记**”切换开关设置为“**开**”。 此时将显示三个选项，用于自定义要标记文件和电子邮件的方式。 <br/>

    选中所有三个复选框。 在每个设置下，选择“自定义文本”****。 此时将打开一个窗格来自定义该特定设置。 在每个选项的“自定义”窗格中输入以下信息（在输入每个选项的设置后选择“保存”）********： <br/>

    - 添加水印**** 
        - 水印文本：“敏感 - 请勿共享”****（提示：输入此值后，将其复制 (Ctrl+C)，以便可以在其他两个文本设置中粘贴 (Ctrl+V) 该文本）
        - 字号：25****
        - 字体颜色：**蓝色**
        - 文本布局：对角线对齐****
            
    - 添加标题**** 
        - 标题文本：敏感 - 请勿共享****
        - 字号：25****
        - 字体颜色：**Red**
        - 对齐文本：居中****
            
    - 添加页脚****
        - 页脚文本：敏感 - 请勿共享****
        - 字号：25****
        - 字体颜色：**Red**
        - 对齐文本：居中****

10. 在“内容标记”**** 页上，选择“下一步”****。 

11. 在“自动标记文件和电子邮件”页上，将“自动标记文件和电子邮件”切换开关设置为“启用”************。 此时将启用将在后续步骤中更新的一系列选项。

12. 在“检测符合这些条件的内容”下，选择“+ 添加条件”，然后选择“内容包含”************。

13. 在“内容包含”窗口中，选择“添加”下拉箭头，然后选择“敏感信息类型”************。

14. 在“敏感信息类型”**** 窗口中，将鼠标悬停在“名称”**** 列标题的左侧。 选中出现的复选框，该复选框会自动选择所有敏感信息类型。 选择“添加”，此时将向标签添加所有这些敏感信息类型****。

15. 在“**文件和电子邮件的自动标记**”页上，将显示所选的所有敏感信息类型。 滚动到窗口底部并更新以下设置：

    - 当内容符合这些条件时：选择“自动应用此标签”。****

    - 应用标签时向用户显示此消息：输入“已检测到敏感内容并将对其进行加密”****。
        
16. 选择**下一步**。

17. 在“定义组和网站的保护设置”页上，将两个复选框留空，然后选择“下一步”********。

18. 在“架构化数据资产的自动标记(预览版)”页上，不要启用架构化数据资产的自动标记（预览版）****。 选择**下一步**。 

19. 在“查看设置并完成”页上查看你输入的信息****。 如果需要更正任何设置，请选择相应的“编辑”选项并进行任何必要的更改****。 当所有信息都正确显示时，选择“创建标签”****。

20. 此时会显示“客户端错误”**** 对话框，指出尝试创建的标签生成的规则 blob 太长。 每条规则一次可以选择的敏感信息类型的最大大小为 49152****。 通过选择所有敏感信息类型（就像前面几步在“敏感信息类型”窗口中执行的操作一样），你已经超出了此限制****。 <br/>

    **注意：** 我们有意让你选择所有敏感信息类型，以便收到此错误。 我们希望你遇到此错误，这样在生产环境中发生此错误时，你便会了解收到错误的原因以及如何更正。  <br/>

    若要更正此问题，请在“客户端错误”对话框中选择“确定”，然后在“查看设置并完成”页中向下滚动到“自动标记文件和电子邮件”部分并选择“编辑”********************。
    
21. 此时将返回到向导中的“选择带标签项的保护设置”页****。 在此页上选择“下一步”，在“加密”页上选择“下一步”，然后在“内容标记”页上选择“下一步”********************。 此时将进入“自动标记文件和电子邮件”页****。 

22. 在“自动标记文件和电子邮件”页上“内容包含”条件的右侧，选择垃圾桶图标************。 这将删除创建的 PII 标签的现有“内容包含”条件********。 <br/>

    在后续步骤中，你将添加一个新条件，该条件仅包含两种敏感度信息类型，而不是像最初所做的那样所有敏感度信息类型。

23. 在“自动标记文件和电子邮件”页的在“检测符合这些条件的内容”下，选择“+ 添加条件”，然后选择“内容包含”****************。

24. 在“内容包含”窗口中，选择“添加”下拉箭头，然后选择“敏感信息类型”************。

25. 在“敏感信息类型”窗口中的敏感信息类型列表中，仅选中“ABA 汇款路线号码”和“美国************ 社会安全号码(SSN)”复选框，然后选择“添加”****。 返回“自动标记文件和电子邮件”页，将显示这两种敏感信息类型****。 选择**下一步**。

26. 在“定义组和网站的保护设置”页上，将两个复选框留空，然后选择“下一步”********。

27. 在“架构化数据资产的自动标记(预览版)”页上，不要启用数据库列的自动标记****。 选择**下一步**。

28. 在“查看设置并完成”页面上，选择“创建标签” 。

29. 在“你的敏感度标签已创建”页上，选择“现在不创建策略”选项，然后选择“完成”。************ 此时将返回到“标签”页****。

30. 现在该发布 PII**** 标签了。 在“标签”页上，如果“PII”标签未显示在标签列表中，请选择菜单栏上的“刷新”************。 如果显示“PII”标签，请选中其左侧显示的复选框****。 

31. 选择标签列表上方菜单栏中显示的“发布标签”选项****。 此时会启动“创建策略”向导。****

32. 在“创建策略”向导的“选择要发布的敏感度标签”页上，“PII”标签已列出，因此请选择“下一步”****************。 

33. 在“分配管理单元”页上，选择“下一步”，因为你要将此 PII 策略分配给 Adatum 的完整目录，而不仅仅是一组选定的管理单元********。

34. 在“发布到用户和组”页上，可以选择策略是适用于所有用户和组，还是仅适用于选定的用户和组****。 在此实验室中，我们使策略适用于所有用户。 默认情况下已选择“用户和组”**** 选项（如果没有，请选择）。 这样可以使策略可供所有用户和组使用。 选择**下一步**。  <br/>

    **注意：** 在实际部署中执行此操作时，如果要将策略限制为仅适用于选定数量的用户或组，则可以选择“编辑”并选择这些用户或组****。 

35. 在“策略设置”**** 页上，选择“用户必须提供删除标签或降低其分类的理由”复选框，然后选择“下一步”********。 

36. 在“将默认标签应用于文档”**** 页上，在显示的下拉菜单中选择“PII”****，然后选择“下一步”****。

37. 在“将默认标签应用于电子邮件”**** 页上，在显示的下拉菜单中选择“PII”****，然后选择“下一步”****。

38. 在“将默认标签应用于会议和日历活动”**** 页上，在显示的下拉菜单中选择“PII”****，然后选择“下一步”****。

39. 在“将默认标签应用于 Fabric 和 Power BI 内容”**** 页上，在显示的下拉菜单中选择“PII”****，然后选择“下一步”****。

40. 在“为策略命名”**** 页上，在“名称”字段中输入“PII 策略”，然后为此敏感度标签策略输入（或复制粘贴）以下说明********：此策略的目的是检测敏感信息，如电子邮件和文档中的 ABA 银行汇款路线号码和美国社会安全号码，并在发现此信息时对其进行加密。**** 用户必须提供删除分类标签的说明。 选择**下一步**。

41. 在“查看并完成”页上查看你输入的信息****。 如果需要更正任何信息，请选择相应的“编辑”选项并进行任何必要的更正****。 如果所有信息正确，请选择“提交”****。

42. 在“新策略已创建”页上，选择“完成”********。

43. 让 Edge 浏览器与所有选项卡一起保持打开状态。 


### 任务 4 – 向文档分配已存在的敏感度标签

如本实验室开始时的说明中所述，无法立即测试在上一任务中创建的敏感度标签和标签策略。 这是因为，最多需要 24 小时才能通过 Microsoft 365 传播新标签策略并使其标签显示在 Microsoft Word 和 Outlook 等应用程序中。

我们改为测试 Microsoft 365 中已存在的一个敏感度标签。 在本实验室中，你将使用“Project - Falcon”敏感度标签，这是一个高度机密标签****。 此标签与你在上一个任务中创建的标签类似，一个不同之处是前者不包含页眉或页脚。 使用这一已存在的标签可以让你更好地了解你创建的标签如何在 Adatum 中使用。

1. 在 LON-CL1 上的 Edge 浏览器中，你仍以“Holly Dickson”身份登录到 Microsoft 365****。

2. 首先查看 Project-Falcon 敏感度标签，该标签将应用于此任务中的文档****。  在 Microsoft Edge 浏览器中，仍应为上一任务中的 Microsoft Purview 门户打开一个标签页****。 在 Microsoft Purview 门户中的导航窗格上，选择“信息保护”下的“标签”************。 

3. 在“标签”页上的标签列表中，选择“高度机密”旁边的向右键 (>)，以显示此标签下的子标签************。 这将显示预先存在的 Project - Falcon 标签****。

4. 选择 Project - Falcon 标签（而不是复选框；选择标签名称）****。 这将打开“Project - Falcon”详细信息窗格****。 查看此标签的定义信息，完成后关闭该窗格。  

5. 现在，将 Project-Falcon 敏感度标签分配给文档****。 选择浏览器中的“主页 | Microsoft 365”标签页返回到 Microsoft 365 主页****。 选择屏幕左侧的“应用”**** 图标。 在显示的“应用”**** 页上，右键单击“Word”**** 磁贴，然后选择“在新标签页中打开”****。 

6. 在“Word | Microsoft 365”标签页中，在页面顶部的“新建”部分下，选择“空白文档”************。

7. 如果出现“隐私选项”**** 窗口，请选择“关闭”****。

8. 如果 Word 功能区显示每个功能的图标，但不按组分隔图标，则选择功能区最右侧的向下箭头，然后在“功能区布局”下，选择“经典功能区”********。 此时会将功能区切换到功能区组（如撤消、剪贴板、字体、段落、样式等）划分的传统功能区样式。

9. 在“Word”文档中，键入以下文本****：**使用个人身份信息 (PII) 测试文档上的敏感度标签；在本例中，使用美国社会安全号码：** 111-11-1111。

10. 由于在本练习开始时启用了敏感度标签，因此 Word 应在页面顶部的功能区上显示“敏感度”组********。 请选择“敏感度”组中的下箭头。**** 在出现的下拉菜单中，应显示敏感度标签类型列表。 选择“高度机密”****，然后在出现的子菜单中选择“Project - Falcon”****。 <br/>

    **注意：** 24 小时后，在上一任务中创建的标签将显示在 Project-Falcon 标签旁边的“高度机密”子菜单中。 但现在，你将使用“Project - Falcon”标签代替它****。

11. 在文档中，注意标签如何在文档顶部应用“机密 - ProjectFalcon”水印****。 Project - Falcon 标签的配置方式与你创建的标签一样，其中水印应该在页面中间沿对角方向显示。 那么，为什么它出现在页面顶部？ 答案是，你使用的是网页版 Word****，默认情况下，它会显示在此处。 要查看用户阅读文档时文档的显示方式，必须在“读取视图”**** 中查看文档，现在将执行此操作。 <br/>

    选择“视图”**** 标签页，然后在 Word 功能区中选择“读取视图”****。 请注意水印如何在文档中间沿对角方向显示。 这就是水印向阅读文档的用户的显示方式。 请注意，如果使用 Word 桌面应用，它将显示标签指定的水印，在这种情况下，就像在“读取视图”中看到的水印一样。 <br/>

    若要退出“读取视图”，请选择页面顶部菜单栏上的“编辑文档”****。 在出现的下拉菜单中，选择“编辑”****。

12. 在第一个验证测试中，你将删除应用于此文档的敏感度标签。 标签策略选项之一要求用户提供删除标签或选择更低分类标签的理由。 现在，你将验证此设置是否正常运行。 <br/>

    在 Word 功能区的“敏感度”组中，选择向下箭头****。 在显示的下拉菜单中，注意“高度机密”旁边会出现一个复选标记****。 将鼠标悬停在“高度机密”上以显示子菜单****。 请注意复选标记在“Project - Falcon”**** 旁边如何显示。 复选标记标识应用于文档的当前标签。  <br/>
 
    若要从本文档中删除标签，请选择此下拉菜单中显示的“Project - Falcon”标签****。
    
13. 在显示的“需要理由”窗口中，选择“其他(说明)”选项********。 在“解释你为什么要更改此标签”字段中，输入“测试从文档中删除标签后会发生什么”，然后选择“更改”************。

14. 请注意文档中水印的消失方式。 在 Word 功能区的“敏感度”组中，选择向下箭头****。 在出现的下拉菜单中，请注意，虽然显示了“高度机密 > Project - Falcon”，但它们旁边没有出现复选标记********。 这表示敏感度标签不再应用于此文档。  

15. 若要将敏感度标签重新应用于文档，请在下拉菜单中选择“高度机密 > Project - Falcon”********。 请注意文档中水印的重新出现方式。

16. 现在，你将保存文档，以便在下一个任务中共享。 包含下拉箭头的文档名称字段显示在页面的左上角、Word 图标右侧（Word 可能会显示 Document 或 Document1 作为临时文件名）********。 选择下拉箭头。 在显示的下拉菜单中，确认文件“位置”显示“Holly Dickson > Documents”********。 <br/>

    在“文件名”字段中，将文件重命名为 ProtectedDocument1，然后选择此文件名菜单外部区域（在文档内选择）********。 请注意，分配给文件的新名称将显示在标题栏中。 

17. 将“ProtectedDocument1”标签页保持打开状态，显示文档****。 你将在下一个任务中返回此文档，以便与 Joni Sherman 共享文档。

你已成功创建了一个 Word 文档，其中包含标题为“Project - Falcon”的高度机密标签****。 


### 任务 5 – 使用 Microsoft Purview 信息保护来保护文档

在前面的任务中，你创建了一个 Word 文档，并使用“Project - Falcon”敏感度标签对其进行保护****。 此标签在文档中插入了一个水印。 在本任务中，你将与 Joni Sherman 共享你创建的文档，并限制 Joni 拥有“仅查看”权限。 这样可以查看 Microsoft Purview 信息保护如何基于配置的参数保护文档。

若要验证分配给文档的保护是否有效，首先将文档发送给两个人 - Joni Sherman 和你自己的个人电子邮件地址。 然后，你将验证 Joni 只能查看文档而无法编辑文档，并且你将验证你无法访问文档，因为它未与你共享。 最后，你将更改对文档的权限，使 Joni 可以编辑文档，并将此更新的文档通过电子邮件发送给她进行测试。 发给 Joni 的两封电子邮件中，一封包含提供只读访问权限的文档链接，另一封包含提供文档编辑权限的文档链接，目的是了解 Microsoft Entra ID Protection 如何提供不同级别的文档保护。 

1. 在 LON-CL1 上的 Edge 浏览器中，你仍以“Holly Dickson”身份登录到 Microsoft 365，并且 Word 标签页打开********。

2. 在 Edge 浏览器中，选择“应用 | Microsoft 365”标签页。**** 

3. 在“应用”**** 页上，右键单击“Outlook”**** 磁贴，然后选择“在新标签页中打开”****。此时会在新浏览器标签页的 Outlook 网页版中打开 Holly 的邮箱。 

4. 在“Outlook 网页版”中，在屏幕顶部选择“新建邮件”********。

5. 在电子邮件窗体中输入以下信息：

    - 更改为：输入“Joni”，然后从用户列表中选择“Joni Sherman”********。 

    - 抄送：输入你自己的个人电子邮件地址（请勿输入 Holly 的电子邮件地址；而是输入你自己的个人电子邮件地址），然后选择显示的消息“使用此地址: <your email address>”****

    - 添加主题：受保护的文档测试 - 仅查看权限****

    - 邮件正文：输入“请打开附加到此电子邮件的受保护文档，并尝试进行更改。”****

6. 在邮件正文中，在上一步中添加的文本下方，附加一个指向你在上一个任务中创建的文档的链接。 但是，要执行此操作，必须先与 Joni Sherman 共享文档，执行此操作时，将应用受限的“仅视图”权限****。 为此，必须保留此电子邮件并返回到文档并与 Joni 共享。 复制在共享过程中创建的链接后，将返回到此电子邮件并粘贴链接。 <br/>

    在 Edge 浏览器中，选择“ProtectedDocument1”标签页，该标签页仍应显示在你上一个任务中创建的文档****。 在页面右上角的 Holly Dickson 姓名和首字母缩写下方，选择“共享”按钮****。 在出现的下拉菜单中，选择“共享”****。

7. 在出现的“共享 ProtectedDocument1”窗口中，选择“复制链接”按钮旁边显示的齿轮（链接设置）图标************。 

8. 在出现的“链接设置”窗口中，选择“你选择的用户”选项。********
    
9. 在“更多设置”下，当前选项“可编辑”********。 你计划与 Joni Sherman 共享此文档，但你只希望 Joni 能够查看文档。 若要更改此权限，请选择“可编辑”****。 在出现的菜单中，查看可用选项。 可以看到，“可编辑”**** 旁边有一个复选标记，表示这是当前设置。 若要限制 Joni 只拥有只读权限，请选择“可查看”，然后选择“应用”********。

10. 你将返回到“共享 ProtectedDocument1”窗口****。 在“添加名称、组或电子邮件”字段中输入“Joni”。******** 将出现名称以“Joni”开头的用户列表。**** 选择“Joni Sherman”****。

11. 在“共享 ProtectedDocument1”窗口中，将鼠标悬停在 Joni 名称右侧的“眼睛”图标上****。 此时将显示“可查看”****，这是你分配给她的关于此文档的当前设置。 “眼睛”图标代表“可查看”。 选择“复制链接”**** 按钮。 

12. “共享 ProtectedDocument1”窗口底部显示“链接已复制”下消息后，选择窗口上角的“X”将其关闭********。

13. 在 Edge 浏览器中，选择“邮件 - Holly Dickson -Outlook”**** 标签页以返回到电子邮件。 在邮件正文中，在之前添加的文本下方，粘贴 (Ctrl+V) 刚刚复制到剪贴板的指向共享文档的链接。 此时应显示名为 ProtectedDocument1.docx 的文件的链接****。 

14. 选择“发送”。

15. 将显示“收件人无法访问连接”消息****。 此消息是 Microsoft Entra ID Protection 发现你在电子邮件中包含你的个人电子邮件地址这一事实的结果，该地址无权访问文档。 在本实验室测试中，请选择“仍要发送”****。

16. 切换到 LON-CL2****。 

17. 在 LON-CL2 上，应以上一个实验室练习中的“Lynne Robbins”身份登录到 Outlook 网页版************。 以 Lynne 身份退出登录。

18. 在 Edge 浏览器中，关闭除“退出登录”标签页之外的所有标签页****。在此标签页中，在地址栏中输入以下 URL：**https://outlook.office365.com** 

19. 在“选取帐户”窗口中，选择“使用另一个帐户”********。

20. 在“登录”窗口中，输入 **JoniS@xxxxxZZZZZZ.onmicrosoft**（其中 xxxxxZZZZZZ 是你的实验室托管提供商提供的租户前缀），然后选择“下一步”********。

21. 在“输入密码”窗口中，输入之前分配给 Joni 帐户的新用户密码，然后选择“登录”********。 

22. 如果出现“欢迎”窗口，请选择“X”将其关闭****。

23. 在 Outlook 网页版 Joni 的收件箱中，你应该会看到 Holly 刚刚发送的电子邮件，其主题行指示该文档具有“仅查看”权限********。 打开此电子邮件。

24. 在电子邮件中，选择附加的文件将其打开。

25. 在显示的“隐私选项”**** 窗口中，选择“关闭”****。 文档将在 Word 网页版中的标题为“ProtectedDocument1.docx”标签页的新浏览器标签页中打开。******** 请注意文档在 Web 网页版的“读取视视图”中的显示方式****。 这是 Joni 表示她只有“查看”权限，无法编辑文档。 若要验证这一点，请尝试选择文档。 请注意显示的消息，指示：“只读。**** 本文档为只读文档。” 请注意“Project - Falcon”策略中指定的水印。**** <br/>

    查看完文档后，关闭“ProtectedDocument1.docx”标签页****。 

26. 现在，你将测试尝试打开发送到你的个人电子邮件地址的文档时会发生什么情况。 使用移动电话或课堂电脑访问你的个人邮箱。 打开 Holly 刚刚发送到你的个人电子邮件地址的电子邮件，然后尝试打开附加的文件。 

27. 由于你没有访问文档的权限，因此应显示“选取帐户”窗口****。 在实际场景中，可以选择使用有权访问文件的帐户登录，或者从 **Holly@xxxxxZZZZZZ.onmicrosoft.com** 帐户请求访问权限。 <br/>

    出于本测试的目的，你刚刚验证了你无法访问该文件，因为该文件未与你共享。 你还验证了 Joni 只能查看文件，但无法编辑文件。 现在，你将通过允许 Joni 编辑文件来更改对文件的共享权限。 你将执行此操作，看看此体验与你刚刚完成的体验有何不同。 

28. 请切换到 LON-CL1****。 

29. 在 LON-CL1 上的 Edge 浏览器中，你仍以“Holly Dickson”身份登录到 Microsoft 365，并且 Word 和 Outlook 的标签页打开************。 选择“邮件 - Holly Dickson - Outlook”标签页****。 

30. 在 Holly 的邮箱中，撰写另一封发送给 Joni Sherman 的电子邮件。 请勿在抄送行中包含你的个人电子邮件地址。 在电子邮件窗体中输入以下信息：

    - 更改为：输入“Joni”，然后从用户列表中选择“Joni Sherman”********。 

    - 抄送：留空

    - 添加主题：受保护的文档测试 - 编辑权限****

    - 邮件正文：输入“请打开附加到此电子邮件的受保护文档，并尝试进行更改。”****

31. 与上一封电子邮件一样，现在必须与 Joni 共享文档，但这次提供“编辑”权限。 要创建，请执行以下步骤： <br/>

    - 在浏览器中选择“ProtectedDocument1”标签页，然后选择菜单栏右侧的“共享”按钮********。 在出现的下拉菜单中，选择“共享”****。 
    - 在“共享 ProtectedDocument1”窗口中，在“添加名称、组或电子邮件”字段中输入“Joni”，然后选择“Joni Sherman”****************。
    - Joni 名字右侧是铅笔（“可编辑”****）图标。 这是共享文档时的默认权限。 选择“复制链接”**** 按钮看看发生了什么情况。
    - 注意显示的“链接已复制”消息****。 此消息指示任何人都可以编辑文档，即使你指定了 Joni 的名称。 这不符合你的需求，你要限制 Joni 作为唯一可以编辑文档的用户。 若要实现该限制，请选择“复制链接”按钮旁边的齿轮（“链接设置”）图标********。 
    - 在出现的“链接设置”窗口中，选择“你选择的用户”选项。******** 此选项是限制所选用户权限的关键。 
    - 在“更多设置”下，如果出现“可编辑”，请选择“应用”************。 但是，如果出现“可查看”，则选择“可查看”，并在出现的菜单中选择“可编辑”，然后选择“应用”****************。 
    - 在“共享 ProtectedDocument1”窗口中，选择“复制链接”按钮********。
    - 注意显示的“链接已复制”消息****。 这一次，此消息指示只有你指定的人员才能编辑文档。 在本例中，编辑将仅限于 Joni，因为她是你唯一指定的人员。 
    - 在浏览器中选择“邮件 - Holly Dickson - Outlook”标签页，然后将链接粘贴到电子邮件正文中****。 

32. 选择“发送”。

33. 切换到 LON-CL2****。 

34. 在 LON-CL2 上，仍以“Joni Sherman”身份登录到 Outlook 网页版************。 在 Joni 的收件箱中，你应该会看到 Holly 刚刚发送的电子邮件，其主题行指示该文档具有“编辑”权限****。 打开此电子邮件。

35. 在电子邮件中，选择附加的文件将其打开。

36. 当 Joni 具有“仅查看”权限时，文档在“读取视图”窗格中打开。 因此，Joni 无法编辑文档。 此版本的文档为 Joni 提供了“编辑”权限，因此这次文档应在 Word 中以正常编辑模式打开。 验证是否可以在文档中输入文本。 

    **注意：** 在本任务中，你刚刚验证了 Microsoft Purview 信息保护是否基于你配置的 PII 策略参数保护文档。 当 Joni 被分配为“仅查看”权限时，文档在“读取视图”中打开，她无法更改文档。 当 Joni 被分配为“编辑”权限时，文档在 Word 中打开，她可以更改文档。 由于 Holly 未与你共享文档，因此当她通过电子邮件将文档发送到你的个人邮箱时，你无法打开该文档。 

## 实验室 4 结束


# 祝贺你！ 本课程的最后一个实验室现已完成。
