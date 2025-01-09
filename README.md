-- Create the Agents table
CREATE TABLE Agents (
    AgentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    ContactNumber VARCHAR(15) UNIQUE NOT NULL,
    CommissionRate DECIMAL(5,2) CHECK (CommissionRate > 0)
);

-- Create the Clients table
CREATE TABLE Clients (
    ClientID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    ContactNumber VARCHAR(15) UNIQUE NOT NULL,
    Email VARCHAR(100) UNIQUE NOT NULL,
    Preferences TEXT
);

-- Create the Transactions table
CREATE TABLE Transactions (
    TransactionID INT PRIMARY KEY,
    PropertyID INT NOT NULL,
    AgentID INT NOT NULL,
    ClientID INT NOT NULL,
    TransactionType VARCHAR(10) CHECK (TransactionType IN ('Buy', 'Sell', 'Rent')),
    Date DATE NOT NULL,
    Amount DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (PropertyID) REFERENCES Properties(PropertyID) ON DELETE CASCADE,
    FOREIGN KEY (AgentID) REFERENCES Agents(AgentID) ON DELETE CASCADE,
    FOREIGN KEY (ClientID) REFERENCES Clients(ClientID) ON DELETE CASCADE
);

-- Create the Properties table
CREATE TABLE Properties (
    PropertyID INT PRIMARY KEY,
    Address VARCHAR(255) NOT NULL,
    Type VARCHAR(50) NOT NULL,
    Price DECIMAL(10,2) NOT NULL,
    AgentID INT NOT NULL,
    FOREIGN KEY (AgentID) REFERENCES Agents(AgentID) ON DELETE CASCADE
);
