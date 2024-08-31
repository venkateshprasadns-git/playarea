# Rename Channels 

This script uses the Slack API to perform operations on Slack channels. It includes two main functions: `add_prefix_to_channel` and `rename_channels` which is used for renaming the channels.
Call whichever function you need, as per your requirement. This script is not deployed in cloud and is to be run on prem on an adhoc basis.

This script is to be used only by Slack Admin team (not for end users)


## Prerequisites

* Slack Application
* Python 3.12
* slack_sdk library


## Environment variables

* token : To generate a Slack API token, you'll need to create a Slack app within Slack and configure it with the appropriate permissions for your use case. Install the App to Your Workspace and after the app is installed to the workspace, the OAuth Access Token can be copied from the "OAuth & Permissions" page.


## How to run the script

1. Save the Script to a file named `rename_channels.py`.
2. Install Dependencies: 
  Ensure you have the `slack_sdk` library installed. You can install it using the following command:
  pip install slack_sdk
3. Add Your Slack Token in the script. Replace the placeholder token="" with your actual Slack API token.
4. Run the Script: Open a terminal or command prompt, navigate to the directory where
  `rename_channels.py` is located, and run the script using the following command
  python rename_channels.py


## How it works

1. Imports and Initialization:
    - `import slack`: Imports the Slack SDK.
    - `token=""`: Placeholder for the Slack API token.
    - `slack_client = slack.WebClient(token=token)`: Initializes the Slack client with the provided 
        token.

2. Function: `add_prefix_to_channel`:
    - Purpose: Adds a prefix to the names of all public channels with members.
    - Steps:
        a. Define `prefix` and `text` variables.
        b. Fetch a list of public channels using `slack_client.conversations_list`.
        c. Check if the API call was successful (`conversations.get('ok')`).
        d. Iterate over each channel in the list.
        e. If the channel has members (`channel['num_members'] is not 0`):
            - Create a new name by adding the prefix to the current channel name.
           - Print the old and new channel names.
           - Join the channel using `slack_client.conversations_join`.
           - Rename the channel using `slack_client.conversations_rename`.
           - Post a message to the channel using `slack_client.chat_postMessage`.
           - Leave the channel using `slack_client.conversations_leave`.

3. Function: `rename_channels`:
    - Purpose: Renames channels by replacing a specific substring in their names.
    - Steps:
        a. Define `string_to_be_replaced` and `string_to_be_replaced_with` variables.
        b. Fetch a list of public channels using `slack_client.conversations_list`.
        c. Check if the API call was successful (`conversations.get('ok')`).
        d. Iterate over each channel in the list.
        e. If the channel name starts with the specified substring
            (`channel['name'].startswith(string_to_be_replaced)`):
            - Create a new name by replacing the substring in the current channel name.
            - Print the old and new channel names.
            - Join the channel using `slack_client.conversations_join`.
            - Rename the channel using `slack_client.conversations_rename`.
            - Leave the channel using `slack_client.conversations_leave`.


