# Contribution 2: Keyboard shortcut to open the "Add application" modal


**Contribution Number:** 2  
**Student:** Donna Carschmit

**Issue:** https://github.com/Joun-Mikhail/careerflow/issues/7 

**Status:** Phase IV - Complete

---

## Why I Chose This Issue

I chose issue #7, "Keyboard shortcut to open the Add application modal," because it is a focused frontend issue that matches my experience with JavaScript and TypeScript. The issue has clear acceptance criteria and gave me a chance to practice keyboard event handling in a real React application.

This issue interested me because it improves the user experience in a small but meaningful way. Instead of requiring users to click the Add application button every time, the Applications page can support a simple keyboard shortcut. I also wanted more practice working with modal behavior, input focus handling, and frontend testing in an open-source project.

---

## Understanding the Issue

### Problem Description

Currently, users must click the Add application button on the Applications page to open the Add application modal. The issue asks for a keyboard shortcut so users can press `n` to open the modal when they are not typing in an input field.

### Expected Behavior

When the user is on the Applications page and presses `n`, the Add application modal should open. The shortcut should only work when the user is not focused inside an input, textarea, select, or editable field. Pressing `Esc` should still close the modal.

### Current Behavior

Before the change, pressing `n` on the Applications page did not open the Add application modal. Users had to manually click the Add application button.

### Affected Components

The main affected file is:

- `frontend/src/pages/ApplicationsPage.tsx`

The existing modal component is also relevant because it already handles closing the modal with `Esc`.

---

## Reproduction Process

### Environment Setup

I set up the CareerFlow project locally using Docker, following the project’s contributing instructions.

I initially tried setting up the backend manually with a Python virtual environment, but decided to use Docker because the contributing guide recommended it as the fastest setup path. I had to make sure Docker Desktop was running before using:

docker compose up --build

Once Docker was running, I was able to open the application locally and test the Applications page.

### Steps to Reproduce

1. Start the project locally with Docker.
2. Open the CareerFlow frontend in the browser.
3. Navigate to the Applications page.
4. Press the n key while focus is not inside an input field.
5. Observe that the Add application modal does not open.

### Reproduction Evidence

- **Commit showing reproduction:** Not applicable because this was reproduced manually before implementing the fix.
- **Screenshots/logs:** I used manual browser testing to confirm the issue.
- **My findings:** The Applications page already had an Add application modal controlled by React state, but there was no keyboard listener for opening it with n.

---

## Solution Approach

### Analysis

The root cause was that the Applications page only opened the Add application modal through the button click handler. There was no global keyboard event handler on the page to detect when the user pressed n.
The fix needed to be careful because the shortcut should not trigger while the user is typing in form fields. Without this guard, pressing n inside an input could accidentally open the modal.

### Proposed Solution

Add a keydown listener in frontend/src/pages/ApplicationsPage.tsx that listens for the n key. The listener should check whether the current focused element is an input, textarea, select, or editable element. If the user is not typing in one of those elements, pressing n should open the Add application modal.
The handler should also call event.preventDefault() so the n key does not get inserted into the first field when the modal opens.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** 
The Applications page needs a keyboard shortcut that opens the Add application modal when the user presses n, but only when the user is not typing in a form field.

**Match:** 
The existing page already uses React state to control whether the Add application modal is open. The existing modal also already supports Esc to close, so the new change only needs to open the modal and should preserve the existing close behavior.

**Plan:** 
1. Modify frontend/src/pages/ApplicationsPage.tsx.
2. Import useEffect from React.
3. Add a keydown listener for the n key.
4. Guard against inputs, textareas, selects, contenteditable elements, and modifier keys.
5. Call event.preventDefault() before opening the modal.
6. Verify that Esc still closes the modal.
7. Run frontend checks before submitting the PR.

**Implement:** 
Branch: [fix-issue-7](https://github.com/DonnaIsabel97/careerflow/tree/fix-issue-7)
Commit: [92c9160](https://github.com/DonnaIsabel97/careerflow/commit/92c9160)

**Review:** 
I reviewed the change against the project’s contributing guidelines. The change is focused, follows the existing React style, uses a conventional commit message, and does not add secrets, debug output, or unrelated changes.

**Evaluate:** 
I verified the behavior manually and ran the frontend checks:
npm run lint
npm run typecheck
npm test
npm run build

---

## Testing Strategy

### Unit Tests

- [x] Test case 1: Pressing n on the Applications page opens the Add application modal.
- [x] Test case 2: Pressing n while focused inside a form field does not open the modal.
- [x] Test case 3: Pressing Esc still closes the modal.

### Integration Tests

- [x] User navigates to the Applications page and opens the Add application modal using the keyboard shortcut.
- [x] User types in an input field and the shortcut does not interrupt normal typing behavior.

### Manual Testing

- Verified that pressing n on the Applications page opens the Add application modal.
- Verified that the modal opens with an empty Role title field.
- Verified that pressing Esc closes the modal.
- Verified that pressing n inside the search input does not open the modal.
- Verified that frontend checks passed.

---

## Implementation Notes

### Week [1] Progress

I implemented the keyboard shortcut for issue #7. The main change was adding a guarded keydown listener in frontend/src/pages/ApplicationsPage.tsx.
The first version opened the modal, but the letter n was also inserted into the Role title field when the modal appeared. I fixed this by adding event.preventDefault() before opening the modal. After that, the modal opened correctly without inserting the shortcut key into the form.
I also tested that the shortcut does not interfere with typing inside inputs and that the existing Esc behavior still works.

### Code Changes

- **Files modified:** frontend/src/pages/ApplicationsPage.tsx
- **Key commits:** - [92c9160-feat(applications): add shortcut for application modal](https://github.com/DonnaIsabel97/careerflow/commit/92c9160)
- **Approach decisions:**
  I kept the change inside the Applications page because the shortcut is page-specific. I also reused the existing modal state instead of creating a new modal flow. The keyboard listener includes guards for form fields so the shortcut does not interfere with normal typing.

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted](https://github.com/Joun-Mikhail/careerflow/pull/10)

**PR Description:** Adds the keyboard shortcut requested in issue #7. On the Applications page, pressing n now opens the Add application modal when the user is not typing in a form field.

**Maintainer Feedback:**
- Maintainer approved and merged the PR.
- No implementation changes were requested.
- Merge required maintainer override due to repository deployment configuration, not because of the code change.

**Status:** Merged

---

## Learnings & Reflections

### Technical Skills Gained

I practiced adding keyboard event handling in a React page and learned more about guarding shortcuts so they do not interfere with normal form input. I also gained more experience testing frontend behavior manually and running project checks before submitting a pull request.

### Challenges Overcome

The main challenge was that the first version opened the modal but also inserted the letter n into the Role title field. I solved this by preventing the default key behavior before opening the modal. I also had to make sure the shortcut only worked when the user was not focused inside a form field.

### What I'd Do Differently Next Time

Next time, I would test keyboard shortcuts against focused inputs earlier in the process. I would also check the project’s existing modal and keyboard handling patterns before writing the first version so I can align with the codebase more quickly.

---

## Resources Used

- [CareerFlow issue #7: Keyboard shortcut to open the Add application modal](https://github.com/Joun-Mikhail/careerflow/issues/7)
- [CareerFlow CONTRIBUTING.md](https://github.com/Joun-Mikhail/careerflow/blob/main/CONTRIBUTING.md)
- [React documentation: `useEffect`](https://react.dev/reference/react/useEffect)
- [MDN Web Docs: `keydown` event](https://developer.mozilla.org/en-US/docs/Web/API/Element/keydown_event)
- [MDN Web Docs: `event.preventDefault()`](https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault)
- [MDN Web Docs: `HTMLElement.isContentEditable`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/isContentEditable)
