# Identifying user team associations

For the assignment of security roles, we use [Power Platform teams](https://docs.microsoft.com/en-us/power-platform/admin/create-team-template-add-entity-form) - this allows us to associate a [security role](../security-roles/roles.md) with an Azure Active Directory security group. It is worth noting that:

- Teams are named by the administrator at time of creation and do not necessarily relate to the security role or AAD group.
- Team associations are stored in the "teammembership_association" of a user within the "Users" Dataverse table. This is a list of GUIDs.
- Team names and GUIDs are stored in the "Teams" Dataverse table.
- Environment variables values and keys are stored across two tables, "Environment Variables Values" and "Environment Variable Definitions".

Below is the standard approach to identify whether a user is assigned to a named team:

1. Create and publish a [security role](../security-roles/roles.md) to the environment.
2. Assign the role to an AAD security group through the Power Platform Admin Center.
3. Create an environment variable to store the name of your team in. In our example this is ```Room Booking Admin Group Name```.
4. Within your app you can obtain the value of your environment variable by looking it up based on the display name:
```
Set(teamName,
    LookUp(
    'Environment Variable Values',
    EnvironmentVariableDefinitionId.displayname= "Room Booking Admin Group Name").value
);
```
5. Obtain the current users information through your preferred approach, for example ```User()``` or ```Office365Users.MyProfile()```:
```
Set(currentUser, User());
```
6. Obtain the GUID of the named team from the "Teams" table:
```
Set(teamId,
    LookUp(Teams,
        name = teamName,
        teamid
    )
);
```
7. Obtain the user from step 5s team membership association from the "Users" table by looking up using their email:
```
Set(usersTeamAssoc,
    Concat(
        LookUp(
            Users,
            internalemailaddress = currentUser.Email
        ).teammembership_association,
        teamid & ";"
    )
);
```
8. Check to see if the user is a member of the group (by checking to see if the teams GUID exists within the users team associations) and store the outcome in a variable for use throughout the applications:
```
Set(isAdmin,
    If(
        teamId
        in
        Text(usersTeamAssoc),
        true,
        false
    )
);
```
