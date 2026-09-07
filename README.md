# CourseFeedback-DB-A-DBMS-Based-Course-Feedback-Management-System

A PHP + MySQL web application for collecting and analyzing student course feedback, built as a DBMS course project.

## Features

- **Student feedback form** — Students select academic year, semester, branch, section, and subject (subjects are dynamically populated based on the selected semester), then rate the course and instructor across several criteria (subject clarity, instructor knowledge, communication, engagement, learning environment, outcomes achieved) and leave optional remarks.
- **Admin login** — Separate authenticated area for viewing and managing collected feedback.
- **Admin dashboard** — Displays all submitted feedback in a filterable table (by year, branch, semester, subject, section) alongside a live bar chart (via Chart.js) showing average scores per metric, updated dynamically as filters are applied.
- **User management** — Admins can add new admin users directly from the dashboard.

## Tech Stack

- **Backend:** PHP, MySQLi
- **Frontend:** HTML, CSS, vanilla JavaScript
- **Database:** MySQL
- **Charts:** [Chart.js](https://www.chartjs.org/) (via CDN)

## Project Structure

```
dbms_SFMS/
├── css/           # Stylesheets (styles.css, styles2.css)
├── database/       # Database schema / setup files
├── php/             # Backend logic:
│   ├── config.php     # Database connection config
│   ├── admin.php        # Admin login handler
│   ├── feedback.php       # Feedback form submission handler
│   ├── logout.php          # Admin logout
│   └── add_user.php         # Add new admin user
├── index.php          # Student feedback form (entry point)
└── adminpage.php        # Admin dashboard (filterable feedback table + chart)
```

## Feedback Criteria

The form captures ratings (1–5 scale) on:

1. Overall quality of course content
2. Instructor effectiveness — subject knowledge, communication skills, availability/approachability, student engagement, overall effectiveness
3. Conduciveness of the learning environment
4. Achievement of course learning outcomes
5. Free-text remarks

## Getting Started

### Prerequisites

- PHP 7.4+ with the `mysqli` extension
- MySQL / MariaDB
- A local server environment such as XAMPP, WAMP, or MAMP

### Setup

1. Clone the repository into your server's web root (e.g. `htdocs` for XAMPP):
   ```bash
   git clone https://github.com/sandeepelayath/dbms_SFMS.git
   ```

2. Create a MySQL database and import the schema from the `database/` directory.

3. Update the database credentials in `php/config.php` to match your local MySQL setup.

4. Start your local server (Apache + MySQL) and navigate to:
   ```
   http://localhost/dbms_SFMS/index.php
   ```

### Usage

- **Students:** fill out the feedback form at `index.php` and submit.
- **Admins:** click "Admin Login" on the form page to sign in and view `adminpage.php`, where feedback can be filtered and visualized, and new admin users can be added.

## Notes

- This project uses raw `mysqli` queries without prepared statements or output escaping in places — treat it as coursework rather than a production-ready system, and harden it (parameterized queries, input sanitization, password hashing) before any real deployment.
- Course/subject data in `index.php` is hardcoded for a specific curriculum (PES University) and can be edited directly in the `courses` JavaScript object to fit other programs.

## License

No license specified. Add one if you intend to share or reuse this code beyond coursework.
