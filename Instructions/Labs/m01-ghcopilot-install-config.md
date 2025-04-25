<!-- ---
lab:
    title: 'Exercise - Install and configure GitHub Copilot'
    description: 'Learn how to install and configure GitHub Copilot in Visual Studio Code.'
--- -->

# Install and configure GitHub Copilot

In this exercise you will <!-- provide a description of what they'll do and why it;s important -->

This exercise should take approximately **15** minutes to complete.

## Before you start

Your development environment must include the following resources:

- Git version control software.
- The .NET SDK 9.0 (or the latest supported version).
- Visual Studio Code updated to the latest version.
- The C# Dev Kit extension (from Microsoft) installed in Visual Studio Code.

Before you start this exercise, you need to:

1. Verify that Git and the .NET SDK are available in your dev environment. If needed, you can download Git using the following URL: <a href="https://git-scm.com/downloads" target="_blank">Download Git</a> and the .NET SDK using the following URL: <a href="https://dotnet.microsoft.com/download/dotnet" target="_blank">Download .NET SDK</a>
1. Verify that Visual Studio Code and the C# Dev Kit extension are available in your dev environment. You can download Visual Studio Code using the following URL: <a href="https://code.visualstudio.com/download" target="_blank">Download Visual Studio Code</a> and the C# Dev Kit extension using the following URL: <a href="https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp-devkit" target="_blank">C# Dev Kit</a>.

For additional help configuring the Visual Studio Code environment, see <a href="https://learn.microsoft.com/training/modules/install-configure-visual-studio-code/" target="_blank">Install and configure Visual Studio Code for C# development</a>

## Exercise scenario

An accident damaged the servers that host the library database and backend services. It'll take weeks for administrators to obtain the funding/authorization required to replace the servers and get the system back online. Your department needs to develop a temporary solution that will enable librarians to perform basic functions.

Your team has met with the librarians. They need a minimal solution that enables them to provide library patrons with essential services like book loans and returns. Your team investigates the available resources and develops a plan. Initially, only you and one other coworker will be assigned to the project. The local government has closed the library until your temporary solution is available. You have three days develop a v1 solution that enables the library to reopen.

While your colleague begins working on the software, you use library records to create JSON files that represent the library's patron accounts, books, and book loans. By the end of the second day you're ready to begin helping with the code. The solution is a console application that can be run on one of the library's laptop computers. The librarians understand that there isn't time for a pretty interface, but stress that the app must be secure and reliable. You have one more day before you need to demonstrate version 1.0 of your app.

You'll use GitHub Copilot to help get the work done as efficiently as possible. If all goes well, your app will be used to support the library's book drives and other offsite functions in the future.

This exercise includes the following tasks:

1. Install GitHub Copilot extensions for Visual Studio Code.
1. Configure GitHub Copilot extensions for Visual Studio Code.

## Install GitHub Copilot extensions for Visual Studio Code

GitHub Copilot is an AI-powered code completion tool that helps developers write code faster and with fewer errors. The following subscription options are available:

- GitHub Copilot Free: This free tier provides limited access to select features of GitHub Copilot, allowing an individual to experience AI-powered coding assistance without a paid subscription. The free tier currently includes 2000 code completions and 50 chat messages per month.
- GitHub Copilot Pro: This paid tier is available to individual GitHub customers who don't have access to GitHub Copilot through an organization or enterprise. It offers full access to all GitHub Copilot features, including advanced capabilities and unlimited usage, for a comprehensive AI coding experience.
- GitHub Copilot for Business: This paid tier is available for organizations with a GitHub Free or GitHub Team plan, or enterprises on GitHub Enterprise Cloud. GitHub Copilot Business gives organizations and enterprises control over Copilot policies, including which members can use Copilot.
- GitHub Copilot Enterprise: This paid tier is available for enterprises on GitHub Enterprise Cloud. In addition to all of the Copilot Business features, Copilot Enterprise provides additional AI features on GitHub. With this subscription plan you can choose to assign either Copilot Enterprise or Copilot Business to each individual organization in the enterprise.

Use the following steps to complete this section of the exercise:

1. Open Visual Studio Code.

1. On the left side menu, select **Extensions**.

1. In the Search Extensions in Marketplace text box, type **GitHub Copilot** and then press Enter.

1. In the filtered list of extensions, select the GitHub Copilot extension authored by GitHub.

1. On the GitHub Copilot extension page, select **Install**.

1. Watch for a GitHub authorization prompt.

    Your experience with authorization might vary depending on whether you've previously authorized Visual Studio Code for your GitHub account.

    - If you've authorized Visual Studio Code for your account on GitHub, GitHub Copilot is automatically authorized.

    - If you haven't authorized Visual Studio Code in your GitHub account, Visual Studio Code prompts you to sign in to GitHub.

    - If you don't receive a prompt asking you to authorize, select the bell icon on the far right side of Visual Studio Code's bottom panel.

     GitHub requests the necessary permissions for GitHub Copilot when the browser opens.

1. To approve the authorization request, select **Authorize Visual Studio Code**.

    A dialog box named Visual Studio Code opens in Visual Studio Code.

1. To confirm your GitHub authorization in the Visual Studio Code dialog box, select **Open**.

## Configure GitHub Copilot extensions for Visual Studio Code

GitHub Copilot settings are configured in your GitHub.com account and the Visual Studio Code environment. In Visual Studio Code, you access settings for GitHub Copilot and GitHub Copilot Chat using the GitHub Copilot status menu. The settings allow you to enable or disable GitHub Copilot for specific languages, configure the behavior of GitHub Copilot Chat, and customize the GitHub Copilot experience to suit your preferences. You can also configure GitHub Copilot settings on GitHub.com to manage your GitHub Copilot subscription, configure the retention of prompts and suggestions, and allow or block suggestions matching public code.



### Enable or disable GitHub Copilot

GitHub Copilot is enabled by default when you install the extension in Visual Studio Code. You can disable GitHub Copilot for a period of time if you need to.

To view the enable and disable options for the GitHub Copilot extension, follow these steps:

1. In Visual Studio Code, open the **Extensions** view.

1. In the list of installed extensions, scroll down until you find **GitHub Copilot**.

1. To display a dropdown menu for the GitHub Copilot extension that lists Enable and Disable options, select on the gear icon next to GitHub Copilot.

    ![Screenshot showing a dropdown menu for the GitHub Copilot extension.](./media/m01-github-copilot-enable-disable.png)

If you want to test the enable/disable options, you can select the disable option. However, be sure to re-enable GitHub Copilot before you continue with this exercise.

## Configure GitHub Copilot and Copilot Chat in Visual Studio Code

The GitHub Copilot extensions are configured with default settings when you install the extensions in Visual Studio Code. You can customize these settings to suit your preferences.

Visual Studio Code provides two ways to access the settings for the GitHub Copilot extensions:

- You can use the `Manage` icon to open the Visual Studio Code Settings tab. On the Settings tab, you can select **Extensions** and then select **Copilot**.
- You can use the GitHub Copilot status icon to access the GitHub Copilot status menu and then select **Edit Settings**.

Using the GitHub Copilot status menu to access settings opens the Visual Studio Code Settings tab with settings filtered for GitHub Copilot. Using the status menu is the quickest way to access the settings for the GitHub Copilot extensions.

### Configure GitHub Copilot settings

To view the configuration settings for GitHub Copilot, follow these steps:

1. On Visual Studio Code's top menu bar, open the **Toggle Chat** dropdown menu.

    The Toggle Chat menu/button is located on the menu bar at the top of the Visual Studio Code window, just to the right of the Searchbox. It displays a small GitHub Copilot logo.

    ![Screenshot showing how to access the GitHub Copilot status menu.](./media/m01-github-copilot-toggle-chat-menu.png)

1. In the GitHub Copilot status menu, select **Configure Code Completions**, and then select **Edit Settings**.

    ![Screenshot showing the Edit Settings menu option for GitHub Copilot.](./media/github-copilot-status-menu.png)

1. Take a minute to review the list of available settings.

    ![Screenshot showing the available GitHub Copilot settings.](./media/github-copilot-settings-1.png)

    Notice that the settings for both GitHub Copilot and GitHub Copilot Chat are listed. Also, under the Extensions label on the left, both extensions are labeled as Copilot. The first Copilot extension is for GitHub Copilot and the second is for GitHub Copilot Chat.

1. Under the Extensions label, select the first Copilot extension.
  
    ![Screenshot showing the setting for the GitHub Copilot extension.](./media/github-copilot-settings-2.png)

    Notice that the settings list is now filtered for GitHub Copilot only.

    The settings for GitHub Copilot include the following options:

    - Enable Auto Completions
    - Enable or disable Copilot completions for specified languages

1. Take a minute to review the settings for **Enable or disable Copilot completions for specified languages**.

    Notice that the settings for this option are configured using a list of languages and a value of **true** or **false** to enable or disable GitHub Copilot for each language. By default, GitHub Copilot is enabled for all languages. This setting is specified with the wildcard character `*` on the first row and the value **true**. The subsequent rows specify languages for which GitHub Copilot is enabled or disabled. For example, GitHub Copilot is enabled for **C#**, **JavaScript**, and **Python** and disabled for **Plaintext** and **Markdown**.

1. Under **Enable or disable Copilot completions for specified languages**, select **markdown**.

    Notice that the value for Markdown is set to **false**. This means that GitHub Copilot is disabled for Markdown files.

1. To enable Copilot for Markdown files, select **Edit Item** (pencil icon), select **false**, change the value to **true**, and then select **OK**.

    ![Screenshot showing the GitHub Copilot settings for Markdown.](./media/github-copilot-settings-3.png)

    You can now use GitHub Copilot document projects using Markdown files.

1. Under the Extensions label, select the second Copilot extension.

    ![Screenshot showing the GitHub Copilot Chat settings.](./media/github-copilot-settings-4.png)

    Notice that the settings list is now filtered for GitHub Copilot Chat only.

    The settings for GitHub Copilot Chat include **Preview** and **Experimental** options. Setting choices include the following options:

    - **Fix Test Failure**: This option is enabled by default so that GitHub Copilot can provide suggestions for fixing test failures.
    - **Follow Ups**: By default, this setting is set to **firstOnly**, which means that GitHub Copilot provides follow-up suggestions only after the first suggestion. The other options are **always** and **never**.
    - **Local Override**: By default, this option is set to **auto**, which means that GitHub Copilot uses the locale of the Visual Studio Code display language.
    - **Scope Selection**: This option is disabled by default. When enabled, the user is prompted for a scope symbol when the user uses `/explain` in Chat without anything selected in the Editor.
    - **Terminal Chat Location**: The default setting is chatView, which specifies the Chat View. The other options are for the Quick Chat area and the Terminal.
    - **Use Project Templates**: This option is enabled by default so that GitHub Copilot uses relevant GitHub project templates when the user uses `/new` in Chat.
    - **Enable Code Actions**: This option is enabled by default so that GitHub Copilot can provide code actions in the Editor.
    - **Trigger Automatically**: This option is enabled by default so that GitHub Copilot suggestions are shown automatically as you type.

    We recommend keeping the default settings during this training. This helps to ensure that you have the expected experience when working on the modules in this learning path. When you have completed the training, you can experiment with these settings to customize your experience with GitHub Copilot and Copilot Chat.



## Clean up

<!-- Good practice - especially as self-paced learners will be using their own subscriptions -->
<!-- Delete this section if it is not needed -->

Now that you've finished the exercise, you should delete the cloud resources you've created to avoid unnecessary resource usage.

1. Step 1
2. etc.
