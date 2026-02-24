---
name: create-quiz
description: Create a comprehensive interactive quiz on any topic from provided online documentation. Generates questions, implements the standard quiz template with Interactive Answer Review feature, and outputs the quiz HTML file in the current working directory.
---

# Create Quiz from Documentation

This skill creates a complete, production-ready interactive HTML quiz on **any topic** from provided online documentation. The quiz is a standalone HTML file with no external dependencies.

## When to Use

- User wants to create a quiz on any subject (technical, certification, training, etc.)
- User provides documentation URLs or topic references
- User requests a comprehensive quiz for study or assessment purposes

## Prerequisites

1. **Documentation URL(s)** (required) - One or more publicly accessible web pages to base questions on
2. **Quiz topic/title** (required) - The subject of the quiz
3. **Desired number of questions** (optional, default: 20, typical range: 10-30)
4. **Category/badge label** (optional) - A short label shown in the header badge
5. **Subtitle text** (optional) - Descriptive text below the title
6. **Color scheme preference** (optional - will suggest based on topic)

## Output Location

**The quiz HTML file is always created in the current working directory.**

The filename follows the pattern: `[topic-slug]-quiz.html` (kebab-case, lowercase).

Examples:
- `kubernetes-networking-quiz.html`
- `aws-security-lake-quiz.html`
- `python-async-quiz.html`
- `terraform-state-management-quiz.html`

## Process Overview

1. **Gather Requirements** - Confirm topic, doc URLs, question count, colors
2. **Analyze Documentation** - Read and understand the documentation content
3. **Generate Questions** - Create comprehensive questions with multiple-choice answers
4. **Implement Quiz File** - Copy the gold standard template and make minimal targeted changes
5. **Validate** - Ensure all features work correctly

## Step-by-Step Implementation

### Step 1: Gather Requirements

Ask the user for (or infer from context):
- **Documentation URL(s)**: The pages to base questions on
- **Quiz Title**: e.g., "Kubernetes Networking", "Terraform State Management"
- **Badge Label**: Short category label (e.g., "K8s Networking", "IaC", "Python Async")
- **Subtitle**: Descriptive text (e.g., "Comprehensive Quiz for CKA Certification")
- **Question Count**: Typical range is 10-30 questions (default: 20)
- **Accent Color**: Suggest based on topic or let user choose

**Color scheme suggestions by topic area**:

| Topic Area | Primary | Secondary | Description |
|------------|---------|-----------|-------------|
| Cloud/Infrastructure | `#6366f1` | `#818cf8` | Indigo |
| Security/Compliance | `#a855f7` | `#c084fc` | Purple |
| Networking | `#06b6d4` | `#22d3ee` | Cyan |
| Monitoring/Observability | `#14b8a6` | `#2dd4bf` | Teal |
| Data/Databases | `#f59e0b` | `#fbbf24` | Amber |
| Programming/Dev | `#22c55e` | `#4ade80` | Green |
| DevOps/CI-CD | `#f97316` | `#fb923c` | Orange |
| AI/ML | `#ec4899` | `#f472b6` | Pink |
| General/Other | `#3b82f6` | `#60a5fa` | Blue |

### Step 2: Analyze Documentation

Use appropriate tools to fetch and read the documentation:
- For AWS docs: Use the AWS Documentation MCP tools
- For Microsoft docs: Use the MS Learn Docs MCP tools
- For other docs: Use web_search or other available tools
- Read and identify key concepts, features, best practices, and use cases

### Step 3: Generate Questions from Documentation

Generate questions covering:
- Core concepts and definitions
- Configuration and setup
- Best practices
- Integration with related technologies
- Troubleshooting and common issues
- Real-world scenarios
- Edge cases and gotchas

**Question Guidelines**:
- Each question MUST have exactly 4 options (A, B, C, D)
- Only ONE correct answer per question
- Include detailed explanation (2-4 sentences) for each answer
- Reference the source documentation URL
- Cover different difficulty levels (mix of easy, medium, hard)
- Include scenario-based questions (not just factual recall)
- Avoid questions that are too easy or too obvious
- Make wrong options plausible (common misconceptions, similar features)
- Explanations should educate, not just confirm the answer
- Explain why each wrong option is incorrect when possible

**Question Structure**:
```javascript
{
    id: 1,
    question: "What is the primary purpose of [concept]?",
    options: [
        "Option A - clearly wrong but plausible",
        "Option B - correct answer",
        "Option C - plausible but incorrect",
        "Option D - common misconception"
    ],
    correct: 1, // 0-indexed position of correct answer
    explanation: "Detailed explanation of why B is correct and why others are wrong. Reference key concepts from the documentation.",
    docLink: "https://docs.example.com/relevant-page"
}
```

### Step 4: Create Quiz File Using Template

**CRITICAL: This is a COPY-PASTE operation from the gold standard template with minimal targeted changes.**

**Reference Template**: `fsx-ontap-sql-server-ha-quiz.html` located at:
`fsx-ontap-sql-server-ha-quiz.html` (workspace root)

**The Process**:
1. **Read the ENTIRE `fsx-ontap-sql-server-ha-quiz.html` file**
2. **Create new file in the CURRENT WORKING DIRECTORY** with the template content
3. **Make ONLY the following specific changes**:
   - Title and topic name
   - Badge label text
   - Header title and subtitle
   - Accent colors (if changing from default indigo)
   - Questions array (replace entirely)
   - Question domain badge text (in `showQuestion()` / `renderQuestion()` function)
   - Question count and exam time stats
4. **DO NOT modify**:
   - HTML structure
   - Element IDs
   - CSS class names
   - JavaScript function logic
   - Function names or signatures
   - Any algorithms

**Why this approach?**
Previous attempts to implement from scratch resulted in inconsistent quizzes with different HTML structure, missing features, and broken functionality. The ONLY reliable method is to copy the gold standard and make minimal targeted changes.

#### 4.1: Copy Template and Make Targeted Changes

**CHANGE 1 - Title** (1 location in `<title>`):
```html
<title>[Topic Name] Quiz | [Context/Certification]</title>
```

**CHANGE 2 - Header Badge** (1 location):
```html
<span class="badge">[Badge Label]</span>
```

**CHANGE 3 - Header Title** (1 location):
```html
<h1>[Quiz Title]</h1>
```

**CHANGE 4 - Subtitle** (1 location):
```html
<p class="subtitle">[Descriptive subtitle text]</p>
```

**CHANGE 5 - Question Domain Badge** (1 location in the JavaScript render/show question function):
```javascript
<span class="question-domain">[Short Topic Label]</span>
```

**CHANGE 6 - Questions Array** (1 location):
Replace the entire `const questions = [...]` array with your generated questions.

**CHANGE 7 - Doc Link Label** (in JavaScript render/show question function):
Change the documentation link text to match the documentation source:
```javascript
// For AWS docs:
"View AWS Documentation"
// For Microsoft docs:
"View Microsoft Documentation"
// For generic docs:
"View Documentation"
```

That's it for content changes.

#### 4.2: Customize Accent Colors (Optional)

**Only if you want a different color scheme than the default indigo:**

Search for ALL occurrences of these values and replace:
- `--accent-primary: #6366f1;` -> Your primary color
- `--accent-secondary: #818cf8;` -> Your secondary color
- `rgba(99, 102, 241,` -> `rgba([R], [G], [B],` (all 10+ occurrences)

**Color conversion**: Convert hex to RGB for rgba() values.

**Locations to update** (search for `rgba(99, 102, 241,`):
- `.option:hover:not(.disabled)`
- `.option.selected` (2 locations - background and box-shadow)
- `.review-table tbody tr:hover`
- `.review-table tbody tr.reviewed` (3 locations)
- `.shuffle-notice`

**If keeping the default indigo theme, SKIP THIS STEP entirely.**

#### 4.3: Update Stats (Question Count & Exam Time)

Calculate exam time: `Number of questions x 2.5 minutes`

Examples:
- 10 questions = 25:00
- 15 questions = 37:30
- 20 questions = 50:00
- 25 questions = 62:30
- 30 questions = 75:00

**Update in these locations**:

1. **Header stats bar** (2 values):
```html
<div class="stat"><div class="stat-value">[N]</div><div class="stat-label">Questions</div></div>
<div class="stat"><div class="stat-value">[M:SS]</div><div class="stat-label">Exam Time</div></div>
```

2. **Initial timer display**:
```html
<span class="timer" id="timer">[M:SS]</span>
```

3. **Initial totalQ display**:
```html
<span id="totalQ">[N]</span>
```

**DO NOT** change the JavaScript timer calculation (`timeRemaining = shuffledQuestions.length * 150`) - it calculates automatically from question count.

#### 4.4: HTML Structure (DO NOT MODIFY)

The HTML structure from the template is already correct. **DO NOT CHANGE**:
- Element IDs
- Class names
- Button order or text
- Any structural elements
- Mode selector
- Results card layout
- Review section table structure

#### 4.5: JavaScript (DO NOT MODIFY)

The JavaScript functions from the template are already correct. **DO NOT CHANGE**:
- Variable names
- Function logic
- Function names
- Element IDs referenced
- Any algorithms
- Shuffle logic
- Timer logic
- Review table logic

**ONLY change**: Replace the `const questions = [...]` array and the question domain badge text.

### Step 5: Validation Checklist

Before declaring success, verify:

- [ ] Quiz file created in **current working directory** with kebab-case filename
- [ ] All questions have valid structure (id, question, 4 options, correct index 0-3, explanation, docLink)
- [ ] `correct` index matches the actual correct option position
- [ ] All docLink URLs are valid and point to real documentation pages
- [ ] CSS accent colors are consistent throughout (if changed from default)
- [ ] HTML structure matches template exactly
- [ ] JavaScript includes ALL required functions (unchanged from template)
- [ ] Question count in header stats matches actual question count
- [ ] Exam time calculation is correct (questions x 2.5 minutes)
- [ ] Timer initial display matches exam time
- [ ] totalQ initial display matches question count
- [ ] Badge, title, subtitle are customized
- [ ] Question domain badge is customized
- [ ] Documentation link text is appropriate for the source
- [ ] Results card shows breakdown boxes (Correct/Incorrect)
- [ ] Review section has proper 5-column table
- [ ] No console errors

## Common Pitfalls to Avoid

### THE #1 MISTAKE: Not Copying the Template Exactly

**DON'T**: Try to implement from scratch or rebuild the HTML/CSS/JS
**DO**: Literally copy `fsx-ontap-sql-server-ha-quiz.html` and make minimal changes

### Other Pitfalls:

1. **Changing HTML structure** - Keep it EXACTLY as the template
2. **Changing element IDs** - Keep all IDs exactly as they are
3. **Rewriting JavaScript functions** - Copy them verbatim, only change questions array
4. **Using different CSS class names** - Keep all classes exactly as they are
5. **Removing or modifying features** - Keep shuffle, Show Answer, all navigation
6. **Forgetting to update question domain badge** - Search for the old label in the render function
7. **Not updating all color references** - If changing colors, update ALL `rgba()` values
8. **Forgetting exam time calculation** - Update in header stats AND initial timer display
9. **Not updating question count** - Update in header stats AND `<span id="totalQ">`
10. **Putting the file in the wrong location** - Always create in the CURRENT WORKING DIRECTORY
11. **Wrong correct index** - Double-check that `correct` matches the 0-indexed position
12. **Broken docLinks** - Verify URLs are real and accessible

## Example Usage

### Example 1: Technical Certification Quiz

**User**: "Create a quiz on Kubernetes networking using this doc: https://kubernetes.io/docs/concepts/services-networking/"

**Assistant Actions**:
1. Confirm: "I'll create a 20-question quiz on Kubernetes Networking with Cyan accent. Output: `kubernetes-networking-quiz.html` in current directory. Proceed?"
2. Fetch documentation and generate 20 questions
3. Copy template, replace questions and metadata
4. Create file in current working directory
5. Validate and report completion

### Example 2: Programming Concepts Quiz

**User**: "Create a 15-question quiz on Python async/await from the official docs"

**Assistant Actions**:
1. Fetch Python async documentation
2. Generate 15 questions covering asyncio, coroutines, event loops, etc.
3. Create `python-async-quiz.html` with Green accent in current directory
4. Validate and report completion

### Example 3: AWS Service Quiz

**User**: "Create a quiz on AWS Lambda from https://docs.aws.amazon.com/lambda/latest/dg/welcome.html"

**Assistant Actions**:
1. Use AWS Documentation MCP to read Lambda docs
2. Generate questions covering Lambda concepts
3. Create `aws-lambda-quiz.html` with Indigo accent in current directory
4. Validate and report completion

## Reference Files

- **Gold Standard Template**: `fsx-ontap-sql-server-ha-quiz.html` (workspace root)
- **Alternative Reference**: Any other quiz HTML file in the workspace root can serve as reference if the gold standard is unavailable

**IMPORTANT**: Always use the gold standard template as your source file to copy from. It has been verified to work correctly and contains all required features including: Learn/Exam modes, shuffle, progress bar, timer, review table with click-to-navigate, and proper results display.

## Success Criteria

Quiz is complete when:
1. File is created in the **current working directory**
2. File is a COPY of the gold standard template with only the specified changes
3. Title, badge, subtitle, and header are customized for the topic
4. Question domain badge is updated in the render function
5. Questions array is replaced with generated questions
6. Question count and exam time are updated in stats and initial display
7. Colors are updated if desired (optional)
8. All questions have valid structure and accurate content
9. All documentation links are valid
10. No structural changes to HTML, CSS, or JavaScript logic

---

## Notes

- Always use the gold standard template - do not improvise the HTML/CSS/JS structure
- Test accuracy of questions by cross-referencing documentation
- Questions should be challenging and educational, not trivial
- Explanations should teach the concept, not just confirm the answer
- If documentation is insufficient for the desired question count, tell the user and suggest a lower count
- The quiz is a standalone HTML file with zero external dependencies - it works offline
- The dark theme with accent colors provides excellent readability
