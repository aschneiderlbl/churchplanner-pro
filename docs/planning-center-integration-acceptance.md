# Planning Center integration acceptance checklist

Source card: [Planning Center integration](https://trello.com/c/2a93lO8z/8-integration-planning-center)  
Status on 2026-10-19: Testing  
Prepared: 2026-10-19

## Definition of done

The integration is ready to leave Testing when a church administrator can connect a Planning Center account, complete a documented first sync, understand exactly which data moved, recover from expected failures, and disconnect safely without support intervention or hidden data loss.

This checklist deliberately separates verified behavior from positioning copy. The marketing claim should not run ahead of the product.

## Test setup

- Use a dedicated Planning Center test organization and a ChurchPlannerPro demo church.
- Seed at least:
  - two households;
  - five people, including one duplicate candidate and one person missing an email address;
  - one archived/inactive record if the integration supports it;
  - one record changed after the initial sync.
- Record the tested ChurchPlannerPro build/commit and Planning Center environment/date.
- Do not use real member, giving, child, health, pastoral-care, or credential data in screenshots or bug reports.

## Acceptance matrix

### 1. Connection and consent

- [ ] Connection starts from the expected ChurchPlannerPro screen.
- [ ] The administrator sees which Planning Center organization will be connected.
- [ ] Requested permissions are the minimum needed for the implemented workflow.
- [ ] Canceling authorization leaves no partial connection.
- [ ] A successful connection returns to ChurchPlannerPro with a clear success state.
- [ ] Expired/revoked authorization produces a useful recovery path.

### 2. First sync

- [ ] The UI states which object types are supported.
- [ ] The first sync imports only those supported object types.
- [ ] Counts shown before/after sync reconcile with source records or explain exclusions.
- [ ] Household/person relationships remain intact where supported.
- [ ] Blank optional fields do not fail the entire sync.
- [ ] Archived/inactive records follow a documented rule.
- [ ] A duplicate candidate is handled by a documented matching rule, not silently duplicated.

### 3. Repeat sync and idempotency

- [ ] Re-running a sync without source changes creates no duplicate records.
- [ ] A source update changes the intended ChurchPlannerPro record once.
- [ ] Conflict behavior is documented when both systems changed the same field.
- [ ] A failed batch can be retried without duplicating previously successful records.
- [ ] The UI shows last successful sync time and the result of the latest attempt.

### 4. Errors and recovery

- [ ] Rate limiting/backoff does not create duplicate jobs or records.
- [ ] A single malformed record is isolated and identified without hiding other successes.
- [ ] Network interruption produces a retryable state.
- [ ] Error copy gives the administrator a next action.
- [ ] Logs contain stable record/job identifiers but no access tokens or unnecessary personal data.
- [ ] Support can distinguish configuration, permission, source-data, and product defects.

### 5. Disconnect and reconnect

- [ ] Disconnect requires explicit confirmation.
- [ ] The UI explains what happens to previously imported data.
- [ ] Tokens are revoked/deleted as designed.
- [ ] A reconnect to the same organization resumes without duplication.
- [ ] Connecting a different organization cannot silently merge it into the existing church.

### 6. Security and privacy

- [ ] Tokens never appear in browser-visible logs, analytics, screenshots, or error text.
- [ ] Stored credentials use the platform’s approved secret storage.
- [ ] Access is scoped to the correct ChurchPlannerPro tenant.
- [ ] An administrator can identify who connected/disconnected the integration and when.
- [ ] Data retention/deletion behavior matches the product’s privacy commitments.

### 7. Admin experience and support

- [ ] Setup instructions match the current UI.
- [ ] Supported and unsupported fields are documented.
- [ ] The administrator can tell whether the integration is healthy without opening developer tools.
- [ ] The Help Center includes connect, first-sync, troubleshooting, disconnect, and support-escalation steps.
- [ ] Screenshots use synthetic data and match the current product.

## Go/no-go gate

Move the card out of Testing only when:

1. all connection, first-sync, idempotency, disconnect, and security checks pass;
2. any unsupported objects/fields are documented in-product or in the Help Center;
3. no open defect can create cross-tenant access, token exposure, silent record loss, or uncontrolled duplication;
4. support has a reproducible escalation packet; and
5. the marketing language is limited to the behavior actually verified.

## Evidence packet

For each failed check, capture:

- test date and build/commit;
- source and destination object identifiers (synthetic/test data only);
- expected vs. actual behavior;
- screenshot or short recording;
- relevant correlation/job identifier;
- retry result;
- severity and owner.

## Current blocker / next owner

**Needs human/product access:** run this checklist against the current integration build and test organization. Static repository and Trello review can define the gate but cannot verify runtime data behavior.

**Andrew/product owner:** identify the current build and test organization, then assign the checklist run.  
**Assistant after evidence is available:** convert results into a pass/fail report and a prioritized defect list.
