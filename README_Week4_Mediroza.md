# Mediroza Hospital --- Week 4 Penetration Testing Project

## 📌 Project Overview

This repository documents my **Week 4 Web Application Penetration
Testing project** performed against the **Mediroza Hospital**
application in an authorized lab environment.

The assessment focused on web application reconnaissance, authentication
testing, exposed resources, sensitive information exposure, database
backup analysis, and evidence collection.

> ⚠️ **Ethical & Legal Notice:** This project was conducted only within
> an authorized training/lab environment. Do not reproduce these
> techniques against systems without explicit permission.

------------------------------------------------------------------------

## 🎯 Objectives

The main objectives of the Week 4 assessment were to:

-   Perform web application reconnaissance.
-   Identify exposed directories and application entry points.
-   Investigate authentication functionality.
-   Analyze HTTP requests and responses.
-   Identify improperly exposed files and resources.
-   Analyze an exposed database backup.
-   Investigate sensitive information exposure.
-   Access confidential patient-report material within the authorized
    lab.
-   Collect and document evidence for a penetration-testing report.

------------------------------------------------------------------------

## 🛠️ Tools & Techniques

The project involved practical use of:

-   **Web Browser / Developer Tools**
-   **HTTP request and response inspection**
-   **Directory and resource enumeration**
-   **robots.txt analysis**
-   **Sitemap analysis**
-   **SQL/database backup analysis**
-   **Manual source and application inspection**
-   **Evidence collection and documentation**

------------------------------------------------------------------------

## 🔎 Reconnaissance

The assessment began with reconnaissance of the Mediroza Hospital web
application.

An exposed `robots.txt` file revealed application paths including:

-   `/patient/`
-   `/admin/`
-   `/old/`

A sitemap was also reviewed to identify publicly referenced application
resources.

------------------------------------------------------------------------

## 🔐 Authentication Testing

The Patient Portal authentication functionality was investigated using
browser Developer Tools.

The login form used a POST request to:

``` text
login.php
```

The form contained username and password parameters.

The HTTP response behavior was reviewed to understand how the
application handled authentication attempts and whether
authentication-related information was exposed.

------------------------------------------------------------------------

## 📂 Exposed Resources

During enumeration, an accessible `/old/` directory was identified.

The directory exposed an SQL database backup:

``` text
mediroza_db_backup_2019.sql
```

This represented a significant information-exposure finding because the
backup contained confidential organizational records.

------------------------------------------------------------------------

## 🗄️ Database Backup Analysis

The exposed SQL backup identified a database named:

``` text
mediroza_hr
```

The backup contained a `staff` table with fields including:

-   Full name
-   Job title
-   Department
-   Email
-   Phone
-   National ID
-   Monthly salary
-   Date joined

The SQL backup also contained a `shareholders` table containing:

-   Shareholder name
-   Share percentage
-   Shares held
-   Share class

The backup itself explicitly warned that it contained confidential staff
and shareholder records.

**Evidence:** `mediroza_db_backup_2019.sql` fileciteturn2file0L1-L6

------------------------------------------------------------------------

## 🏥 Patient Portal / Confidential Report Access

The assessment also involved investigation of the restricted patient
area.

A confidential pathology laboratory report was successfully accessed
within the authorized lab environment.

The report demonstrated the potential impact of unauthorized access to
protected medical information.

### ⚠️ Privacy

Patient-identifying information and medical results are **not reproduced
in this README**.

Screenshots shared publicly should be appropriately redacted to remove:

-   Patient name
-   Patient ID
-   Date of birth
-   Medical/laboratory results
-   Other personally identifiable or sensitive information

------------------------------------------------------------------------

## 📊 Key Security Findings

  ------------------------------------------------------------------------
  Finding                 Description             Potential Impact
  ----------------------- ----------------------- ------------------------
  Exposed directories     Sensitive application   Increased attack surface
                          paths were discoverable 

  Exposed database backup SQL backup was          Disclosure of
                          accessible from a web   confidential
                          directory               organizational data

  Sensitive database      Staff and shareholder   Privacy and
  records                 information was stored  information-disclosure
                          in the exposed backup   risk

  Patient-area exposure   Confidential            Potential exposure of
                          laboratory-report       protected medical
                          material was accessible information
                          during the authorized   
                          assessment              

  Authentication testing  Patient portal login    Useful for assessing
  opportunity             behavior was observable authentication controls
                          through HTTP inspection 
  ------------------------------------------------------------------------

------------------------------------------------------------------------

## 🧠 Key Lessons Learned

This project reinforced several important penetration-testing
principles:

1.  **Reconnaissance matters.**\
    Simple files such as `robots.txt` can reveal useful application
    paths.

2.  **Backups must be protected.**\
    Old database backups should never be publicly accessible through a
    web directory.

3.  **Sensitive data requires strong access controls.**\
    Staff, shareholder, and patient information should be protected from
    unauthorized access.

4.  **Evidence is essential.**\
    A professional penetration test requires clear documentation of what
    was discovered and how it was verified.

5.  **Authorization is critical.**\
    Security testing should only be performed against systems where
    explicit permission has been provided.

------------------------------------------------------------------------

## 🛡️ Recommended Remediation

Based on the findings observed during the lab assessment, recommended
defensive measures include:

-   Remove database backups from publicly accessible web directories.
-   Store backups outside the web root.
-   Apply strict access controls to sensitive application directories.
-   Review web-server directory listing configuration.
-   Protect patient records with strong authentication and authorization
    controls.
-   Encrypt sensitive backups at rest.
-   Regularly audit publicly accessible files and directories.
-   Monitor access to sensitive patient and staff information.
-   Remove unnecessary legacy files and application components.
-   Perform regular vulnerability assessments and penetration tests.

------------------------------------------------------------------------

## 📁 Evidence

Evidence collected during the assessment included:

-   Patient Portal screenshot
-   Login form inspection
-   HTTP POST request inspection
-   HTTP response inspection
-   `robots.txt` enumeration
-   Sitemap inspection
-   Exposed `/old/` directory
-   Exposed SQL database backup
-   Database structure and record analysis
-   Authorized patient-report access evidence

**Important:** Sensitive patient information should remain private and
should not be committed to a public GitHub repository.

------------------------------------------------------------------------

## ⚠️ Disclaimer

This repository is intended for **educational and cybersecurity training
purposes only**.

All testing described in this project was performed within an authorized
lab environment. The techniques and findings should not be used against
systems, networks, applications, or data without explicit authorization.

------------------------------------------------------------------------

## 👨‍💻 Author

**Cybersecurity Student**

Focus areas:

-   Penetration Testing
-   Ethical Hacking
-   Web Application Security
-   Network Security
-   Information Security

------------------------------------------------------------------------

## 🔐 Final Note

Week 4 provided hands-on experience in moving from **reconnaissance →
enumeration → application analysis → information exposure → evidence
collection → security recommendations**.

The project strengthened my understanding of how seemingly small
security weaknesses can lead to exposure of highly sensitive
information.
