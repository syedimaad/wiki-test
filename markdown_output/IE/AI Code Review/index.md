[Comparisons between multiple AI code review
tools](https://docs.google.com/spreadsheets/d/1kaA4q04FEaHyuFNwr-dAFAU4EAL2Mcubbkf8XCdK4k4/edit?gid=0#gid=0)

## Tools that be used to review code

**AI Assistants (ChatGPT, Claude, Gemini etc):**

AI assistants can be utilized to perform initial code reviews by
analyzing the merge request (MR) diff directly. When provided with the
appropriate prompt and context, these tools can generate detailed and
structured feedback, helping identify potential issues and improvements.

#### Steps to Generate a Review Using an AI Assistant:

1.  Navigate to **GitLab → Merge Requests**.

2.  Open the merge request that requires review.

3.  In the browser URL, append `.diff` at the end of the merge request
    number (e.g., `.../merge_requests/123.diff`).

4.  This will open a plain-text representation of the MR diff. Copy the
    content and save it in a `.txt` file.

5.  Open the AI assistant of your choice and upload the `.diff` file.

6.  Provide the assistant with the below prompt and initiate the
    request.

Review the differences in this GitLab Merge Request (MR) diff file. Act
as a Lead iOS Developer, performing a comprehensive and high-quality
review of the code. Your task is to identify and explain all possible
issues and improvements, from critical bugs to minor enhancements. Use
the following checklist as a foundation, but do not limit your review to
it: 1. Spelling errors in identifiers, comments, and user-visible
strings 2. Consistency in naming conventions (types, methods, variables,
enums) 3. Potential memory leaks or retain cycles (e.g., misuse of
closures, delegates, view controllers) 4. Avoidance of hardcoded
strings---recommend localization and configuration usage 5. Logic
optimizations and algorithmic improvements 6. Code structure and
readability (grouping, comments, abstraction) 7. Thread-safety and
multi-threading risks (e.g., dispatching UI updates off the main thread)
8. UI operations on background threads (verify all UI tasks run on the
main queue) 9. Auto Layout or constraint issues for different
orientations or device types (including notch/notchless considerations)
10. Appropriate use of view/lifecycle methods (in UIKit or SwiftUI) 11.
Identification of potential security risks (e.g., insecure storage,
injection, weak permissions) 12. Adherence to SwiftUI architectural best
practices (e.g., proper state management, view decomposition) 13. Basic
code hygiene (unused code, print statements, empty/redundant methods)
This checklist serves as a starting point---you are expected to go
beyond and evaluate any other relevant areas you find important as a
senior reviewer. Review Format & Output Expectations: \* Begin with a
summary walkthrough of the diff, outlining the overall purpose and
potential impact of the changes. \* Highlight critical issues first,
followed by suggestions for enhancements and readability. \* Provide
code snippets to demonstrate both the current and improved versions: \*
Existing Code \* Suggested Improvement \* Why This Is Better \* Include
visual aids (e.g., diagrams, flow explanations) if it helps clarify
architectural or flow-level insights. \* Nitpick where
appropriate---even minor consistency or redundancy issues should be
flagged. \* Before concluding, double-check all your suggestions to
ensure they are actionable, accurate, and justified. Reference
Standards: Use your expertise and multiple sources to back your
recommendations: \* Swift API Design Guidelines \* Apple Developer
Documentation (e.g., UIKit, SwiftUI, Combine) \* Internal best practices
(if applicable) \* Industry standards in scalable iOS architecture
(e.g., MVVM, Clean Architecture, SOLID principles)

7.  We can attach the chat link or generate a text file of the AI review
    provided by the AI assistant. Below prompt can be used to generate
    the text file.

> "Please download the entire suggestions into a .txt file"

------------------------------------------------------------------------

**Performing Code Reviews Using GitHub Copilot**

GitHub Copilot can also assist with code reviews by executing a
predefined set of prompts documented in a Markdown file(.md).

**Steps to Use GitHub Copilot for Code Review:**

1.  We will create a .md file(code_review.md) which would be added in
    dev. This file will have a set of prompts that will perform the code
    review.

Prompt 1: Check the current git diff and create a relevant commit
message, Use the following prompt to generate a detailed code review:
Prompt 2: Perform a comprehensive code review on the differences in this
GitLab Merge Request (MR) diff file. Act as a Lead iOS Developer,
performing a comprehensive and high-quality review of the code. Your
task is to identify and explain all possible issues and improvements,
from critical bugs to minor enhancements. Use the following checklist as
a foundation, but do not limit your review to it: 1. Spelling errors in
identifiers, comments, and user-visible strings 2. Consistency in naming
conventions (types, methods, variables, enums) 3. Potential memory leaks
or retain cycles (e.g., misuse of closures, delegates, view controllers)
4. Avoidance of hardcoded strings---recommend localization and
configuration usage 5. Logic optimizations and algorithmic improvements
6. Code structure and readability (grouping, comments, abstraction) 7.
Thread-safety and multi-threading risks (e.g., dispatching UI updates
off the main thread) 8. UI operations on background threads (verify all
UI tasks run on the main queue) 9. Auto Layout or constraint issues for
different orientations or device types (including notch/notchless
considerations) 10. Appropriate use of view/lifecycle methods (in UIKit
or SwiftUI) 11. Identification of potential security risks (e.g.,
insecure storage, injection, weak permissions) 12. Adherence to SwiftUI
architectural best practices (e.g., proper state management, view
decomposition) 13. Basic code hygiene (unused code, print statements,
empty/redundant methods) This checklist serves as a starting point---you
are expected to go beyond and evaluate any other relevant areas you find
important as a senior reviewer. Review Format & Output Expectations: \*
Begin with a summary walkthrough of the diff, outlining the overall
purpose and potential impact of the changes. \* Highlight critical
issues first, followed by suggestions for enhancements and readability.
\* Provide code snippets to demonstrate both the current and improved
versions: \* Existing Code \* Suggested Improvement \* Why This Is
Better \* Include visual aids (e.g., diagrams, flow explanations) if it
helps clarify architectural or flow-level insights. \* Nitpick where
appropriate---even minor consistency or redundancy issues should be
flagged. \* Before concluding, double-check all your suggestions to
ensure they are actionable, accurate, and justified. Reference
Standards: Use your expertise and multiple sources to back your
recommendations: \* Swift API Design Guidelines \* Apple Developer
Documentation (e.g., UIKit, SwiftUI, Combine) \* Internal best practices
(if applicable) \* Industry standards in scalable iOS architecture
(e.g., MVVM, Clean Architecture, SOLID principles) Prompt 3: If new
files are added to the project, DO NOT MISS reviewing the new file
changes along with the existing file changes

2.  After completing your code changes (prior to committing), open
    **GitHub Copilot Chat** in your IDE.

3.  Navigate to the code_review.md file that contains your structured
    prompts.

4.  In the Copilot chat interface, ensure that **context is set to the
    code_review.md file**

5.  Execute the following refined command in Copilot Chat:

> "Read through the Markdown file and follow each prompt step by step.
> Provide a detailed, accurate, and structured code review based on the
> content."
