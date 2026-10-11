# Master Prompt — Future GRE Mock Test Portal

Build a polished, production-ready browser-based GRE mock-test web portal called **GRE Mock Test Lab**.

## 1. Goal

Create a simple, fast, responsive web application for GRE General Test practice. The portal should focus on Verbal Reasoning and Quantitative Reasoning and should be easy for students to use on desktop and mobile.

Do NOT include Analytical Writing in the test flow.

The product must be structured so that the front end, question bank, scoring/reporting, and backend can later be maintained independently.

## 2. GRE test structure

Use these module timings and question counts:

### Verbal
- Section/Module 1: 12 questions, 18 minutes
- Section/Module 2: 15 questions, 23 minutes

### Quant
- Section/Module 1: 12 questions, 21 minutes
- Section/Module 2: 15 questions, 26 minutes

A full mock therefore contains:
- 27 Verbal questions
- 27 Quant questions
- 54 total questions
- 88 total minutes

The student must be able to choose:
1. Full Mock
2. Verbal Only
3. Quant Only

The implementation should preserve the module sequence and timing for the selected mode.

## 3. Mock-test library

Provide at least 60 mock-test/set choices.

Each mock should have:
- Mock number
- Title
- Verbal modules
- Quant modules
- Mixed difficulty
- Topic metadata
- Question IDs
- Explanations
- Correct answer
- Question type

Do not claim that template-generated questions are production-ready. For a production release, every question must be individually reviewed and validated.

## 4. Question types

Support:
- Single-answer multiple choice
- Multiple-select questions
- Numeric-entry questions
- Quantitative Comparison if appropriate
- Text Completion
- Sentence Equivalence
- Reading Comprehension

The data model should make it easy to add future question types without rewriting the test engine.

## 5. Student test interface

Create a clean ETS-inspired practice interface without copying ETS branding or proprietary UI.

Required features:
- Visible countdown timer
- Pause/resume
- Current module indicator
- Question number
- Progress indicator
- Previous/Next
- Question navigator
- Mark for review
- Answered/unanswered status
- Confirmation before submitting
- Automatic submission when time expires
- Responsive layout
- Keyboard-friendly controls
- Accessible labels and focus states

## 6. Quant calculator

Provide a basic on-screen calculator for Quant modules.

It should support:
- +, −, ×, ÷
- decimal numbers
- parentheses
- clear
- backspace
- equals

Do not use unsafe unrestricted JavaScript evaluation for calculator input in the production version. Use a safe expression parser or controlled calculation engine.

## 7. Results and explanations

After a module:
- Show number correct
- Show accuracy
- Show topic performance
- Show questions requiring review
- Show correct answer
- Show the student's answer
- Show explanation
- Show difficulty

After the full mock:
- Show combined performance
- Show Verbal performance
- Show Quant performance
- Show topic weaknesses
- Show recommended areas for practice

Do not present raw accuracy as an official GRE scaled score.

## 8. Cumulative analytics

Provide a cumulative report across completed mocks.

Include:
- Tests completed
- Total questions attempted
- Total correct
- Overall accuracy
- Verbal accuracy
- Quant accuracy
- Topic-level accuracy
- Weakest topics
- Recent test history
- Progress over time

If charts are used, keep them simple and readable.

## 9. Future backend architecture

The previous simple Google Apps Script/Google Sheets approach was useful for learning, but the future production version should avoid putting authentication and business logic into a fragile client-side/static layer.

Use a proper architecture such as:
- Front end: React/Next.js or clean HTML/CSS/JavaScript
- Backend API: secure server-side application
- Database: PostgreSQL or another reliable relational database
- Authentication: secure server-side/session-based authentication
- Authorization: protected admin routes
- Hosting: GitHub Pages/Cloudflare/Vercel for front end plus a suitable backend service

Keep secrets, passwords, API keys, and admin credentials off the client.

## 10. User/admin system for the future version

The current GitHub package intentionally excludes all user/admin functionality.

When authentication is added later:
- Login required
- Admin can create student accounts
- Admin can reset student passwords
- Students can update profile information
- Students cannot change their own password if that is the chosen product rule
- Admin dashboard is protected server-side
- Passwords must be securely hashed
- Never hard-code real credentials into HTML/JavaScript
- Never store plaintext passwords in localStorage

## 11. Question bank requirements

For a real launch, create a structured question bank rather than hard-coding questions into one HTML file.

Suggested fields:
- question_id
- mock_id
- section
- module
- question_number
- question_type
- topic
- subtopic
- difficulty
- prompt
- options
- correct_answer
- explanation
- source/review status
- version
- active flag

Every question should be:
- individually authored or properly licensed
- checked for correctness
- checked for ambiguity
- checked for formatting
- checked for duplicate concepts
- reviewed for GRE-appropriate difficulty

Do not copy ETS questions or copyrighted material.

## 12. Branding

Use the name:
**GRE Mock Test Lab**

Include a small disclaimer:
**Independent practice platform · not affiliated with ETS**

Every page should include:
**please contact Velox Dynamics (+88-01611-599922) for any queries**

## 13. UX style

Keep the interface:
- professional
- clean
- academic
- fast
- responsive
- low-clutter
- easy for first-time users

Avoid unnecessary animations.

Prioritize:
1. readable questions
2. clear timer
3. easy navigation
4. reliable saving
5. clear explanations
6. useful reports

## 14. Data safety

Do not expose:
- passwords
- API keys
- database credentials
- admin credentials
- private student data

Do not rely on localStorage for production authentication.

LocalStorage may be used only for harmless temporary UI state or an explicitly offline/demo mode.

## 15. Testing requirements

Before delivery, test:
- login/authentication if enabled
- every mock mode
- timer accuracy
- automatic submission
- pause/resume
- question navigation
- marked questions
- unanswered questions
- multi-select scoring
- numeric scoring
- calculator
- module transitions
- final reports
- cumulative reports
- mobile layout
- refresh/reload behavior
- backend failure handling
- unauthorized admin access

## 16. Important lessons from the prototype

The earlier prototype taught these implementation lessons:

1. Keep the front-end test engine separate from authentication.
2. Do not mix a static web app with insecure client-side admin credentials.
3. If using Google Apps Script, be careful with spreadsheet ranges when a sheet has only headers or no data rows.
4. Functions that search for rows must return a safe "not found" value and callers must check it before calling `getRange`.
5. Deployment changes require publishing a new version.
6. Multiple Google accounts in one browser can make Apps Script testing confusing; use a clean/incognito session when necessary.
7. A web app URL ending in `/exec` is the deployed web app; `/macros/library/` is not the portal.
8. Keep the initial version simple and verify each layer before adding another layer.

## 17. Deliverables

Produce:
- Complete source code
- Clear folder structure
- README
- Setup instructions
- Environment variable example if needed
- Database schema/migrations
- Seed/demo data
- Test instructions
- Deployment instructions

The final product should be maintainable by a non-expert developer and should avoid unnecessary infrastructure complexity.

Start by building the clean front-end test engine first. Then add the database. Then add authentication/admin functionality. Then add analytics and production hardening.
