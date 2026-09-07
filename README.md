# 🎓 Student Tracker Pro

**Student Tracker Pro** is a Windows-based Student Management and Attendance System built using **C++ and the Win32 API**.

The application provides an administrator dashboard for managing student records, tracking attendance, searching students, and storing student information locally.

---

## 🚀 Features

### 🔐 Admin Login

* Secure administrator login screen.
* Prevents access to the student management dashboard without authentication.
* Provides login and logout functionality.

### 👨‍🎓 Student Registration

* Register new students with details including:

  * Student ID
  * Name
  * Phone number
  * Parent/Guardian phone number
  * Age
  * Date of Birth
  * Email
* Prevents duplicate student IDs.
* Validates that all required fields are completed.

### ✏️ Student Management

* Edit existing student records.
* Remove students from the database.
* View complete student information.
* Double-click a student from the dashboard to view their details.

### 🟢 Attendance Tracking

* **Check In** students when they arrive.
* **Check Out** students when they leave.
* Automatically records the time of check-in and check-out.
* Prevents invalid repeated check-ins or check-outs.
* Displays the current attendance status.

### 🔎 Student Search

* Search students using their **ID or name**.
* Results update dynamically while typing.
* Student records are displayed in sorted ID order.

### 📅 Date of Birth Calendar

* Integrated Windows calendar control for selecting a student's date of birth.
* Automatically formats the selected date.

### 💾 Local Data Persistence

* Student information is stored locally in `student_data.txt`.
* Data is loaded automatically when the application starts.
* Changes are saved when records are modified.
* Provides a **Save & Exit** option.

### 🗑️ Database Reset

* Allows the administrator to clear all stored student records.
* Requires confirmation before deleting the database.

### 🖥️ Desktop UI

* Full-screen Windows desktop interface.
* Dark-themed dashboard.
* Sidebar-based navigation.
* Custom fonts, colors, controls, and owner-drawn student list.

---

## 🧠 How It Works

The application follows a simple management workflow:

```text
                    ┌──────────────┐
                    │ Admin Login  │
                    └──────┬───────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │   Main Dashboard  │
                 └─────────┬─────────┘
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
      Register           Search          Attendance
      Student           Student        Check In/Out
          │                │                │
          └────────────────┼────────────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ Student Records │
                  └────────┬────────┘
                           │
                           ▼
                  student_data.txt
```

## Student records are maintained in memory using a `vector<Student>` and synchronized with a local text file for persistence.

## 🛠️ Tech Stack

### Programming Language

* **C++**

### Windows Technologies

* **Win32 API**
* **Windows Common Controls**
* **Windows GUI**
* **Month Calendar Control**

### C++ Libraries

* `<vector>`
* `<string>`
* `<algorithm>`
* `<fstream>`
* `<ctime>`

### Data Storage

* Local text-file storage using `student_data.txt`.

---

## 📁 Project Structure

```text
Student-Tracker/
│
├── main.cpp
│
├── student_data.txt
│
└── README.md
```

> The exact project structure may vary depending on how the Visual Studio/MinGW project is organized.

---

## 📊 Student Data

Each student record contains:

```text
Student ID
Name
Phone
Parent/Guardian Phone
Age
Date of Birth
Email
Status
Last Check-In
Last Check-Out
```

The application maintains these fields through the `Student` data structure.

---

## ⚙️ Core Functionality

### Sorting

Students are automatically sorted by their ID before being displayed or saved.

```cpp
sort(students.begin(), students.end(),
    [](const Student& a, const Student& b) {
        return a.id < b.id;
    });
```

### Attendance

When a student checks in, their status is changed to:

```text
Present
```

and the current time is recorded.

When they check out, their status becomes:

```text
Checked Out
```

and the checkout time is recorded.

### Data Persistence

Student records are written to `student_data.txt` and loaded again when the application starts.

---

## 🖥️ Getting Started

### Prerequisites

You need a Windows development environment with a C++ compiler capable of building Win32 applications.

Recommended:

* Visual Studio with C++ Desktop Development
* Windows SDK

### Build & Run

1. Clone or download the repository.
2. Open the C++ project in Visual Studio.
3. Make sure the Windows SDK is installed.
4. Build the project.
5. Run the generated executable.

The project links against the Windows Common Controls library (`comctl32.lib`) for controls such as the calendar.

---

## 🎯 Project Objectives

The main objectives of Student Tracker Pro are:

* Simplify student record management.
* Provide a straightforward attendance tracking system.
* Reduce manual attendance management.
* Maintain student information in a structured format.
* Provide quick student search and retrieval.
* Demonstrate practical use of C++ with the Windows API.

---

## 🔒 Data & Security

The application uses local file storage for student information.

The administrator login provides a basic access-control mechanism for the application interface. Student records are stored locally rather than in a remote database.

---

## 📄 License

This project is intended for educational and project-development purposes.
