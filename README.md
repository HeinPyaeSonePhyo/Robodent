# RoboDent — Dental Clinic Management System

A full-stack web application for running a dental clinic. Patients can browse services, create an account and book appointments online, while clinic staff manage dentists, schedules, treatments, patients and bookings from a dedicated admin dashboard.

##  Features

###  Patient portal
- Responsive landing page with services, pricing, dentist team, testimonials and a before/after slider
- Patient **sign up**, **login** and **logout**
- **Forgot / reset password** (verified with email, date of birth and phone number)
- **Online appointment booking** — choose a treatment, a dentist and a date/time
- Live **dentist availability check** for the selected day
- View your profile and **cancel** your appointment
- Search for dentists, plus About, Services, Team and Contact pages

###  Admin dashboard
- Admin login
- Dashboard with total **patients**, **dentists** and **appointments**, plus the weekly duty roster
- **Dentist management** — add, edit and delete dentists, upload photos and assign specializations
- **Dentist schedule management** — set duty days and working hours per dentist
- **Treatment management** — add, edit and delete treatments and prices
- **Patient management** — view, search, edit and delete patients
- **Appointment management** — view, search and delete bookings

###  Smart booking rules
- Appointments can only be booked on days/hours the dentist is on duty
- No double-booking: the same dentist can't have two appointments at the same time
- A **1-hour buffer** is enforced between a dentist's appointments
- Past dates are rejected
- Sign-up requires a valid date of birth (minimum age 3)

---

##  Tech stack

| Layer | Technology |
|-------|------------|
| Backend | PHP (procedural, `mysqli`) |
| Database | MySQL / MariaDB |
| Frontend | HTML5, CSS3, Bootstrap 5, JavaScript |
| Libraries | jQuery, Owl Carousel, WOW.js, Animate.css, Tempus Dominus, TwentyTwenty, SweetAlert2, Font Awesome |
| Local server | XAMPP / WAMP / MAMP |

---

##  Project structure

```
Robodent/
├── dental/
│   ├── Admin/                 # Admin dashboard (staff side)
│   │   ├── adminlogin.php
│   │   ├── dashboard.php
│   │   ├── dentis.php                 # Dentist management
│   │   ├── dentist_schedule.php       # Duty schedules
│   │   ├── treatment.php              # Treatments & prices
│   │   ├── patients.php               # Patient management
│   │   ├── appointment.php            # Appointment management
│   │   └── uploads/                   # Dentist photos
│   └── Patients/              # Patient website (public side)
│       ├── index.php
│       ├── signup.php / Login.php / logout.php
│       ├── forgot_password.php / reset_password.php
│       ├── appointment.php / appointment_progress.php
│       ├── process_appointment.php / check_schedule.php / cancel_appointment.php
│       ├── patient_profile.php
│       ├── about.php / service.php / team.php / contact.php
│       └── css/ js/ img/ lib/ scss/
├── schema.sql                 # Database structure + sample data
└── README.md
```

---

## Getting started

### Prerequisites
- [XAMPP](https://www.apachefriends.org/) (or any Apache + PHP + MySQL stack)
- PHP 7.4 or newer

### Installation

1. **Clone the repository**
   ```bash
   git clone (https://github.com/HeinPyaeSonePhyo/Robodent)
   ```

2. **Copy the project into your web root**
   Move the `dental` folder into `xampp/htdocs/` so it is served at `http://localhost/dental/`.
   > Keep the folder name `dental` — the admin menu links to `/dental/Patients/`.

3. **Create the database**
   - Start **Apache** and **MySQL** in the XAMPP control panel.
   - Open phpMyAdmin → **Import** → choose `schema.sql`.
   - This creates the `robodent` database, all tables, and some sample data.

4. **Configure the database connection**
   Edit `dental/Admin/DB.php` and `dental/Patients/DB.php`:
   ```php
   $conn = new mysqli("localhost:3308", "root", "", "robodent");
   ```
   The project ships with MySQL port `3308`. If your MySQL runs on the default port, change it to `localhost:3306` (or just `localhost`).

5. **Check the admin menu link**
   `dental/Admin/leftnav.php` links to `http://localhost:8080/dental/Patients/`. Update the host/port if your Apache runs elsewhere.

6. **Open the app**
   | Area | URL |
   |------|-----|
   | Patient website | `http://localhost/dental/Patients/` |
   | Admin panel | `http://localhost/dental/Admin/adminlogin.php` |

### Demo admin login
The sample data in `schema.sql` creates a demo admin:

| Email | Password |
|-------|----------|
| `admin@robodent.com` | `admin123` |

> ⚠️ Demo credentials only — change them before using the project anywhere real.


##  Database

`schema.sql` defines these tables:

| Table | Purpose |
|-------|---------|
| `admin` | Admin accounts |
| `patients` | Registered patients |
| `dentists` | Dentist profiles and photos |
| `treatments` | Treatments and prices |
| `dentist_specialization` | Which dentist performs which treatment |
| `dentist_schedule` | Duty days and working hours per dentist |
| `appointment` | Booked appointments |

---

##  Roadmap

This started as an academic project, so it is meant for learning and demos rather than production use. Planned improvements:

- [ ] Hash passwords with `password_hash()` / `password_verify()`
- [ ] Protect every admin page with a session check
- [ ] Use prepared statements everywhere (search, delete and insert queries)
- [ ] Move database credentials to a config / `.env` file
- [ ] CSRF protection and stricter file-upload validation
- [ ] Email confirmations and reminders for appointments
- [ ] Support any email provider (currently `@gmail.com` only)
- [ ] Appointment status (pending / confirmed / completed)

---

##  Credits

- Front-end layout built on a free Bootstrap dental-clinic HTML template — please credit the original template author according to its license.
- [Bootstrap](https://getbootstrap.com/), [Owl Carousel](https://owlcarousel2.github.io/OwlCarousel2/), [WOW.js](https://wowjs.uk/), [Animate.css](https://animate.style/), [Tempus Dominus](https://getdatepicker.com/), [SweetAlert2](https://sweetalert2.github.io/), [Font Awesome](https://fontawesome.com/)

---



## Author
Made by Hein Pyae Sone Phyo — https://github.com/HeinPyaeSonePhyo

⭐ If you found this project useful, consider giving it a star!
