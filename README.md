# MMU Confessions

> An anonymous confession platform for the Multimedia University (MMU) community.

Link: https://mmu-confessions-5gch.onrender.com

<br>

![App Preview](docs/static/png/app_preview_screen.png)

<br>

## Table of Contents

- [MMU Confessions](#mmu-confessions)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Background \& Context](#background--context)
  - [Features](#features)
  - [Prerequisites \& Installation Instructions](#prerequisites--installation-instructions)
    - [Prerequisites](#prerequisites)
    - [Installation instructions](#installation-instructions)
  - [Usage](#usage)
    - [Landing page](#landing-page)
    - [Main page](#main-page)
    - [User Profiles](#user-profiles)
    - [Admin Panel](#admin-panel)
    - [Create A Confession](#create-a-confession)
    - [Interacting With Confessions](#interacting-with-confessions)
  - [Project Links](#project-links)
  - [Acknowledgements](#acknowledgements)
  - [Authors](#authors)
  - [Contacts](#contacts)

<br>

## Introduction

MMU Confessions is a web application designed to allow members of the Multimedia University (MMU) community to share their confessions anonymously. Inspired by popular confession pages, this app offers a platform where users can express themselves freely while ensuring their privacy is maintained. The app is built using Flask and is intended for use in a browser.

<br>

## Background \& Context

This project serves as a capstone for students enrolled in the Foundation in Information Technology program at MMU. As a group project, it includes three to four members who selected the web development track from the available options of game development, desktop application development, and web development.

The project is conducted under the supervision of lecturer, Mr.Willie Poh Kaw Lik (klpoh@mmu.edu.my), requiring regular reporting of weekly progress. The team employs an agile project management methodology, utilizing ClickUp for task management and coordination.

The expected outcomes of this project are to develop a solution to simple IT problems using programming tools and to prepare students for solving real-world problems.

<br>

## Features

1. **User Authentication**

   - 🔐 User registration, login and logout.
   - 📧 Email verification for user registration and password reset.

2. **User Profiles**

   - 🖼️ Customizable profiles with avatars.
   - 📄 View created and liked posts, replied messages, bookmarks and rejected posts.

3. **Admin Approval System**

   - ✅ Admin approval for submitted posts with statuses such as rejected, pending, and approved.
   - 🔍 Confessions require admin approval before being publicly posted.

4. **Tagging System**

   - 🏷️ Users can tag their confessions with relevant pre-made tags (e.g., faculties, topics).

5. **Notification System**

   - 🔔 Users receive notifications for various actions, such as replies to their confessions or comments.

6. **Confession Posts & Comments**

   - ✍️ Basic CRUD operations for confessions and comments, including anonymous submissions.
   - 👍 Like and reply functionalities for comments.
   - 🚩 Reporting feature for inappropriate content.

7. **Other Features**
   - 🔍 Advanced searching to assist users in finding specific confessions easily by filtering and sorting parameters.
   - 📑 Infinite scrolling pagination to simplifies navigation through numerous posts.
   - 🎨 Theming with white and dark mode for a comfortable viewing experience.

<br>

## Prerequisites & Installation Instructions

**Note:** We strongly recommend using git bash for Windows users and terminal for Linux and macOS users to minimize installation issues.

### <ins>Prerequisites</ins>

Third party providers are Supabase, Cloudinary, and SendGrid. You will need to create an account with them and obtain the necessary API keys.

Before starting the installation process, please ensure you have registered for the following third-party services:

1. **[Supabase](https://supabase.io/)** - [PostgreSQL](https://www.postgresql.org/) cloud database provider to store all the data.
2. **[Cloudinary](https://cloudinary.com/)** - A cloud-based image and video management service.
<!-- 3. **[smtp2go](https://www.smtp2go.com/)** - A cloud-based email service that provides email delivery services. -->

### <ins>Installation instructions</ins>

1. Create a new folder and clone the repository.

   ```bash
   git clone https://github.com/desmz/mmu_confessions.git .
   ```

<br>

2. Create a virtual environment.

   We strongly recommend running the app in a virtual environment. You can create a virtual environment by typing the following command in the terminal.

   ```bash
   python3 -m venv .venv
   ```

   If you are using Python 2.x. Use the command below:
   ```bash
   python -m venv .venv
   ```

   <br>

   Activate the virtual environment by typing the following command in the terminal.

   <br>

   If you are using Linux or macOS, type the following command in the terminal.

   ```bash
   source .venv/bin/activate
   ```

   If you are using Windows, type the following command in the terminal.

   ```bash
   source .venv/Scripts/activate
   ```

<br>

3. Install the dependencies using pip.

   Ensure you have Python 3.6 or higher installed on your system. If not, please install it first.

   ```bash
   pip install -r requirements.txt
   ```

<br>

4. Create a `.env` file in the root directory and add the environment variables from the [`.env.example`](.env.example) file.

   ```env
   # generate with "openssl rand -base64 30"
   SECRET_KEY=
   DEBUG=True
   DATABASE_URL=postgresql://user:password@localhost/dbname
   FLASK_APP=app
   FLASK_DEBUG=1
   FLASK_RUN_HOST=localhost
   # development or production
   ENV=development
   #list of time zone: https://en.wikipedia.org/wiki/List_of_tz_database_time_zones 
   TZ=Asia/Kuala_Lumpur

   # Email verification
   # generate with "openssl rand -base64 30"
   SECURITY_PASSWORD_SALT=
   MAIL_DEFAULT_SENDER="MMU Confessions <noreply@mmu-confessions.com>"
   MAIL_SERVER="smtp.gmail.com"
   MAIL_PORT=587
   MAIL_USE_TLS=True
   MAIL_USE_SSL=False
   MAIL_USERNAME=
   # If the MAIL_SERVER is smtp.gmail.com, generate an App Password from google: https://myaccount.google.com/apppasswords
   MAIL_PASSWORD=

   # Microsoft OAuth (archieved)
   # MICROSOFT_CLIENT_ID= #your_microsoft_client_id_here
   # MICROSOFT_CLIENT_SECRET= #your_microsoft_client_secret_here

   # Cloudinary
   CLOUDINARY_CLOUD_NAME=#your_cloudinary_cloud_name_here
   CLOUDINARY_API_KEY=#your_cloudinary_api_key_here
   CLOUDINARY_API_SECRET=#your_cloudinary_api_secret_here

   # Supabase
   SUPABASE_PASSWORD=#your_supabase_password_here
   ```

   Alternatively, you can generate a `.env` file with the command below in Linux:

   ``` bash
   cp .env.example .env
   ```


   After that, run the following command to set the environment variables.

   ```bash
   source .env
   ```

<br>

5. Optional: Seed the database with sample data.

   You can seed the database with sample data by running the following command. By default, the seeding configuration level is simple.

   ```bash
   python3 manage.py seeds --simple
   ```

   If you want to seed the database with more data, you can specify the configuration level as follows:

   ```bash
   python3 manage.py seeds --medium
   ```

   or

   ```bash
   python3 manage.py seeds --complex
   ```

   **Note:** The estimated time for complex seeding level is approximately 15-30 minutes. Make sure you have a stable internet connection.

<br>

6. Run the application 🚀

   Once the installation is complete, you can run the app by typing the following command in the terminal.

   ```bash
   python3 manage.py run
   ```

   <br>

7. Optional: Change to admin role.

   To access the admin panel, you need to change the role of the user to admin.

   ```bash
   python3 manage.py role --admin
   ```

## Usage

### Landing page

When you first access the application, you will be greeted with the landing page, which provides an overview of the app's features and a brief introduction to the platform.

![Landing page](docs/static/png/landing_page.png)

<br>

### Main page

The main page displays all the confessions submitted by users. Users can filter and sort the posts based on various parameters.

![Main page](docs/static/png/main_page.png)

<br>

### User Profiles

Users can customize their profiles with avatars and view their created and liked posts, replied messages, and bookmarks.

![User Profiles](docs/static/png/user_profiles.png)

<br>

### Admin Panel

Admins have the ability to approve submitted posts, ensuring that only appropriate content is posted. They can mark posts as rejected, pending, or approved.

![Admin Panel](docs/static/png/admin_panel.png)

<br>

### Create A Confession

Users can submit anonymous confessions and tag them with relevant pre-made tags.

![Submit Confessions](docs/static/png/submit_confessions.png)

<br>

### Interacting With Confessions

Users can comment on posts, and like and reply to comments. There are also reporting features for inappropriate content.

![Comments On Post](docs/static/png/comments_on_post.png)

<br>

## Project Links

- UI Design with [Figma](https://www.figma.com/design/iTrOc7WoVzP9QY7ADc7fHS/MMU-Confession?node-id=0-1&t=DqBYySOI8IgpUHTG-1)
- ERD Diagram with [Lucidchart](https://lucid.app/lucidchart/3ef772a7-f5f1-4a70-82c1-72a8e38f29b4/edit?viewport_loc=-1488%2C-485%2C4904%2C2416%2C0_0&invitationId=inv_418ec412-4007-4dbf-b191-7fdca5e25e06)

<br>

## Acknowledgements

We would like to thank the following resources and individuals for their support and guidance:

- Project structure inspired by [penn-club-rating](https://github.com/abhisuri97/penn-club-ratings/tree/master)

<br>

## Authors

Made with ❤️ by:

- [Desmond Lee](https://github.com/djesmond1015)
- [Vincent Yeap](https://github.com/YBoonShen)
- [Marcus Liew](https://github.com/MarcusLiewZY)
- [Robin Chew](https://github.com/ChewWZ)

<br>

## Contacts

If you have any questions, feel free to contact us at:

- Gmail: desm.swe@gmail.com
- Gmail: boonshen1159@gmail.com
- Gmail: marcusliewzhiyong@gmail.com
- Gmail: robinchew2203@gmail.com

Don't forget to give us a star if you like this project! ⭐🥰
