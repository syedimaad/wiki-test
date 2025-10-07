## Useful prompt examples with code context

### **A. Code Cleanliness & Readability**

  -------------------------------------------------------------------------- ----------------------------------------------
  Prompt                                                                     What It Tests
  "Refactor this ViewController to reduce code duplication."                 Detecting and abstracting repeated logic
  "Make this SwiftUI View more readable and modular."                        Extracting subviews, separating layout logic
  "Can you rename variables in this method to make their purpose clearer?"   Understanding intent and naming conventions
  "Split this function into smaller, more focused methods."                  Comprehension of SRP and logic flow
  -------------------------------------------------------------------------- ----------------------------------------------

------------------------------------------------------------------------

### **B. Architectural Improvements**

  ---------------------------------------------------------------------------- -------------------------------------------------------------
  Prompt                                                                       What It Tests
  "Move business logic out of this ViewController to make it more testable."   Separation of concerns, introduction of ViewModel/Presenter
  "Convert this feature from MVC to MVVM."                                     Understanding of iOS architectures
  "Refactor this singleton into a dependency-injected service."                Design principles and testability
  "Extract this networking logic into a reusable service layer."               Reusability and clean architecture practices
  ---------------------------------------------------------------------------- -------------------------------------------------------------

------------------------------------------------------------------------

### **C. Swift-Specific Refactoring**

  ----------------------------------------------------------------------------------- -------------------------------------------------------
  Prompt                                                                              What It Tests
  "Convert this for-loop to a more idiomatic Swift style using map/compactMap/etc."   Functional Swift knowledge
  "Use property wrappers to simplify this code."                                      Knowledge of `@State`, `@Binding`, `@Published`, etc.
  "Can you use Result types instead of completion handlers?"                          Modern Swift APIs
  "Migrate this legacy Objective-C bridging code to native Swift."                    Swift transition understanding
  ----------------------------------------------------------------------------------- -------------------------------------------------------

------------------------------------------------------------------------

### **D. SwiftUI Refactors**

  ------------------------------------------------------------------------------ ---------------------------------------
  Prompt                                                                         What It Tests
  "Break this SwiftUI View into smaller views for better preview and testing."   SwiftUI best practices
  "Refactor to remove \@State where it's not needed."                            Understanding of data flow in SwiftUI
  "Use ViewBuilder or Group to clean up this layout."                            Layout structuring in SwiftUI
  "Improve this animation code to be more declarative."                          Declarative animation design
  ------------------------------------------------------------------------------ ---------------------------------------

------------------------------------------------------------------------

### **E. Performance & Safety**

  ------------------------------------------------------------------------- --------------------------------------------
  Prompt                                                                    What It Tests
  "Detect and fix retain cycles in this Combine pipeline."                  Memory management with closures/publishers
  "Suggest optimizations for this view rendering too frequently."           View lifecycle, diffing, SwiftUI rendering
  "Can you make this async code safer using structured concurrency?"        Modern concurrency refactor
  "This ViewController leaks memory --- can you identify why and fix it?"   Static/dynamic memory analysis patterns
  ------------------------------------------------------------------------- --------------------------------------------

------------------------------------------------------------------------

### F. Project-Wide Improvements

  ---------------------------------------------------------------------- -------------------------------------------------
  Prompt                                                                 What It Tests
  "Can you suggest any modularization strategies for this app?"          Target/project organization
  "What can be done to reduce the build time of this Xcode project?"     Xcode internals, compiler flags
  "Can you convert this manual dependency into Swift Package Manager?"   Dependency strategies
  "Analyze this project and suggest any dangerous anti-patterns."        Smell detection, static code analysis awareness
  ---------------------------------------------------------------------- -------------------------------------------------

------------------------------------------------------------------------

### **G. Testing & Maintainability**

  ------------------------------------------------------------ ----------------------------------------------------
  Prompt                                                       What It Tests
  "Write unit tests for this class."                           Understanding of logic boundaries and test targets
  "Refactor this code to be more testable."                    Dependency injection, modularity
  "Suggest improvements to make this API easier to mock."      Mockability, protocol-oriented design
  "This function is hard to test --- what would you change?"   Identifying hidden side effects or entangled logic
  ------------------------------------------------------------ ----------------------------------------------------
