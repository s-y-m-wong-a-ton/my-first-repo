# Style Guide

## 1. Headings

**Decision:** Use sentence-style capitalization in most titles and headings: capitalize the first word and lowercase the rest. **Exceptions:** Proper nouns, including brand, product, and service names, are always capitalized. If a title or heading includes a colon, capitalize the first word after it.

**Examples:**
- Correct: "How to configure the database"
- Incorrect: "How To Configure The Database"

## 2. Oxford comma

**Decision:** Use a comma before the conjunction in a list of three or more items.

**Examples:**
- Correct: "Acceptable cookware types include those made from copper, stainless steel, glass, and ceramic."
- Incorrect: "Acceptable cookware types include those made from copper, stainless steel, glass and ceramic."

## 3. Second person

**Decision:** Use second person most of the time.

**Examples:**
- Correct: "If you don't set a power level within 1 minute, the hob automatically switches off."
- Incorrect: "If the user doesn't set a power level within 1 minute, the hob automatically switches off."

## 4. Contractions
**Decision:** Use common contractions, such as it’s, you’re, that's, and don’t, to create a conversational tone.

**Note:** 
- Avoid ambiguous or awkward contractions, such as there'd, it'll, and they'd.
- Don't mix contractions and their spelled-out equivalents (e.g. can't and cannot).
- Never form a contraction from a noun and a verb, such as _Microsoft’s developing a
lot of new cloud services_.

**Examples:**
- Correct: "If they're wet..."
- Incorrect: "If they are wet..."

## 5. UI element formatting

**Decision:** Make UI elements bold.

**Examples:**
- Correct: "Click **Save** to continue."
- Incorrect: "Click "Save" to continue."

## 6. The word "the" before UI elements

**Decision:** Omit the word "the" before UI elements in instructions.

**Examples:**
- Correct: "Click **Save**"
- Incorrect: "Click the **Save** control"

## 7. Bulleted and numbered lists

**Decision:** Use a bulleted list for things that have something in common but don't need to appear in a particular order. Use a numbered list for sequential items (like a procedure) or prioritized items (like a top 10 list).

**Examples:**
- Correct: "**To stop cooking:**
   1. Touch the cooking zone selection control for the zone you want to turn off.
   2. Touch **-** repeatedly until the display shows **0**. The cooking zone turns off.
   3. Touch **ON/OFF** to turn off the entire hob. **Important:** An **H** will flash on zones that are still hot. Wait until **H** disappears before touching the surface."
- Incorrect: "**To stop cooking:**
   - Touch the cooking zone selection control for the zone you want to turn off.
   - Touch **-** repeatedly until the display shows **0**. The cooking zone turns off.
   - Touch **ON/OFF** to turn off the entire hob. **Important:** An **H** will flash on zones that are still hot. Wait until **H** disappears before touching the surface."

## 8. List punctuation

**Decision:** Don't use a period at the end of list items unless they're complete sentences, even if the complete sentence is very short.

**Examples:**
- Correct: 
   - Complete sentences (with periods): 
      - The system verifies your credentials.
      - Your account is created automatically.
      - You receive a confirmation email.
    - Fragments (no periods): 
       - Prerequisites
       - Installation steps
       - Configuration options
- Incorrect: 
   - Complete sentences (without periods): 
      - The system verifies your credentials
      - Your account is created automatically
      - You receive a confirmation email
    - Fragments (with periods): 
       - Prerequisites.
       - Installation steps.
       - Configuration options.

## 9. Active or passive voice

**Decision:** Use active voice as much as possible.

**Note:** Passive voice is acceptable when the actor is unknown or when focusing on the action rather than the actor. Example: "The file was corrupted" (we don't know who/what corrupted it).

**Examples:**
- Correct: "You can set the power level between 0 and 9."
- Incorrect: "The power level can be set between 0 and 9."

## 10. Numbers

**Decision:** Spell out one through nine except when: following UI elements (press 1 or 2), referring to numbered steps (Step 1, Step 2), or in technical contexts where numerals improve scannability. 

**Examples:**
- Correct: "You need three prerequisites before starting."
- Correct: "Configure at least 5 servers for production."
- Correct: "Set the timeout to 9 seconds." (technical specification)
- Incorrect: "You need 3 prerequisites before starting."
- Incorrect: "Configure at least five servers for production."
- Incorrect: "Set the timeout to nine seconds." (technical specification)

## 11. Acronyms

**Decision:**

**Spelling out acronyms:**
- Spell out acronyms on first use, followed by the acronym in parentheses: "application programming interface (API)"
- Exception: Don't spell out widely known acronyms like HTML, USB, FAQ, or URL
- Exception: Don't spell out acronyms listed in Merriam-Webster Dictionary
- Exception: If a term appears only once, spell it out without introducing the acronym in parentheses
- If your audience is familiar with an acronym, use it without spelling out

**Capitalization:**
- Use ALL CAPS for acronyms where each letter is pronounced separately: API, USB, HTML
- Use title case for acronyms pronounced as words: SaaS, IoT
- In spelled-out forms, lowercase all words except proper nouns: "application programming interface" but "Hypertext Markup Language"

**Formatting:**
- Don't use periods: USA, not U.S.A.
- Form plurals by adding lowercase "s": APIs, URLs (not API's or URL's)
- Form possessives normally: the API's documentation (singular), the APIs' documentation (plural).

**Examples:**

**Multiple uses (spell out first time):**
- Correct: "Conversation as a platform (CaaP) has the potential to make booking a flight easy. Developers are looking to CaaP to make computing more accessible."
- Incorrect: "CaaP has the potential to make booking a flight easy. Developers are looking to CaaP to make computing more accessible." (not spelled out on first use)

**Single use (spell out, no parentheses):**
- Correct: "There are many dynamic-link libraries in Windows."
- Incorrect: "There are many dynamic-link libraries (DLLs) in Windows." (appears only once, don't introduce acronym)

**Widely known acronyms (use acronym):**
- Correct: "Learn how to connect a USB device to your laptop."
- Incorrect: "Learn how to connect a universal serial bus device to your laptop." (USB is widely known)

**Not spelled out first:**
- Incorrect: "There are many DLLs in Windows. Applications call DLLs all the time." (not spelled out on first use)

## 12. Code and Command Formatting

**Decision:** Use code formatting (monospace/backticks) for:
- Commands users type: `python --version`
- Code snippets: `import requests`
- File names and paths: `requirements.txt`, `/home/user`
- Terminal or command output: `Python 3.11.0`
- Variable names and function names in text: `my_function()`

**Examples:**
- Correct: "Type `cd Documents` to change directories."
- Correct: "The `requests` library makes HTTP calls easy."
- Incorrect: "Type cd Documents to change directories." (not formatted)
- Incorrect: "Type **cd Documents** to change directories." (bold is for UI elements, not commands)

**Code blocks vs. inline code:**
- Use inline code (`command`) for short commands mentioned in sentences
- Use code blocks (fenced with ```) for:
  - Commands that should be copied and pasted
  - Multi-line code or commands
  - Command sequences that go together
  - When you want to show command prompt or output

**Examples:**
Inline (correct for short mention):
- Type `ls` to list files.
Code block (correct for emphasis or copying):
- List the files in your directory:
```bash
  ls -la
```

# 13. Keyboard keys

**Decision:** 
- Use bold formatting and title case for keyboard keys: **Enter**, **Ctrl**, **Esc**.
- Combine keys in keyboard shortcuts using a + sign: **Ctrl+C**
- Because special character names could be confused with an action (such as +) or be difficult to see, always spell out the following special character names: Plus sign, Minus sign, Hyphen, Period, and Comma.

**Examples:**
- Correct: **Ctrl+Shift+?** (a question mark is not one of the special characters that needs to be spelled out)
- Incorrect: Press **Ctrl+Shift+,** to open settings. (comma should be spelled out)
- Correct: Press **Ctrl+Shift+Comma** to open settings.