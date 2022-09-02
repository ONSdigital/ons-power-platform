# Code review process

Due to the low-code/no-code nature of Power Platform, there is limited tooling and support for performing traditional code reviews. These are the methodologies we use to review applications moving into production.

We also use a [code review checklist](./code-checklist.md) to assess a solution, app and PowerApps function code against our standards.

## Solution and app checker

Both the [solution checker](https://docs.microsoft.com/en-us/power-apps/maker/data-platform/use-powerapps-checker) and [app checker](https://powerapps.microsoft.com/en-us/blog/new-app-checker-helps-you-fix-errors-and-make-accessible-apps/) should be run against apps and any issues resolved or addressed with suitable reasoning.

## Power Apps Language Tooling

The [Power Apps Language Tooling](https://github.com/microsoft/PowerApps-Language-Tooling) library allows you to unpack solution and canvas app folders into their constituent files. This will include:

- *.fx.yaml files which contain the components and PowerApps function code App.OnStart and each screen (found within /Src in an unpacked canvas app).
- Connections.json files which contain information on connection references (found within the /Connections folder of an unpacked canvas app).
- Entity.xml files which contain details on any custom entities (Dataverse tables) within a solution (found within the Entities/<ENTITYNAME> folder in an unpacked solution).
- <ROLENAME>.xml files which contain details of the privileges granted by any custom security roles within a solution (found within the Roles folder in an unpacked solution).

As well as all other information about a solution or canvas app.

Using this alongside source code management tools (for example, using git diff or a pull request process) will allow you to run static analysis scripts on an app, review PowerApps function code and quickly identify and review changes to an existing app.

**Note**: This library is still experimental, so we are currently only using it for review purposes. Any changes to code should be done by the GUI editor.

## Power Apps Code Review Tool

This is a [tool produced by the Microsoft CAT team](https://github.com/microsoft/powerapps-tools/tree/master/Tools/Apps/Microsoft.PowerApps.CodeReview) to assist with reviewing Power Apps.

It provides you with a Power App that makes use of the Power Apps Language Tooling to perform analysis on an app and provide a method for tracking reviews.

It is still be work-in-progress so should not be considered a full review process and only used to assist reviews.
