# Deploying Quarto on Google App Engine with Identity-Aware Proxy

## Objective

- Deploy a Quarto website on App Engine, which has the advantage that the engine is turned on/off automatically ([standard environment](https://cloud.google.com/appengine/docs/the-appengine-environments))
- Use Identity-Aware Proxy to secure the website and manage users via Google IAM

## Step 1: deploy Quarto on app engine
The `app.yaml` in the root is all you need to deploy a static site on App Engine ([docs](https://cloud.google.com/appengine/docs/standard/hosting-a-static-website#creating_the_appyaml_file)). Before deploying, make sure:
- you have installed the Google Cloud CLI
- have a Google Cloud project with App Engine enabled; make sure to use the standard environment which can scale to zero instances when no requests are received ([docs](https://cloud.google.com/appengine/docs/the-appengine-environments))
- have enabled OAauth with the consent screen in the project ([docs](https://support.google.com/cloud/answer/10311615?hl=en))

 With that done, you can then run

```gloud app deploy```

from the project's root folder.

## Step 2: enable the Identity-Aware proxy

Follow the steps from [the documentation](https://cloud.google.com/iap/docs/enabling-app-engine). Using Google IAM, you can add any user that has a Google account. Note that you can [use an existing email address to create a Google account](https://support.google.com/accounts/answer/27441?hl=en#existingemail). By default, the app is only accessible to internal users (of the organization).

### Easy way to make app accessible to external users

If you want to use Google's OAuth workflow (and hence save yourself the time of building your own), you can either go through a lenghty approval process, or you can:

- Choose to go in testing mode, which allows you up to 100 users
- Make sure to add the external users (as test users) on the project's [OAuth consent screen](https://console.cloud.google.com/apis/credentials/consent)
- Add the IAP-secured Web App user role to the user in the [Identity-Aware Proxy applications tab](https://console.cloud.google.com/security/iap?tab=applications)

