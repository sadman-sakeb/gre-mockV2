# GRE Mock Test Lab

A browser-based GRE Verbal + Quant practice portal built as a static HTML application.

## Current package

This GitHub-ready version intentionally contains **no user login, password, admin panel, profile system, or backend authentication**.

It is designed as a front-end prototype that can be published easily with GitHub Pages.

### Included features

- 60 practice mock-test tiles
- GRE-style Verbal and Quant practice flow
- Timed modules
- Pause/resume timer
- Question navigator
- Mark-for-review
- Basic Quant calculator
- Module reports
- Explanations for reviewed questions
- Topic-level diagnostic feedback
- Cumulative browser-local history
- Responsive desktop/mobile layout
- Required Velox Dynamics contact footer

## Important limitation

The current question bank is prototype/demo content generated from templates. It should **not** be treated as a production GRE question bank until every item has been individually authored, reviewed, validated for correctness, and checked for originality/copyright.

The app also produces practice diagnostics, not official ETS scaled scores or percentiles.

## Publish on GitHub Pages

1. Create a new GitHub repository.
2. Upload `index.html` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and `/ (root)`.
6. Save.
7. GitHub will provide the public Pages URL.

## Next development phase

When you are ready to build the full production portal, add a real backend/authentication layer separately. Do not put passwords or admin credentials in this static HTML file.

Recommended architecture for a future version:
- Front end: HTML/CSS/JavaScript or React
- Database/auth: a proper backend service
- Question bank: structured database with versioning
- Results: server-side storage per student
- Admin tools: protected server-side routes
- Hosting: GitHub Pages for front end, plus a backend service/API
