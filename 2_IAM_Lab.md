## IAM Lab

#### IAM dashboard

* Sign in link can be customised.
* IAM Resources section lists the number of users, groups and roles that have been set up.
* Security Status section has a checklist with 5 items in it:
  - Delete your root access keys
  - Activate MFA on your root account
  - Create individual IAM members
  - Use groups to assign permissions
  - Apply an IAM password policy

#### Activating MFA

Upon selecting 'Manage MFA', you will be asked whether the device is hardware or virtual. Selecting virtual will prompt you that a AWS-MFA compatible app must be installed (usually just Google Authenticator).

#### Adding users

Go to the User tab, and select 'Create user'. There are two different access types; programmatic access enables a **access key ID** and **secret access key** for the AWS CLI, API and other development tools whereas AWS Management Console access is simply access to the console. Both of these levels of access can be given to a single user. Password stuff to follow is pretty self explanatory - can set a custom password of console generated one.

#### Adding permissions

It then asks us to set the permissions for that user. We have three options:

1. Add user to group.
2. Copy permissions from another user.
3. Attach existing policies directly.

If no group exists, we can create one from this page. We need to add permission policies to this group though. There are lots of default policies that exist, and we can look at the .JSON code that makes up each policy.

Once we've added policies, we can review the user about to be created on the next page. Creating the user will give us the access key ID and secret access key, as well as their password and an option to email login instructions to the user.

The username/password pair is used to login to the AWS console and the access key ID/secret access key is used to interact with AWS through command prompt.

This is the **only opportunity** to see the secret access key you will **ever get**. These credentials can be downloaded though so it's okay.

#### Adding a IAM password policy

Clicking 'Manage password policy' will bring us to a page with a checklist containing password features (*expiring in 30 days, needing uppercase characters etc.*)

#### Creating roles

Go to the Roles tab in the sidebar. IAM roles are a suceure way of granting permissions to entities that you trust. Examples of trusted entities are:

*  IAM user in another account
* Application code running on an EC2 instance that needs to perform actions on an AWS resource
* An AWS service that needs to act on resources in your account to provide it's features
* Users from a corporate directory who use identity federation through SAML

When we go to create the role, we need to select the type of trusted entity and what services that entity needs.

Then we attach permission policies to the role. Once we've done that, we give the role a name and description and click 'Create role'.
