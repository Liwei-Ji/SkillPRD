# PRD-to-Jira Automation

This directory contains specialized instruction sets for automating the transition from **SkillPRD** content to Jira.

## Contents
- **[SKILL.md](SKILL.md)**: The core automation protocol. It identifies product definitions and development tasks within a PRD and converts them into Jira API-compatible JSON format.

## Workflow
1. **Generate PRD**: Use the root `SKILL.md` to produce a complete Standard PRD (Style 1).
2. **Initialize Automation**: Open a new AI session and load `automation/SKILL.md`.
3. **Provide Input**: Paste the PRD content generated in step 1.
4. **Get Payload**: The AI will output a JSON code block compatible with the Jira `bulk create` format.
5. **Import to Jira**: Import the JSON via Jira API, automation scripts (e.g., Python), or supported third-party plugins.

## Mapping Structure
- **Epic**: Corresponds to the PRD's Product Overview.
- **Story**: Corresponds to the PRD's User Stories.
- **Sub-task**: Corresponds to the PRD's Functional Requirements.

---

## Implementation Guide (Quick Integration)

Once you have the JSON payload, you can import it into Jira using the following `curl` command:

```bash
curl --request POST \
  --url 'https://your-domain.atlassian.net/rest/api/2/issue/bulk' \
  --user 'your-email@example.com:<your_api_token>' \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --data-raw '<PASTE_AI_GENERATED_JSON_HERE>'
```

### Reference
- [Official Jira Cloud API: Bulk Create Issues](https://developer.atlassian.com/cloud/jira/platform/rest/v2/api-group-issues/#api-rest-api-2-issue-bulk-post)
- [How to generate an API Token](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/)
