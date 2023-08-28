# Project Proposal App
Daml templates designed to manage the interaction of an employer, employees and applicants to the company.

## I. Overview
Applicants can fill up applications and interact with the employer to agree with a salary. Employees can request vacation and the employer desides to approve the request or not. Employer can fire employees.
- Templates are located in `daml/Employees.daml`
- Test script are located in `daml/Test.daml`
- Initialization scripts for test are in `daml/PartiesSetUp.daml`
- Initialization for navigator is in `daml/Main.daml`

## II. Workflow

### Employer and applicants interaction
1. An applicant has a new employee application. Applicant is signatory and employer is observer. Applicant can exercise the choice EditApplicationInformation to edit the personal information of the applicant.
2. Employer makes an offer (indicates the salary) to the applicant.
3. Applicant can either accept the offer or make a counter offer.
4. If applicant makes a counter offer, employer can either accept the counter offer or make a new offer.
5. If employer makes a new offer, applicant can either accept the offer or make a counter offer.
6. If applicant accepts the new offer, then the employer can review and accept the application which means that an employee account is created by the employer. This employer account will have the personal information of the applicant.

### Employer and employee interaction
1. An employee can request vacation.
2. Employer can either deny the vacation request or accept it.
3. If it is accepted, then the employee's account will have True in its onVacation, otherwise it will have False.
For the test scripts there an auxiliary function that reviews if there will be other employees available if the vacation request is accepted. If there would be at least one more employee available, then the vacation request will be accepted.

[Video working project](https://youtu.be/fynFx02APDQ)

## III. Testing
To test all scripts:
Run:
```
$ daml start
```
which will run the prewritten scripts in `Test.daml`

## IV. Running
To load the project into the sandbox and start navigator:
```
$ daml start
```