# cloudflare-pages-action-demo

[Cloudflare Pages GitHub Action](https://github.com/cloudflare/pages-action) demo.

## Setup

[Login to Cloudflare](https://www.cloudflare.com/).

Go to [My Profile](https://dash.cloudflare.com/profile) > [API Tokens](https://dash.cloudflare.com/profile/api-tokens) > [Create Token](https://developers.cloudflare.com/fundamentals/api/get-started/create-token/) > enter **Token name**:

```
Cloudflare Pages
```

Add **Permissions**:

| Type | Service | Permission |
| --- | --- | --- |
| Account | Cloudflare Pages | Edit |

Click **Continue to summary** > **Create Token**.

Copy the API token and save it in your repository's **Settings** > **Secrets and variables** > **Actions** > **New repository secret**:

```
CLOUDFLARE_PAGES_API_TOKEN
```

Repeat the step above for **Dependabot**.

Copy your [Cloudflare's account ID](https://developers.cloudflare.com/fundamentals/get-started/basic-tasks/find-account-and-zone-ids/) by going to the [dashboard](https://dash.cloudflare.com/), navigating to **Workers**, or copying it from the browser URL:

```
https://dash.cloudflare.com/abcdef1234567890abcdef1234567890
```

Create a **New repository secret** like the previous step:

```
CLOUDFLARE_ACCOUNT_ID
```


