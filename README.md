# User Management Automation Script

## Overview

This repository contains a Bash script (`create_users.sh`) designed to automate the process of creating users, assigning groups, and managing passwords in a Linux environment. The script reads from a specified file containing user information, creates users and groups as specified, sets up home directories with appropriate permissions, generates random passwords, and logs all actions.

## Features

- Creates users with personal groups.
- Assigns users to additional groups.
- Generates random passwords for each user.
- Logs all actions to `/var/log/user_management.log`.
- Stores generated passwords securely in `/var/secure/user_passwords.csv`.

## Prerequisites

- Linux-based system.
- Bash shell.
- Root or sudo privileges to run the script.

## Usage

1. Clone this repository:
    ```sh
    git clone <repository-url>
    cd <repository-directory>
    ```

2. Prepare the user file:
    - Create a text file containing user information in the format `username;groups`.
    - Example:
      ```
      light;sudo,dev,www-data
      idimma;sudo
      mayowa;dev,www-data
      ```

3. Run the script with the user file as an argument:
    ```sh
    sudo bash create_users.sh <path_to_user_file>
    ```

## Script Details

The script performs the following steps:

1. **Setup**:
    - Defines secure folder, log file, and password file locations.
    - Creates the secure folder if it does not exist.
    - Ensures the log and password files exist and are properly secured.

2. **Input Validation**:
    - Checks if the user file is provided and exists.

3. **User and Group Management**:
    - Reads the user file line by line.
    - For each user:
        - Creates a personal group if it does not exist.
        - Creates the user with a home directory and assigns the personal group.
        - Generates and sets a random password for the user.
        - Assigns the user to additional groups as specified.

4. **Logging**:
    - Logs all actions performed by the script to the log file.

## Example User File

The user file should be formatted with each line containing a username and groups, separated by a semicolon (`;`). Groups are separated by commas (`,`).

Example:
```txt
light;sudo,dev,www-data
idimma;sudo
mayowa;dev,www-data
```


## Security

- The generated passwords are stored securely in `/var/secure/user_passwords.csv` with file permissions set to allow only the owner to read the file.
- Logs are stored in `/var/log/user_management.log`.

## Additional Resources

- Learn more about the HNG Internship: [HNG Internship](https://hng.tech/internship)
- Explore hiring opportunities: [HNG Hire](https://hng.tech/hire)
- Check out premium services: [HNG Premium](https://hng.tech/premium)

## License

This project is licensed under the MIT License.

## Author

Jessica Chioma Chimex

## Acknowledgements

Special thanks to the `HNG` Internship program for inspiring this project.
