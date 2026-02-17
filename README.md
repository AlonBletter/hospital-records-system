# Hospital Records System

A C++ project for managing hospital-related records, including doctors, researchers, and institutional data.

## Overview

This project provides a simple system for storing and managing hospital information. It demonstrates object-oriented design, data management, and structured record handling in C++.

The system is designed to model relationships between hospital entities such as medical staff and research personnel.

## Features

* Management of hospital records
* Doctor and researcher data handling
* Object-oriented design
* Structured data representation

## Purpose

This project was created for learning and demonstrating software design principles, data modeling, and C++ development practices.


## Class diagram

```mermaid
classDiagram
direction LR

class Hospital {
  -ResearchInstitute m_researchInstitute
  -set_Department m_departments
  -set_Patient m_patients
  -set_Employee m_employees
  +addDepartment(department_name)
  +addEmployee(employee, department_name)
  +addEmployee(researcher)
  +addPatient(patient, department_name)
  +searchDepartment(name) Department
  +searchPatient(patient_id) Patient
  +searchEmployee(employee_id) Employee
  +saveHospital(filename)
  +loadHospital(filename)
  +showEmployees()
  +showResearchers()
  +showDoctorResearchers()
  +showPatientByID(id)
}

class ResearchInstitute {
  -set_Researcher m_researchers
  -Hospital m_hospital
  -int m_pureResearchers
  +getAllResearchers()
  +searchResearcher(researcher_id) Researcher
  +showResearchers()
  +showDoctorResearchers()
  -addResearcher(researcher)
}

class Department {
  +addEmployee(emp)
  +loadDepartment(inFile)
  +setHospital(hospital)
}

class Employee {
  +getEmployeeId() int
  +clone() Employee
}

class Patient
class Nurse
class Doctor
class Surgeon
class Researcher
class DoctorResearcher
class SurgeonResearcher

Employee <|-- Nurse
Employee <|-- Doctor
Doctor <|-- Surgeon

Researcher <|-- DoctorResearcher
Surgeon <|-- SurgeonResearcher
DoctorResearcher <|-- SurgeonResearcher

class VisitCard
class SurgeonCard
class Article
class Date

VisitCard o-- Date
SurgeonCard o-- Date
Researcher "1" o-- "*" Article : writes

Hospital *-- ResearchInstitute
Hospital "1" *-- "*" Department
Hospital "1" *-- "*" Patient
Hospital "1" *-- "*" Employee

Department "1" --> "1" Hospital
Department "1" o-- "*" Patient
Department "1" o-- "*" Employee

ResearchInstitute "1" --> "1" Hospital
ResearchInstitute "1" o-- "*" Researcher

VisitCard --> Doctor
SurgeonCard --> Surgeon
```
