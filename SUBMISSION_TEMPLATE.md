# Submission: Jakub Kozłowski

## Time Spent

Total time: 210min

## Ticket Triage

### Tickets I Addressed

List the ticket numbers you worked on, in the order you addressed them:

1. **CFG-142**: Fixed the debounce function and used it instead.
2. **CFG-148**: Could not reproduce. See Clarification section
3. **CFG-151**: Improved handling and displaying error messages
4. **CFG-147**: Could not reproduce. See Clarification section
5. **CFG-146**: Modified saving draft. Using timestamp instead of isoString for draft for consistency. Draft save alert remain the same as it is local state of the app.
6. **CFG-152**: Made color swatches focusable, added missing styles on buttons, made modal working properly with keyboard. Did not find any custom dropdown mentioned in the ticket description
6. **CFG-157**: Added native dialog on tab close. Added custom dialog on discard.
7. **CFG-156**: Could not reproduce. See Clarification section

### Tickets I Deprioritized

List tickets you intentionally skipped and why:

| Ticket  | Reason                 |
| ------- | ---------------------- |
| CFG-143 | Demands a lot of time for debugging (20min for each modification). Does not block the user from using the app |
| CFG-149 | We have loading indicator on a "Add to cart" button that is right below the price and also the whole price section is grayed out during the price calculation. No time for it now |
| CFG-153 | This is a feature request that we need more time for dealing with it. |
| CFG-155 | This is a feature request. It is flagged as "nice to have" so deprioritized |

### Tickets That Need Clarification

List any tickets where you couldn't proceed due to ambiguity:

| Ticket  | Question                  |
| ------- | ------------------------- |
| CFG-144 | Mismatch with CFG-144 - we need joint decision wether to keep it or remove it |
| CFG-145 | Mismatch with CFG-145 - same as above - we need joint decision |
| CFG-148 | Could not reproduce. Also what is "Premium Material upgrade"? I assumed it was "Premium Plastic" as a Material. Having that no error for me |
| CFG-147 | Could not reproduce. I see the comments in the code regarding this bug. The thing is that the url encoder does not even use the label of that option so this is impossible. We can mark it for future improvement if special characters may appear in the name of an option. |
| CFG-150 | What is the desired look on mobile devices? Note: it is a css thing |
| CFG-154 | Awaiting clarifications for discussion under the ticket (in notes section). |
| CFG-156 | Could not reproduce. Checked all list renderings in code. Please try reproducing on latest version of the app. |

---

## Technical Write-Up

### Critical Issues Found

Describe the most important bugs you identified:

#### Issue 1: Price stuck on $0.00

**Ticket(s):** CFG-142

**What was the bug?**

The root cause was the logic handling race condition in function calculating the price. It compared actual timestamp with requestId being a simple counter.

**How did you find it?**

Related to mentioned in the ticket bug about a price. Briefly commented bug in the code.

**How did you fix it?**

Decided to fix debounce function that was already there but never used.

**Why this approach?**

This was the quickest approach. The debounce function was ready with redudant useRef. Using debounce function you do not have to think about handling race conditions and comparing times and finding right logic.

---

#### Issue 2: Keyboard navigatin

**Ticket(s):** CFG-152

**What was the bug?**

User did not have an option to select a color since custom radio buttons were used.
Additionally, no option to close dialogs with a keyboard instantly (the focus was on the trigger element and the user had to navigate to the very end to find the dialog).

**How did you find it?**

Mentioned in the ticket -> Manual testing

**How did you fix it?**

Added missing functionalities

**Why this approach?**

Quickest approach without redefining new components

---

### Other Changes Made

Brief description of any other modifications:

- added focus style for quick add button as well even if not mentioned in the ticket

---

## Code Quality Notes

### Things I Noticed But Didn't Fix

List any issues you noticed but intentionally left:

| Issue   | Why I Left It                                         |
| ------- | ----------------------------------------------------- |
| calculatePrice bugs and comments | since I decided to go with debounce functions the comments in calculatePrice are not related and the requestId counter is rendant. No time to clean the code. |
| bug comments | Bugs mentioned in the comments. No time to clean the code. Not mentioned in the tickets |

### Potential Improvements for the Future

If you had more time, what would you improve?

1. Clean the code regarding calculatePrice function
2. Secure share url encoding for future when special character appear in option name
3. Split ProductConfigurator.tsx into more files
4. Solve the rest of bugs mentioned in the comments
5. Solve eslint errors

---

## Questions for the Team

Questions you would ask in a real scenario:

1. all question mentioned in clarification sections
2. What is behind 47 inside joke :)

---

## Assumptions Made

List any assumptions you made to proceed:

1. -

---

## Self-Assessment

### What went well?

Implementation, understanding the new code I haven't worked with - well documented.

### What was challenging?

Prioritizing tickets

### What would you do differently with more time?

Prioritize accessibility ticket higher since the client has audit soon and it may risk on our cooperation. Also a big blocker for keyboard only users.

---

## Additional Notes

Anything else you want us to know:

-