# Study Planner

Study Planner is a Streamlit-based productivity app for organizing study tasks, tracking progression, and managing a personal study workload. It combines a dashboard, a task management page, and a profile/authentication page into one focused study workflow.

## About the project

The app is designed for students and learners who want a simple structure for:
- keeping track of upcoming study tasks,
- planning time by deadline,
- reviewing workload and completion progress,
- creating an account for a personal study dashboard,
- managing tasks from a single, easy-to-use UI.

## Features

- Dashboard overview with summary metrics
  - total tasks
  - completed tasks
  - active tasks
  - completion rate
- Weekly time-allocation chart to visualize planned study effort
- Upcoming deadlines panel
- Active task detail list
- Task management page with:
  - add task
  - mark task as done
  - delete task
  - clear completed tasks
- Profile page with login and registration system
- Secure local authentication config using `streamlit-authenticator`
- Remember-me login option

## How it works

The app uses Streamlit multipage navigation:
- `main.py` loads the dashboard overview
- `pages/1_Tasks.py` handles task CRUD logic
- `pages/2_Profile.py` handles the login and account flow
- `_studyplanner_auth.py` centralizes authentication logic and config management

When a user logs in or creates an account, the app stores credentials in `auth_config.yaml`. Task data is stored in the Streamlit session state while the app is running, which makes the planner lightweight and easy to run locally without a database.

## Installation

Requirements:
- Python 3.10+
- macOS/Linux shell or compatible terminal

1. Clone or download the project.
2. Open a terminal in the project folder.
3. Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

4. Install dependencies:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## Running the app

From the project folder:

```bash
source .venv/bin/activate
streamlit run .venv/Main.py
```

You can also run from the project directory with:

```bash
./.venv/bin/python -m streamlit run .venv/Main.py
```

Then open the local URL printed in the terminal, usually:

```text
http://localhost:8501
```

## Authentication and password rules

The app uses `streamlit-authenticator` and validates account registration constraints. Passwords are expected to meet a stronger pattern, typically requiring uppercase, lowercase, and special characters.

The app may optionally use a password-reset email flow if an environment variable is configured:

```bash
export STREAMLIT_AUTHENTICATOR_API_KEY="your_api_key_here"
```

Keep this key private and do not commit it to GitHub.

## Usage guide

1. Open the app and go to the Profile page.
2. Create an account if needed.
3. Log in using the credentials you created.
4. Go to the Tasks page to add new studies.
5. Enter:
   - subject
   - topic/chapter
   - deadline
   - duration in minutes
6. Mark tasks as complete or delete them as needed.
7. View dashboard metrics and upcoming tasks on the main page.

## Project structure

```text
.
├── .venv/
├── .gitignore
├── README.md
├── requirements.txt
├── _studyplanner_auth.py
├── auth_config.yaml
├── .venv/Main.py
├── .venv/pages/
│   ├── 1_Tasks.py
│   └── 2_Profile.py
└── ...
```

## Limitations

- Tasks are kept in session state, so they are not permanently stored across restarts unless additional persistence is added.
- Authentication is local and file-based, which is suitable for demos but not production-grade multi-user security.
- Email password reset requires a valid external email service and API key.
- There is no database or dashboard analytics backend yet.
- The app is designed for a single local environment rather than a hosted service.

## Future improvements

- Add persistent storage with SQLite or PostgreSQL
- Add user-specific task storage per account
- Add editing and rescheduling for existing tasks
- Add calendar view and study streak tracking
- Add reminders and notifications
- Add data export/import
- Add search and filters by subject, status, and due date
- Add richer charts and study analytics
- Improve production security for authentication and secrets handling
- Deploy to Streamlit Cloud or a cloud-hosted environment

## Notes

This project is a practical study-planning app built for learning and local use. It is a good base for expanding into a full personal productivity tool.

Here is a glance at the home page:

<img width="1680" height="1050" alt="Study planner home page" src="https://github.com/user-attachments/assets/2a583052-eccb-416d-9bd1-5a221f37d731" />

Here is a glance at the tasks page:

<img width="1680" height="986" alt="Study Planner tasks page" src="https://github.com/user-attachments/assets/573ae426-68e8-47fb-a845-a5b42f917952" />

Here is a glance at the login and register page:

<img width="1680" height="1050" alt="Study Planner Accounts and login page" src="https://github.com/user-attachments/assets/1024f180-6688-45c9-9c3a-4bab05fdf3cb" />



