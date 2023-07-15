# FirebaseAnalyticsSetup

Goodjob on adding the Google plist properly as well as adding the Bundle ID without any typos

&nbsp;

## Initial Firebase Package Setup


1. Make sure to install the correct `Firebase Analytics` package with the Swift Package Manager. 

<img width="787" alt="Screen Shot 2023-07-15 at 3 02 06 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/bced5c45-6163-447a-af6a-3026e8baf3d9">

&nbsp;

You have to install the package named `Firebase Analytics`, not `FirebaseAnalyticsSwift`, as the latter is an extension of the main package. 
So remove the Firebase packages, reinstall them and be sure to check the right box.

[https://stackoverflow.com/questions/56718121/how-to-delete-swift-package-dependency-in-xcode-11](url)

&nbsp;

2. Remove the `import Firebase` statements at the top of your `ContentView.swift` file.
  
   Add `import FirebaseAnalytics` instead

(For more Firebase services, you'll have to repeat this process of reinstalling and then importing their respective libraries. This is a good habit as Xcode can be funky sometimes and so package errors could be resolved simply by removing and reinstalling)

&nbsp;

3. You accidentally put the `UIApplicationDelegateAdaptor` in the `ContentView` struct. It belongs in the `Saber_LibraryApp` struct!

<img width="856" alt="Screen Shot 2023-07-15 at 3 17 55 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/8c58cace-3463-4e37-a373-9530df11086b">

4. Move your AppDelegate to this same file, and add `import FirebaseCore` at the top
   
   &nbsp;
   
5. In your `GoogleService-info.plist`, set the `IS_ANALYTICS_ENABLED` to `YES`
   
<img width="1008" alt="Screen Shot 2023-07-15 at 3 24 49 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/1e49c24d-d9f5-467d-b0a8-f8bb1843ba97">


(Sidenote: I'd generally advise sticking to a whole number for your `Minimum Deployment` project version numbers, so 16.0 instead of 16.4 since packages have to be maintained often by companies in order to accomodate newer versions of Xcode projects and thats typically not the case.)

&nbsp;

6. Add this bit of code into your `ContentView` struct
   
  ```
    init() {
       Analytics.logEvent("First Log", parameters: [AnalyticsParameterItemName: "Test"])
    }
  ```

<img width="779" alt="Screen Shot 2023-07-15 at 3 32 39 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/84ab481a-cb3a-4530-a5f2-c8bf963b9ec5">

&nbsp;

7. Lastly, you want to go into the scheme editor and add this `-FIRAnalyticsDebugEnabled`
<img width="855" alt="Screen Shot 2023-07-15 at 3 46 19 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/f9db653d-ff12-453e-98db-ef42e5a32ef0">

&nbsp;

<img width="948" alt="Screen Shot 2023-07-15 at 3 46 31 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/31fae904-cb0d-4d60-9e6b-fef30ae56813">

&nbsp;

You'll know the setup was successful once you see the 'Saber Library[55933:1131344] 10.13.0 - [FirebaseAnalytics][I-ACS023016] Analytics is ready to receive events' statements in the debug console (lldb). 
You'll have to wait at least 24 hours for the events to begin showing up in your Firebase Analytics console 

[https://stackoverflow.com/questions/60140204/firebase-analytics-custom-events-not-showing-in-events-list](url)

Congratulations on fixing it! And dont forget that StackOverflow is your friend

&nbsp;
&nbsp;

# Sources

[https://firebase.google.com/docs/ios/setup](url)

[https://firebase.google.com/docs/analytics/get-started?platform=ios](url)
