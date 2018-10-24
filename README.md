# AWS ADFS login

Library for user login (client side) using AWS ADFS (Active Directory Federation Service).

## Example

Errors are ignored to make example shorter and more readable

```
// Load aws roles
roles, _ := LoadAWSRoles(adfsHost, user, password)

// List all accounts
accounts := roles.Accounts()

// Filter roles by account
accountRoles := roles.RolesByAccountId("123456789")

// Get specific role and log in
admin, _ := roles.RoleByRoleArn("arn:aws:iam::123456789:role/Admin")
creds, _ := admin.Login()

```

MFA Duo

```
devices, _ := MFA(adfsHost, user, password)

// factor can be 'Phone Call', 'Duo Push', or 'Passcode'
// passcode is required only with 'Passcode' factor
roles, _ := devices["phone1"].Factors["Duo Push"].LoadAWSRoles("")
```
