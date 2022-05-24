# asana2jira

A simple bash script to convert Asana tasks to Jira tickets.  Utilizes [jira-cli](https://github.com/ankitpokhrel/jira-cli) for Jira API calls but makes direct curl calls for Asana.

## Setup
1) Install [jira-cli](https://github.com/ankitpokhrel/jira-cli) locally.  It will handle the API calls on the Jira side. Jira-cli also sets a default project which is where the a2j script imports to (this can be overriden when calling jira-cli, however I didn't plumb that through to the cli call in my script yet). 
2) Create a personal access token (PAT) in Asana.  For specific details on how to do this, see the [Asana API instructions](https://asana.com/guide/help/api/api). You must export `ASANA_PAT_TOKEN` from your shell for the script to read.
3) `chmod` the a2j script to allow execution and run it!

## Usage
```a2j <asana_id> [-t jira_issue_type] [-P parent issue]```

* `<asana_id>` is required and is the 16 digit id from the task URL.  To find this ID, open your asana ticket and look at the URL.  The `asana_id` is the LAST id in that URL.  For example, with url:
```https://app.asana.com/0/0000000000000000/1111111111111111```
the `asana_id` is `1111111111111111`.

* Jira issue type is optional.  It defaults to Task, but you can override with Bug, Story, Epic

* Parent issue is optional.  If provided, the parent issue should be the Jira ID of an epic the new ticket will be created under.

