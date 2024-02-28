## this is sql task 2

## database design

![ ](/Sql%20task%202.png)

## query for creating this database

-- Create a database
CREATE DATABASE StudentManagementDatabase;
USE StudentManagementDatabase;

-- Create tables
CREATE TABLE Students (
StudentID INT PRIMARY KEY,
FirstName VARCHAR(255),
LastName VARCHAR(255),
Email VARCHAR(255),
DateOfBirth DATE,
PhoneNumber INT,
PaymentStatus VARCHAR(50),
PortalAccessStatus VARCHAR(50),
);

CREATE TABLE Courses (
CourseID INT PRIMARY KEY,
CourseName VARCHAR(255),
Description TEXT
);

CREATE TABLE Enrollments (
EnrollmentID INT PRIMARY KEY,
StudentID INT,
CourseID INT,
EnrollmentDate DATE,
Feedback TEXT,
SessionRatingStatus VARCHAR(50),
MentorRatingStatus VARCHAR(50),
FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)

);

CREATE TABLE Portals (
PortalID VARCHAR(50) PRIMARY KEY,
Location VARCHAR(255),
Status VARCHAR(50)
);

CREATE TABLE Sessions (
SessionID INT PRIMARY KEY,
CourseID INT,
StartDate DATE,
StartTime TIME,
Status VARCHAR(50),
FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

CREATE TABLE Tasks (
TaskID INT PRIMARY KEY,
CourseID INT,
Title VARCHAR(255),
Description TEXT,
EndDate DATE,
EndTime TIME,
Status VARCHAR(50),
FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

CREATE TABLE Submissions (
SubmissionID INT PRIMARY KEY,
TaskID INT,
StudentID INT,
SubmissionDate DATE,
Resources TEXT,
Status VARCHAR(50),
FOREIGN KEY (TaskID) REFERENCES Tasks(TaskID),
FOREIGN KEY (StudentID) REFERENCES Students(StudentID)
);

CREATE TABLE MockInterviews (
MockInterviewID INT PRIMARY KEY,
StudentID INT,
SessionID INT,
Status VARCHAR(50),
SessionDate DATE,
Location VARCHAR(255),
FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
FOREIGN KEY (SessionID) REFERENCES Sessions(SessionID)
);

CREATE TABLE PlacementPreparation (
PreparationID INT PRIMARY KEY,
StudentID INT,
TaskID INT,
Status VARCHAR(50),
FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
FOREIGN KEY (TaskID) REFERENCES Tasks(TaskID)
);

CREATE TABLE Instructors (
InstructorID INT PRIMARY KEY,
Name VARCHAR(255)
);

CREATE TABLE InstructorTasks (
InstructorTaskID INT PRIMARY KEY,
InstructorID INT,
TaskID INT,
CourseID INT,
Status VARCHAR(50),
FOREIGN KEY (InstructorID) REFERENCES Instructors(InstructorID),
FOREIGN KEY (TaskID) REFERENCES Tasks(TaskID),
FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

CREATE TABLE Projects (
ProjectID INT PRIMARY KEY,
StudentID INT,
CourseID INT,
Title VARCHAR(255),
Description TEXT,
Status VARCHAR(50),
FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
