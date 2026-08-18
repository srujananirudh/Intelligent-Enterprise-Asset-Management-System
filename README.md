# Intelligent Enterprise Asset Management System

A ServiceNow-based enterprise asset lifecycle management application for managing organizational assets, maintenance activities, asset requests, approvals, notifications, and management dashboards using rule-based automation.

> **Project Status:** Completed / Portfolio-Ready  
> **Platform:** ServiceNow Developer Instance (PDI)  
> **Application:** Intelligent Enterprise Asset Management System

---

## 1. Project Overview

Organizations manage large numbers of IT and enterprise assets such as laptops, desktops, servers, and networking devices. Tracking asset condition, risk, maintenance, requests, and allocation manually can lead to delayed maintenance, poor visibility, and inefficient asset management.

This project provides a centralized ServiceNow application for managing the asset lifecycle from registration and condition assessment through maintenance, requests, allocation, and reporting.

The system uses configured fields, business rules, and rule-based automation to support risk classification, maintenance prioritization, recommended actions, notifications, and workflow automation.

---

## 2. Objectives

- Centralize enterprise asset information in ServiceNow.
- Track asset condition, risk, confidence, cost, and lifecycle information.
- Implement rule-based asset risk and condition analysis.
- Automate maintenance-related processes using Flow Designer.
- Send risk-based maintenance notifications.
- Manage asset requests and approval processes.
- Automatically update an asset to **Allocated** when the related request is processed.
- Provide reports and dashboards for operational visibility.
- Demonstrate an end-to-end enterprise asset lifecycle management process.

---

## 3. Main Project Workflow

```text
Asset Registration
       |
       v
Asset Assessment
       |
       +----> Risk Score
       +----> Condition
       +----> Confidence
       +----> Damage Analysis
       +----> Suggested Action
       |
       v
Maintenance Management
       |
       +----> Risk-based Automation
       +----> Maintenance Notifications
       +----> Maintenance Completion
       |
       v
Asset Request
       |
       v
Approval / Processing
       |
       v
Requested Asset Lookup
       |
       v
Asset Status = Allocated
       |
       v
Reports & Dashboards
```

---

## 4. ServiceNow Data Model

### Asset

The Asset table stores enterprise asset information.

Important fields include:

- Asset Name
- Asset Number
- Serial Number
- Brand
- Model
- Category
- Cost
- Status
- AI Condition
- AI Confidence
- AI Risk Score
- Maintenance Priority
- Last Inspection
- Remarks

The project contains populated asset records representing different categories, conditions, and risk levels.

### Maintenance

The Maintenance table stores maintenance activities associated with assets.

Important fields include:

- Maintenance Number
- Maintenance Title
- Asset
- Maintenance Date
- Issue Type
- Status
- Cost
- Description
- Technician
- Reported By
- AI Damage Analysis
- AI Suggested Action
- Maintenance Priority
- Maintenance Recommendation

### Asset Request

The Asset Request table manages requests for enterprise assets.

Important information includes:

- Request Number
- Requested Asset
- Requester
- Request details
- Approval information
- Request status
- Request-related information

---

## 5. Rule-Based Asset and Maintenance Features

The project uses configured fields and rule-based logic to support asset and maintenance decision-making.

### Risk Score

Assets are classified into risk levels such as:

- High
- Medium
- Low

The risk classification is used by maintenance prioritization and notification workflows.

### Asset Condition

The system records the current condition of an asset, including values such as:

- Good
- Damaged

### Confidence

A confidence value is maintained alongside the asset assessment information.

### Damage Analysis

Maintenance records can store an analysis of the identified asset issue or damage.

### Suggested Action

The system stores a recommended action based on the available asset and maintenance information.

### Maintenance Priority

Maintenance activities can be categorized according to their priority, such as:

- Critical
- Medium
- Low

These values support maintenance monitoring and notification workflows.

---

## 6. Flow Designer Automation

The project contains multiple ServiceNow Flow Designer automations for asset and maintenance lifecycle management.

### Asset Enrichment Flow

Purpose:

- Trigger when an Asset record is created or updated.
- Evaluate configured asset information and rules.
- Update the appropriate asset assessment fields.

The flow was tested successfully.

### Asset Maintenance Intelligence Flow

Purpose:

- Evaluate asset maintenance and risk information.
- Apply the configured maintenance logic.
- Update relevant maintenance information.

The flow was tested successfully.

### Maintenance Risk Automation

Purpose:

- Trigger when a Maintenance record is created or updated.
- Evaluate the maintenance risk or priority.
- Process the appropriate risk-based branch.
- Update maintenance information.
- Trigger the relevant notification actions.

### High Risk Maintenance Notification

Purpose:

- Detect high-risk maintenance.
- Send a notification requiring immediate attention.
- Process the maintenance record accordingly.

High-risk testing was completed successfully.

### Medium and Low Risk Notifications

Separate notification logic is used for Medium and Low risk maintenance records.

These flows were configured and tested as part of the project implementation.

### Maintenance Completion Flow

```text
Maintenance Status = Completed
             |
             v
      Update Related Asset
```

This helps keep asset information synchronized after maintenance completion.

### Asset Request Approval Flow

```text
Asset Request Created / Updated
             |
             v
Requested Asset is not empty
             |
             v
Look Up Asset Record
             |
             v
Update Asset Record
Status = Allocated
```

The final flow test completed successfully.

---

## 7. Notifications

Risk-based notifications are used to communicate maintenance requirements.

### High Risk

Recommended action:

**Immediate maintenance required**

### Medium Risk

Recommended action:

**Schedule maintenance soon**

### Low Risk

Recommended action:

**Routine maintenance**

High, Medium, and Low risk notification scenarios were configured and tested by the project team.

---

## 8. Reports and Dashboard

The project includes a management dashboard containing visualizations for asset and maintenance monitoring.

Dashboard components include:

- Total Assets
- Assets by Risk Score
- Assets by Condition
- Maintenance Overview
- Maintenance by Issue Type
- Maintenance Priority

The dashboard provides a quick overview of asset distribution, risk levels, asset condition, and maintenance activity.

---

## 9. Testing and Validation

The application was validated through individual flow tests and end-to-end functional checks.

### Verified Components

- Asset enrichment flow
- Asset maintenance automation
- High-risk maintenance automation
- High-risk notification
- Medium-risk notification
- Low-risk notification
- Asset Request Approval Flow
- Asset records
- Maintenance records
- Dashboard visualizations

### Successful Asset Request Test

The Asset Request Approval Flow was tested successfully through:

```text
Trigger
  -> Look Up Asset Record
  -> Update Asset Record
```

After the flow execution, the related asset was successfully updated to:

**Status = Allocated**

---

## 10. Example Asset Scenarios

### High-Risk Asset

Example:

- Category: Networking Device
- Risk Score: High
- Condition: Damaged
- Status: Allocated after asset request processing

### Low-Risk Asset

Example:

- Category: Laptop
- Risk Score: Low
- Condition: Good
- Confidence: 0.9

These scenarios demonstrate that the system can manage assets with different conditions and risk levels.

---

## 11. Technology Stack

- **ServiceNow**
- **App Engine Studio**
- **Flow Designer**
- **ServiceNow Tables and Forms**
- **Business Rules**
- **Rule-Based Automation**
- **ServiceNow Reports**
- **ServiceNow Dashboards**

---

## 12. Key Benefits

- Centralized asset lifecycle management
- Improved asset visibility
- Automated maintenance workflows
- Risk-based maintenance prioritization
- Automated maintenance notifications
- Faster asset request processing
- Automatic asset allocation updates
- Management-level dashboard visibility
- Reduced manual tracking
- Structured asset and maintenance data management

---

## 13. Limitations

The current implementation primarily uses configured fields, business rules, and rule-based logic.

It does not claim to be a trained predictive machine-learning system. The project focuses on demonstrating practical ServiceNow application development, workflow automation, rule-based decision logic, notifications, reports, dashboards, and functional testing.

---

## 14. Future Enhancements

Possible future improvements include:

- Predictive maintenance using historical asset data
- Machine-learning-based failure prediction
- Integration with external monitoring or IoT systems
- Automated incident creation
- Advanced SLA tracking
- Asset depreciation and financial analytics
- More advanced role-based access controls
- Additional notification integrations
- REST API integrations with external asset management systems

---

## 15. Project Outcome

The completed application demonstrates an end-to-end enterprise asset lifecycle:

**Register → Assess → Classify Risk → Maintain → Notify → Request → Approve → Allocate → Monitor**

The project demonstrates practical experience with ServiceNow application development, data modeling, business rules, Flow Designer automation, rule-based decision logic, notifications, reports, dashboards, and functional testing.

---

## 16. Team Members and Responsibilities

### 1. [Srujan Anirudh](https://github.com/srujananirudh) — Core ServiceNow Development

- Initiated the project and established the overall ServiceNow application structure.
- Created the core application tables and main data model.
- Created and configured major Flow Designer automations.
- Worked on Asset, Maintenance, and Asset Request workflow logic.
- Implemented and tested the Asset Request Approval Flow.
- Contributed to overall application integration and functional validation.

### 2. [Pusuluri Sanmitha](https://github.com/Sanmitha2905) — Rule-Based Asset and Maintenance Automation

- Worked on rule-based asset and maintenance functionality.
- Configured Risk Score, Condition, Confidence, Damage Analysis, and Suggested Action fields.
- Worked on maintenance risk and priority logic.
- Configured and tested maintenance-related flows.
- Supported end-to-end functional testing and application validation.

### 3. [Nakka Dharani Goud](https://github.com/nakkadharanigoud) — Notifications, Reports and Dashboards

- Worked on risk-based maintenance notification workflows.
- Configured and tested High, Medium, and Low risk notification scenarios.
- Created ServiceNow reports and dashboard visualizations.
- Configured Total Assets, Risk Score, Asset Condition, Maintenance Overview, Issue Type, and Maintenance Priority visualizations.
- Performed dashboard validation and supported final project verification.
---
