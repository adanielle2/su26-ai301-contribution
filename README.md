# Contribution 1: Enter icon is not visible

**Contribution Number:** 1
**Student:** Alicia Danielle
**Issue:** [GitHub issue link](https://github.com/singh-odyssey/travellers/issues/158)
**Status:** Phase II / Complete

---

## Why I Chose This Issue

I chose this issue because it is a confirmed bug with a clear and well-defined expected behavior: a missing enter icon in the chat component that should be visible to guide users to submit their query. Being labeled as a "good first issue," it felt like a manageable starting point for my first open-source contribution without being overwhelming.

I hope to learn what it feels like to contribute to a real-world open-source project, from setting up an unfamiliar codebase locally, to understanding how to track down the right component to fix, to submitting a pull request that gets reviewed by actual maintainers. This is my first time doing this kind of project and I'm excited to go through the full process end to end.

## Understanding the Issue

### Problem Description

The send button in the TravelBox chatbot component is rendered as a plain blue circle with no icon inside it. There is no visual indicator to show users that the button submits their message, making it confusing and unclear.

### Expected Behavior

The send button should display a visible enter/send icon so users can clearly identify it as the button to submit their chat query.

### Current Behavior

The send button appears as a plain blue circle with no icon, giving no visual cue to the user that it is a submit button.

### Affected Components

- `src/components/Chatbot.tsx` — the send button inside the chat input section is missing an icon

---

## Reproduction Process

### Environment Setup

- Cloned the forked repository locally
- Ran `npm install` to install dependencies (received deprecation warnings but no errors)
- Created a `.env` file with `NEXTAUTH_SECRET` and `NEXTAUTH_URL`
- Ran `npm run dev` and opened `http://localhost:3000` in the browser

### Steps to Reproduce

1. Go to `http://localhost:3000`
2. Look at the bottom right of the page — a chat widget is visible
3. Click the chat bubble icon to open the TravelBox chat panel
4. Observe the send button on the right side of the input field, it appears as a plain blue circle with no icon

### Reproduction Evidence

- **Screenshots/logs:** The send button renders as a solid blue circle with no icon inside it
- **My findings:** Inside `src/components/Chatbot.tsx`, the send button element has no children, the icon was never added to the button

---

## Solution Approach

### Analysis

The root cause is in `src/components/Chatbot.tsx`. The send button is fully styled but has no icon inside it. The project already uses the `lucide-react` icon library (the `MessageCircle` icon is imported at the top of the file), so the fix simply requires importing and adding the appropriate send icon.

### Proposed Solution

Import the `SendHorizontal` icon from `lucide-react` and place it inside the send button element.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** The send button in the chatbot component is an empty styled button; it needs a visible icon added inside it.

**Match:** The codebase already uses `lucide-react` for icons: the `MessageCircle` icon is imported at the top of `Chatbot.tsx`. The same pattern can be used to add a send icon.

**Plan:**
1. In `src/components/Chatbot.tsx`, update the import to add `SendHorizontal`:
```tsx
   import { MessageCircle, SendHorizontal } from "lucide-react";
```
2. Add the icon inside the send button:
```tsx
   <button
  onClick={sendMessage}
  disabled={loading}
  className="h-14 w-14 rounded-full bg-blue-600 text-white shadow-md flex items-center justify-center transition-all duration-300 hover:scale-110">
  <SendHorizontal size={22} />
</button>
  
```

**Implement:** [[Link to branch](https://github.com/adanielle2/travellers/tree/fix/enter-icon-not-visible)]

**Review:**
- [x] Follows the project's existing icon pattern using `lucide-react`
- [x] No new dependencies added
- [x] Button functionality unchanged; only a visual fix
- [x] Ran `npm run lint` with no errors

**Evaluate:** Verify the fix by opening `http://localhost:3000`, clicking the chat icon, and confirming the send button now displays a visible arrow/send icon inside the blue circle.


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
