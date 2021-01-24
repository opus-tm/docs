
# Introduction 

![OpusLogo](./images/logo64.png)

Opus is a workforce management application for small teams.

Here are our:
* [Privacy Policy](./legal/privacy.md)
* [Terms and Conditions](/legal/tac.md)
* [License](./legal/LICENSE.md)

Want to contribute to Opus? Check out [how to contribute](./CONTRIBUTING.md).

## Overview
We designed Opus as a lightweight team management platform to provide small teams with the facilites to collaborate and connect with their fellow teammates. While there's no limit to how many people can be added to an Opus team, we feel that our services are best fitted to teams of less than 75 people.

### Structure
When a user joins Opus, they will not be part of any teams. To access the tools on the site, they will need to receive an invite from a user in a team that already exists. Once they are added to it, they will enter the team at the lowest permission level and can interact with the team features as usual. Teams in Opus have two tiers: a main team, and subgroups of that team. Subgroups can be used to divide up the team into specialized sections, perhaps by department, instrument, or position, based on the purpose of the team.

### Widgets
Widgets are available for each of the tools that Opus provides. Each widget provides a snapshot of the tool for the user by displaying three recent items in list form. 
* On the user's dashboard: Widgets are displayed for Announcements, Calendar, Contacts, and Teams. Each one of these widgets links to its corresponding feature; in addition, the Teams widget also has individual links to the pages for each of the teams that it displays.
* On a team's page: Like the user dashboard, widgets are displayed for each of the current features. However, when viewing widgets on an individual team's page, the widget will only show data for that specific team. Additionally, the widgets will link to the corresponding feature, but the data that is shown will automatically be filtered by the team that the user navigated from. For instance, if a user clicks on the Announcements widget from the 'Basketball' team page, they will be redirected to the route '/announcements/Basketball', which will initially be filtered to show all announcements for the 'Basketball' team.

## Current Features
Below is a list of tools and features that we've implemented for the Minimum Viable Product presentation on Tuesday, January 26th. Announcements, Calendar, and Contacts pages all display their corresponding data in a table view, using the NPM package 'react-bootstrap-table-next'. This allows each of them to be sorted by any column the user chooses.

### Announcements
Users within a team can create an announcement that all other users in that team can view. Each announcements is displayed in a table view with its priority (High, Medium, Low), the user that created it, the team it was created for, the expiration date of the announcement, its associated event (if it has one), and the announcement message. Announcements can be filtered by team and priority using the corresponding dropdown menu or by accessing the announcements route paired with the desired team: '/announcements/{teamName}'.

### Calendar

### Contacts

### Teams and Subgroups

## Proposed Future Features and Enhancements
While the MVP presentation date limited how much we could feasibly do on this project, we have taken the time to brainstorm ideas for future enhancements to Opus, which are listed below.

### Chat Service
Many messaging platforms already exist, but it would be a bonus to include a chat system within the Opus app where users could stay in touch with contacts from the various teams that they are a part of. We would also like to implement a group chat feature so that users could have a running conversation with their entire team or subgroup, depending on the team's needs.

### Permissions
While we had planned to include this in the MVP, time constraints and backend configurations required us to move this feature to after MVP. We plan to implement this on the backend with three lists for each team, each containing the ids of the corresponding users: 'owners', 'managers', and 'users'. Owners have full access to the site's features including editing a team name, promoting members up to owner, and deleting the team that they are the owner of. Managers can create team-wide events and announcements, remove and add users to the team, create new subgroups, and promote members up to manager. Users will have the ability to leave teams, create events between themselves and other users, and view announcements and events of their corresponding team. Each permission level inherits the permissions of the levels below it. These lists can then be fetched from the API to determine what level of access the current user is allowed on the site.

### To Do List


