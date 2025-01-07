CREATE TABLE Locations (
    LocationID INT PRIMARY KEY AUTO_INCREMENT,
    City VARCHAR(100),
    State VARCHAR(100),
    Country VARCHAR(100)
);

CREATE TABLE Patients (
    PatientID INT PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    DateOfBirth DATE,
    Gender VARCHAR(10),
    PhoneNumber VARCHAR(15),
    LocationID INT,
    FOREIGN KEY (LocationID) REFERENCES Locations(LocationID)
);

CREATE TABLE Facilities (
    FacilityID INT PRIMARY KEY AUTO_INCREMENT,
    FacilityName VARCHAR(100),
    Address VARCHAR(255),
    PhoneNumber VARCHAR(15)
);

CREATE TABLE Visits (
    VisitID INT PRIMARY KEY AUTO_INCREMENT,
    PatientID INT,
    FacilityID INT,
    VisitDate DATE,
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID),
    FOREIGN KEY (FacilityID) REFERENCES Facilities(FacilityID)
);

CREATE TABLE GitHubRepositories (
    RepoID INT PRIMARY KEY AUTO_INCREMENT,
    PatientID INT,
    RepoName VARCHAR(255) NOT NULL,
    RepoURL VARCHAR(2083) NOT NULL,
    Description TEXT,
    CreatedAt DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID)
);
