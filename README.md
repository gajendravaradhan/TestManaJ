# TestManaJ

![GitHub repo size](https://img.shields.io/github/repo-size/scottydocs/README-template.md)
![GitHub contributors](https://img.shields.io/github/contributors/scottydocs/README-template.md)




TestManaJ is a automation utility that performs the process of injecting test results into third-party test management tools, such as ALM or JIRA.


TestmanaJ's detailed and customizable data-driven properties *save the user time* in manually uploading automation results and facilitates a **single** location for manual and automated test execution reporting.


## Features
* Dynamically construct API Requests for common third-party Test Management Tools.
* Easy to use
* High level of Customization
* Works with any Java Framework
* Detailed Reports made Easy
* Prebuilt Implementations with Common Frameworks
* Fast Execution

## Before you begin

Ensure you have met the following requirements:

* You have installed the latest version of  <a href="https://maven.apache.org/download.cgi" > Maven 3.5 </a>
* You have installed the latest version of  <a href="https://www.oracle.com/java/technologies/javase-downloads.html" > Java 8 </a>
* You have an IDE


## Installing TestManaJ

To install TestManaJ, follow these steps:

* Download Java Jar file from the GitHub repository.
* We recommend to simply import the Jar into your project's IDE. However, you may also reference the JAR file into your `pom.xml`, or any other method of your choosing.
* Lastly, download the ALM resources folder and place on your local. This directory can be placed anywhere on your native project or windows explorer.



## Configuring TestManaJ
Below is a list of test run, and run step properties available for setting:


<table>
<tr>
  <th>Test Run Properties</th>
  <td>
  comments
| status
| execution date
| execution time
| owner
| cycle id
| test config id
| subtype id
| test id
| test name
| ei system id
| pc procedure name
| has linkage
| path
| state
| test config id
| name
| os build
| os sp
| test cycle name
| os config
| cycle
| duration
| last modified date/time
| test description
| assign rcyc
| test sync
| test instance
| cycle name
| pc reservation id
| attachment(s)
  </td>
</tr>
<tr>
  <th>Test Step Properties</th>
  <td>
| Test id
| Comp status
| Description
| Rel Obj id
| Obj id
| Has linkage
| Execution date
| Execution time
| Desstep id
| Has picture
| Tree parent id
| Bpt path
| Actual
| Step order
| Level
| Expected
| Line number
| Comp subtype name
| Extended reference
| Execution time
| Parent id
  </td>
</tr>
<tr>

</table>

## Usage
Below you will find an example of a hashmap that will pass the `ExecuteApp` class to ALM

```java
public class ExecuteApp {

   public static void main(String[] args) throws Exception {

       String testCaseName = "TC_19  Create a New Submission for a Full Application";

        LinkedHashMap<String, String> runProperties = new LinkedHashMap<>();
        runProperties.put("attachment", // Your file path );
        runProperties.put("comments", "This is a comment");

        LinkedHashMap<String, LinkedHashMap<String, String>> steps = new LinkedHashMap<>();

        LinkedHashMap<String, String> stepProperties = new LinkedHashMap<>();
        stepProperties.put("status", "Passed");
        stepProperties.put("description", "Given I navigate to www.google.com");
        stepProperties.put("execution-time",//"HH:MM:SS");
        steps.put("Step 1", stepProperties);

        stepProperties = new LinkedHashMap<>();
        stepProperties.put("status", "Passed");
        stepProperties.put("description", "Given I enter text search into search.bar");
        stepProperties.put("expected", "Google Home Page Should Load");
        steps.put("Step 2", stepProperties);

        stepProperties = new LinkedHashMap<>();
        stepProperties.put("status", "Failed");
        stepProperties.put("description", "Then google.results are displayed");
        stepProperties.put("actual", "Exception in thread \"main\" java.util.NoSuchElementException\n" +
                "at java.util.Scanner.throwFor(Scanner.java:838)\n" +
                "at java.util.Scanner.next(Scanner.java:1461)\n" +
                "at java.util.Scanner.nextInt(Scanner.java:2091)\n" +
                "at java.util.Scanner.nextInt(Scanner.java:2050)\n" +
                "at Addition.main(Addition.java:16)");
        stepProperties.put("attachment", //Your file path );
        steps.put("Step 3", stepProperties);

        stepProperties = new LinkedHashMap<>();
        stepProperties.put("status", "No Run");
        stepProperties.put("description", "Then google.logo is displayed");
        stepProperties.put("execution-date",//"YYYY-MM-DD");
        steps.put("Step 4", stepProperties);

        stepProperties = new LinkedHashMap<>();
        stepProperties.put("status", "No Run");
        stepProperties.put("description", "Then I click google.home");
        steps.put("Step 5", stepProperties);

        String almResoucesPath = SystemUtils.getUserDir().toString();

        updateALMForTestCase(testCaseName, steps, runProperties, almResoucesPath);
   }

   public static void updateALMForTestCase(String testCaseName, LinkedHashMap<String, LinkedHashMap<String, String>> steps, LinkedHashMap<String, String> runProperties, String almResourcesPath) throws Exception {
      App executeApp = new App(almResourcesPath);
      executeApp.updateTestRun(testCaseName, steps, runProperties);
   }

}
```



## Executing in TestManaJ
* The only thing left to do is call the method then validate results in your third-party test managment tool.


## Contributing to TestManaJ

To contribute to TestManaJ, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b <branch_name>`.
3. Make your changes and commit them: `git commit -m '<commit_message>'`
4. Push to the original branch: `git push origin <project_name>/<location>`
5. Create the pull request.

Alternatively see the GitHub documentation on [creating a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).

<!---## Contributors

Thanks to the following people who have contributed to this project:

* [@sethmwatson](https://github.com/sethmwatson) 📖
* Teddy Gajewski 🐛📖
* Justin Hanke 🐛

You might want to consider using something like the [All Contributors](https://github.com/all-contributors/all-contributors) specification and its [emoji key](https://allcontributors.org/docs/en/emoji-key).
--->

<!---## Contact

If you have absolutely any questions or concerns do not hesitate to contact our support team.  

 EY_NGeTAF_Support.GID@ey.net --->

## License

This project uses the following license: [CC0](<link>)
