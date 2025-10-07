## 1. **Why Prefer SPM Over CocoaPods?**

### 📦 SPM Benefits:

- **Official Apple support** (built into Swift & Xcode)

- **No need for** `.xcworkspace` or modifying project files

- **Lightweight** & fast (no Ruby, no `pod install`)

- **First-class CI/CD support**

- No local installation needed --- version-controlled & centralized

### ⚠️ CocoaPods Status:

- **CocoaPods is goinf into Read-only mode**\
  [https://blog.cocoapods.org/CocoaPods-Specs-Repo/](https://blog.cocoapods.org/CocoaPods-Specs-Repo/){card-appearance="inline"}

------------------------------------------------------------------------

## 2. **Validations Before Adding a Swift Package**

Always check:

  ------------------------------------ -----------------------------------------------------
  ✅ Validation                        💡 Why it matters
  **Publisher authenticity**           Use known orgs like `Alamofire`, `Firebase`, etc.
  **License**                          Make sure it aligns with your product's legal needs
  **Maintenance**                      Check activity, open issues, and update frequency
  **Version pinning**                  Prefer semantic versioning (e.g. `from: "2.0.0"`)
  **No branch-based imports**          Avoid using `branch: "main"` in production
  **Audit** `binaryTarget` **usage**   Beware of hidden/inaccessible code
  ------------------------------------ -----------------------------------------------------

note

*Commit* `Package.resolved` *for team consistency.*

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
*Commit* `Package.resolved` *for team consistency.*
:::
::::

------------------------------------------------------------------------

## 3. **Make Your Swift Framework SPM-Compatible**

### Steps:

1.  **Reorganize folder structure**:

    MyLibrary/ ├── Sources/ │ └── MyLibrary/ └── Tests/ └──
    MyLibraryTests/

2.  **Create** `Package.swift` in the root:

    // swift-tools-version:5.9 import PackageDescription let package =
    Package( name: \"MyLibrary\", platforms: \[.iOS(.v13)\], products:
    \[.library(name: \"MyLibrary\", targets: \[\"MyLibrary\"\])\],
    targets: \[.target(name: \"MyLibrary\"), .testTarget(name:
    \"MyLibraryTests\", dependencies: \[\"MyLibrary\"\])\] )

3.  **Expose public symbols** (`public class`, `public func`)

4.  ✅ (Optional) Add a Git tag like `1.0.0` to make it usable via SPM
    from other projects

## Current state of Availability

  ---------------------------- ------------------------- --------------------------------------------------------------- --------------------------------------------------------
  **Dependency**               **Version**               **Package**                                                     **Cocoapods (Old)**
  AdContextEvaluator            :branch =\> \'1.8.7\'    In house: Needs to be created                                   NA
  Alamofire                     4.9.1                    [Link](https://github.com/Alamofire/Alamofire.git)              [Link](https://cocoapods.org/pods/Alamofire)
  AmazonPublisherServicesSDK    4.4.3                    NA                                                              NA
  BSImagePicker                 2.10.3                   NA                                                              [Link](https://cocoapods.org/pods/BSImagePicker)
  DHAnalyticsiOS                :tag =\> \'DH-1.0.16\'   In house: Needs to be created                                   Link
  FBAudienceNetwork             6.12.0                   NA                                                              
  FBSDKCoreKit                  14.0.0                   NA                                                              
  FBSDKLoginKit                 14.0.0                   NA                                                              
  FBSDKShareKit                 14.0.0                   NA                                                              
  FLAnimatedImage               1.0.12                                                                                   
  Firebase/Analytics            10.25.0                  [Link](https://github.com/firebase/firebase-ios-sdk.git)        
  Firebase/Crashlytics          10.25.0                  [Link](https://github.com/firebase/firebase-ios-sdk.git)        
  Firebase/DynamicLinks         10.25.0                  [Link](https://github.com/firebase/firebase-ios-sdk.git)        
  GzipSwift                     5.1.1                    [Link](https://github.com/1024jp/GzipSwift.git)                 [Link](https://cocoapods.org/pods/GzipSwift)
  Google-Mobile-Ads-SDK         11.8.0                   NA                                                              
  GoogleAds-IMA-iOS-SDK         3.12.1                   NA                                                              
  GooglePlaces                  7.0.0                    NA                                                              
  GoogleSignIn                  5.0.2                    NA                                                              
  Hakawai                       7.1.6                    NA                                                              
  lottie-ios                    3.5.0                    [Link](https://github.com/airbnb/lottie-ios.git)                
  ReachabilitySwift                                      NA                                                              
  SDWebImage                   5.15                      [Link](https://github.com/SDWebImage/SDWebImage.git)            [Link](https://cocoapods.org/pods/SDWebImage)
  SDWebImageWebPCoder          0.1                       [Link](https://github.com/SDWebImage/SDWebImageWebPCoder.git)   [Link](https://cocoapods.org/pods/SDWebImageWebPCoder)
  SSZipArchive                                           [Link](https://github.com/ZipArchive/ZipArchive.git)            [Link](https://cocoapods.org/pods/SSZipArchive)
  SwiftLint                     \~\> 0.46                [Link](https://github.com/realm/SwiftLint.git)                  [Link](https://cocoapods.org/pods/SwiftLint)
  Texture                       3.2.0                    NA                                                              [Link](https://cocoapods.org/pods/Texture)
  ---------------------------- ------------------------- --------------------------------------------------------------- --------------------------------------------------------

As seen in the above table, many Dependencies are not SPM compatible
yet. Until the time that they are, we will need to use both SPM and
Cocoapods.
