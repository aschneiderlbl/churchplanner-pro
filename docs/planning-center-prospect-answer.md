# Planning Center prospect answer pack

Prepared: 2026-10-20  
Status: Draft for review; not sent  
Related product card: [Planning Center integration](https://trello.com/c/2a93lO8z/8-integration-planning-center)  
Related marketing card: [Planning Center comparison](https://trello.com/c/oMRwHhV0/1-comparison-page-planning-center)

## Use this while the integration remains in Testing

Be direct about the current state. Do not describe the integration as production-ready until the [acceptance checklist](planning-center-integration-acceptance.md) has runtime evidence for connection, supported objects, first sync, repeat sync, failure recovery, disconnect, and tenant isolation.

## Short reply draft

Thanks for asking about Planning Center. ChurchPlannerPro is designed to help a small church run recurring administration in one place while keeping useful systems already in place.

Our Planning Center integration is currently in testing, so I do not want to overpromise its scope before we verify your exact workflow. The most useful next step is a short workflow review: which Planning Center products you use, which records or tasks need to move between systems, who owns the process today, and what a successful handoff would look like.

After that review, I can show you what the current build supports, what setup and migration help includes, and where a workaround or later phase would be required.

Would you be open to a 20-minute walkthrough of the workflow you most want to simplify?

## Optional pricing paragraph

ChurchPlannerPro is $9.99/month for software only or $39/month for Fully Managed with a dedicated support specialist working alongside your church. Both plans include setup, cleanup, import, and verification help. Specialist hours, unlimited labor, onsite coverage, and response times are not implied and should be scoped before purchase.

Canonical source: [current pricing](https://github.com/aschneiderlbl/hive/blob/main/product/pricing.md).

## Discovery checklist

Ask only what is needed to qualify the workflow:

1. Which Planning Center products are in use today?
2. Which workflow creates the most re-entry, cleanup, or follow-up work?
3. Which records or actions must move between Planning Center and ChurchPlannerPro?
4. Is one-way import sufficient, or is two-way behavior required?
5. Which system must remain the source of truth for each data type?
6. What would make the first 30 days successful?
7. What synthetic or test data can be used for a proof without exposing member information?

## Internal qualification gate

Before making a capability claim, record:

- tested ChurchPlannerPro build/commit;
- Planning Center test organization and test date;
- supported object and field list;
- sync direction and matching rules;
- result of reconnect, retry, and duplicate-prevention tests;
- known gaps and owner;
- privacy/security result, using synthetic data only.

## Review checklist

- [ ] Confirm the prospect’s actual Planning Center products and required workflow.
- [ ] Run only the relevant acceptance-checklist sections against a test organization.
- [ ] Remove claims not supported by evidence.
- [ ] Keep the integration described as **Testing** until the release gate passes.
- [ ] Have Andrew review the final prospect-specific reply before it is sent.
