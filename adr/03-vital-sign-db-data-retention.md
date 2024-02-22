# Vital Sign Database Data Retention

## Status

  - Proposed: 2/18/2024
  - Accepted: 2/19/2024

## Participants

  - Mike Wolford
  - Ryan Hertzog
  - Pete Pallo
  - Brandon Moriarty
  - Megin Mathew

## Context

  - Patient vital sign data can be requested for the past 24 hour time period.
  - Data should be retained longer than the 24 hour time period in order to allow for failures and recovery.

## Decision

  - Keep data in the system for at least 48 hours to help with recovery, failures, and delays with data processing.

## Consequences

  - A larger retention window than necessary allows for more analysis and reporting.
  - Extra data acts as a backup in case of unexpected issues within the initial 24 hour window..
  - It provides a safety net for critical reporting needs.
  - There will be additional storage overhead which will result in additional infrastructure cost.
  - Older data is less relevant over time and will not be as valuable for any real time analysis and reporting needs.

