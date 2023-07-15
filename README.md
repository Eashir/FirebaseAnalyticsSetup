# FirebaseAnalyticsSetup



Goodjob on adding the Google plist properly as well as adding the Bundle ID without any typos



#Initial Firebase Package Setup

I'll be going off the sources listed at the bottom of the page. I'm starting with Step 4 of the first link I posted. 

Make sure to install the correct Firebase Analytics package with the Swift Package Manager. 

<img width="787" alt="Screen Shot 2023-07-15 at 3 02 06 AM" src="https://github.com/Eashir/FirebaseAnalyticsSetup/assets/20934684/bac188de-37a3-4ab2-8657-f0aba457bd44">

You have to install the package named Firebase Analytics, not FirebaseAnalyticsSwift, as the latter is an extension of the main package. 


So remove the Firebase package https://stackoverflow.com/questions/56718121/how-to-delete-swift-package-dependency-in-xcode-11

Reinstall and be sure to check the right box.

(Removing and adding packages can be a good hbit)


As for the 


#Sources

https://firebase.google.com/docs/ios/setup
https://firebase.google.com/docs/analytics/get-started?platform=ios
