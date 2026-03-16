# 🧮 Enhanced Calculator

A clean, fully functional browser-based calculator built with pure HTML, CSS, and vanilla JavaScript. Supports basic arithmetic, parentheses for grouping, percentage calculations, and decimal numbers.

---

## 🖥️ Preview

Click the buttons on the calculator to build a math expression. Hit **=** to see the result, or **C** to clear the display and start over.

---

## ✨ Features

- ➕ **Basic arithmetic** — Addition, Subtraction, Multiplication, Division
- 🔢 **Decimal support** — Use the `.` button for decimal numbers
- 🔣 **Parentheses** — Group expressions like `(5+3)*2`
- 💯 **Percentage** — `%` converts a number to its decimal equivalent (e.g. `50%` → `0.5`)
- 🧹 **Clear button (C)** — Resets the display back to `0`
- ⚠️ **Error handling** — Displays `Error` for invalid expressions instead of crashing
- 🎯 **Floating point fix** — Results are rounded to 10 decimal places to avoid issues like `0.1 + 0.2 = 0.30000000000000004`

---

## 📁 Project Structure

```
enhanced-calculator/
│
├── index.html       # Calculator layout and button structure
├── style.css        # Grid layout and button styling
└── script.js        # All calculation logic and event handling
```

---

## 🚀 Getting Started

No installation or dependencies required.

### Option A — Using Git (if you have Git installed)

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/enhanced-calculator.git
   ```

2. **Open in your browser**
   ```bash
   cd enhanced-calculator
   open index.html
   ```
   Or simply double-click `index.html` to open it in your browser.

---

### Option B — Without Git (download as ZIP)

> 👉 Use this option if you don't have Git or Git Bash installed on your PC.

1. Go to the repository page on GitHub
2. Click the green **`<> Code`** button near the top right
3. Select **"Download ZIP"** from the dropdown
4. Once downloaded, **right-click** the ZIP file and select **"Extract All"** (Windows) or **"Open"** (Mac)
5. Open the extracted folder and **double-click `index.html`** — it will open directly in your browser

> ✅ No terminal, no Git, no setup needed — it just works!

---

## 🧠 How It Works

### Button Click Flow

Every button on the calculator shares a single event listener loop using `forEach`. Each button carries its value in a `data-value` HTML attribute.

```
User clicks a button
        │
        ▼
handleButtonClick(value)
        │
        ├── value === 'C'  ──▶ clearDisplay()  → resets display to '0'
        │
        ├── value === '='  ──▶ calculateResult()
        │                          │
        │                    Replace % with /100
        │                          │
        │                      eval(expression)
        │                          │
        │               ┌──────────┴──────────┐
        │             Valid               Invalid
        │               │                    │
        │         Round to 10 dp       show 'Error'
        │               │
        │         Show result on display
        │
        └── anything else ──▶ appendToDisplay(value)
                                    │
                              display === '0'?
                               Yes → replace
                               No  → append
```

### Percentage Logic

The `%` button doesn't calculate immediately — it stores the symbol in the expression. When `=` is pressed, `%` is replaced with `/100` before evaluation:

| You Type  | Evaluated As | Result |
|-----------|--------------|--------|
| `50%`     | `50/100`     | `0.5`  |
| `200*50%` | `200*50/100` | `100`  |

---

## 🔍 Button Reference

| Button | Function                          |
|--------|-----------------------------------|
| `0–9`  | Append digit to display           |
| `.`    | Append decimal point              |
| `+` `-` `*` `/` | Append operator          |
| `(`  `)` | Append parenthesis              |
| `%`    | Append percent (converts to /100) |
| `C`    | Clear display → reset to `0`      |
| `=`    | Evaluate the full expression      |

---

## 🛠️ Built With

- **HTML5** — Button layout using `data-value` attributes
- **CSS3** — Grid-based calculator layout
- **Vanilla JavaScript (ES6)** — DOM manipulation, event handling, `eval()`

---

## 📚 Concepts Covered

This project is great for learning and practicing:

- DOM selection (`getElementById`, `querySelectorAll`)
- Looping over elements (`forEach`)
- Event listeners (`click`)
- `data-*` HTML attributes (`dataset.value`)
- String manipulation (`replace`, `+=`, `textContent`)
- `eval()` for dynamic expression evaluation
- `try...catch` for error handling
- `parseFloat` and `toFixed` for number formatting
- Regular Expressions (`/%/g` global replace)

---

## 🤝 Contributing

Pull requests are welcome! Ideas for improvement:
- ⌨️ Add keyboard input support
- 🕓 Show a calculation history log
- 🌗 Add a dark / light theme toggle
- √ Add a square root or power button

---
