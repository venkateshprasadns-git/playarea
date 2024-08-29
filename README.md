Kudos bot for engagementThis bot identifies 5 top users who commented in threads and 2 top users who reacted the most on posts/threads in public channels which have 50+ audience. After identifying, it sends them a short Kudos message in their Kudos bot DM.
This helps us to encourage more users to contribute to posts and threads and attempt to make the community more responsive and transparent.


Prerequisites


* Slack Application
* Python 3.12
* requests library
* slack_sdk library
* numpy library
* google-cloud-secret-managerlibrary
* ratelimitlibrary

Slack Application

Here we are using slack app Kudos Bot and contact Engineering Collaboration team if you may have any questions

Methods used in the app:

* conversations.replies
* conversations.history
* conversations.list
* chat.postMessage

Environment variables

Ensure the following secrets are set in Google cloud secret manager:

* SLACK_TOKEN : User tokens represent workspace members. They are issued for the user who installed the app and for users who authenticate the app
* SLACK_BOT_TOKEN : Bot tokens represent a bot associated with an app installed in a workspace. Unlike user tokens, they're not tied to a user's identity—they're only tied to your app. Since acting independently allows your app to stay installed even when an installing user is deactivated, using bot tokens is usually for the best.


Ensure the following secrets are set in code with correct project id and token name from GCP:

* SLACK_USER_TOKEN_NAME : Token name used to store SLACK_TOKEN
* SLACK_BOT_TOKEN_NAME : Token name used to store SLACK_BOT_TOKEN_NAME.
* GCP_PROJ_ID : This is project ID and NOT project name. You can pick from Project details or from URL.



Usage 

This script is scheduled using Google scheduler with below frequency where it identifies users and send messages in their Kudos Bot DM



How it works

