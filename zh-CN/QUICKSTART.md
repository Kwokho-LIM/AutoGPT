# 快速入门指南

> 有关完整的入门教程系列<-单击此处[](https://aiedge.medium.com/autogpt-forge-e3de53cc58ec)

欢迎使用快速入门指南！本指南将带您完成设置和运行自己的AutoGPT代理的过程。无论您是经验丰富的人工智能开发人员还是刚刚起步，本指南都将为您提供必要的步骤，让您使用AutoGPT快速开启人工智能开发之旅。

## 系统要求

这个项目支持Linux（基于Debian）、Mac和Linux的Windows子系统(WSL)。如果您使用的是Windows系统，则需要安装WSL。您可以在这里找到WSL的安装说明。[](https://learn.microsoft.com/en-us/windows/wsl/)


## 获取设置
1. **分叉存储库
   **要分叉存储库，请执行以下步骤：
   - 导航到存储库的主页。

   ![仓库](docs/content/imgs/quickstart/001_repo.png)
   - 在页面的右上角，单击Fork。

   ![创建分叉UI](docs/content/imgs/quickstart/002_fork.png)
   - 在下一页，选择您的GitHub帐户以在下创建分叉。
   - 等待分叉过程完成。现在，您的GitHub帐户中有一个存储库的副本。

2. **克隆存储库
   **要克隆存储库，您需要在系统上安装Git。如果你没有安装Git，你可以从这里下载。安装Git后，请按照以下步骤操作：[](https://git-scm.com/downloads)
   - 打开你的终端。
   - 导航到要克隆存储库的目录。
   - 为刚刚创建的分叉运行git clone命令

   ![克隆存储库](docs/content/imgs/quickstart/003_clone.png)

   - 然后在ide中打开项目

   ![在IDE中打开项目](docs/content/imgs/quickstart/004_ide.png)

4. **设置项目
   **接下来，我们需要设置所需的依赖项。我们有一个工具可以帮助您完成回购中需要的所有任务。
   可以通过键入运行run命令来访问它。/run在终端中。````

   您需要使用的第一个命令是。/run setup这将指导您完成设置系统的过程。`
   最初，您将获得安装flutter、chrome和设置github访问令牌的说明，如下图所示：`

   > 注意：对于高级用户。github访问令牌仅用于./run arena enter命令，以便系统可以自动创建PR


   ![设置项目](docs/content/imgs/quickstart/005_setup.png)

### 对于Windows用户

如果您是Windows用户并在安装WSL后遇到问题，请按照以下步骤解决这些问题。

#### 更新WSL
在Powershell或命令提示符中运行以下命令：
1. 启用可选的WSL和虚拟机平台组件。
2. 下载并安装最新的Linux内核。
3. 将WSL 2设置为默认值。
4. 下载并安装Ubuntu Linux发行版（可能需要重启）。

```shell
wsl——安装
```

有关更多详细信息和其他步骤，请参阅Microsoft的WSL设置环境文档。[](https://learn.microsoft.com/en-us/windows/wsl/setup/environment)

#### 解决FileNotFoundError或“没有这样的文件或目录”错误
当你跑的时候。/run setup，如果您遇到像没有这样的文件或目录或FileNotFoundError这样的错误，这可能是因为Windows风格的行尾（CRLF回车换行）与Unix/Linux风格的行尾（LF换行）不兼容。``````

要解决这个问题，您可以使用dos2unix实用程序将脚本中的行尾从CRLF转换为LF。`下面是如何在脚本上安装和运行dos2unix：```

```shell
sudo apt更新
sudo apt安装dos2unix
dos2unix./run
```

执行上述命令后，运行。/run setup应该可以成功工作。``

#### 在WSL文件系统中存储项目文件
如果您继续遇到问题，请考虑将项目文件存储在WSL文件系统中，而不是Windows文件系统中。这种方法避免了与路径转换和权限相关的问题，并提供了更一致的开发环境。

    您可以继续运行该命令，以获得有关您的设置进度的反馈。
    安装完成后，该命令将返回如下输出：

![安装完成](docs/content/imgs/quickstart/006_setup_complete.png)

## 创建您的代理

    现在设置已经完成，是时候创建代理模板了。
    为此，请运行`./run agent create YOUR_AGENT_NAME`，将YOUR_AGENT_NAME替换为您选择的名称。 有效名称示例：swiftyosgpt或SwiftyosAgent或swiftyos_agent

![创建代理](docs/content/imgs/quickstart/007_create_agent.png)

    创建您的代理后，是时候正式进入竞技场了！
    为此，请运行`./run arena enter YOUR_AGENT_NAME`

![进入竞技场](docs/content/imgs/quickstart/008_enter_arena.png)

> 注意：对于高级用户，创建一个新分支，并在arena目录中创建一个名为YOUR_AGENT_NAME.json的文件。然后提交它并创建一个PR以合并到主回购中。只允许单个文件条目。json文件需要以下格式。
```json
{
 "github_repo_url"："https://github.com/Swiftyos/YourAgentName",
 "timestamp"："2023-09-18T10：03:38.051498",
 "commit_hash_to_benchmark"："ac36f7bfc7f23ad8800339fa55943c1405d80d5e",
 "branch_to_benchmark"："master"
}
```
- github_repo_url：指向您的分叉的url
- timestamp：此文件上次更新的时间戳
- commit_hash_to_benchmark：条目的提交哈希值。每次你准备好正式参加黑客马拉松的东西时，你都会更新
- branch_to_benchmark：用于开发代理的分支，默认为master。


## 运行您的代理

您的代理可以使用./run agent start YOUR_AGENT_NAME启动``

这将在http：//localhost：8000/上启动代理``

![启动代理](docs/content/imgs/quickstart/009_start_agent.png)

前端可以从http：//localhost：8000/访问，您首先需要使用google帐户或github帐户登录。``

![登录](docs/content/imgs/quickstart/010_login.png)

登录后，你会得到一个类似这样的页面。您的任务历史记录位于页面左侧，“聊天”窗口可将任务发送给您的代理。

![登录](docs/content/imgs/quickstart/011_home.png)

当您完成代理时，或者如果您只需要重新启动它，请使用Ctl-C结束会话，然后您可以重新运行start命令。

如果您遇到问题并希望确保代理已停止，有一个./run agent stop命令将终止使用端口8000的进程，该端口应该是代理。``

## 对您的代理进行基准测试

也可以使用cli访问基准测试系统：

```bash
agpt%./运行基准
用法：cli.py基准[选项]命令[参数]...

  启动基准测试并列出测试和类别的命令

选项：
  --帮助显示此消息并退出。

命令：
  类别基准类别组命令
  start启动基准测试命令
  测试基准测试组命令
agpt%./运行基准类别     
用法：cli.py基准类别[选项]命令[参数]...

  基准类别组命令

选项：
  --帮助显示此消息并退出。

命令：
  列表列表基准类别命令
agpt%./运行基准测试      
用法：cli.py基准测试[选项]命令[参数]...

  基准测试组命令

选项：
  --帮助显示此消息并退出。

命令：
  details基准测试details命令
  列表列表基准测试命令
```

该基准被分成不同类别的技能，您可以测试您的代理。您可以看到哪些类别可用
```bash
./run基准类别列表
#以及有哪些测试可用
./run基准测试列表
```

![登录](docs/content/imgs/quickstart/012_tests.png)


最后，您可以使用

```bash
./run benchmark start YOUR_AGENT_NAME
```

>
