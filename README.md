# week-5-software-engineering-essentials
GERTRUDE EIBAN
Exercises A
User Manual Procedure (20 minutes)


User Manual Procedure: Setting Up a GitHub Repository and Making a First Commit
1. Prerequisites
Before starting, make sure you have:
A computer with Windows, macOS, or Linux.
A working internet connection.
A GitHub account.
Git installed on your computer.
Git Bash, Command Prompt, Terminal, or another command-line application.
Basic knowledge of creating and opening folders.
A text editor such as Visual Studio Code or Notepad.
A project folder containing at least one file to upload.
2. Procedure
Step 1: Open Git Bash
Action: Open Git Bash on your computer.
Expected result: A Git Bash terminal window opens and displays a command prompt.
Step 2: Create a project folder
Action: Create a new folder named my-project.
Expected result: A folder named my-project appears on your computer.
Step 3: Open the project folder in Git Bash
Action: Navigate to the my-project folder using the cd command.
Expected result: The terminal prompt shows that you are inside the my-project directory.
Step 4: Create a project file
Action: Create a text file named README.txt inside the project folder.
Expected result: The README.txt file appears inside my-project.
Step 5: Add project information
Action: Write a short description of the project in README.txt.
Expected result: The README file contains the project description.
Step 6: Initialize Git
Action: Run git init in the project folder.
Expected result: Git creates a local repository and reports that an empty Git repository has been initialized.
Step 7: Check the repository status
Action: Run git status.
Expected result: Git shows README.txt as an untracked file.
Step 8: Add the project file to Git
Action: Run git add README.txt.
Expected result: The README file is placed in Git's staging area.
Step 9: Check the staging area
Action: Run git status.
Expected result: README.txt appears under “Changes to be committed.”
Step 10: Create the first commit
Action: Run git commit -m "Initial commit".
Expected result: Git creates the first commit and displays information about the committed file.
Step 11: Sign in to GitHub
Action: Open GitHub in your web browser and sign in to your account.
Expected result: Your GitHub account homepage or dashboard appears.
Step 12: Create a new repository
Action: Select the option to create a new repository on GitHub.
Expected result: GitHub displays the new-repository creation page.
Step 13: Enter the repository name
Action: Enter my-project as the repository name.
Expected result: The repository name is displayed in the repository-name field.
Step 14: Create the repository
Action: Select Create repository.
Expected result: GitHub creates the new my-project repository.
Step 15: Copy the repository URL
Action: Copy the HTTPS URL displayed for the new GitHub repository.
Expected result: The repository URL is stored in your computer's clipboard.
Step 16: Connect the local repository to GitHub
Action: Run git remote add origin followed by the GitHub repository URL.
Expected result: The local Git repository is connected to the GitHub repository.
Step 17: Rename the local branch
Action: Run git branch -M main.
Expected result: The current branch is renamed to main.
Step 18: Push the first commit
Action: Run git push -u origin main.
Expected result: The first commit is uploaded to GitHub and the terminal reports a successful push.
Step 19: Open the GitHub repository
Action: Refresh the GitHub repository page in your browser.
Expected result: README.txt and the first commit are visible in the GitHub repository.
3. Screenshot Description
Screenshot to include: Take a screenshot of the GitHub repository page after completing the push.
The screenshot should clearly show:
The repository name my-project.
The README.txt file.
The main branch.
Evidence that the first commit has been made, such as the commit message “Initial commit.”
This screenshot demonstrates that the local Git repository was successfully connected to GitHub and that the first commit was uploaded.
4. Troubleshooting
Common Error: git: command not found or 'git' is not recognized
This error usually means that Git is not installed or is not correctly added to the computer's PATH.
Solution: Install Git from the official Git website, restart the terminal, and run git --version to confirm that Git is available.
5. Conclusion
The repository is now set up locally and on GitHub. The first project file has been tracked by Git, committed to the local repository, and pushed to the remote GitHub repository. Future changes can be recorded using the same basic cycle: edit → add → commit → push.
Exercise B: API Reference 
Endpoint
HTTP Method: POST
Endpoint Path: /api/v1/projects/{project_id}/tasks
Description
This endpoint creates a new task inside a specified project.
The requesting user must be authenticated and must have permission to create tasks in the project.
The task requires a title, an assignee, a due date, and a priority. A description is optional.
Path Parameters
Parameter
Data Type
Required
Description
project_id
Integer
Yes
The unique ID of the project where the new task will be created.

Request Body Parameters
The request body must be provided in JSON format.
Parameter
Data Type
Required
Description
title
String
Yes
The name or title of the task.
description
String
No
Additional information about the task.
assignee_id
Integer
Yes
The unique ID of the user assigned to the task.
due_date
String (ISO 8601 date)
Yes
The date by which the task should be completed. Format: YYYY-MM-DD.
priority
String
Yes
The priority of the task. Allowed values are low, medium, or high.

Request Headers
Header
Required
Description
Authorization
Yes
Authentication token for the requesting user. Format: Bearer <token>.
Content-Type
Yes
Specifies that the request body is JSON. Use application/json.
Accept
Yes
Specifies that the client expects a JSON response. Use application/json.

Example Request
POST /api/v1/projects/42/tasks
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
Content-Type: application/json
Accept: application/json

Request Body
{
  "title": "Prepare project presentation",
  "description": "Create the slides for the final project presentation.",
  "assignee_id": 17,
  "due_date": "2026-09-15",
  "priority": "high"
}

Response Codes
201 Created
The task was successfully created.
400 Bad Request
The request contains invalid or incorrectly formatted data, such as an invalid priority value or incorrectly formatted due date.
401 Unauthorized
The request does not contain valid authentication credentials.
403 Forbidden
The user is authenticated but does not have permission to create tasks in the specified project.
404 Not Found
The specified project or assignee does not exist.
409 Conflict
The request conflicts with the current state of the project, such as assigning a task to a user who cannot be assigned tasks in that project.
422 Unprocessable Entity
The request is correctly formatted but contains validation errors, such as an empty title or invalid field value.
500 Internal Server Error
An unexpected error occurred on the server while processing the request.
Example Successful Response
HTTP Status: 201 Created
{
  "id": 1058,
  "project_id": 42,
  "title": "Prepare project presentation",
  "description": "Create the slides for the final project presentation.",
  "assignee": {
    "id": 17,
    "name": "Jane Smith"
  },
  "due_date": "2026-09-15",
  "priority": "high",
  "status": "todo",
  "created_at": "2026-09-04T08:30:00Z"
}

Response Field Descriptions
Field
Data Type
Description
id
Integer
Unique ID of the newly created task.
project_id
Integer
ID of the project containing the task.
title
String
Title of the task.
description
String
Additional task information.
assignee
Object
Information about the user assigned to the task.
assignee.id
Integer
Unique ID of the assigned user.
assignee.name
String
Name of the assigned user.
due_date
String
Task deadline in YYYY-MM-DD format.
priority
String
Task priority: low, medium, or high.
status
String
Current task status. A newly created task starts as todo.
created_at
String
Date and time when the task was created in ISO 8601 format.




