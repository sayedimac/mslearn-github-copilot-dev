<!-- ---
lab:
    title: 'Exercise - Analyze and document code using GitHub Copilot'
    description: 'Learn how to install and configure GitHub Copilot in Visual Studio Code.'
--- -->

# Analyze and document code using GitHub Copilot

GitHub Copilot can help you understand and document a codebase by generating explanations and documentation.

This exercise should take approximately **20** minutes to complete.

## Before you start

Before you start this exercise, you need to complete the following tasks:

1. Verify required tools and resources.
1. Verify that GitHub Copilot is enabled in Visual Studio Code.

### Verify required tools and resources

This exercise requires a lab environment (either a hosted environment or a local PC) that's configured for C# development using Visual Studio Code and GitHub Copilot. Access to a GitHub account with GitHub Copilot enabled is required.

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
    > If you don't have a GitHub account, you can create an individual account from the GitHub login page (select **Create an account**), and then activate the **GitHub Copilot Free** plan in the next section. If you have access to a GitHub Copilot Pro, GitHub Copilot Business, or GitHub Copilot Enterprise subscription from within the lab environment, you can use your existing GitHub Copilot subscription to complete this exercise.

### Configure the GitHub Copilot Free plan in Visual Studio Code

GitHub offers three Copilot plans for individual developers, and two plans for organizations and enterprises. The plans are designed to meet the needs of individual developers, teams, and organizations. The GitHub Copilot Free plan is available to all individual GitHub users, while the paid plans are available to individuals and organizations that require additional features and capabilities.

> [!NOTE]
> If you've already verified access to a GitHub Copilot subscription i your lab environment, you can skip this section and proceed to the exercise scenario.

Complete the following steps to verify that your lab environment is configured correctly:

1. Open Visual Studio Code.

1. On the Visual Studio Code Status Bar, to activate GitHub Copilot, hover the mouse pointer over the Copilot icon, and then select **Set up Copilot**.

    ![Screenshot showing the GitHub Copilot Settings button.](./media/m00-github-copilot-setup.png)

1. On the **Sign in to use Copilot for free** page, select **Sign in**.

    The GitHub account sign in page opens in your default web browser.

1. On the GitHub sign in page, enter the GitHub account credentials that you'll be using for this exercise, and then select **Sign in**.

1. Follow the online instructions to authenticate your account and authorize access in Visual Studio Code.

    You'll be directed back to Visual Studio Code when the authentication/authorization process is complete.

1. To verify that GitHub Copilot is activated, open Visual Studio Code's **Extensions** view.

    You should see the GitHub Copilot and GitHub Copilot Chat extensions listed in the **Installed** section of the Extensions view.

    ![Screenshot showing GitHub Copilot the Visual Studio Code Extensions view.](./media/m00-github-copilot-extensions-vscode.png)

You're now ready to complete the exercise.

## Exercise scenario

You're a developer working in the IT department of your local community. The backend systems that support the public library were lost in a fire. Your team needs to develop a temporary solution to help the library staff manage their operations until the system can be replaced. Your team chose GitHub Copilot to help speed up the development process.

This exercise includes the following tasks:

- Set up the library application in Visual Studio Code.
- Use GitHub Copilot to explain the library application codebase.
- Use GitHub Copilot to create a README.md file for the library application.

## Set up the library application in Visual Studio Code

Your colleague has developed an initial version of the library application and has made it available as a .zip file. You'll need to download the zip file, extract the code files, and then open the solution in Visual Studio Code.

Use the following steps to set up the library application:

1. To download a zip file containing the library application, select the following URL: [GitHub Copilot lab - Analyze and document code](https://github.com/MicrosoftLearning/mslearn-github-copilot-dev/raw/refs/heads/main/DownloadableCodeProjects/Downloads/AZ2007LabAppM2.zip)

    The zip file is named **AZ2007LabAppM2.zip**.

1. Extract the files from the **AZ2007LabAppM2.zip** file.

    For example:

    1. Navigate to the downloads folder in your lab environment.

    1. Right-click **AZ2007LabAppM2.zip**, and then select **Extract all**.

    1. Select **Show extracted files when complete**, and then select **Extract**.

1. Open the extracted files folder, then copy the **AccelerateDevGHCopilot** folder to a location that's easy to access, such as your Windows Desktop folder.

1. Open the **AccelerateDevGHCopilot** folder in Visual Studio Code.

    For example:

    1. Open Visual Studio Code in your lab environment.

    1. In Visual Studio Code, on the **File** menu, select **Open Folder**.

    1. Navigate to the Windows Desktop folder, select **AccelerateDevGHCopilot** and then select **Select Folder**.

1. In the Visual Studio Code SOLUTION EXPLORER view, verify the following solution structure:

    - AccelerateDevGHCopilot\
        - src\
            - Library.ApplicationCore\
            - Library.Console\
            - Library.Infrastructure\
        - tests\
            - UnitTests\

1. Ensure that the solution builds successfully.

    For example, in the SOLUTION EXPLORER view, right-click **AccelerateDevGHCopilot**, and then select **Build**.

    You'll see some Warnings, but there shouldn't be any Errors.

## Use GitHub Copilot to explain the library application codebase

It's important to understand an application's architecture and key features before documenting the project. GitHub Copilot can help you to understand an unfamiliar codebase by generating explanations at the solution, file, and code line levels.

### Analyze code using prompts in the Chat view

GitHub Copilot's Chat view includes a chat-based interface that allows you to interact with GitHub Copilot using natural language prompts. When evaluating an existing codebase for the first time, you can create prompts that generate an explanation at the workspace or project level, or at the code block or code line level. To assist you in specifying the context of your prompt, GitHub Copilot provides chat participants, chat variables, and slash commands.

- Chat participants are used to scope your prompt to a specific domain.
- Chat variables are used to include specific context in your prompt.
- Slash commands are used to avoid writing complex prompts for common scenarios.

Use the following steps to complete this section of the exercise:

1. Ensure that the **AccelerateDevGHCopilot** solution is open in Visual Studio Code.

1. Open GitHub Copilot's Chat view.

    To open the Chat view, select the **Toggle Chat** button at the top of the Visual Studio Code window.

    ![Screenshot showing the GitHub Copilot status menu.](./media/m02-github-copilot-toggle-chat.png)

    You can also open the Chat view using the **Ctrl+Alt+I** keyboard shortcut.

1. In the Chat view, enter a prompt that uses GitHub Copilot's **@workspace** Chat participant to generate a description of the project.

    For example, enter the following prompt in the Chat view:

    ```plaintext
    @workspace describe this project
    ```

    Use Chat participants, such as the `@workspace`, to scope your prompt to a specific domain. Chat participants are like domain experts who have a specialty that they can help you with. Use @workspace when you want GitHub Copilot to consider the structure of your project, how different parts of your code interact, or design patterns in your project.

    To see a list of all available chat participants, type **@** in the chat prompt box.

1. Take a few minutes to compare GitHub Copilot's response with the actual project files.

    You should see a response similar to the following description:

    ```markdown

    This project is a .NET solution named AccelerateDevGHCopilot that appears to be a library and application framework with a modular structure. It is organized into three main components under the *src* directory and a unit testing project under the *tests* directory. Here's a breakdown:
    
    ## Solution Structure

    - Solution File: AccelerateDevGHCopilot.sln

        - Contains references to the projects in the solution.

    ## Projects

    1. Library.ApplicationCore:
    
        - A core library targeting .NET 8.0.
        - Likely contains core entities, enums, interfaces, and services.
        - No external dependencies are defined in its project.assets.json.

    2. Library.Infrastructure:
    
        - Provides infrastructure-level functionality.
        - Depends on Library.ApplicationCore and uses Microsoft.Extensions.Configuration and related packages.
        - Targets .NET 8.0.

    3. Library.Console:
    
        - A console application that likely serves as the entry point for the project.
        - Depends on Library.ApplicationCore and Library.Infrastructure.
        - Uses Microsoft.Extensions.DependencyInjection, Microsoft.Extensions.Configuration.Json, and other related packages.
        - Targets .NET 8.0.

    4. UnitTests:
    
        - A unit testing project for the solution.
        - Depends on Library.ApplicationCore.
        - Uses testing frameworks like xUnit, NSubstitute, and coverlet.collector.
        - Targets .NET 8.0.

    ## Key Features

    - Dependency Injection: The use of Microsoft.Extensions.DependencyInjection suggests that the project employs dependency injection for managing dependencies.
    - Configuration Management: The use of Microsoft.Extensions.Configuration and Microsoft.Extensions.Configuration.Json indicates support for configuration management, likely using JSON files.
    - Unit Testing: The UnitTests project ensures the solution is well-tested with xUnit and mocking frameworks like NSubstitute.
    - .NET 8.0: All projects target .NET 8.0, leveraging the latest features of the .NET ecosystem.

    ```

1. Use the SOLUTION EXPLORER view to expand the project folders.

1. Locate and open the **ConsoleApp.cs** file.

    The ConsoleApp.cs file is located in the **src/Library.Console** folder.

1. Take a minute to examine the code file.

1. Enter a prompt in the Chat view that generates a description of the **ConsoleApp** class.

    For example, enter the following prompt in the Chat view:

    ```plaintext
    @workspace #class describe the ConsoleApp class
    ```

    Use chat variables, such as **#class**, to include specific context in your prompt. To see a list of all available chat variables, type **#** in the chat prompt box.

    > [!NOTE]
    > GitHub Copilot considers your chat history and the code files you have open in Visual Studio Code when constructing a context for your prompt and generating a response.

1. Take a minute to verify the accuracy of GitHub Copilot's response.

    You should see a response similar to the following description:

    ```markdown

    The ConsoleApp class in ConsoleApp.cs is responsible for managing the console-based user interface of the library management system. It handles user interactions, processes user inputs, and coordinates actions with the underlying services and repositories.

    ### Fields

    - _currentState: Tracks the current state of the console application.
    - matchingPatrons: A list of patrons that match a search query.
    - selectedPatronDetails: Holds details of the currently selected patron.
    - selectedLoanDetails: Holds details of the currently selected loan.
    - _patronRepository: An instance of IPatronRepository for accessing patron data.
    - _loanRepository: An instance of ILoanRepository for accessing loan data.
    - _loanService: An instance of ILoanService for performing loan-related operations.
    - _patronService: An instance of IPatronService for performing patron-related operations.

    ### Constructor

    - ConsoleApp(ILoanService loanService, IPatronService patronService, IPatronRepository patronRepository, ILoanRepository loanRepository): Initializes the ConsoleApp with the provided services and repositories.

    ### Methods

    - Run(): The main entry point for running the console application.
    - PatronSearch(): Handles the logic for searching patrons.
    - ReadPatronName(): Reads the patron's name from the console input.
    - PrintPatronsList(List<Patron> matchingPatrons): Prints a list of matching patrons to the console.
    - PatronSearchResults(): Handles the logic for displaying and selecting from the search results.
    - ReadInputOptions(CommonActions options, out int optionNumber): Reads input options from the console.
    - WriteInputOptions(CommonActions options): Writes the available input options to the console.
    - PatronDetails(): Displays details of the selected patron.
    - LoanDetails(): Displays details of the selected loan and handles actions like extending or returning the loan.

    The class uses a state machine approach to manage different states of the console application, such as searching for patrons, displaying search results, showing patron details, and handling loan details.

    ```

1. Open the **Program.cs** file and examine the code.

1. Enter a prompt in the Chat view that generates an explanation of the Program.cs file.

    For example, enter the following prompt in the Chat view:

    ```plaintext
    @workspace /explain Explain the Program.cs file
    ```

    Use Slash commands, such as **/explain**, to avoid writing complex prompts for common scenarios. To see a list of all available slash commands, type **/** in the chat prompt box. Available slash commands may vary, depending on your environment and the context of your chat.

1. Take a minute to review the detailed response generated by GitHub Copilot.

    You should see a response that breaks down the Program.cs file, practically line-by-line, and explains the purpose of each line or code section.

1. Close the Program.cs file.

### Improve chat responses by adding context

GitHub Copilot uses context to generate more relevant responses. Identifying relevant code files is one way to establish context.

Opening files in the code editor is one way to establish context, but you can also add files to the Chat context using drag-and-drop operations or by using the **Attach Context** button in the Chat view.

Use the following steps to complete this section of the exercise:

1. Expand the **Library.Infrastructure** project, and then expand the **Data** folder.

1. Use a drag-and-drop operation to add the following files from the SOLUTION EXPLORER view to the Chat context: **JsonData.cs**, **JsonLoanRepository.cs**, and **JsonPatronRepository.cs**.

    GitHub Copilot uses the Chat Context to understand the code files that are relevant to your prompt. You can add files to the Chat context using drag-and-drop operations, or you can use the **Attach Context** button in the Chat view.

    Instead of adding individual files manually, you can let Copilot find the right files from your codebase automatically. This can be useful when you don't know which files are relevant to your question.

    To let Copilot find the right files automatically, add #codebase in your prompt or select Codebase from the list of context types.

1. Enter a prompt in the Chat view that generates an explanation of the data access classes.

    For example, enter the following prompt in the Chat view:

    ```plaintext
    @workspace Explain how the data access classes work
    ```

1. Take a couple minutes to review the response.

    You should see a response that includes information similar to the following description:

    ```markdown
    The `JsonData` class in `JsonData.cs` is responsible for managing the loading and saving of data from JSON files. It handles various entities such as `Author`, `Book`, `BookItem`, Patron`, and `Loan`. The class uses the `IConfiguration` interface to read file paths from the configuration settings, ensuring that the correct JSON files are loaded.
    
    The constructor of the `JsonData` class initializes the file paths for each entity by reading from the configuration section "JsonPaths". If the paths are not specified in the configuration, it defaults to specific paths within a "Json" directory.
    
    The `EnsureDataLoaded` method checks if the data is already loaded and, if not, calls the `LoadData` method to load the data from the JSON files. The `LoadData` method reads the JSON files and deserializes them into the respective lists of entities.
    
    The `SaveLoans` and `SavePatrons` methods handle saving the loan and patron data back to the JSON files. These methods ensure that only a subset of properties is saved, maintaining data integrity and consistency.
    
    The class also provides methods to populate entities with related data. For example, `GetPopulatedPatrons` and `GetPopulatedPatron` methods populate patron entities with their associated loans. Similarly, `GetPopulatedLoan` and `GetPopulatedBookItem` methods populate loan and book item entities with their related data.
    
    The `LoadJson` and `SaveJson` methods are utility methods for reading from and writing to JSON files. They use the `JsonSerializer` class to handle the serialization and deserialization processes.
    
    Overall, the `JsonData` class serves as a central point for managing the persistence of data in JSON format, ensuring that the application can load, save, and manipulate data efficiently.
    ```

1. Take a couple minutes to examine the JSON data files that are used to simulate library records.

    The JSON data files are located in the `src/Library.Console/Json` folder.

    The data files use ID properties to link entities. For example, a `Loan` object has a `PatronId` property that links to a `Patron` object with the same ID. The JSON files contain data for authors, books, book items, patrons, and loans.

    > [!NOTE]
    > Notice that Author names, book titles, and patron names have been anonymized for the purposes of this guided project.

### Build and run the application

Running the application helps you understand the user interface, key features of the application, and how app components interact.

Use the following steps to complete this section of the exercise:

1. Ensure that you have the **Solution Explorer** view open.

    The Solution Explorer view is not the same as the Explorer view. The Solution Explorer view uses project and solution files as "directory" nodes to display the structure of the solution.

1. To run the application, right-click **Library.Console**, select **Debug**, and then select **Start New Instance**.

    If the **Debug** and **Start New Instance** options aren't displayed, ensure that you're using the Solution Explorer view and not the Explorer view.

    The following steps guide you through a simple use case.

1. When prompted for a patron name, type **One** and then press Enter.

    You should see a list of patrons that match the search query.

    > [!NOTE]
    > The application uses a case-sensitive search process.

1. At the "Input Options" prompt, type **2** and then press Enter.

    Entering **2** selects the second patron in the list.

    You should see the patron's name and membership status followed by book loan details.

1. At the "Input Options" prompt, type **1** and then press Enter.

    Entering **1** selects the first book in the list.

    You should see book details listed, including the due date and return status.

1. At the "Input Options" prompt, type **r** and then press Enter.

    Entering **r** returns the book.

1. Verify that the message "Book was successfully returned." is displayed.

    The message "Book was successfully returned." should be followed by the book details. Returned books are marked with `Returned: True`.

1. To begin a new search, type **s** and then press Enter.

1. When prompted for a patron name, type **One** and then press Enter.

1. At the "Input Options" prompt, type **2** and then press Enter.

1. Verify that first book loan is marked `Returned: True`.

1. At the "Input Options" prompt, type **q** and then press Enter.

1. Stop the debug session.

## Create the project documentation for the README file

The README file is an essential part of any GitHub repository. The README provides information based on the needs of the project, project contributors, and stakeholders.

For this guided project exercise, your README file should include the following sections:

- **Project Title**: A brief, clear title for the project.
- **Description**: A detailed explanation of what the project is and what it does.
- **Project Structure**: A breakdown of the project structure, including key folders and files.
- **Key Classes and Interfaces**: A list of key classes and interfaces in the project.
- **Usage**: Instructions on how to use the project, often including code examples.
- **License**: The license that the project is under.

In this section of the exercise, you'll use GitHub Copilot to create project documentation and add it to your `README.md` file.

Use the following steps to complete this section of the exercise:

1. Open the Chat view.

    When you're interested in specific code or files, you can use drag-and-drop operations to add files to the Chat view context. In this case, you're interested in the overall solution, so you'll use the `@workspace` participant rather than adding individual files.

1. To generate project documentation for your README file, enter the following prompt:

    ```plaintext
    @workspace Generate the contents of a README.md file for the code repository. Use "Library App" as the project title. The README file should include the following sections: Description, Project Structure, Key Classes and Interfaces, Usage, License. Format all sections as raw markdown. Use a bullet list with indents to represent the project structure. Do not include ".gitignore" or the ".github", "bin", and "obj" folders.
    ```

    > [!NOTE]
    > Using multiple prompts, one for each section of the README file would produce more detailed results. A single prompt is used in this exercise to simplify the process.

1. Review the response to ensure each section is formatted as markdown.

    > [!NOTE]
    > You can update sections individually to provide more detailed information or if they aren't formatted correctly. You can also copy GitHub Copilot's response to the README file and then make corrections directly in the markdown file.

1. Copy the suggested documentation sections to the README.md file.

    ```markdown
    # Library App
    
    ## Description
    Library App is a console-based application for managing library operations such as patron management, book loans, and membership renewals. It uses a JSON-based data storage system and provides various services to handle library functionalities.
    
    ## Project Structure
    - AccelerateDevGHCopilot.sln
    - README.md
    - src
      - `Library.ApplicationCore/`
        - `Entities/`
          - `Author.cs`
          - `Book.cs`
          - `BookItem.cs`
          - `Loan.cs`
          - `Patron.cs`
        - `Enums/`
          - `LoanExtensionStatus.cs`
          - `LoanReturnStatus.cs`
          - `MembershipRenewalStatus.cs`
        - `Interfaces/`
          - `IPatronRepository.cs`
          - `IPatronService.cs`
          - `ILoanRepository.cs`
          - `ILoanService.cs`
        - `Library.ApplicationCore.csproj`
        - `Services/`
          - `PatronService.cs`
          - `LoanService.cs`
      - `Library.Console/`
        - `appSettings.json`
        - `CommonActions.cs`
        - `ConsoleApp.cs`
        - `ConsoleState.cs`
        - `Library.Console.csproj`
        - `Program.cs`
      - `Library.Infrastructure/`
        - `Data/`
          - `JsonData.cs`
          - `JsonLoanRepository.cs`
          - `JsonPatronRepository.cs`
        - `Library.Infrastructure.csproj`
    - tests
      - `UnitTests/`
        - `ApplicationCore/`
          - `LoanService/`
            - `ReturnLoan.cs`
            - `ExtendLoan.cs`
          - `PatronService/`
            - `RenewMembership.cs`
        - `UnitTests.csproj`
    
    ## Key Classes and Interfaces
    - **Entities**
      - **Author**: Represents an author with properties like `Id` and `Name`.
      - **Book**: Represents a book with properties like `Id`, `Title`, `AuthorId`, `Genre`, `ImageName`, and `ISBN`.
      - **BookItem**: Represents a specific copy of a book with properties like `Id`, `BookId`, `AcquisitionDate`, and `Condition`.
      - **Loan**: Represents a loan with properties like `Id`, `BookItemId`, `PatronId`, `LoanDate`, `DueDate`, and `ReturnDate`.
      - **Patron**: Represents a library patron with properties like `Id`, `Name`, `MembershipStart`, `MembershipEnd`, and `Loans`.
    
    - **Enums**
      - **LoanExtensionStatus**: Enum for loan extension statuses.
      - **LoanReturnStatus**: Enum for loan return statuses.
      - **MembershipRenewalStatus**: Enum for membership renewal statuses.
    
    - **Interfaces**
      - **IPatronRepository**: Interface for patron repository with methods like `GetPatron`, `SearchPatrons`, and `UpdatePatron`.
      - **IPatronService**: Interface for patron service with method `RenewMembership`.
      - **ILoanRepository**: Interface for loan repository with methods like `GetLoan` and `UpdateLoan`.
      - **ILoanService**: Interface for loan service with methods like `ReturnLoan` and `ExtendLoan`.
    
    - **Services**
      - **PatronService**: Implements `IPatronService` to handle patron-related operations.
      - **LoanService**: Implements `ILoanService` to handle loan-related operations.
    
    - **Console**
      - **ConsoleApp**: Main console application class that handles user interactions and application flow.
      - **ConsoleState**: Enum for different states of the console application.
      - **CommonActions**: Enum for common actions in the console application.
    
    - **Infrastructure**
      - **JsonData**: Handles loading and saving data to JSON files.
      - **JsonLoanRepository**: Implements `ILoanRepository` to manage loan data.
      - **JsonPatronRepository**: Implements `IPatronRepository` to manage patron data.
    
    ## Usage
    1. Clone the repository.
    2. Open the solution file AccelerateDevGHCopilot.sln in Visual Studio.
    3. Build the solution to restore dependencies.
    4. Run the `Library.Console` project to start the console application.
    5. Follow the on-screen instructions to search for patrons, view patron details, extend loans, return books, and renew memberships.
    
    ## License
    This project is licensed under the MIT License.
    ```

1. Adjust the formatting manually if needed, and then save the updated README.md file.

1. Open Visual Studio Code's Source Control view.

1. To have GitHub Copilot generate a commit message, select the icon on the right side of the message box.

    You should see a commit message similar to the following message:

    ```plaintext
    chore: Update README.md with project description and usage instructions
    ```

1. Stage and Commit the file updates.

1. Sync (or Push) your updates to the GitHub repository.

## Check your work

To check your work, complete the following steps:

1. Open the GitHub repository for the AccelerateDevGHCopilot project.

1. Use the **Code** tab to review the updated README.md file.

1. Ensure that the project structure described in the README file aligns the folder structure of the repository.

1. Review the commit history and locate the commit message generated by GitHub Copilot.
