Here are all the command lines for PT Creation Orchestrator v1.5:

Phase 1: Planning & Prototype Creation
/start

Initialize session and request:
{{PT_REQUEST_DOC}}, {{TASK_TITLE}}, {{TARGET_AUDIENCE}}, {{SKILLS_LIST}}.

/run format_request

Format {{PT_REQUEST_DOC}} into HTML using [PROMPT: HTML_FORMATTER].

/run identify_prototypes

Analyze request doc, group questions into prototypes, and initialize Master Creation Log.

Output: TSV table of mappings.

/run create_prototypes

Interactive: Requests {{EXISTING_PT_SAMPLES}} (or "none").

Generates XML for prototypes using [PROMPT: CREATE_PROTOTYPES].

Updates log with GeneratedXML.

Output: Sanitized TSV code block of all prototypes (newlines/tabs escaped as \\n/\\t).

Phase 2: Finalization & Iteration
/add pt_ids

Update NewlyCreatedPT_ID fields in the log with backend IDs.

/run create_remaining_pts

Generates XML for non-prototypes using [PROMPT: CREATE_REMAINING_PTS].

Updates log with GeneratedXML.

Output: Sanitized TSV code block of all remaining PTs.

/update_xml [QuestionID]

Overwrites GeneratedXML for a specific question.

Example: /update_xml New1 prompts for new XML.

/revise [QuestionID]

Edits XML for a question based on user instructions.

Example: /revise New2 prompts for revision details.

/get_xml [QuestionID]

Displays raw XML for a single question.

Example: /get_xml New3.

/show_log

Displays log summary in TSV format:
Question ID | Prototype? | Mapped To | NewlyCreatedPT_ID.

/help

Lists all commands.

