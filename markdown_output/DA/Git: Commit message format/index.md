  ------------ ----------------
  Created by   
  Approvers    
  Status       PUBLISHEDGreen
  Version      3
  ------------ ----------------

Sticking to a format will help us in maintaining *easier-to-read commit
history* and in *code-reviews*.

Below is the *recommended format*:

\<TYPE\>: \<SUMMARY\> \<BODY\> \<FOOTER\>

**TYPE** : feat/fix/refactor/doc/build etc.

**SUMMARY** : What is the change

**BODY** : Why is this change needed, alternative fixes considered, etc.
Give full details. Include relevant links.

**FOOTER** : Jira/Bugzilla link

(All fields are mandatory. Inspired from
[github-angular](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit)
)

------------------------------------------------------------------------

**Example:**

fix: catch \`PatternSyntaxException\` thrown when creating \`Regex\`
with invalid pattern If BE configured invalid regular-expression pattern
in \`cronetEnabledApiPaths\`, PatternSyntaxException is thrown when
creating \`Regex\` instance. This will break the interceptor flow and no
network calls can be made. Try-catch the exception and return false.
This will cause the interceptor to proceed with okhttp-path. Fixes
https://bugzilla.newshunt.com/eterno/show_bug.cgi?id=41281
