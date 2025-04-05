# GitHub Issue Tags for Content Management Workflow

## Content Stage Tags
- `research`: For tasks related to gathering information, user interviews, or documentation analysis
- `planning`: For content structure, outline creation, and content strategy
- `writing`: For initial content drafting tasks
- `review`: For content that needs technical or editorial review
- `revision`: For content that needs updates based on feedback
- `final`: For content that is ready for production

## Content Type Tags
- `chapter`: For issues related to main book chapters
- `example`: For creating practical examples or use cases
- `exercise`: For "Try This" interactive elements
- `visual`: For screenshots, diagrams, or other visual elements
- `template`: For reusable templates to be included in the guide
- `glossary`: For terminology definitions and explanations

## Priority Tags
- `p1`: Critical for initial release
- `p2`: Important but not blocking
- `p3`: Nice to have, lower priority

## User Focus Tags
- `beginner`: Content specifically targeting new users
- `intermediate`: Content for users with some familiarity
- `advanced`: Content for more experienced users
- `persona-sarah`: Content targeting the marketing manager persona
- `persona-mark`: Content targeting the graduate student persona
- `persona-elena`: Content targeting the small business owner persona

## Technical Tags
- `accessibility`: Issues related to making content accessible
- `formatting`: Issues related to markdown or styling
- `cross-reference`: Issues related to linking between content sections
- `terminology`: Issues related to consistent word choice and definitions

## Process Tags
- `blocked`: Cannot proceed until another issue is resolved
- `needs-decision`: Requires stakeholder input before proceeding
- `ready-for-review`: Content is ready for editorial or technical review
- `feedback-implemented`: Changes from feedback have been applied

## Production Tags
- `image-needed`: Requires screenshot or diagram creation
- `proofreading`: Needs final language check
- `formatting-check`: Needs verification of proper markdown/styling
- `ready-for-export`: Content is ready for conversion to final formats

## Issue Templates

### Chapter Creation Template
```
Title: [Chapter X] - [Chapter Name]

## Overview
Brief description of what this chapter will cover.

## Sections
- [ ] Section 1: [Name]
- [ ] Section 2: [Name]
- [ ] Section 3: [Name]

## Required Elements
- [ ] Examples for [key concept]
- [ ] "Try This" exercises (at least 2)
- [ ] Screenshots for [feature/concept]
- [ ] Real-world use case for each persona

## Dependencies
- Depends on: #[issue number] (if applicable)

Labels: chapter, [stage], [priority]
```

### Visual Asset Template
```
Title: Create [type of visual] for [concept/feature]

## Description
Brief description of what the visual should illustrate.

## Visual Requirements
- [ ] Show [specific elements]
- [ ] Include annotations for [features]
- [ ] Ensure accessibility (alt text, color contrast)
- [ ] Follow visual style guide

## Target Location
- Chapter: [chapter number/name]
- Section: [section name]

Labels: visual, [stage], [priority]
```

### Review Request Template
```
Title: Review [chapter/section] on [topic]

## Content to Review
Link or reference to content needing review.

## Review Focus
- [ ] Technical accuracy
- [ ] Clarity for target audience
- [ ] Progression of concepts
- [ ] Appropriate examples/exercises
- [ ] Terminology consistency

## Timeline
Requested completion date: [date]

Labels: review, [content type], [priority]
``` 