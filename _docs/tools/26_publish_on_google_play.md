---
title: Publishing to the GooglePlay
category: Tools Setup
permalink: tools/publish_on_google_play
order: 26
---



<br/>
<iframe width="560" height="315" src="https://www.youtube.com/embed/tiJtN8Jzbo0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>
<br/>

This guide walks you through the step-by-step process of publishing your Houzi Flutter app on the GooglePlay store, from setting up your developer account to making your app live.

## Prerequisites

Before you begin, ensure you have the following:

- **Google Play Developer Account** ($25 one-time registration fee).
- **App Name** – A unique and engaging title.
- **App Descriptions**:
  - **Short Description** (max 80 characters).
  - **Long Description** (detailed features & benefits).
- **App Assets**:
  - **App Icon** (512 x 512).
  - **Feature Graphic** (1024 x 500).
  - **At least 4 high-quality screenshots**.
- **Privacy Policy & Data Safety URLs** – A public link outlining data collection and usage.
- **Contact Email** – Displayed on the Play Store listing.
- **Android App Bundle (.AAB)** – The new standard for Play Store submissions.
- **Testers** – Google requires **at least 12 testers** to run a **14-day closed testing** before public release.
- **Test Account** – A login credential if your app requires authentication.



## Generate the Android App Bundle (AAB)

1. Open **Android Studio** and load your **Flutter project**.
2. Ensure correct configurations:
   - **Unique App ID (Package Name)**.
   - **App Icon & Splash Screen**.
   - **Branding & Theme**.
   - **Keystore Signing** (mandatory for Play Store releases).
   - **Firebase Integration** (for analytics, push notifications).
   - **Google Cloud APIs** for maps, play integrity and places apis.
3. Build the **Android App Bundle (.AAB)**:
   - Navigate to **Build > Flutter > Build App Bundle**.
   - Let it compile.
   - Locate the generated **.aab** file inside the `build/app/outputs/bundle/release/` directory.



## Setting Up Google Play Console and Creating an App
1. Log in to **[Google Play Console](https://play.google.com/console)**.
2. Create a **New App**.
3. Provide:
   - **App Name**
   - **Primary Language**
   - **App or Game**
   - **Free or Paid**
   - **Agree to some declarations**
4. Save changes.



## Preparing for Closed Testing Release
Google Requires Some Configurations Before Applying to Production
1. **Privacy & Data Safety**:
   - Declare what **user data is collected and used**.
   - Provide options for **data deletion**.
2. **App Access**:
   - If your app requires login, provide a **test account**.
3. **Ads Declaration**:
   - If your app contains ads, select **Yes**.
4. **Content Rating**:
   - Complete Google’s **content rating questionnaire**.
5. **Target Audience**:
   - Select the **appropriate age group** (e.g., 18+, Kids, General).
6. **Some App related Declarations** 
   - Is it news, health, financial or education related app.
6. **App category and Contact details** 
   - Whats your app category, and how users can contact you.
8. **Store Listing Setup** 
   - Add app name, app icon, app banner, screenshots and save.
9. Prepare for **Closed Testing**.
   - Goto  Test and Release > Closed Testing and  
   - Create New Track or use existing Alpha track.
   - Set the **Testing Countries**.
   - Choose existing email list or Add Testers to new email list.
   - Upload the binary in the **Release**. tab.
   - Create New Release.
   - Send for review.



## Waiting for Approval

- Google will review the **closed testing** release.
- This process takes **2-5 business days**.
- If rejected, Google provides reasons to fix and resubmit.



## Invite Testers to Closed Testing App
Once app is approved for closed testing. Now is the time to share link with closed testers.
1. In **Google Play Console**, go to **Testers**.
2. Add **at least 12 testers** if not already added. 
3. Copy the link for Androdi app.
4. Share the with your testers.
5. Get the app downloaded on at leaster 12 tester phones.

## Running Closed Testing for 14 Days

- **Google requires 14 days of testing** before public release.
- Monitor feedback from testers.
- Address any reported **bugs or crashes**.
- Update the app as needed and re-upload the new **.AAB file**.
- Keep the 12 testers opted in for 14 days continously. 
- After 14 days, you can proceed to production.

## Apply to Production

Once the 14-day testing is complete, it is time to **Apply for Production**.

## Release to Production
Once approved, you can release your app to Production.
1. In **Google Play Console**, go to **Production > Create Release**.
2. Select **Google Play App Signing** (recommended for security).
3. Upload your **.AAB file**.
4. Add **Release Notes** (e.g., bug fixes, new features).
5. Click **Review & Submit**.

## Google Play Review Process

- Google reviews the app within **3-7 days**.
- If rejected:
  - Review the feedback.
  - Fix the issues.
  - Resubmit the app.
- Once approved, **your app is live on Google Play Store!**



## Congratulations!

Your **Houzi Flutter App** is now published on the **Google Play Store**. Keep improving it, monitor performance, and engage with users for long-term success!

