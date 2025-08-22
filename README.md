The Bank Loan Management System automates the end-to-end lifecycle of loan processing—from customer onboarding and product setup to application approval, repayment tracking, and reporting.
It supports multiple loan types including:
Personal Loans
Home Loans
Vehicle Loans
This system is ideal for banks and financial institutions seeking a robust backend solution for managing loan workflows efficiently.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Core Modules
Module	Description
Customer Management	Handles customer registration, KYC verification, and account maintenance.
Loan Product Management	Manages loan offerings, interest rates, tenures, and eligibility criteria.
Loan Application	Facilitates loan application workflows, approvals, and status tracking.
Repayment Management	Automates repayment schedules, tracks payments, and calculates balances.
Reporting & Auditing	Generates loan statistics, repayment summaries, and customer portfolios.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Tech Stack
Backend: Java (Spring MVC) / ASP.NET Core MVC
Database: MySQL / SQL Server
Architecture: MVC
Tools: Maven, Visual Studio, Tomcat, Kestrel
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Database Schema Highlights
-- Customer Table
CREATE TABLE Customer (
  customerid INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100),
  phone VARCHAR(15),
  address TEXT,
  kycStatus ENUM('PENDING', 'VERIFIED')
);
-- LoanProduct Table
CREATE TABLE LoanProduct (
  loanProductid INT AUTO_INCREMENT PRIMARY KEY,
  productName VARCHAR(50),
  interestRate DECIMAL(5,2),
  minAmount DECIMAL(10,2),
  maxAmount DECIMAL(10,2),
  tenure INT
);
-- LoanApplication Table
CREATE TABLE LoanApplication (
  applicationid INT AUTO_INCREMENT PRIMARY KEY,
  customerid INT,
  loanProductid INT,
  loanAmount DECIMAL(10,2),
  applicationDate DATE,
  approvalStatus ENUM('PENDING', 'APPROVED', 'REJECTED'),
  FOREIGN KEY (customerid) REFERENCES Customer(customerid),
  FOREIGN KEY (loanProductid) REFERENCES LoanProduct(loanProductid)
);
-- Repayment Table
CREATE TABLE Repayment (
  repaymentid INT AUTO_INCREMENT PRIMARY KEY,
  applicationid INT,
  dueDate DATE,
  amountDue DECIMAL(10,2),
  paymentDate DATE,
  paymentStatus ENUM('PENDING', 'COMPLETED'),
  FOREIGN KEY (applicationid) REFERENCES LoanApplication(applicationid)
);
---------------------------------------------------------------------------------------------------------------------
Local Deployment Guide
🔧 Environment Setup
Install MySQL or SQL Server
Install Java JDK or .NET SDK
Configure DB credentials in application.properties or appsettings.json
---------------------------------------------------------------------------------------------------------------------
Steps to run 
# Clone the repository
git clone https://github.com/your-username/bank-loan-management-system.git
# For Java (Spring MVC)
mvn clean install
Run on Tomcat → http://localhost:8080
# For ASP.NET Core
Open in Visual Studio
Run on Kestrel → http://localhost:5000
------------------------------------------------------------------------------------------------------------------------
Reporting Features
Loan performance dashboards
Repayment status summaries
Outstanding loan reports
Customer portfolio insights
--------------------------------------------------------------------------------------------------------------------------
Conclusion:
This project delivers a comprehensive backend solution for loan lifecycle management in the BFSI domain. 
Its modular design ensures maintainability, scalability, and ease of integration with existing systems—making it a valuable tool for modern banking operations.
---------------------------------------------------------------------------------------------------------------------------
