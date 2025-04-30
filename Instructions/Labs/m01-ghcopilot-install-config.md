<!-- ---
lab:
    title: 'Exercise - Examine GitHub Copilot settings and interface basics'
    description: 'Learn how to configure GitHub Copilot settings and access GitHub Copilot features in Visual Studio Code.'
--- -->

# Examine GitHub Copilot settings and interface basics

In this exercise you examine GitHub Copilot settings and explore the GitHub Copilot user interface in Visual Studio Code.

This exercise should take approximately **15** minutes to complete.

## Before you start

Before you start this exercise, you need to complete the following tasks:

1. Verify that your lab environment includes the required tools and resources.
1. Verify that GitHub Copilot is enabled in Visual Studio Code.

### Verify required tools and resources

This exercise requires a lab environment (either a hosted environment or a local PC) that's configured for C# development using Visual Studio Code and GitHub Copilot. Access to a GitHub account with GitHub Copilot enabled is also required.

Complete the following steps to verify that your lab environment is configured correctly:

1. Verify that Git version 2.48 or later is installed in your lab environment.

    Run `git --version` in a terminal window to check the version of Git installed.

    If you're running Windows and you want to update Git, you can use the following command:

    ```bash
    git update-git-for-windows
    ```

    If necessary, you can download Git using the following URL: <a href="https://git-scm.com/downloads" target="_blank">Download Git</a>.

1. Verify that the latest LTS or STS version of the .NET SDK is installed in your lab environment.

    Run `dotnet --version` in a terminal window to check the version of the .NET SDK installed.

    If necessary, you can download the .NET SDK using the following URL: <a href="https://dotnet.microsoft.com/download/dotnet" target="_blank">Download .NET SDK</a>.

1. Verify that Visual Studio Code and the C# Dev Kit extension are installed in your lab environment.

    If necessary, you can download Visual Studio Code using the following URL: <a href="https://code.visualstudio.com/download" target="_blank">Download Visual Studio Code</a>

    You can install the C# Dev Kit extension using the Extensions view in Visual Studio Code.

1. Verify that you have access to a GitHub account and GitHub Copilot subscription.

    You can log in to your GitHub account using the following URL: <a href="https://github.com/login" target="_blank">GitHub login</a>. Check your GitHub account settings to verify that you have access to a GitHub Copilot subscription.

    > [!IMPORTANT]
    > If you don't have a GitHub account, you can create an individual account from the GitHub login page (select **Create an account**), and then activate the GitHub Copilot Free plan in the next section. If you have access to a GitHub Copilot Pro, GitHub Copilot Business, or GitHub Copilot Enterprise subscription from within the lab environment, you can use your existing GitHub Copilot subscription to complete this exercise.

### Verify GitHub Copilot access in Visual Studio Code

GitHub offers three Copilot plans for individual developers, and two plans for organizations and enterprises. The plans are designed to meet the needs of individual developers, teams, and organizations. The GitHub Copilot Free plan is available to all individual GitHub users, while the paid plans are available to individuals and organizations that require additional features and capabilities.

Use the following steps to complete this section of the exercise:

1. Open Visual Studio Code.

1. On the bottom panel of Visual Studio Code, to activate GitHub Copilot, select the GitHub Copilot **Settings** button, and then select **Set up Copilot**.

    ![Screenshot showing the GitHub Copilot Settings button.](./media/m01-github-copilot-settings-button.png)

1. On the **Sign in to use Copilot for free** page, select **Sign in**.

    The GitHub account sign in page opens in your default web browser.

1. On the GitHub sign in page, enter your GitHub account credentials, and then select **Sign in**.

1. Follow the instructions to authenticate your account and authorize access in Visual Studio Code.

    You will be directed back to Visual Studio Code when the authorization is complete.

1. To verify that GitHub Copilot is activated, open Visual Studio Code's **Extensions** view.

    You should see the GitHub Copilot and GitHub Copilot Chat extensions listed in the **Installed** section of the Extensions view.

    ![Screenshot showing the GitHub Copilot status menu.](./media/m01-github-copilot-extensions-vscode.png)

You're now ready to complete the exercise.

## Exercise scenario

You're a developer working in the IT department of a rural community. The backend systems that support the public library were lost in a fire. Your team needs to develop a temporary solution to help the library staff manage their operations until the system can be replaced. Your team chose GitHub Copilot to help speed up the development process.

This exercise includes the following tasks:

1. Activate GitHub Copilot Free in Visual Studio Code using your individual GitHub account.
1. Configure the GitHub Copilot extensions for Visual Studio Code.

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
