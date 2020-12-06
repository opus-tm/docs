# docs
Documentation
DBMS ER Diagram 
Login Workflow
Figma 

Structure:
Every team is composed of groups
Every user is a member of one main group (with everyone in it)
Each team can have any number of groups (development, HR, etc)
Also possible to create temporary groups that expire after a designated period of time
Each group has different roles that can be assigned that are independent of one another
For example, User A could be a manager in the group “Development”, but only a member in the group “Full Team”
This would give User A access to change the settings of the “Development” group, but not of the “Full Team” group

Features
This group describes the general features we’d like to implement in our project, with just a brief description of their functionality and what we’d like them to do. For more in-depth information about each one, go to the screen or widget group with the given feature’s information.
Announcement board:
Managers and owner can post messages for everyone here
Chat:
All users can create a chat with any other user
Calendar:
Specific to each user
User can display any combination of their events, team events, or group events
Event Creator:
Only available to managers, contains information about employee availability
Can use this to create events for groups that will appear on that groups’ users calendars
Attendance
Create events
Can add members to be required or optional for each event
Events get added to the group calendar by default
Announcements based on event details
Creation, in progress, ended
Widget on home screen that gives you status of upcoming events, clock in/out button once it’s active
Verification step?
To Do
Allows users or group admins? to create a list of tasks that need to get done. Wouldn’t be robust enough to replace something like GitLab or Azure, but it might be useful to have for individuals and groups.
Could be used as a reference for what projects are being worked on and where they’re at.


Screens
Landing Screen 
URL /login/ or /
Seen by users who aren’t logged in
Routes to login and maybe says something about what our product does
Dashboard (Main screen)
URL /
Seen by users who are logged in
Composed of a sidebar, navbar and widgets as content on the screen
Composed of a number of widgets
Each ‘app’ (Calendar, Chat) may have its own widget 
Announcements + Upcoming events
Calendar
URL /calendar/
The calendar will have several checkboxes, similar to Google Calendar or Microsoft Outlook, each corresponding to a given group. These will be nested, similar to how the dashboard displays teams and groups.
The checkboxes will toggle whether or not the group’s events are displayed on the user’s calendar.
For example: say we have a user that is a part of team A and team B. Within team A, the user is a member of the “Full team” and “HR” groups. Within team B, the user is a member of the “Full team” and “Finance” groups. Thus, the user has six checkboxes available to them, nested by the teams
team A
Full team
HR
team B
Full team
Finance
Clicking on “team B”, for instance, will display all events from the team B groups: Full team and Finance, and both of their corresponding checkboxes will have “checked=true”
Clicking again on group “Full team” will deselect that calendar and will only display the events from the “Finance” group of team B. After this action, the “team B” and “Finance” checkboxes will have “checked=false” and the “Full team” will have “checked=true”
Any combination of checkboxes should be tolerated, regardless of crossover between a user’s teams and groups.
Chat
URL /calendar/
Upon being added to a group, a user is also added to a chat with everyone in that group
Can also send messages to any other user
Widget for chat on each group’s that redirects to the chat page, but displays the most recent messages or activity from that group chat
Profile
URL /profile/
Icon with profile pic in top right corner
Clicking it displays a dropdown
View Profile
Brings the user to a screen where they can view and edit their specific information (we’ll need to iron these options out, but could add a secondary email, change phone number, change name, and so on)
Change Status
Displays another menu to the side that displays the options for a user’s status: Active, Away, Busy
This will be populated by the user’s calendar by default
Change Theme
Displays another menu to the side that displays the various styles that we define
Log Out
Logs the user out and returns them to the landing screen
Team Settings 
URL /{team-name}/settings
Every user has access to the settings page for every subgroup
Managers will have additional actions they can perform (elevate user permissions,invite/remove user)
Invite: Input that takes in the email of the user to invite
If this email is not already registered to a user, send an email to that user with a link to our website, asking them to login or register if they don’t have one. They also receive a code in this email that they’ll be prompted for after registration
User must register with the same email that they receive the invite to
Backend will maintain an “invited” property of a group that is a string with emails of everyone who’s been invited
We can then parse this string and verify that the user’s email is in the “invited” string, and then add them to that group
Displays metadata about team (date created, members w/roles, clicking on a user’s name brings you to their profile -- option to chat, view info, etc. If a user navigates to their own profile, they can edit the information)
	
Later: 
Drive
URL /drive/

Widgets
This group details only the functionality of the widgets. If a user is redirected to a different page, the functionality/workflow is described in that page’s group
Calendar
On user dashboard: Displays a user’s upcoming events
On click, this will redirect the user to the calendar page, and display their calendar (maybe the next week) with all events from all groups displayed.
On group dashboard: Displays a team’s upcoming events
On click, this will redirect the user to the calendar page and display their calendar with only the events belonging to the group page that the user was just on.
Announcement board
On the user dashboard: displays most recent messages from any of the teams/groups that the user is in.
For example, if the user is in a team “Luther” and group “Computer Science”, and an announcement is posted by user “Roman_Y”, that would appear in every user that is in the Computer Science group with the header “Luther / Computer Science : Roman_Y posted {msg_body}”
On a group dashboard: displays most recent messages only from that group, regardless of what other groups a user is part of.
Messages also have priority levels (Low, Medium, High, Critical) that are color-coded. We can probably mimic or use bootstrap’s color schemes for this.
Also would be a good idea to have some way to indicate whether or not an announcement has been read by the user
Easiest way would probably be a small dot or exclamation mark similar to another email or message service.
Chat
Members
Only available from a group’s dashboard
Displays users in a given group that are online
Clicking it redirects users to a dedicated “Members” page that shows every member of the group, regardless of their status. Displays people’s names in a table with their email, phone number, and status. Table should be sortable on name (first name and last name?) and status
Each user also has a small chat icon next to their name, which redirects the user to the chat screen, open to the user’s chat history with that user. If there isn’t any history, a new chat is created.
To Do List?
Tentative feature/widget, but pretty easy to implement--either way, not planning to implement a specific page for this
On user dashboard: user can add and remove events with titles, priorities, due dates, and descriptions.
On group dashboard: users with permissions can do the same, users without permissions can view

Other Notes:
teams can select certain style themes that’s the default for an employee, but the employee can also choose to change their theme themselves
Avatars for users: essentially select a default profile image of any color they’d like
team images? Provide a handful of images that teams can choose to represent them.
Would be nice to allow users and teams to upload and store their own images, but not sure where we’d store those.
Possible structure change for future: having a “workspace” like Slack that’s yet another hierarchical layer
Workspace contains various teams (currently our highest level), and those teams still contain groups (which are smaller teams--currently our smallest level and would stay that way)
If a user creates an account but doesn’t have a team, a link will be shown on their dashboard to create or join a team -- this pops up a create/join modal
Sidebar to navigate between teams/groups/tools -- see https://www.figma.com/file/IBJwEJZslohbEBoovEx31K/Dashboard?node-id=0%3A1 for general layout
