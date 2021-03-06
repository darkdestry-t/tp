---
layout: page
title: User Guide
---

A-Bash Book is an enhanced version of Address Book 3 app for managing your contacts, optimized for use via a Command Line Interface (CLI) while still having the benefits of a Graphical User Interface (GUI). If you type fast, A-Bash Book will allow you to quickly complete your contact management tasks.

* Table of Contents
  {:toc}

--------------------------------------------------------------------------------------------------------------------

## Quick start

1. Ensure you have Java `11` or above installed in your Computer.

1. Download the latest `a-bash-book.jar` from [here](https://github.com/AY2021S2-CS2103T-T12-3/tp/releases).

1. Copy the file to the folder you want to use as the _home folder_ for your A-Bash Book data.

1. Double-click the file to start the app. The GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Ui](images/Ui.png)

1. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and pressing Enter will open the help window.<br>
   Some example commands you can try:

    * **`list`** : Lists all contacts.

    * **`add`**`-n John Doe -p 98765432 -e johnd@example.com -a John street, block 123, #01-01` : Adds a contact named `John Doe` to the Address Book.

    * **`delete`**`3` : Deletes the 3rd contact shown in the current list.

    * **`clear`** : Deletes all contacts.

    * **`exit`** : Exits the app.

1. Refer to the [Features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add -n NAME`, `NAME` is a parameter which can be used as `add -n John Doe`.

* Items in square brackets are optional.<br>
  e.g `-n NAME [-t TAG]` can be used as `-n John Doe -t friend` or as `-n John Doe`.

* Items with `…`​ after them can be used multiple times including zero times.<br>
  e.g. `[-t TAG]…​` can be used as ` ` (i.e. 0 times), `-t friend`, `-t friend -t family` etc.

* Parameters can be in any order.<br>
  e.g. if the command specifies `-n NAME -p PHONE_NUMBER`, `-p PHONE_NUMBER -n NAME` is also acceptable.

* If a parameter is expected only once in the command but you specified it multiple times, only the last occurrence of the parameter will be taken.<br>
  e.g. if you specify `-p 12341234 -p 56785678`, only `-p 56785678` will be taken.

* Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `exit` and `clear`) will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</div>

### Viewing help : `help`

Shows a message explaning how to access the help page.

![help message](images/helpMessage.png)

Format: `help`


### Adding a person: `add`

Adds a person to the address book.

Format: `add -n NAME -p PHONE_NUMBER -e EMAIL -a ADDRESS [-t TAG]…​`

<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
A person can have any number of tags (including 0)
</div>

Examples:
* `add -n John Doe -p 98765432 -e johnd@example.com -a John street, block 123, #01-01`
* `add -n Betsy Crowe -t friend -e betsycrowe@example.com -a Newgate Prison -p 1234567 -t criminal`

### Listing all persons : `list`

Shows a list of all persons in the address book.

Format: `list`

### Editing a person : `edit`

Edits an existing person in the address book.

Format: `edit INDEX [-n NAME] [-p PHONE] [-e EMAIL] [-a ADDRESS] [-t TAG]…​`

* Edits the person at the specified `INDEX`. The index refers to the index number shown in the displayed person list. The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing tags, the existing tags of the person will be removed i.e adding of tags is not cumulative.
* You can remove all the person’s tags by typing `-t ` without
  specifying any tags after it.

Examples:
*  `edit 1 -p 91234567 -e johndoe@example.com` Edits the phone number and email address of the 1st person to be `91234567` and `johndoe@example.com` respectively.
*  `edit 2 -n Betsy Crower -t ` Edits the name of the 2nd person to be `Betsy Crower` and clears all existing tags.

### Locating persons by name: `find`

Finds persons whose names contain any of the given keywords.

Format: `find KEYWORD [MORE_KEYWORDS]`

* The search is case-insensitive. e.g `hans` will match `Hans`
* The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
* Only the name is searched.
* Only full words will be matched e.g. `Han` will not match `Hans`
* Persons matching at least one keyword will be returned (i.e. `OR` search).
  e.g. `Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `find John` returns `john` and `John Doe`
* `find alex david` returns `Alex Yeoh`, `David Li`<br>
  ![result for 'find alex david'](images/findAlexDavidResult.png)

### Deleting a person : `delete`

Deletes the specified person from the address book.

Format: `delete INDEX`

* Deletes the person at the specified `INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `list` followed by `delete 2` deletes the 2nd person in the address book.
* `find Betsy` followed by `delete 1` deletes the 1st person in the results of the `find` command.

### Clearing all entries : `clear`

Clears all entries from the address book.

Format: `clear`

### Exiting the program : `exit`

Exits the program.

Format: `exit`

### Tab Auto Completion [coming soon]

<!-- Pressing tab when typing a command will autocomplete it.

Example: You want to execute command `delete`. Typing `de<tab>` will auto complete `de` to `delete` -->

### Live command suggestion [coming soon]

<!-- In addition to tab auto complete feature, A-Bash Book will also attempt to suggest commands available to the user.

![](https://via.placeholder.com/350x150/000000/FFFFFF?text=Hi)

Users will be able to press tab to cycle through the available options. -->

### Find feature: fuzzy search [coming soon]

<!-- Find command has been enhanced to match full words from partial keywords by similarity.

Example: Searching for ‘jon’ will return results that are similar and ranked by similarity, e.g.  jonathan, john, johnny, ... -->

### Alias [coming soon]
<!--
An alias is a shortcut command that a user can create to reference a default supported command.

Format: `alias [-p ] [ALIAS_NAME/COMMAND_NAME]`

Key:
    `-p `    Print the current values

Examples:


| Example | Description |
| --------------- | -------- |
|`alias ls/list`  | associates a new ls command to list, such that the ls command will behave identically to the list command (ie. ls will now generate the list of all contacts).|
|`alias ls/list -n  -p  -e  -t `| associates a new ls command to list, such that the ls command will behave identically to the list command with the options.|
|`alias f/find`   | associates a new f command to find, such that the f command will behave identically to the find command (ie. f Alex Yeoh will now return contacts equals or similar to Alex Yeoh).|
|`alias ls`       |        will print the VALUE associated with the ls alias.|
|`alias -p `       |        will print all the registered aliases| -->

### Removing Alias [coming soon]

<!-- The unalias command can be used to remove each name from the list of defined aliases.

Format: `unalias ALIAS_NAME`

Examples:
| Example | Description |
| --------------- | -------- |
|`unalias ls`| will remove the alias `ls`|
|`unalias d`| will remove the alias `d`| -->

### List options [coming soon]

<!-- List options provide the user with the choice to tweak their list return result according to the specified option(s).

Format: each option should start with OPTION/ and be separated by a whitespace, where OPTION/ refers to the option Key.
ie. `list [OPTION_1/ OPTION_2/ … OPTION_N/]`

Key:
| Key | Description |
| --------------- | -------- |
|`n`|    Name|
|`p`|     Phone number|
|`e`|    Email|
|`a`|    Address|
|`t`|    Tag|
|`b` |   Birthday (new)|
|`g` |   Gender (new) |
|`no`|    Notes (new) |

Examples:
| Example | Description |
| --------------- | -------- |
|`list -n `| returns the list of all contacts with name as the only field.|
|`list -n -b -g`| returns the list of all contacts with name, birthday, gender as the only fields.|

Tip:
Combine the Alias feature with custom options to have a customized view. E.g. `alias list=”list -n  -p  -e  -t ` to only show the name, phone number, email and tags. -->


### Saving the data

A-Bash Book data are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Editing the data file

A-Bash Book data are saved as a JSON file `[JAR file location]/data/addressbook.json`. Advanced users are welcome to update data directly by editing that data file.

<div markdown="span" class="alert alert-warning">:exclamation: **Caution:**
If your changes to the data file makes its format invalid, A-Bash Book will discard all data and start with an empty data file at the next run.
</div>

--------------------------------------------------------------------------------------------------------------------

## FAQ

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous A-Bash Book home folder.

--------------------------------------------------------------------------------------------------------------------

## Command summary

Action | Format, Examples
--------|------------------
**Add** | `add -n NAME -p PHONE_NUMBER -e EMAIL -a ADDRESS [-t TAG]…​` <br> e.g., `add -n James Ho -p 22224444 -e jamesho@example.com -a 123, Clementi Rd, 1234665 -t friend -t colleague`
**Clear** | `clear`
**Delete** | `delete INDEX`<br> e.g., `delete 3`
**Edit** | `edit INDEX [-n NAME] [-p PHONE_NUMBER] [-e EMAIL] [-a ADDRESS] [-t TAG]…​`<br> e.g.,`edit 2 -n James Lee -e jameslee@example.com`
**Find** | `find KEYWORD [MORE_KEYWORDS]`<br> e.g., `find James Jake`
**List** | `list`
**Help** | `help`
**Alias** | _[coming soon]_
**Unalias** | _[coming soon]_
