<!-- ---
lab:
    title: 'Exercise - Refactor and improve existing code sections using GitHub Copilot'
    description: 'Learn how to refactor and improve existing code sections using GitHub Copilot in Visual Studio Code.'
--- -->

# Refactor and improve existing code sections using GitHub Copilot

GitHub Copilot can be used to evaluate your entire codebase and suggest changes that refactor and/or improve your code. In this exercise, you use GitHub Copilot to refactor specified sections of a C# application while making improvements to code quality, reliability, performance, and security.

This exercise should take approximately **15** minutes to complete.

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
> If you've already verified access to a GitHub Copilot subscription in your lab environment, you can skip this section and proceed to the exercise scenario.

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

You're a developer working in the IT department of your local community. The backend systems that support the public library were lost in a fire. Your team needs to develop a temporary solution to help the library staff manage their operations until the system can be replaced. Your team chose GitHub Copilot to accelerate the development process.

You handed off an initial version of the library application for review. The review team identified opportunities to improve code quality, performance, readability, maintainability, and security. 

The following updates are assigned to you:

1. Refactor the EnumHelper class to use static dictionaries instead of reflection.

    - Using static dictionaries will improve performance (removes the overhead of reflection).
    - Eliminating reflection also improves code readability, maintainability, and security.

1. Refactor the data access methods to use LINQ (Language Integrated Query) rather than foreach loops.

    - Using LINQ provides a more concise and readable way to query collections, databases, and XML documents.
    - Using LINQ can improve code readability, maintainability, and performance.

This exercise includes the following tasks:

1. Set up the library application in Visual Studio Code.
1. Use GitHub Copilot to refactor the EnumHelper class.
1. Update the data access methods to use LINQ.

## Set up the library application in Visual Studio Code

You need to download the existing application, extract the code files, and then open the solution in Visual Studio Code.

Use the following steps to set up the library application:

1. To download a zip file containing the library application, select the following URL: [GitHub Copilot lab - refactor existing code](https://github.com/MicrosoftLearning/mslearn-github-copilot-dev/raw/refs/heads/main/DownloadableCodeProjects/Downloads/AZ2007LabAppM5.zip)

    The zip file is named **AZ2007LabAppM5.zip**.

1. Extract the files from the **AZ2007LabAppM5.zip** file.

    For example:

    1. Navigate to the downloads folder in your lab environment.

    1. Right-click **AZ2007LabAppM5.zip**, and then select **Extract all**.

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

## Use GitHub Copilot to refactor the EnumHelper class

Reflection is a powerful feature that allows you to inspect and manipulate objects at runtime. However, reflection can be slow and there are potential security risks associated with reflection that should be considered.

The existing EnumHelper class uses reflection to retrieve the description attribute of an enum value. You need to refactor the EnumHelper class to use dictionaries instead of reflection. Using dictionaries can improve performance and eliminate any security concerns associated with using reflection.

In this exercise, you use GitHub Copilot to help you refactor the EnumHelper class.

Use the following steps to complete this section of the exercise:

1. Use Visual Studio Code's SOLUTION EXPLORER view to expand the **Library.ApplicationCore** folder, and then expand the **Enums** folder.

1. Open the EnumHelper.cs file and review the code.

    ```csharp
    using System.ComponentModel;
    using System.Reflection;
    
    namespace Library.ApplicationCore.Enums;
    
    public static class EnumHelper
    {
        public static string GetDescription(Enum value)
        {
            if (value == null)
                return string.Empty;
    
            FieldInfo fieldInfo = value.GetType().GetField(value.ToString())!;
    
            DescriptionAttribute[] attributes =
                (DescriptionAttribute[])fieldInfo.GetCustomAttributes(typeof(DescriptionAttribute), false);
    
            if (attributes != null && attributes.Length > 0)
            {
                return attributes[0].Description;
            }
            else
            {
                return value.ToString();
            }
        }
    }
    ```

    The `GetDescription` method uses reflection to retrieve the description attribute of an enum value. The method checks if the `value` parameter is null. If it is, the method returns an empty string. Otherwise, it uses reflection to get the field information for the enum value and retrieves the custom attributes of type `DescriptionAttribute`. If any attributes are found, it returns the description; otherwise, it returns the string representation of the enum value.

1. Open the GitHub Copilot Chat view.

    The Chat view provides a managed conversational interface for interacting with GitHub Copilot.

    You can toggle the Chat view between open and closed using the **Toggle Chat** button, which is located at the top of the Visual Studio Code window, just to the right of the search textbox.

    ![Screenshot showing the Copilot Toggle Chat button.](./media/m01-github-copilot-toggle-chat.png)

    You can also use the keyboard shortcut **Ctrl+Alt+I** to toggle the Chat view.

1. Notice that the Chat view opens in **Ask** mode by default.

    The Chat mode is displayed near the bottom-right corner of the Chat view.

    The Set Mode menu includes three chat modes: **Ask**, **Edit**, and **Agent**. Each mode is designed for different types of interactions with GitHub Copilot.

    - **Ask**: Use this mode to ask GitHub Copilot questions about your codebase. You can ask GitHub Copilot to explain code, suggest changes, or provide information about the codebase.
    - **Edit**: Use this mode to edit code in your workspace. You can use GitHub Copilot to refactor code, add comments, or make other changes to your code.
    - **Agent**: Use this mode to run GitHub Copilot as an agent. You can use GitHub Copilot to run commands, execute code, or perform other tasks in your workspace.

1. Ensure that the Chat mode is set to **Ask**.

   GitHub Copilot's responses are displayed in the Chat view wen you're working in **Ask** mode.

1. Add the following files to the Chat context:

    - EnumHelper.cs
    - LoanExtensionStatus.cs
    - LoanReturnStatus.cs
    - MembershipRenewalStatus.cs

    You can use a drag-and-drop operation to add the files from Visual Studio Code's explorer view to the Chat view. You can also use the **Add Context** button in the Chat view to add the files.

    > **NOTE**: Adding files to the Chat context ensures that GitHub Copilot considers those files when generating a response. The relevance and accuracy of responses increase when GitHub Copilot understands the context associated with your prompts.

1. Enter the following prompt:

    ```plaintext
    @workspace I need to refactor the `EnumHelper` class and remove any code that uses reflection. Use static dictionaries to supply enum description attributes. Use a separate dictionary for each enum. The dictionaries should use values from the `LoanExtensionStatus.cs`, `LoanReturnStatus.cs`, and `MembershipRenewalStatus.cs` files. Explain how to update the EnumHelper class using dictionaries rather than reflection and provide the updated code.
    ```

    When writing a prompt that asks GitHub Copilot how to solve a problem, be sure explain the problem that you're trying to solve. Use concise sentences to provide details and specify constraints. Also, be sure to tell GitHub Copilot what to include in the response.

    In this case, your prompt begins by explaining the problem. You tell GitHub Copilot that you need to refactor the `EnumHelper` class and remove any code that uses reflections. You tell GitHub Copilot that you want to use dictionaries to supply enum description attributes. You specify that you want a separate dictionary for each enum, and you tell GitHub Copilot that the enum values should be sourced from specific files that you specify by name. You finish by asking GitHub Copilot to explain how to update the `EnumHelper` class, and you ask for a code sample containing the updated code.

1. Take a minute to review the response provided by GitHub Copilot.

    The response should be similar to the following example:

    ```markdown

    To refactor the `EnumHelper` class to use dictionaries for each enum, you need to create a dictionary for each enum type that maps the enum values to their descriptions. This will eliminate the need for reflection at runtime.

    Here's how you can update the `EnumHelper` class:

    1. Create dictionaries for each enum type.
    2. Populate these dictionaries with the enum values and their corresponding descriptions.
    3. Update the `GetDescription` method to use these dictionaries.

    Below is the updated code for the EnumHelper class:

    ```

    ```csharp

    using System.ComponentModel;
    using System.Collections.Generic;
    
    namespace Library.ApplicationCore.Enums;

    public static class EnumHelper
    {
        private static readonly Dictionary<MembershipRenewalStatus, string> MembershipRenewalStatusDescriptions = new()
        {
            { MembershipRenewalStatus.Success, "Membership renewal was successful." },
            { MembershipRenewalStatus.PatronNotFound, "Patron not found." },
            { MembershipRenewalStatus.TooEarlyToRenew, "It is too early to renew the membership." },
            { MembershipRenewalStatus.LoanNotReturned, "Cannot renew membership due to an outstanding loan." },
            { MembershipRenewalStatus.Error, "Cannot renew membership due to an error." }
        };

        private static readonly Dictionary<LoanReturnStatus, string> LoanReturnStatusDescriptions = new()
        {
            { LoanReturnStatus.Success, "Book was successfully returned." },
            { LoanReturnStatus.LoanNotFound, "Loan not found." },
            { LoanReturnStatus.AlreadyReturned, "Cannot return book as the book is already returned." },
            { LoanReturnStatus.Error, "Cannot return book due to an error." }
        };

        private static readonly Dictionary<LoanExtensionStatus, string> LoanExtensionStatusDescriptions = new()
        {
            { LoanExtensionStatus.Success, "Book loan extension was successful." },
            { LoanExtensionStatus.LoanNotFound, "Loan not found." },
            { LoanExtensionStatus.LoanExpired, "Cannot extend book loan as it already has expired. Return the book instead." },
            { LoanExtensionStatus.MembershipExpired, "Cannot extend book loan due to expired patron's membership." },
            { LoanExtensionStatus.LoanReturned, "Cannot extend book loan as the book is already returned." },
            { LoanExtensionStatus.Error, "Cannot extend book loan due to an error." }
        };

        public static string GetDescription(Enum value)
        {
            if (value == null)
                return string.Empty;

            return value switch
            {
                MembershipRenewalStatus status => MembershipRenewalStatusDescriptions[status],
                LoanReturnStatus status => LoanReturnStatusDescriptions[status],
                LoanExtensionStatus status => LoanExtensionStatusDescriptions[status],
                _ => value.ToString()
            };
        }
    }

    ```

    ```markdown

    This refactored EnumHelper class uses dictionaries to store the descriptions for each enum type. The GetDescription method now uses pattern matching to determine the type of the enum and retrieves the description from the appropriate dictionary. This approach avoids the use of reflection and improves performance.

    ```

1. In the Chat view, hover the mouse pointer over the code snippet included in the response.

1. Notice the three buttons that appear in the top-right corner of the code snippet.

1. Hover the mouse pointer over each of the buttons to see a tooltip that describes the action.

    These buttons can the used to either insert the code into the code editor or copy the code to the clipboard.

1. In the Chat view, select **Set Mode**, and then select **Edit**.

    When prompted to confirm the change, select **Yes**.

    In **Edit** more, GitHub Copilot displays responses as code update suggestions in code editor. The Edit mode is generally used when implementing a new feature, fixing a bug, or refactoring code.

1. Enter the following prompt:

    ```plaintext
    @workspace Refactor the `EnumHelper` class using dictionaries rather than reflection to get enum description attributes. Use a separate dictionary for each enum. Use the enum values in the `LoanExtensionStatus.cs`, `LoanReturnStatus.cs`, and `MembershipRenewalStatus.cs` files.
    ```

    This prompt tells GitHub Copilot to refactor the `EnumHelper` class using dictionaries rather than reflection to get enum description attributes. It also specifies that a separate dictionary should be used for each enum, and that the enum values should be taken from the specified files.

1. Take a minute to review the suggested code updates.

    Review the suggested updates to ensure that the enum values are coming from the `LoanExtensionStatus.cs`, `LoanReturnStatus.cs`, and `MembershipRenewalStatus.cs` files.

    Open each of the enum files and verify that the enum values in the dictionaries are correct. If there are discrepancies, have GitHub Copilot update the dictionaries for each enum individually. For example, you can use the following prompt for the `LoanExtensionStatus` enum:

    ```plaintext
    @workspace Use the description values in LoanExtensionStatus.cs to update the LoanExtensionStatus dictionary in the EnumHelper class. Provide the updated code for the LoanExtensionStatus dictionary in the EnumHelper class.
    ```

    If necessary, use the same approach for the `LoanReturnStatus` and `MembershipRenewalStatus` enums.

1. Take a minute to review the `GetDescription` method.

    ```csharp
    public static string GetDescription(Enum value)
    {
        if (value == null)
            return string.Empty;
    
        return value switch
        {
            MembershipRenewalStatus status => MembershipRenewalStatusDescriptions[status],
            LoanReturnStatus status => LoanReturnStatusDescriptions[status],
            LoanExtensionStatus status => LoanExtensionStatusDescriptions[status],
            _ => value.ToString()
        };
    }
    ```

    This code uses pattern matching to determine the type of the enum and retrieve the description from the appropriate dictionary. The `switch` statement checks the type of the enum `value` and returns the corresponding description from the dictionary. If the enum value is not found in the dictionary, the method returns the enum value as a string.

    If you ask GitHub Copilot to refactor this code and eliminate the lambda expressions, it becomes easier to read:

    ```csharp
    public static string GetDescription(Enum value)
    {
        if (value == null)
            return string.Empty;

        switch (value)
        {
            case MembershipRenewalStatus status:
                return MembershipRenewalStatusDescriptions[status];
            case LoanReturnStatus status:
                return LoanReturnStatusDescriptions[status];
            case LoanExtensionStatus status:
                return LoanExtensionStatusDescriptions[status];
            default:
                return value.ToString();
        }
    }
    ```

1. Build your solution to ensure that there are no errors.

    You'll see warnings. You can ignore them for now.

## Update the data access methods to use LINQ

LINQ (Language Integrated Query) is a powerful feature in C# that allows you to query collections, databases, and XML documents in a uniform way. LINQ provides a more concise and readable way to query data compared to traditional foreach loops.

This section of the exercise includes the following tasks:

- Refactor the methods in JsonData.cs to use LINQ.
- Refactor the methods in JsonLoanRepository.cs to use LINQ.
- Refactor the methods in JsonPatronRepository.cs to use LINQ.

### Refactor the methods in JsonData.cs to use LINQ

The JsonData class includes the following data access methods: GetPopulatedPatron, GetPopulatedLoan, GetPopulatedBookItem, GetPopulatedBook. These methods use foreach loops to iterate over collections and populate objects. You can refactor these methods to use LINQ to improve code readability and maintainability.

Use the following steps to complete this section of the exercise:

1. Open the JsonData.cs file.

1. Select the `GetPopulatedPatron` method.

    The `GetPopulatedPatron` method is designed to create a fully populated `Patron` object. It copies the basic properties of the `Patron` and populates its `Loans` collection with detailed `Loan` objects.

    ```cs
    public Patron GetPopulatedPatron(Patron p)
    {
        Patron populated = new Patron
        {
            Id = p.Id,
            Name = p.Name,
            ImageName = p.ImageName,
            MembershipStart = p.MembershipStart,
            MembershipEnd = p.MembershipEnd,
            Loans = new List<Loan>()
        };

        foreach (Loan loan in Loans!)
        {
            if (loan.PatronId == p.Id)
            {
                populated.Loans.Add(GetPopulatedLoan(loan));
            }
        }

        return populated;
    }
    ```

1. Open an inline chat, and then enter a prompt that refactor's the method using LINQ.

    ```plaintext
    #selection refactor selection to `return new Patron` using LINQ
    ```

1. Take a minute to review the suggested update.

    The suggested update should look similar to the following code:

    ```csharp
    public Patron GetPopulatedPatron(Patron p)
    {
        return new Patron
        {
            Id = p.Id,
            Name = p.Name,
            ImageName = p.ImageName,
            MembershipStart = p.MembershipStart,
            MembershipEnd = p.MembershipEnd,
            Loans = Loans!
                .Where(loan => loan.PatronId == p.Id)
                .Select(GetPopulatedLoan)
                .ToList()
        };
    }
    ```

    First off, a LINQ query is used to replace the `foreach (Loan loan in Loans!)` loop. With the LINQ code in place, you can use an object initializer to assign object properties to the new `Patron` object. This alleviates the need for a separate `populated` instance of the `Patron` object. Overall, the updated code is shorter and more readable.

    The code uses the input patron `p` to assign some basic properties to the new `Patron` object. Then it populates the `Loans` collection with loans that are associated with the input Patron, transforming each loan using the `GetPopulatedLoan` method.

    You can break down the LINQ code line that populates the `Loans` collection:

    - `Loans!`: The `Loans!` expression accesses the `Loans` collection. The `!` operator is a null-forgiving operator, indicating that the developer is confident that `Loans` is not null. You should ensure that `Loans` is properly initialized before calling the `GetPopulatedPatron` method.
    - `.Where(loan => loan.PatronId == p.Id)`: This code filters the loans to include only those that belong to the input patron `p`.
    - `.Select(GetPopulatedLoan)`: This code transforms each filtered loan using the `GetPopulatedLoan` method.
    - `.ToList()`: Converts the result to a `List<Loan>`.

1. To accept the suggested update, select **Accept**.

    Now that you've seen how to refactor the `GetPopulatedPatron` method, you can refactor the `GetPopulatedLoan`, `GetPopulatedBookItem`, and `GetPopulatedBook` methods to use LINQ as well.

1. Refactor the `GetPopulatedLoan`, `GetPopulatedBookItem`, and `GetPopulatedBook` methods using the same approach.

    For example, use the following prompts to refactor the three methods:

    For the `GetPopulatedLoan` method:

    ```plaintext
    #selection refactor selection to `return new Loan` using LINQ. Use `GetPopulatedBookItem` for the `BookItem` property. Use `Single` for BookItem and Patron properties.
    ```

    For the `GetPopulatedBookItem` method:

    ```plaintext
    #selection refactor selection to `return new BookItem` using LINQ. Use `GetPopulatedBook` and `Single` for the `BookItem` property.
    ```

    For the `GetPopulatedBook` method:

    ```plaintext
    #selection refactor selection to `return new Book` using LINQ. Use `Where` and `Select` for `Author` property. Use `First` author.
    ```

1. After accepting the suggested updates, take a minute to review your code changes.

    You updated code should look similar to the following code:

    ```csharp
    public Loan GetPopulatedLoan(Loan l)
    {
        return new Loan
        {
            Id = l.Id,
            BookItemId = l.BookItemId,
            PatronId = l.PatronId,
            LoanDate = l.LoanDate,
            DueDate = l.DueDate,
            ReturnDate = l.ReturnDate,
            BookItem = GetPopulatedBookItem(BookItems!.Single(bi => bi.Id == l.BookItemId)),
            Patron = Patrons!.Single(p => p.Id == l.PatronId)
        };
    }

    public BookItem GetPopulatedBookItem(BookItem bi)
    {
        return new BookItem
        {
            Id = bi.Id,
            BookId = bi.BookId,
            AcquisitionDate = bi.AcquisitionDate,
            Condition = bi.Condition,
            Book = GetPopulatedBook(Books!.Single(b => b.Id == bi.BookId))
        };
    }

    public Book GetPopulatedBook(Book b)
    {
        return new Book
        {
            Id = b.Id,
            Title = b.Title,
            AuthorId = b.AuthorId,
            Genre = b.Genre,
            ISBN = b.ISBN,
            ImageName = b.ImageName,
            Author = Authors!.Where(a => a.Id == b.AuthorId).Select(a => new Author {
                Id = a.Id,
                Name = a.Name
            }).First()
        };
    }
    ```

1. Use the **Explain** smart action to see an explanation of the LINQ queries.

    The **Explain** smart action provides a detailed explanation of the LINQ queries used in the code.

    For example, you can use the **Explain** smart action on the `GetPopulatedBook` method to see an explanation of the LINQ query used to populate the `Author` property of the `Book` object.

    ```csharp
    Author = Authors!.Where(a => a.Id == b.AuthorId).Select(a => new Author {
        Id = a.Id,
        Name = a.Name
    }).First()
    ```

    The **Explain** smart action provides a detailed explanation of the LINQ query used to populate the `Author` property of the `Book` object.

    For example, the explanation might look like this:

    ```plaintext
    The active selection is a C# code snippet that assigns a value to the Author property. This value is derived from a collection of Author objects named Authors. The code uses LINQ (Language Integrated Query) to filter and transform the data within this collection.
    
    First, the Authors! expression uses the null-forgiving operator (!) to indicate that Authors is not null, even if the compiler might think otherwise. This is a way to suppress nullable warnings. The Where method is then called on the Authors collection to filter the elements. The lambda expression a => a.Id == b.AuthorId is used to find all Author objects where the Id matches the AuthorId property of another object b.
    
    After filtering, the Select method is used to project each filtered Author object into a new Author object. This is done by creating a new instance of the Author class and copying the Id and Name properties from the original Author object.
    
    Finally, the First method is called to retrieve the first element from the resulting sequence. This means that the Author property will be assigned the first Author object that matches the filter criteria and has been projected into a new Author instance.
    
    This approach ensures that the Author property is set to a new Author object with the same Id and Name as the first matching Author in the Authors collection.
    ```

1. Build your solution to ensure that there are no errors.

    You'll see warnings. You can ignore them for now.

### Refactor the methods in JsonLoanRepository.cs to use LINQ

The JsonLoanRepository class includes the `GetLoan` and `UpdateLoan` data access methods. You'll refactor these two methods, replacing foreach loops with LINQ to improve code readability and maintainability.

Use the following steps to complete this section of the exercise:

1. Open the `JsonLoanRepository.cs` file.

1. Select the `GetLoan` method.

    The `GetLoan` method is designed to retrieve a loan by its ID.

    ```csharp
    public async Task<Loan?> GetLoan(int id)
    {
        await _jsonData.EnsureDataLoaded();

        foreach (Loan loan in _jsonData.Loans!)
        {
            if (loan.Id == id)
            {
                Loan populated = _jsonData.GetPopulatedLoan(loan);
                return populated;
            }
        }

        return null;
    }
    ```

1. Open the inline chat, and then enter a prompt that refactors the method using LINQ.

    For example, enter the following prompt:

    ```plaintext
    #selection refactor selection using LINQ with `_jsonData.Loans!. Use `Where`, `Select` and `GetPopulatedLoan` to return `FirstOrDefault`.
    ```

1. Take a minute to review the suggested update.

    The suggested update should look similar to the following code:

    ```csharp
    public async Task<Loan?> GetLoan(int id)
    {
        await _jsonData.EnsureDataLoaded();

        Loan? loan = _jsonData.Loans!
            .Where(l => l.Id == id)
            .Select(l => _jsonData.GetPopulatedLoan(l))
            .FirstOrDefault();

        return loan;
    }
    ```

    The updated code uses LINQ to filter the loans collection to include only the loan with the specified ID. Notice that `loan` should be declared as nullable (`Loan? loan`). It then transforms the loan using the `GetPopulatedLoan` method and returns the first result. If no matching loan is found, `FirstOrDefault` returns `null`. The method then returns this loan object, which may be null if no loan with the specified `id` exists. This approach ensures that the returned loan is fully populated with all necessary related data, providing a comprehensive view of the loan record.

    This code could be further simplified:

    ```csharp
    public async Task<Loan?> GetLoan(int id)
    {
        await _jsonData.EnsureDataLoaded();

        return _jsonData.Loans!
            .Where(l => l.Id == id)
            .Select(l => _jsonData.GetPopulatedLoan(l))
            .FirstOrDefault();

    }
    ```

1. To accept the updated GetLoan method, select **Accept**.

1. Select the `UpdateLoan` method.

    ```csharp
    public async Task UpdateLoan(Loan loan)
    {
        Loan? existingLoan = null;
        foreach (Loan l in _jsonData.Loans!)
        {
            if (l.Id == loan.Id)
            {
                existingLoan = l;
                break;
            }
        }

        if (existingLoan != null)
        {
            existingLoan.BookItemId = loan.BookItemId;
            existingLoan.PatronId = loan.PatronId;
            existingLoan.LoanDate = loan.LoanDate;
            existingLoan.DueDate = loan.DueDate;
            existingLoan.ReturnDate = loan.ReturnDate;

            await _jsonData.SaveLoans(_jsonData.Loans!);

            await _jsonData.LoadData();
        }
    }
    ```

1. Open the inline chat, and then enter a prompt that refactors the method using LINQ.

    For example, enter the following prompt:

    ```plaintext
    #selection refactor selection using LINQ find an existing loan `_jsonData.Loans!. Replace existing loan.
    ```

1. Take a minute to review the suggested update.

    The suggested update should look similar to the following code:

    ```csharp
    public async Task UpdateLoan(Loan loan)
    {
        Loan? existingLoan = _jsonData.Loans!.FirstOrDefault(l => l.Id == loan.Id);

        if (existingLoan != null)
        {
            existingLoan.BookItemId = loan.BookItemId;
            existingLoan.PatronId = loan.PatronId;
            existingLoan.LoanDate = loan.LoanDate;
            existingLoan.DueDate = loan.DueDate;
            existingLoan.ReturnDate = loan.ReturnDate;

            await _jsonData.SaveLoans(_jsonData.Loans!);

            await _jsonData.LoadData();
        }
    }
    ```

    The updated code uses LINQ to find the existing loan in the loans collection. It then updates the existing loan with the new loan data. The method then saves the updated loans collection and reloads the data. This approach ensures that the loan data is updated correctly and that the changes are persisted to the data store.

    You can also add the code to ensure the data is loaded before the method is executed:

    ```csharp
    public async Task UpdateLoan(Loan loan)
    {
        await _jsonData.EnsureDataLoaded();

        Loan? existingLoan = _jsonData.Loans!.FirstOrDefault(l => l.Id == loan.Id);

        if (existingLoan != null)
        {
            existingLoan.BookItemId = loan.BookItemId;
            existingLoan.PatronId = loan.PatronId;
            existingLoan.LoanDate = loan.LoanDate;
            existingLoan.DueDate = loan.DueDate;
            existingLoan.ReturnDate = loan.ReturnDate;

            await _jsonData.SaveLoans(_jsonData.Loans!);

            await _jsonData.LoadData();
        }
    }

1. To accept the updated UpdateLoan method, select **Accept**.

1. Build your solution to ensure that there are no errors.

    You'll see warnings. You can ignore them for now.

### Refactor the methods in JsonPatronRepository to use LINQ

The `JsonPatronRepository` class includes the `SearchPatrons`, `GetPatron`, and `UpdatePatron` methods, and it's a great candidate for optimization. You'll refactor these methods, replacing foreach loops with LINQ to improve code readability and maintainability.

Use the following steps to complete this section of the exercise:

1. Open the `JsonPatronRepository.cs` file.

1. Select the `SearchPatrons` method.

    The `SearchPatrons` method is designed to search for patrons by name.

    ```csharp
    public async Task<List<Patron>> SearchPatrons(string searchInput)
    {
        await _jsonData.EnsureDataLoaded();

        List<Patron> searchResults = new List<Patron>();
        foreach (Patron patron in _jsonData.Patrons)
        {
            if (patron.Name.Contains(searchInput))
            {
                searchResults.Add(patron);
            }
        }
        searchResults.Sort((p1, p2) => String.Compare(p1.Name, p2.Name));

        searchResults = _jsonData.GetPopulatedPatrons(searchResults);

        return searchResults;
    }
    ```

1. Open the inline chat, and then enter a prompt that refactors the method using LINQ.

    For example, enter the following prompt:

    ```plaintext
    #selection refactor selection using LINQ with `_jsonData.Patrons!. Replace the loop with `Where`, `OrderBy`, and `GetPopulatedPatrons`.
    ```

1. Take a minute to review the suggested update.

    The suggested update should look similar to the following code:

    ```csharp
    public async Task<List<Patron>> SearchPatrons(string searchInput)
    {
        await _jsonData.EnsureDataLoaded();

        List<Patron> searchResults = _jsonData.Patrons!
            .Where(patron => patron.Name.Contains(searchInput))
            .OrderBy(patron => patron.Name)
            .ToList();

        searchResults = _jsonData.GetPopulatedPatrons(searchResults);

        return searchResults;
    }
    ```

1. To accept the updated SearchPatrons method, select **Accept**.

1. Select the `GetPatron` method.

    The `GetPatron` method is designed to return the patron matching the specified `id`.

    ```csharp
    public async Task<Patron?> GetPatron(int id)
    {
        await _jsonData.EnsureDataLoaded();

        foreach (Patron patron in _jsonData.Patrons!)
        {
            if (patron.Id == id)
            {
                Patron populated = _jsonData.GetPopulatedPatron(patron);
                return populated;
            }
        }
        return null;
    }
    ```

1. Open the inline chat, and then enter a prompt that refactors the method using LINQ.

    For example, enter the following prompt:

    ```plaintext
    #selection refactor selection using LINQ with `_jsonData.Patrons!. Use `Where`, `Select` and `GetPopulatedPatron` to return `FirstOrDefault`
    ```

1. Take a minute to review the suggested update.

    The suggested update should look similar to the following code:

    ```csharp
    public async Task<Patron?> GetPatron(int id)
    {
        await _jsonData.EnsureDataLoaded();

        var patron = _jsonData.Patrons!
            .Where(p => p.Id == id)
            .Select(p => _jsonData.GetPopulatedPatron(p))
            .FirstOrDefault();

        return patron;
    }
    ```

    This code could be simplified further:

    ```C#
    public async Task<Patron?> GetPatron(int id)
    {
        await _jsonData.EnsureDataLoaded();

        return _jsonData.Patrons!
            .Where(p => p.Id == id)
            .Select(p => _jsonData.GetPopulatedPatron(p))
            .FirstOrDefault();
    }
    ```

1. To accept the updated GetPatron method, select **Accept**.

1. Select the `UpdatePatron` method.

    The `UpdatePatron` method is designed to update the patron with the specified `id`.

    ```csharp

    public async Task UpdatePatron(Patron patron)
    {
        await _jsonData.EnsureDataLoaded();
        var patrons = _jsonData.Patrons!;
        Patron existingPatron = null;
        foreach (var p in patrons)
        {
            if (p.Id == patron.Id)
            {
                existingPatron = p;
                break;
            }
        }
        if (existingPatron != null)
        {
            existingPatron.Name = patron.Name;
            existingPatron.ImageName = patron.ImageName;
            existingPatron.MembershipStart = patron.MembershipStart;
            existingPatron.MembershipEnd = patron.MembershipEnd;
            existingPatron.Loans = patron.Loans;
            await _jsonData.SavePatrons(patrons);
            await _jsonData.LoadData();
        }
    }
    ```

1. Open the inline chat, and then enter a prompt that refactors the method using LINQ.

    For example, enter the following prompt:

    ```plaintext
    #selection refactor selection using LINQ to find `patron` in `_jsonData.Patrons!. Replace existing patron with `patron`.
    ```

1. Take a minute to review the suggested update.

    The suggested update should look similar to the following code:

    ```csharp
    public async Task UpdatePatron(Patron patron)
    {
        await _jsonData.EnsureDataLoaded();
        var patrons = _jsonData.Patrons!;
        var existingPatron = patrons.FirstOrDefault(p => p.Id == patron.Id);
        if (existingPatron != null)
        {
            existingPatron.Name = patron.Name;
            existingPatron.ImageName = patron.ImageName;
            existingPatron.MembershipStart = patron.MembershipStart;
            existingPatron.MembershipEnd = patron.MembershipEnd;
            existingPatron.Loans = patron.Loans;
            await _jsonData.SavePatrons(patrons);
            await _jsonData.LoadData();
        }
    }
    ```

1. To accept the updated UpdatePatron method, select **Accept**.

### Check your work

Use the following steps to check your work:

1. To clean the solution, right-click `AccelerateAppDevGitHubCopilot`, and then select **Clean**.

    This action removes any build artifacts from the previous build. Cleaning the solution will effectively reset the JSON data files to their original values during (in the output directory).

1. Build the application and ensure there are no errors.

1. Run the application.

    You can run the application from the Solution Explorer view by right-clicking the `Library.Console` project, selecting **Debug**, and then selecting **Start New Instance**.

1. When prompted for a patron name, type **One** and then press Enter.

1. At the "Matching Patrons" prompt, type **2** and then press Enter.

1. At the "Book Loans" prompt, type **1** and then press Enter.

1. At the "Input Options" prompt, type **r** and then press Enter.

1. Verify that the message "Book was successfully returned." is displayed.

1. To begin a new search, type **s** and then press Enter.

1. When prompted for a patron name, type **One** and then press Enter.

1. At the "Matching Patrons" prompt, type **2** and then press Enter.

1. Verify that first book loan is marked `Returned: True`.

1. At the "Input Options" prompt, type **q** and then press Enter.

1. Stop the application.

## Summary

In this exercise, you learned how to

## Clean up

Now that you've finished the exercise, take a minute to ensure that you haven't made changes to your GitHub account or GitHub Copilot subscription that you don't want to keep. If you made any changes, revert them now.
