# Contribution 2: Keyboard shortcut to open the "Add application" modal


**Contribution Number:** 2  
**Student:** Donna Carschmit
**Issue:** https://github.com/Joun-Mikhail/careerflow/issues/7 
**Status:** Phase I - Complete

---

## Why I Chose This Issue

I chose issue #460, "Typing should autofocus the chatbar," because it combines a straightforward user experience improvement with an opportunity to work on frontend functionality in a real-world application. Since I have experience with JavaScript and TypeScript, I thought it would be a good way to apply those skills while learning how a larger open-source project handles keyboard events and focus management.

My goal is to become more comfortable navigating an unfamiliar codebase and contributing to production software. From reading the discussion, I understand that the challenge is to automatically focus the chat input without affecting existing keyboard shortcuts. I'm looking forward to learning how these interactions are implemented and to making a small improvement that enhances the overall user experience.

---

## Understanding the Issue

### Problem Description

Currently, users must manually click on the chat input before they can start typing a message if the input is not already focused. This makes the messaging experience feel less smooth compared to other desktop messaging applications.


### Expected Behavior

When a user begins typing while viewing a conversation, the chat input should automatically receive focus so they can start composing a message immediately. This behavior should not interfere with existing keyboard shortcuts or navigation controls.

### Current Behavior

If the chat input is not focused, typing does not automatically place the cursor in the message box. Users must first click on the chat input before they can begin typing.

### Affected Components

Based on the issue discussion, this feature will likely involve the chat input component and the keyboard event handling responsible for managing focus. It will also require reviewing the existing keyboard shortcuts to ensure they continue to function as intended.

---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
