# FirebaseAnalyticsSetup



Goodjob on adding the Google plist properly as well as adding the Bundle ID without any typos



## Initial Firebase Package Setup

1. Make sure to install the correct Firebase Analytics package with the Swift Package Manager. 

<img width="787" alt="Screen Shot 2023-07-15 at 3 02 06 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/bac188de-37a3-4ab2-8657-f0aba457bd44">


You have to install the package named Firebase Analytics, not FirebaseAnalyticsSwift, as the latter is an extension of the main package. 
So remove the Firebase packages, reinstall them and be sure to check the right box. [https://stackoverflow.com/questions/56718121/how-to-delete-swift-package-dependency-in-xcode-11](url)


(Removing and adding packages can be a good hbit)

2. Remove the import Firebase statements at the top of your ContentView.swift file
Add import FirebaseAnalytics instead

3. You accidentally put the UIApplicationDelegateAdaptor in the ContentView struct. It belongs in the Saber_LibraryApp struct!

<img width="856" alt="Screen Shot 2023-07-15 at 3 17 55 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/fce3e1e9-84c0-49d8-856b-08084d2dc64c">

4. In your GoogleService-info.plist, set the IS_ANALYTICS_ENABLED to YES
   
<img width="1008" alt="Screen Shot 2023-07-15 at 3 24 49 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/f96fe3ba-2dfe-4078-b274-3fbec029f02e">


I'd generally advise sticking to a whole number for your Minimum Deployment version numbers. Packages have to be maintained often in order to accomodate newer versions and thats typically not the case.

5. Add this bit of code into your ContentView struct
   
  ```   init() {
        Analytics.logEvent("First Log!", parameters: [AnalyticsParameterItemName: "Test"])
    }```
   
#Sources

https://firebase.google.com/docs/ios/setup
https://firebase.google.com/docs/analytics/get-started?platform=ios
