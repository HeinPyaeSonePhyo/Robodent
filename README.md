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
### Appointment Booking Rules

- Appointments can only be booked when the selected dentist is scheduled
  to work
- The selected appointment time must fall within the dentist's working hours
- The same dentist cannot have two appointments at exactly the same time
- A **1-hour time conflict check** is applied between appointments for the
  same dentist
- Patients cannot book using an invalid/past schedule
- Patient registration requires the date of birth to indicate an age of at
  least 3 years
- Appointment booking requires the patient to be logged in
- Appointment booking currently accepts **Gmail addresses only**

---

##  Tech stack

| Layer | Technology |
|-------|------------|
| Backend | PHP (procedural, `mysqli`) |
| Database | MySQL / MariaDB |
| Frontend | HTML5, CSS3, Bootstrap 5, JavaScript |
| UI / Libraries | jQuery, Owl Carousel, WOW.js, Animate.css, Tempus Dominus, TwentyTwenty, SweetAlert2, Font Awesome |
| Server | Apache |
| Development Environment | XAMPP / WAMP / MAMP |

---

##  Project structure

```
Robodent/
├── dental/
│   ├── Admin/
│   │   ├── adminlogin.php
│   │   ├── dashboard.php
│   │   ├── DB.php
│   │   ├── dentis.php
│   │   ├── dentist_schedule.php
│   │   ├── display_image.php
│   │   ├── leftnav.php
│   │   ├── patients.php
│   │   ├── treatment.php
│   │   ├── treatment2.php
│   │   ├── update_dentist.php
│   │   ├── update_dentist_schedule.php
│   │   ├── update_patient.php
│   │   ├── update_treatments.php
│   │   └── uploads/
│   │
│   └── Patients/
│       ├── index.php
│       ├── about.php
│       ├── appointment.php
│       ├── appointment_progress.php
│       ├── cancel_appointment.php
│       ├── check_schedule.php
│       ├── contact.php
│       ├── DB.php
│       ├── fetch_profile.php
│       ├── footer.php
│       ├── forgot_password.php
│       ├── Login.php
│       ├── logout.php
│       ├── patient_profile.php
│       ├── process_appointment.php
│       ├── reset_password.php
│       ├── service.php
│       ├── signup.php
│       ├── team.php
│       ├── topnav.php
│       ├── css/
│       ├── js/
│       ├── img/
│       ├── lib/
│       └── scss/
│
└── README.md

---

## Getting started

### Prerequisites
- XAMPP, WAMP, MAMP or another Apache + PHP + MySQL/MariaDB environment
- PHP 7.4 or newer
- MySQL / MariaDB
- A modern web browser

### Installation

1. **Clone the repository**
   ```bash
   git clone (https://github.com/HeinPyaeSonePhyo/Robodent)\
   cd Robodent
   ```

2. **Copy the project into your web root**
   Move the `dental` folder into `xampp/htdocs/` so it is served at `http://localhost/dental/`.
   > Keep the folder name `dental` — the admin menu links to `/dental/Patients/`.

3. **Create the database**
   - Start **Apache** and **MySQL** in the XAMPP Control Panel.
   - Open **phpMyAdmin** and create a new database named `robodent`.
   - The application requires the following tables:
     - `admin`
     - `patients`
     - `dentists`
     - `treatments`
     - `dentist_specialization`
     - `dentist_schedule`
     - `appointment`

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

| Email | Password |
|-------|----------|
| `admin@robodent.com` | `admin123` |

> ⚠️ Demo credentials only — change them before using the project anywhere real.


##  Database


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

- [ ] Hash patient passwords using `password_hash()` / `password_verify()`
- [ ] Strengthen admin authentication and session protection
- [ ] Use prepared statements consistently throughout the application
- [ ] Move database credentials to a configuration file or environment
      variables
- [ ] Add CSRF protection
- [ ] Improve file-upload validation and restrictions
- [ ] Add email verification
- [ ] Add appointment confirmation and reminder emails
- [ ] Remove the Gmail-only appointment restriction
- [ ] Add appointment status such as pending, confirmed and completed
- [ ] Improve database installation by including a complete SQL schema
- [ ] Improve validation and error handling

##  Credits

- Front-end layout built on a free Bootstrap dental-clinic HTML template — please credit the original template author according to its license.
- [Bootstrap](https://getbootstrap.com/), [Owl Carousel](https://owlcarousel2.github.io/OwlCarousel2/), [WOW.js](https://wowjs.uk/), [Animate.css](https://animate.style/), [Tempus Dominus](https://getdatepicker.com/), [SweetAlert2](https://sweetalert2.github.io/), [Font Awesome](https://fontawesome.com/)

---



## Author
Made by Hein Pyae Sone Phyo — https://github.com/HeinPyaeSonePhyo

⭐ If you found this project useful, consider giving it a star!
