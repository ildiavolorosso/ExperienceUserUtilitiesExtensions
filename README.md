# Experience User Utilities Extentions
Person Account-related extensions to the [ExperienceUserUtilities](https://github.com/ildiavolorosso/ExperienceUserUtilities) package.

## Introduction
The [ExperienceUserUtilities](https://github.com/ildiavolorosso/ExperienceUserUtilities) package provides Flow-based utilities that allow common user administration tasks for Experience Cloud users to occur without leaving the Contact record in Lightning Experience. This allows administrators and agents to stay productive by staying out of Salesforce Setup.

But the base utility package does not include support for administering users from [Person Account](https://help.salesforce.com/apex/HTViewHelpDoc?id=sf.account_person.htm&language=en_US) records. This was done to avoid creating a dependency that would limit installation of that package to only orgs where Person Accounts are active. This package adds flows and actions for Person Account support.

## Prerequisites

- Your Salesforce org must have the [ExperienceUserUtilities](https://github.com/ildiavolorosso/ExperienceUserUtilities) package installed.
- Your Salesforce org must have [Person Accounts](https://help.salesforce.com/s/articleView?id=000328922&type=1) enabled.
- Your Salesforce org must have at least one Lightning Record page (built using Lightning App Builder) dedicated to Person Accounts (see [these instructions](https://help.salesforce.com/s/articleView?id=000314811&type=1)).

## Post-Installation Configuration
This package installs several items that complement the base Experience User Utilities:
- Wrapper flows that handle resolution of the Person Account's Contact Id, then call the base utilities for User Details, Resetting Passwords, Freezing/Unfreezing a user, and Disable/Deactivate/Reactivate user.
- Corresponding Account object actions for the three administrative wrapper flows above.
- Permission Sets and Permission Set Groups that enable access to the wrapper flows.

These items require some setup in your sandbox or Salesforce org:

### Add appropriate users to the Permission Set Group
The package installs a Permission Set Group named **Manage_Experience_Users_From_Lightning**. This permission set is used to grant internal users access to the Flows in this package, as well as to flows in the base Experience User Utility package. Click into this permission set group and assign it to any users who will be administering Experience Cloud users from within Lightning Experience.

### Embed the User Details Flow on the Person Account Lightning Page

### Add Administrative Actions to the Appropriate Person Account Page Layouts



