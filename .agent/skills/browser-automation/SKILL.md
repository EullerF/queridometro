---
name: browser-automation
description: Browser automation and web testing principles using the native browser subagent.
when_to_use: "When needing to test web applications via browser, scrape data, or automate UI tasks using the built-in browser_subagent tool."
allowed-tools: browser_subagent
---

# Browser Automation & Subagent Testing

> Control the web natively. Use the built-in subagent to test, scrape, and automate web interactions directly.

## 🤖 1. The Browser Subagent (`browser_subagent`)

The `browser_subagent` is a native capability of the Antigravity agent. It spins up a headless/visual browser instance to perform complex, multi-step actions on any website. 

### When to use it:
| Scenario | Why use the Subagent? |
|----------|-----------------------|
| **E2E Testing** | Validate UI components, logins, and dynamic forms in real-time. |
| **Data Scraping** | Extract content from websites that require JavaScript or logins. |
| **Workflow Automation** | Fill forms, click through processes, or automate repetitive web tasks. |

---

## 🛠️ 2. Core Principles for Subagent Instructions

When invoking the `browser_subagent` tool, you must write a highly detailed `Task` description. The subagent is an independent agent that only knows what you tell it in that prompt.

### Best Practices for Prompts:

1. **Be Specific:** Provide exact URLs. 
2. **Step-by-Step:** List actions logically (e.g., "1. Go to URL, 2. Click 'Login', 3. Type 'admin' in the username field").
3. **Stop Conditions:** Tell the subagent exactly when to stop and what to report back (e.g., "Stop when the success message appears and return the text of the message").
4. **Resilience:** Ask the subagent to wait for elements to load or try alternative selectors if one fails.

---

## 🧪 3. Testing Web Apps (No Playwright required)

Instead of writing and maintaining Playwright scripts for simple checks, you can use the `browser_subagent` to rapidly test local or remote apps.

### Workflow for Testing:

1. **Start the local server:** Use a terminal command (e.g., `npm run dev`) and ensure it's running in the background.
2. **Invoke the Subagent:** Call the `browser_subagent` pointing to `http://localhost:3000` (or appropriate port).
3. **Define the Test Case:** Ask the subagent to perform the user journey (e.g., "Add an item to the cart and verify the total price updates").
4. **Analyze the Result:** The subagent will return a report and automatically record a WebP video of the interaction.

---

## 🎥 4. Artifacts & Debugging

- **Videos:** Every subagent session is automatically recorded as a WebP video in the artifacts directory. This is perfect for debugging UI failures or presenting proof of testing.
- **Context Re-use:** If a task requires multiple phases, you can use `ReusedSubagentId` to continue a previous session without starting over (saving time and maintaining login states).

---

## 🚫 5. Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|-------|
| Send vague instructions like "Test the page". | Send explicit instructions: "Go to /login, enter X, click Y, verify Z". |
| Assume the page loads instantly. | Ask the subagent to wait for specific elements to appear. |
| Use the subagent for simple static HTML reading. | Use `read_url_content` for fast, invisible text extraction of static pages. |
