# FirebaseAnalyticsSetup



Goodjob on adding the Google plist properly as well as adding the Bundle ID without any typos



## Initial Firebase Package Setup

&nbsp;

1. Make sure to install the correct `Firebase Analytics` package with the Swift Package Manager. 

<img width="787" alt="Screen Shot 2023-07-15 at 3 02 06 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/bac188de-37a3-4ab2-8657-f0aba457bd44">

&nbsp;

You have to install the package named `Firebase Analytics`, not `FirebaseAnalyticsSwift`, as the latter is an extension of the main package. 
So remove the Firebase packages, reinstall them and be sure to check the right box.

[https://stackoverflow.com/questions/56718121/how-to-delete-swift-package-dependency-in-xcode-11](url)

&nbsp;

2. Remove the `import Firebase` statements at the top of your `ContentView.swift` file. Add `import FirebaseAnalytics` instead (For more Firebase services, you'll have to repeat this process of reinstalling and then importing their respective libraries. This is a good habit as Xcode can be funky sometimes and so package errors could be resolved simply by removing and reinstalling)

&nbsp;

3. You accidentally put the `UIApplicationDelegateAdaptor` in the `ContentView` struct. It belongs in the `Saber_LibraryApp` struct!

<img width="856" alt="Screen Shot 2023-07-15 at 3 17 55 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/fce3e1e9-84c0-49d8-856b-08084d2dc64c">

&nbsp;

4. In your `GoogleService-info.plist`, set the `IS_ANALYTICS_ENABLED` to `YES`
   
<img width="1008" alt="Screen Shot 2023-07-15 at 3 24 49 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/f96fe3ba-2dfe-4078-b274-3fbec029f02e">


I'd generally advise sticking to a whole number for your `Minimum Deployment` version numbers, so 16.0 instead of 16.4 since packages have to be maintained often by companies in order to accomodate newer versions of Xcode projects and thats typically not the case.

&nbsp;

5. Add this bit of code into your `ContentView` struct
   
  ```
    init() {
       Analytics.logEvent("First Log", parameters: [AnalyticsParameterItemName: "Test"])
    }
  ```

<img width="779" alt="Screen Shot 2023-07-15 at 3 32 39 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/59e53fa2-3ff9-4138-a4e6-e128965d7939">

&nbsp;

6. Lastly, you want to go into the scheme editor and add this `-FIRAnalyticsDebugEnabled`
<img width="855" alt="Screen Shot 2023-07-15 at 3 46 19 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/bdebbe38-ccc9-4322-90a7-57b1f9b28047">

&nbsp;

<img width="948" alt="Screen Shot 2023-07-15 at 3 46 31 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/652b5291-c634-4d06-a999-f231ea3eb344">

&nbsp;

You'll have to wait at least 24 hours for the events to begin showing up in your Firebase Analytics console 

[https://stackoverflow.com/questions/60140204/firebase-analytics-custom-events-not-showing-in-events-list](url)


&nbsp;
&nbsp;

# Sources

[https://firebase.google.com/docs/ios/setup](url)

[https://firebase.google.com/docs/analytics/get-started?platform=ios](url)
