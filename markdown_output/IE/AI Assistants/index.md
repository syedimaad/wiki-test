none

## Assistants in consideration

Widely used and suggested AI assistants for Xcode:

1.  [Github
    CoPilot](https://github.blog/changelog/2024-10-29-github-copilot-code-completion-in-xcode-is-now-available-in-public-preview/)

    1.  Mostly free of cost for unlimited prompts and responses.
        Integrates well with xcode with support for variable context
        (current file, group of files, project, etc.)

    2.  Has an agent mode that can hold more context, and can plan multi
        step solutions

    3.  *Allows custom instructions to be added to workspace as global
        to be considered by the LLM. The workspace instructions can be
        committed to git with the project for the entire team to
        access.*

    4.  Has decent number of options for LLM: GPT 4o and 4.1, Claude
        Sonet 3.5

    5.  Has issues working on the project file of a swift project

    6.  **Install using Homebrew:**

        brew install \--cask github-copilot-for-xcode

2.  [Alex Sidebar](https://www.alexcodes.app/)

    1.  Paid, only 2 queries and code completions are allowed in the
        free mode, per day.

    2.  Has slightly better outputs for code completion and creation
        (but needs to be tested more which is not possible with the
        small free query limit).

    3.  Has a varied list of options for LLMs including Open AI GPT,
        Claude, Gemini, and DeepSeek.

3.  [Code AI](https://xcode-ai.com/)

    1.  Paid, less of an agent but more of a predefined command runner.
        Similar pricing structure as Alex Sidebar --- only a few inputs
        free

    2.  No separate assistant UI to interact with, prompts need to be
        written as comments in Xcode editor

    3.  Seems rudimentary is features and use.

note

**Github CoPilot is the most useful of the considered assistants.** This
conclusion is based on basic and additional features, ease of use, LLM
options, availability of Agent Mode, and pricing.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Github CoPilot is the most useful of the considered assistants.** This
conclusion is based on basic and additional features, ease of use, LLM
options, availability of Agent Mode, and pricing.
:::
::::

## Pricing

  -------------------- ------------------ ---------------------------------------------------------------------------------------------
  **Github CoPilot**   **Alex Sidebar**   **Code AI**
                                          *Official Pricing unavailable at the moment. Got 200 INR per month from a discord comment.*
  -------------------- ------------------ ---------------------------------------------------------------------------------------------

## Read further

true
