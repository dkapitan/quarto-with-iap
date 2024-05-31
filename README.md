# Deploying Quarto on Google App Engine with Identity-Aware Proxy

## Objective

- Deploy a Quarto website on App Engine, which has the advantage that the engine is turned on/off automatically ([standard environment](https://cloud.google.com/appengine/docs/the-appengine-environments))
- Use Identity-Aware Proxy to secure the website and manage users via Google IAM

## Step 1: deploy Quarto on app engine
](
The `app.yaml` in the root is all you need to deploy a static site on App Engine ([docs](https://cloud.google.com/appengine/docs/standard/hosting-a-static-website#creating_the_appyaml_file). Assuming you have already installed the Google Cloud CLI just run

```gloud app deploy```

from the project's root folder.

## Step 2: enable the Identity-Aware proxy

Follow the steps from [the documentation](https://cloud.google.com/iap/docs/enabling-app-engine). Using Google IAM, you can add any user that has a Google account. Note that you can [use an existing email address to create a Google account](https://support.google.com/accounts/answer/27441?hl=en#existingemail).


... and that's it!
