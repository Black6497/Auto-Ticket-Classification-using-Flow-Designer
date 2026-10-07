# Auto Ticket Classification using Flow Designer

**Team ID:** SWTID-2026-7310 | **Team Size:** 5

| Role | Name |
|------|------|
| Team Leader | Mohan Kumar S |
| Team Member | Muhammed Ibrahim A |
| Team Member | Ponakilan J |
| Team Member | Pradeep B |
| Team Member | Ragulprathap R |

## Overview
The school IT helpdesk receives many incident requests every day from students and teachers: Wi-Fi issues, projector failures, password problems and slow computers. IT staff used to read every ticket and assign the category by hand, which was slow and error-prone.

This project automates ticket classification with **ServiceNow Flow Designer**. When a ticket is created, the flow reads the keywords in the *Short description*, sets the **Category** and **Subcategory**, and emails the caller a confirmation. The solution is **no-code** and easy to maintain.

## Objectives
- Automatically classify incidents at the time of creation.
- Reduce manual effort for IT agents.
- Improve ticket routing efficiency.
- Implement a no-code, easily maintainable solution.

## How It Works
1. The caller creates a ticket in the custom table **Incident WorkFlow** (`u_incident_workflow`) and enters only the Caller and Short description.
2. The flow **Auto Classify School IT Tickets** starts when a record is created and Category is empty.
3. If / Else-If conditions check the Short description and update the record:

| Keyword in Short description | Category | Subcategory |
|------------------------------|----------|-------------|
| Wi-Fi / Network | Network | Wi-Fi |
| Projector | Hardware | Projector |
| Forgot password | Access | Forgot Password |
| Slow computer | Performance | Slow Computer |

4. A **Send Email** action notifies the caller: *"Your Request for the issue has been submitted."*

## Technology
- ServiceNow (Global application scope)
- Flow Designer (trigger, If / Else-If, Update Record, Send Email)
- Form Designer, custom table with auto-number (INC prefix), dependent choice fields (Category to Subcategory)
- Update Set: `Project Update Set`, exported as XML

## Project Documentation
The documents are organised phase by phase:

| Phase | Contents |
|-------|----------|
| 1. Ideation Phase | Problem statements, Empathy map, Brainstorming and prioritization |
| 2. Requirement Analysis | Customer journey map, Solution requirements, Data flow diagram and user stories, Technology stack |
| 3. Project Design Phase | Problem-solution fit, Proposed solution, Solution architecture |
| 4. Project Planning Phase | Product backlog, sprint plan, velocity, burndown chart |
| 5. Project Development Phase | Functional and performance testing, UAT test sheet, UAT report |
| 6. Project Documentation | Final project report (DOCX and PDF) |

## Testing Summary
- Network / Wi-Fi ticket classified as Network > Wi-Fi.
- Projector ticket classified as Hardware > Projector.
- Confirmation emails verified in System Logs > Emails.
- Auto-numbers generated without duplication.

## Deployment
1. In ServiceNow, open **System Update Sets > Local Update Sets** and open *Project Update Set*.
2. Set the State to **Complete** and save.
3. Under Related Links choose **Export to XML**.
4. On the target instance, import the XML from **Retrieved Update Sets**, then preview and commit it.

## Future Scope
- Automatic assignment group and agent based on category.
- More keywords and issue types.
- SLA tracking and escalation.
- Chatbot intake and SMS / Teams notifications.
- Predictive intelligence or an ML classifier.

## Conclusion
The project delivers an end-to-end, no-code automation for a school IT helpdesk. It cuts manual categorisation, keeps ticket data consistent and acknowledges every ticket instantly.
