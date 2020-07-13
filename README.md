# Single Sign On (SSO) using OpenID Connect (OIDC) and AWS Cognito to access AWS Resources

This JavaScript app allows users to sign in to OKTA using their username and password and enables them to access any AWS Resource. I used OKTA as the Identity Provider, but similar steps can be applied for any other Identity Providers too.

## How it works

The diagram below explains the overall flow from a user accessing the sample app to gaining the access to an AWS Resource.
![Image of the flow](https://media-exp1.licdn.com/dms/image/C5612AQGRXdmf517x2A/article-inline_image-shrink_1000_1488/0?e=1600300800&v=beta&t=CLMJz9Zbn3xGv5aJRRjfuKyQLUXF6iSvRS50xJKBdtY)


1. The user accesses the sample app and clicks on Sign In with OKTA button.
2. The app redirects the user to OKTA for signing in. After successful authentication, the app receives an ID token from OKTA.
3. The app exchanges the ID token for a Cognito token. Cognito verifies the id_token with the provider before issuing a cognito token.
4. The app exchanges the Cognito token for temporary AWS security credentials.
5. The app uses the credentials to access any AWS Resource. In this case, we'll be hitting an API Gateway.
6. It is worthwhile to note that the app never stores any long-term credentials and that the AWS SDK for JavaScript helps you accomplish steps 3 to 5 with just a few lines of code.
