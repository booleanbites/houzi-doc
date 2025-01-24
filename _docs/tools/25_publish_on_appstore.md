---
title: Direct Messages
category: Tools Setup
permalink: tools/publish_on_appstore
order: 25
---



<br/>
<iframe width="560" height="315" src="https://www.youtube.com/embed/guBGjsT-SLs" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>
<br/>

# Publishing Your Houzi Flutter App on the Apple App Store

This guide walks you through the step-by-step process of publishing your Houzi Flutter app on the Apple App Store, from setting up your developer account to making your app live.

## Prerequisites
Before you begin, ensure you have the following:
- **Apple Developer Account** – A paid Apple Developer account is required to publish apps.
- **Xcode Installed** – You’ll need Xcode to build and submit your app.
- **App Store Connect Access** – This is where you’ll manage your app listing.
- **App Name & Subtitles** – A unique catchy app name and subtitle for your app.
- **App Bundle Identifier** – A unique identifier for your app.
- **App Icons and Screenshots** – Prepare all required graphics for the App Store listing.
- **Support and Privacy Policy URL** – A link to your app’s privacy policy and support page.
- **Keywords** – Keywords to make your app discoverable on AppStore.
- **Test Account** – A test account that Apple Review Team can use to test your app.

---

## Step 1: Setting Up Your Apple Developer Account
1. Visit [Apple Developer](https://developer.apple.com/) and sign in with your Apple ID.
2. Enroll in the **Apple Developer Program** by following the on-screen instructions.
3. Pay the annual $99 fee to activate your account.
4. Once approved, sign in to [App Store Connect](https://appstoreconnect.apple.com/).

---

## Step 2: Configuring Your App in App Store Connect
1. Log in to **App Store Connect** and go to **My Apps**.
2. Click the **+** button and select **New App**.
3. Enter the following details:
   - **App Name** – The name of your app as it will appear on the App Store.
   - **Primary Language** – The main language of your app.
   - **Bundle ID** – Must match the one used in your Xcode project.
   - **SKU** – A unique identifier for your app.
   - **User Access** – Set permissions if needed.
4. Under the **Distribution tab**, fill in the following:
   - **App Preview & Screenshots**, some crisp high quality screenshot of app features.
   - **App Description**, about features of the app and how it makes life easier for your users.
   - **Keywords** to help your app be discoverable in App Store.
   - **Support URL** linking to a page where users can reach for support queries.
   - **Version number and Copyright** correct version number and copyright statement.
   - **Support Contact Information** about how Apple Review team can reach if required.
   - Under **App Review Information**, provide demo account details (if required) and any special instructions.  
5. Under the **App Information** option on the left, configure subtitle, content right and age rating.
6. Under the **App Privacy** option on the left, provide **Privacy URL**, and fill out Data Safety form. It is a long process, so take your time.
7. Under the **Pricing and Availability** section, choose your app’s price tier and availability location.

---

## Step 3: Preparing Your App for Submission
1. Open **Xcode** and load your **Houzi Flutter** project.
2. Ensure the following settings are correctly configured:
   - **Bundle Identifier** matches App Store Connect.
   - **Signing & Capabilities** is set to **Automatically manage signing**.
   - **Deployment Target** matches the required iOS version.
3. Run your app on a **real iOS device** for testing.

---

## Step 4: Archiving and Uploading Your App
1. In Xcode, select **Product > Archive**.
2. Once the build process is complete, open **Organizer** and select the latest archive.
3. Click **Distribute App** and choose **App Store Connect**.
4. Select **Upload** and ensure that all app metadata is correct.
5. Click **Upload** and wait for the submission to complete.

---

## Step 5: Submitting for Review
1. Go to **App Store Connect > My Apps**.
2. Under the **TestFlight tab**, check the status of binary, if it is ready for submission. We're ready.
3. Under the **Distribution tab**, scroll down to binary section and choose the latest binary.
4. Click save on the top right.
5. Click **Add for Review**.
6. Click **Submit for Review**.

---

## Step 6: Apple’s Review Process
- Apple will review your app, which typically takes **24-48 hours** but can extend up to **7 days**.
- If the app is rejected, carefully read the feedback, make necessary fixes, and resubmit.
- If the app is approved, it will be listed on the **Apple App Store**!

---

## Step 7: Post-Publication Maintenance
1. **Monitor App Analytics** in App Store Connect to track performance.
2. **Update Your App Regularly** to fix bugs and introduce new features.
3. **Engage With Users** by responding to reviews and feedback.
4. **Optimize In-App Purchases** for better monetization.

---

## Final Thoughts
Congratulations! You’ve successfully published your **Houzi Flutter App** on the Apple App Store. Follow these steps carefully, and you’ll ensure a smooth launch process.

If you have any questions, feel free to reach out. Happy publishing!

