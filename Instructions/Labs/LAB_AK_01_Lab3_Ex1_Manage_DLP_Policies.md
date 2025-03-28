# 学习路径 1 - 实验室 3 - 练习 1 - 管理 DLP 策略  

你扮演 Adatum 的新 Microsoft 365 管理员 Holly Dickson，已将 Microsoft 365 部署到虚拟化实验室环境中。 随着 Microsoft 365 试点项目的推进，后续步骤是在 Adatum 中实现数据丢失防护 (DLP) 策略。 首先在本练习中创建自定义 DLP 策略，然后测试与电子邮件消息存档和包含敏感数据的电子邮件相关的 DLP 策略。 

### 任务 1 – 使用自定义设置创建 DLP 策略

在本练习中，你将在 Microsoft Purview 门户中创建数据丢失防护策略以防止敏感数据被用户共享。 如果用户希望分享包含 IP 地址的内容，你创建的 DLP 策略将通知他们。 

策略将包含两个规则或操作，每个都取决于消息中的 IP 地址数量。 如果消息包含一个 IP 地址，该策略将通过策略提示通知相关人员，并且仍通过电子邮件发送消息。 但是，如果内容包含两个或更多个 IP 地址，则会阻止该邮件，并向发件人发送一封具有高敏感度级别的事件邮件，同时将显示一个策略提示，如果发件人在策略提示中提供业务理由，则允许发件人解除电子邮件阻止。

1. 在 LON-CL1 上的 Edge 浏览器中，你仍以“Holly Dickson”身份登录到 Microsoft 365****。 

2. 在 **Microsoft Edge** 中，Microsoft Purview 门户仍应处于打开状态；如果没有，请打开一个新选项卡并导航到 **https://compliance.microsoft.com**。

3. 在 **Microsoft Purview** 门户中，选择导航窗格中的“**解决方案**”、“**数据丢失防护**”，然后选择“**策略**”。

4. 在“**策略**”页中，选择菜单栏上的“**+ 创建策略**”选项以启动“**创建策略**”向导。

5. 在“**从模板开始或创建自定义策略**”页上，“**类别**”列显示策略类别。 除了“**自定义**”类别，每个策略类别都提供可用于创建该类型策略的模板。 此类别不提供任何特定模板；相反，它允许组织从头开始创建自定义策略。 选择类别时，将出现“**模板**”列，其中显示了所选类别可供选择的模板。 选择模板时，将出现另一列，其中显示该模板中受保护的信息类型。 <br/> 

    例如，在侧窗格中选择“**财务**”，然后滚动浏览可在“**模板**”列中选择的各种模板。 选择一两个模板以查看它保护的信息类型。 如果需要，可以选择每个剩余类别以查看提供了哪些模板类型。 
  
6. 在本实验室中，你将创建自定义 DLP 策略。 在“**类别**”列中选择“**自定义**”，在“**模板**”列中选择“**自定义策略**”模板，然后选择“**下一步**”。

7. 在“**为 DLP 策略命名**”页面上，输入以下信息，然后选择“**下一步**”：  <br/>

      - 名称：**IP 地址 DLP 策略**
      - 说明：**此策略检测电子邮件中是否存在 IP 地址。最终用户会收到检测通知，管理员会也收到通知。包含 2 个或多个 IP 地址的电子邮件将被阻止发送。**

8. 在“分配管理单元”**** 页面上，选择“下一步”****。 

9. 在“**选择分配策略的位置**”页上，确认以下位置的“**状态**”切换已设置为“**开**”（如果其中任一位置默认设置不是“**开**”，则立即将其设置为“**开**”）： <br/>

    - **Exchange 电子邮件**
    - **SharePoint 站点**
    - **OneDrive 帐户**
    - **Teams 聊天和频道消息**

    将所有其他位置设置为“**关**”，然后选择“**下一步**”。

10. 在“**定义策略设置**”页上，应默认设置“**创建或自定义高级 DLP 规则**”选项（如果默认未选中，则现在选择该选项），然后选择“**下一步**”。 

11. 在“**自定义高级 DLP 规则**”页上，选择菜单栏上的“**+创建规则**”。

12. 在“**创建规则**”页上，输入以下信息：
    
      - 名称：**单个 IP 地址规则**
    
      - 说明：**电子邮件包含 IP 地址**
    
      - 在“**条件**”部分下，选择“**+添加条件**”，然后从下拉菜单中选择“**内容包含**”。 然后输入以下条件设置：
    
        - 在“**内容包含**”字段中，选择“**添加**”下拉菜单，然后选择“**敏感信息类型**”。
        
        - 在“**敏感信息类型**”窗格的“**搜索**”字段中键入 **IP**，然后按 Enter。
        
        - 在搜索结果中，选中“**IP 地址**”复选框，然后选择“**添加**”。
        
     - 向下滚动到“**用户通知**”部分，将“**使用通知来提醒用户并帮助引导他们正确使用敏感信息**”切换开关设置为“**开**”。

    - 选中“**使用策略提示在 Office 365 服务中通知用户**”复选框。 在“**策略提示**”部分中，选中“**自定义策略提示文本**”复选框。 

        - Holly 希望你自定义策略提示消息，因此在此字段中输入以下文本：**注意！你在此消息中输入了敏感信息（IP 地址）。系统不会阻止你发送此消息，但请检查收件人是否有权查看此敏感数据。** 

    - 选中“**发送前将策略提示以对话形式显示给最终用户(仅适用于 Exchange 工作负载)**”复选框。 
    
    - 在“**事件报告**”部分中，确认“**当规则匹配发生时向管理员发送警报**”切换开关已设置为“**开**”（如有必要，请将其设置为“**开**”）

    - 选择页面底部的“保存”按钮****。

13. 在“**自定义高级 DLP 规则**”页上，现在应显示刚刚创建的**单个 IP 地址规则**。 选择“**+创建规则**”选项以创建第二个 DLP 规则。 

14. 在“**创建规则**”页上，输入以下信息：
    
    - 名称：**多个 IP 地址规则**
    
    - 说明：**电子邮件包含两个或多个 IP 地址**
    
    - 在“**条件**”部分下，选择“**+添加条件**”，然后从下拉菜单中选择“**内容包含**”。 然后输入以下条件设置：
    
        - 在“**内容包含**”字段中，选择“**添加**”下拉菜单，然后选择“**敏感信息类型**”。
        
        - 在“**敏感信息类型**”窗格的“**搜索**”字段中键入 **IP**，然后按 Enter。
        
        - 选中“**IP 地址**”复选框，然后选择“**添加**”。

        - 在“**敏感信息类型**”部分下，将显示** IP 地址**信息类型。 在 IP 地址行的右侧，“**实例计数**”设置从 **1** 更改为**任意**。 将第一个字段的值从 1 更改为 **2**。 通过进行此更改，此规则将仅在电子邮件中出现 2 个或多个 IP 地址时才适用。 
    
    - 在“**操作**”部分，选择“**+添加操作**”。 在出现的下拉菜单中，选择“**限制访问或加密 Microsoft 365 位置中的内容**”。 然后输入以下操作设置：

    - 如果“**限制访问或加密 Microsoft 365 位置中的内容**”部分下未显示任何选项，请立即选择以展开此部分。 此部分应显示“**阻止用户接收电子邮件或访问共享 SharePoint、OneDrive 和 Teams 文件**”选项，该选项默认处于选中状态。 将此选项保持选中状态。

    - 在 **“阻止用户接收电子邮件或访问共享 SharePoint、OneDrive 和 Teams 文件**”选项下，选择“**阻止所有人**”选项。
    
    - 在“**用户通知**”部分中，将“**使用通知来提醒用户并帮助引导他们正确使用敏感信息**”切换开关设置为“**开**”。 

    - 选中“**使用策略提示在 Office 365 服务中通知用户**”复选框。 在“**策略提示**”部分中，选中“**自定义策略提示文本**”复选框。 

        - Holly 希望自定义策略提示消息，因此在此字段中输入以下文本：**注意！你在此消息中输入了敏感信息（多个 IP 地址）。如果尝试发送此消息，将会被阻止。解除此阻止表示你已授权将此敏感数据发送给收件人。** 

    - 选中“**发送前将策略提示以对话形式显示给最终用户(仅适用于 Exchange 工作负载)**”复选框。 
    
    - 在“**用户覆盖**”部分中，选中“**允许从 Microsoft 365 个文件和 Microsoft Fabric 项中覆盖**”复选框。 这将启用指示如何处理覆盖的其他设置。 选中以下两个选项的每个复选框：

        - **需要业务理由才可覆盖**
        - **如果规则报告为误报，则自动覆盖该规则**
    
    - 在“**事件报告**”部分中，确认“**当规则匹配发生时向管理员发送警报**”切换开关已设置为“**开**”（如有必要，请将其设置为“**开**”）

    - 选择页面底部的“保存”按钮****。

15. 在“**自定义高级 DLP 规则**”页上，现在应同时显示**单个 IP 地址规则**和**多个 IP 地址规则**。 选择**下一步**。

16. 在“**策略模式**”页上，选择“**立即打开策略**”选项，然后选择“**下一步**”。

17. 在“**查看和完成**”页上，查看刚刚创建的策略。 如果需要更正任何信息，请选择相应的“**编辑**”选项并进行更正。 当一切正常时，选择“**提交**”。

18. 可能需要一分钟左右的时间才会出现“**新策略已创建**”页面。 出现后，选择“**完成**”。

19. 使 Edge 浏览器保持打开状态。 不要关闭任何选项卡。


现已创建 DLP 策略，可用于扫描组织中发送或共享的电子邮件和文档中的 IP 地址。


### 任务 2 – 关闭绕过 DLP 策略的“发送到 Kindle”功能

Adatum 的 Microsoft 365 管理员 Holly Dickson 最近了解到 Microsoft 365 中的“**发送到 Kindle**”功能，该功能可让你在几分钟内将 Microsoft Word 文档直接发送到 Kindle 库。 传输的文件可以像具有可调整字体大小的 Kindle 书籍一样显示，也可以像具有固定布局的打印文档一样显示，以便保留页面设计格式。 

此功能的问题在于，DLP 策略没有考虑到 Word 文件共享到 Kindle 的情况，这实际上会绕过 DLP 控制。 由于 Adatum 不会使用此“**发送到 Kindle**”功能，因此 Holly 希望将其关闭，以避免用户绕过公司 DLP 策略的可能性。 

若要关闭此设置，必须在 Microsoft Intune 管理中心为 Office 应用创建策略。 在创建的策略中，将“**关闭发送到 Kindle**”设置添加到策略，然后启用此设置。 在策略中启用此设置可在完成策略创建后关闭“**发送到 Kindle**”功能。 此时，用户将无法再将 Word 文档发送到其 Kindle 库。

**备注：** 应考虑在实际 Microsoft 365 部署中解决此问题。 有关此“**发送到 Kindle**”功能的详细信息，请参阅 https://support.microsoft.com/office/send-to-kindle-a53d880d-9952-4bf1-abc5-6bce8db5a273。

1. 在 LON-CL1 上的 Edge 浏览器中，你仍以“Holly Dickson”身份登录到 Microsoft 365****。 

2. 在 Edge 浏览器中，找到“**Microsoft 365 管理中心**”选项卡。在 Microsoft 365 管理中心的导航窗格中，在“**管理中心**”组下，选择“**Endpoint Manager**”。

3. 在新选项卡中打开的“**Microsoft Intune 管理中心**”中，选择导航窗格中的“**应用**”。

4. 在“**应用 | 概述**”页的中间导航窗格中，选择“**策略**”部分下的“**Office 应用的策略**”。

5. 在“**应用 | Office 应用的策略**”页上，选择“**创建**”按钮。 这会启动向导来创建新策略。 在剩余的步骤中，你将在此策略中启用“**关闭发送到 Kindle**”设置。

6. 在“**从基本信息开始**”页上，在“**名称**”字段中输入“**关闭发送到 Kindle 设置**”，然后选择”**下一步**”。

7. 在“**选择范围**”页上，选择“**此策略配置适用于所有用户**”选项，然后选择“**下一步**”。

8. 在“**配置设置**”页上，注意设置列表上方显示的指标。 租户配置有 2200 多个 Office 应用设置。 若要快速找到此设置，请在“**搜索**”字段中输入 **Kindle**，然后按 **Enter**。 这应会显示策略名称中包含 **Kindle** 的任何策略。

9. 可以看到，只有一个 Kindle 设置，即“**关闭发送到 Kindle**”。 选择此设置，这将打开“**关闭发送到 Kindle**”窗格。

10. 在“**关闭发送到 Kindle**”窗格中，将显示此设置适用的平台和应用程序。 在此说明下，选择“**显示更多**”选项。 阅读完此设置的完整说明。

11. 在“**配置设置**”字段中选择下拉箭头。 在出现的下拉菜单中，选择“**已启用**”。

12. 在窗格底部，选择“**应用**”按钮。

13. 在“**配置设置”** 页上，应显示“**关闭发送到 Kindle**”策略，并且其“**状态**”应设置为“**已配置**”。 选择**下一步**。

14. 在“**查看配置并创建**”页上，选择“**创建**”按钮。 

15. 在“**新策略已创建**”页上，选择“**完成**”。
 
16. 使 Edge 浏览器保持打开状态。 不要关闭任何选项卡。


通过在刚刚创建的新策略中启用“**关闭发送到 Kindle**”设置，已关闭了“**发送到 Kindle**”功能。 这将防止 Adatum 用户将 Word 文档发送到其 Kindle 库，从而绕过公司的 DLP 策略。


# 继续进行实验室 3 - 练习 2 
