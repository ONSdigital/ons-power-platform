# Setting application-wide configuration

You should use the ```OnStart``` attribute of App to set variables used and reused widely throughout your application. This can include:
- Using ```Set(gblCurrentUserEmail, User().Email);``` to save the current users email address.
- Using ```Param()``` to capture parameters passed to the canvas app. This can be used for activities such as deep linking from emails. For example, passing a unique ID to the canvas app in order to navigate directly to it: ```Set(locItemID, Param("ref"));```.
- Looking up environment variables for use within the application. See [environment-variables](./environment-variables.md).
- Verifying team membership. See [team-association](./team-association.md).
- Looking up user role associations. See [role-association](./role-association.md).

In addition, you can create collections to handle configuration options like colour palettes or navigation options:

```
Set(
    AppConfig,
    {
        PrimaryFillColor: ColorValue("#003C57"),
        SecondaryFillColor: ColorValue("#003C57"),
        PrimaryTextColor: ColorValue("#222222"),
        PrimaryBorderColor: ColorValue("#222222"),
        DisabledFillColor: ColorValue("#F5F5F6"),
        DisabledBorderColor: ColorValue("#E2E2E3"),
        DisabledChevronColor: ColorValue("#BCBCBD"),
        ValidationErrorFillColor: ColorValue("#FAE6E8"),
        ValidationErrorColor: ColorValue("#D0021B"),
        PrimaryButtonColor: ColorValue("#0F8243"),
        SecondaryButtonColor: ColorValue("#E2E2E3"),
        GhostButtonColor: ColorValue("#206095"),
        SeparatorColor: ColorValue("#E6ECEE"),
        NextButtonColor: ColorValue("#00A3A6")
    }
);
```

These can then be accessed within components using ```AppConfig.PrimaryFillColor```.
