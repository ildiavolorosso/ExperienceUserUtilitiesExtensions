# Experience User Utilities Extensions
Person Account-related extensions to the [ExperienceUserUtilities](https://github.com/ildiavolorosso/ExperienceUserUtilities) package.

## Introduction
The [Experience User Utilities](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3u00000PuquwEAB) package provides Flow-based utilities that allow common user administration tasks for Experience Cloud users to occur without leaving the Contact record in Lightning Experience. This allows administrators and agents to stay productive by staying out of Salesforce Setup.

But the base utility package does not include support for administering users from [Person Account](https://help.salesforce.com/apex/HTViewHelpDoc?id=sf.account_person.htm&language=en_US) records. This was done to avoid creating a dependency that would limit installation of that package to only orgs where Person Accounts are active. This package adds flows and actions for Person Account support.

## Prerequisites

- Your Salesforce org must have the Experience User Utilities installed: [AppExchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3u00000PuquwEAB) | [GitHub](https://github.com/ildiavolorosso/ExperienceUserUtilities)
- Your Salesforce org must have [Person Accounts](https://help.salesforce.com/s/articleView?id=000328922&type=1) enabled.
- Your Salesforce org must have at least one Lightning Record page (built using Lightning App Builder) dedicated to Person Accounts (see [these instructions](https://help.salesforce.com/s/articleView?id=000314811&type=1)).

## Installation
Install [this package](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N4V00000GuGt3UAF) from the AppExchange.

## Post-Installation Configuration
This package installs several items that complement the base Experience User Utilities:
- Wrapper flows that handle resolution of the Person Account's Contact Id, then call the base utilities for User Details, Resetting Passwords, Freezing/Unfreezing a user, and Disable/Deactivate/Reactivate user.
- Corresponding Account object actions for the three administrative wrapper flows above.
- Permission Sets and Permission Set Groups that enable access to the wrapper flows.

These items require some setup in your sandbox or Salesforce org:

### Add appropriate users to the Permission Set Group
The package installs a [Permission Set Group](https://help.salesforce.com/s/articleView?language=en_US&type=5&id=perm_set_groups.htm) named **Manage_Experience_Users_From_Lightning**. This permission set is used to grant internal users access to the Flows in this package, as well as to flows in the base Experience User Utility package. Click into this permission set group and assign it to any users who will be administering Experience Cloud users from within Lightning Experience.

![Permission Set Group Assignment](https://github.com/ildiavolorosso/ExperienceUserUtilitiesExtensions/blob/main/screenshots/1.ss.permission-set-group.png?raw=true)

This permission set group assigns both the base package's permission set and this package's permission set, enabling access to all administrative utility flows in both packages.

### Embed the User Details Flow on the Person Account Lightning Page

Edit the appropriate person account pages in Lightning App Builder. Add a Flow component to the page, and configure it to display the **Person Account: Experience User Details** flow. And be sure to pass the recordId into the Flow!

![Person Account Record Page](https://github.com/ildiavolorosso/ExperienceUserUtilitiesExtensions/blob/main/screenshots/2.ss.lex-person-account-page.png)

When you save this page, you may be prompted to activate it. Since these utilities only operate on Person Accounts, it's critically important that you review your record type settings to make sure this page is only used for Person Accounts.

![Person Account LEX Page Activation](https://github.com/ildiavolorosso/ExperienceUserUtilitiesExtensions/blob/main/screenshots/3.ss.LEX-page-activation-settings.png)

### Add Administrative Actions to the Appropriate Person Account Page Layouts

When Person Accounts are active in your org or sandbox, you will have at least one page layout listed under Person Accounts in Setup's Object Manager. For each person account page layout, you'll need to add three actions in the Salesforce Mobile and Lightning Experience Actions section:
- Reset Password
- Freeze/Unfreze User
- Disable/Deactivate/Reactivate User

![Person Account Page Layout](https://github.com/ildiavolorosso/ExperienceUserUtilitiesExtensions/blob/main/screenshots/4.ss.person-account-page-layout.png)

# Extending the Flows

All flows in this package are provided as templates. You may create your ovn copies of the flows, but you should not need to do that for these simple wrapper flows. We suggest extending the flows in the base package to implement your own custom logic and running these flows as-is.

# Important Note
This package is provided as part of the [Salesforce Labs](https://appexchange.salesforce.com/category/salesforce-labs-apps) program. As such, they are not officially supported by Salesforce. We may try to correct any issues that arise, but please keep in mind that we can't guarantee that issues will be addressed.
