# GitHub CLI Commands for Content Workflow

## Setting Up GitHub Labels

First, create all the required labels in your repository:

```bash
# Content Stage Tags
gh label create research --color 0052CC --description "Tasks related to gathering information or research"
gh label create planning --color 0052CC --description "Content structure and strategy tasks"
gh label create writing --color 0052CC --description "Initial content drafting tasks"
gh label create review --color 0052CC --description "Content needing technical or editorial review"
gh label create revision --color 0052CC --description "Content needing updates based on feedback"
gh label create final --color 0052CC --description "Content ready for production"

# Content Type Tags
gh label create chapter --color 5319E7 --description "Issues related to main book chapters"
gh label create example --color 5319E7 --description "Creating practical examples or use cases"
gh label create exercise --color 5319E7 --description "Creating 'Try This' interactive elements"
gh label create visual --color 5319E7 --description "Screenshots, diagrams, or other visual elements"
gh label create template --color 5319E7 --description "Reusable templates for the guide"
gh label create glossary --color 5319E7 --description "Terminology definitions and explanations"

# Priority Tags
gh label create p1 --color B60205 --description "Critical for initial release"
gh label create p2 --color D93F0B --description "Important but not blocking"
gh label create p3 --color FBCA04 --description "Nice to have, lower priority"

# User Focus Tags
gh label create beginner --color 006B75 --description "Content for new users"
gh label create intermediate --color 006B75 --description "Content for users with some familiarity"
gh label create advanced --color 006B75 --description "Content for more experienced users"
gh label create persona-sarah --color 006B75 --description "Content for marketing manager persona"
gh label create persona-mark --color 006B75 --description "Content for graduate student persona"
gh label create persona-elena --color 006B75 --description "Content for small business owner persona"

# Technical Tags
gh label create accessibility --color 1D76DB --description "Making content accessible"
gh label create formatting --color 1D76DB --description "Markdown or styling issues"
gh label create cross-reference --color 1D76DB --description "Linking between content sections"
gh label create terminology --color 1D76DB --description "Consistent word choice and definitions"

# Process Tags
gh label create blocked --color C5DEF5 --description "Cannot proceed until another issue is resolved"
gh label create needs-decision --color C5DEF5 --description "Requires stakeholder input"
gh label create ready-for-review --color C5DEF5 --description "Content ready for review"
gh label create feedback-implemented --color C5DEF5 --description "Changes from feedback applied"

# Production Tags
gh label create image-needed --color BFDADC --description "Requires visual creation"
gh label create proofreading --color BFDADC --description "Needs final language check"
gh label create formatting-check --color BFDADC --description "Verify proper markdown/styling"
gh label create ready-for-export --color BFDADC --description "Ready for conversion to final formats"
```

## Creating Common Issue Types

### Creating a New Chapter Issue

```bash
gh issue create \
  --title "Chapter 1 - Introduction to Tana" \
  --body "## Overview
Brief introduction to Tana for beginners.

## Sections
- [ ] What is Tana?
- [ ] Why use Tana?
- [ ] Getting started with your first workspace

## Required Elements
- [ ] Examples for basic Tana concepts
- [ ] 'Try This' exercises (at least 2)
- [ ] Screenshots of Tana interface
- [ ] Real-world use case for each persona

## Dependencies
None - this is the first chapter" \
  --label "chapter,planning,p1,beginner"
```

### Creating a Visual Asset Issue

```bash
gh issue create \
  --title "Create annotated screenshot for Tana workspace setup" \
  --body "## Description
Create a screenshot showing the initial Tana workspace setup process with clear annotations.

## Visual Requirements
- [ ] Show the main Tana interface
- [ ] Include annotations for key UI elements
- [ ] Ensure accessibility (alt text, color contrast)
- [ ] Follow visual style guide for annotation colors and fonts

## Target Location
- Chapter: 1 - Introduction to Tana
- Section: Getting started with your first workspace" \
  --label "visual,planning,p1,beginner,image-needed"
```

### Creating a Review Request Issue

```bash
gh issue create \
  --title "Review Chapter 1 Introduction to Tana" \
  --body "## Content to Review
See draft in drafts/chapter1-introduction.md

## Review Focus
- [ ] Technical accuracy of Tana descriptions
- [ ] Clarity for non-technical users
- [ ] Progression of concepts
- [ ] Appropriate examples/exercises
- [ ] Terminology consistency with glossary

## Timeline
Requested completion date: [2 days from now]" \
  --label "review,chapter,p1,ready-for-review"
```

### Creating a Content Revision Issue

```bash
gh issue create \
  --title "Revise Chapter 1 based on user feedback" \
  --body "## Feedback Summary
During user testing, beginners found the following sections unclear:
- Explanation of basic navigation
- Difference between items and tags

## Required Changes
- [ ] Simplify navigation explanation with more screenshots
- [ ] Add clearer real-world analogies for items vs. tags
- [ ] Ensure reading level stays at 8th grade or below
- [ ] Update exercises to be more guided

## Related Issues
Related to #12 (Review Chapter 1)" \
  --label "revision,chapter,p1,beginner,feedback-implemented"
```

## Milestone Creation

Create milestone for each major content phase:

```bash
gh api repos/{owner}/{repo}/milestones -f title="Research Phase" -f description="Gather information, user research, and planning" -f due_on="YYYY-MM-DDT00:00:00Z"
gh api repos/{owner}/{repo}/milestones -f title="Content Creation" -f description="Draft all chapters and visual elements" -f due_on="YYYY-MM-DDT00:00:00Z"
gh api repos/{owner}/{repo}/milestones -f title="Review & Testing" -f description="User testing and content revisions" -f due_on="YYYY-MM-DDT00:00:00Z"
gh api repos/{owner}/{repo}/milestones -f title="Production" -f description="Final preparation and export to publication formats" -f due_on="YYYY-MM-DDT00:00:00Z"
```

## Adding Issues to Milestones

```bash
# Get milestone ID first
gh api repos/{owner}/{repo}/milestones --jq '.[0].number'

# Add issue to milestone
gh issue edit {issue-number} --milestone {milestone-id}
```

## Creating Custom Project Views

```bash
# First create project
gh api graphql -f query='
mutation {
  createProject(input: {ownerId: "OWNER_ID", name: "Tana for Real People", body: "Content development tracking"}) {
    project {
      id
      number
    }
  }
}
'

# Add custom fields and views for content workflow
```

Remember to replace `{owner}`, `{repo}`, and other placeholders with your actual repository information. 