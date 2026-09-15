\# Practical Development Setup



\*\*Name:\*\* Abdirahman Yahye Iman

\*\*Course:\*\* Software Engineering

\*\*Assignment:\*\* Practical Development Setup

\*\*Date:\*\* September 15, 2026



\---



\# Task 1: Flutter \& Dart Environment Setup



\## Flutter Doctor



I installed Flutter and verified the development environment using:



```bash

flutter doctor

```



\### Flutter Doctor Output



```text

Doctor summary:

\[√] Flutter (Channel stable, 3.47.4, on Microsoft Windows \[Version 10.0.22631.6060], locale en-US)

\[√] Windows Version (11 Pro Education 64-bit, 23H2, 2009)

\[X] Android toolchain - develop for Android devices

&#x20;   X Unable to locate Android SDK.

\[√] Chrome - develop for the web

\[X] Visual Studio - develop Windows apps

&#x20;   X Visual Studio not installed; this is necessary to develop Windows apps.

\[√] Connected device (3 available)

\[√] Network resources



! Doctor found issues in 2 categories.

```



Flutter is installed and working. Chrome is available for Flutter web development. Android development requires the Android SDK, and Windows desktop development requires Visual Studio.



\## Flutter Project



I created the Flutter application using:



```bash

flutter create my\_first\_app

cd my\_first\_app

flutter devices

```



Available devices:



```text

Windows (desktop) • windows • windows-x64

Chrome (web)      • chrome  • web-javascript

Edge (web)        • edge    • web-javascript

```



\## Hot Reload vs Hot Restart



\*\*Hot Reload\*\* applies code changes to a running Flutter application without completely restarting the application. It normally preserves the current application state. It is useful when making small UI or code changes and quickly checking the result.



\*\*Hot Restart\*\* completely restarts the Flutter application and resets its current state. It is useful when Hot Reload does not properly apply a change or when I need the application to start again from its initial state.



\---



\# Task 2: MySQL Database Management



\## Database and Table Creation



I created a database called `school` and a `students` table.



```sql

CREATE DATABASE school;



USE school;



CREATE TABLE students (

&#x20;   id INT AUTO\_INCREMENT PRIMARY KEY,

&#x20;   name VARCHAR(100),

&#x20;   email VARCHAR(150) UNIQUE,

&#x20;   enrolled\_on DATE

);

```



\## Insert Sample Records



```sql

INSERT INTO students (name, email, enrolled\_on)

VALUES

('Abdirahman', 'abdirahman@example.com', '2026-09-15'),

('Ahmed', 'ahmed@example.com', '2026-09-15');

```



\## Query the Students Table



```sql

SELECT \* FROM students;

```



\### Query Result



```text

+----+------------+------------------------+-------------+

| id | name       | email                  | enrolled\_on |

+----+------------+------------------------+-------------+

|  1 | Abdirahman | abdirahman@example.com | 2026-09-15  |

|  2 | Ahmed      | ahmed@example.com      | 2026-09-15  |

+----+------------+------------------------+-------------+

```



\## MySQL Security Reflection



Using the MySQL `root` account directly in an application is poor security practice because the root account has very high privileges. If an application is compromised, an attacker could potentially modify or delete databases, access sensitive information, or create other accounts.



A better approach is to create a dedicated application user with only the permissions required by the application.



Example:



```sql

CREATE USER 'school\_app'@'localhost'

IDENTIFIED BY 'StrongPassword123!';



GRANT SELECT, INSERT, UPDATE, DELETE

ON school.\*

TO 'school\_app'@'localhost';



FLUSH PRIVILEGES;

```



The application account should use a strong unique password, and credentials should not be hard-coded into application source code.



\---



\# Task 3: Python Environment \& Dependency Isolation



\## Project Directory



I created the project directory:



```powershell

mkdir python\_setup\_lab

cd python\_setup\_lab

```



\## Virtual Environment



I created an isolated Python virtual environment:



```powershell

python -m venv venv

```



Because PowerShell initially restricted script execution, I used:



```powershell

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

```



Then activated the environment:



```powershell

.\\venv\\Scripts\\Activate.ps1

```



The activated environment was shown by:



```text

(venv) PS C:\\Users\\user\\python\_setup\_lab>

```



\## Install Requests



I installed the `requests` package using:



```powershell

python -m pip install requests

```



\## Verify Installed Packages



I verified the installed packages using:



```powershell

pip list

```



The important package was:



```text

requests 2.34.2

```



along with its supporting dependencies such as:



```text

certifi

charset-normalizer

idna

urllib3

```



\## Export Dependencies



I exported the environment dependencies using:



```powershell

pip freeze > requirements.txt

```



The `requirements.txt` file contains the installed dependencies required to reproduce the environment.



\---



\# Task 4: VS Code Workspace Configuration



I configured Visual Studio Code for the development environment.



\## Installed Extensions



The following extensions were installed:



\* Flutter — Dart Code

\* Dart — Dart Code

\* Python — Microsoft

\* Pylance — Microsoft

\* MySQL for Visual Studio Code



\## Python Interpreter



I selected the Python interpreter inside the virtual environment:



```text

python\_setup\_lab\\venv\\Scripts\\python.exe

```



The VS Code integrated terminal confirmed that the virtual environment was active:



```text

(venv) PS C:\\Users\\user\\python\_setup\_lab>

```



\## VS Code Configuration Screenshot



The full-screen screenshot for this task shows:



\* The installed VS Code extensions

\* The integrated terminal with `(venv)` active

\* The selected Python `venv` interpreter in the VS Code status bar



\*\*VS Code Screenshot:\*\*



![VS Code Configuration Screenshot](Screenshot%202026-09-15%20060054.png)



\---



\# Conclusion



This assignment verified the main development tools required for my software engineering environment:



\* Flutter and Dart for application development

\* MySQL for database management

\* Python virtual environments for dependency isolation

\* VS Code for development and workspace configuration



The Python dependencies were exported to `requirements.txt`, and the project files were committed to GitHub for submission.



