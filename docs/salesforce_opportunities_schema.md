# Salesforce Opportunities Schema Documentation

## Overview
The Salesforce Opportunities schema defines the structure and properties of opportunity records within Salesforce. Each opportunity represents a potential revenue-generating event.

## Field Descriptions
| Field Name         | Description                                                                 | Field Category           |
|--------------------|-----------------------------------------------------------------------------|--------------------------|
| Id                 | Unique identifier for the opportunity.                                      | System                   |
| Name               | The name of the opportunity.                                               | Required                 |
| StageName         | The current stage of the opportunity (e.g. Proposal, Negotiation).        | Required                 |
| CloseDate         | The date by which the opportunity is expected to close.                   | Required                 |
| Amount             | The total amount expected from the opportunity.                            | Required                 |
| AccountId         | The Id of the account associated with the opportunity.                    | Reference                |
| OwnerId           | The Id of the user who owns the opportunity.                              | Reference                |
| Probability        | The probability of closing the opportunity, expressed as a percentage.    | Optional                 |
| LeadSource        | The source of the lead for this opportunity (e.g. Web, Referral).        | Optional                 |
| Description        | A brief description of the opportunity.                                    | Optional                 |
| Type               | The type of opportunity (e.g. New Business, Existing Business).           | Optional                 |
| CreatedDate       | The date the opportunity record was created.                              | System                   |
| LastModifiedDate   | The date the opportunity record was last modified.                        | System                   |
| IsClosed           | Indicates whether the opportunity is closed.                               | System                   |
| IsWon             | Specifies whether the opportunity has been won.                           | System                   |

## Categories
- **Required**: Essential fields that must have a value for the record to be valid.
- **Optional**: Fields that can enhance the record but are not mandatory.
- **System**: Fields managed by Salesforce automatically for record tracking and management.
- **Reference**: Fields that indicate relationships with other records in Salesforce.