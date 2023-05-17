# cloudflare-pages-action-demo

[![publish-to-cloudflare-pages](https://github.com/remarkablemark/cloudflare-pages-action-demo/actions/workflows/publish-to-cloudflare-pages.yml/badge.svg)](https://github.com/remarkablemark/cloudflare-pages-action-demo/actions/workflows/publish-to-cloudflare-pages.yml)

[Cloudflare Pages GitHub Action](https://github.com/cloudflare/pages-action) demo.

## Setup

[Login to Cloudflare](https://www.cloudflare.com/).

### API Token

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

### Account ID

Copy your [Cloudflare's account ID](https://developers.cloudflare.com/fundamentals/get-started/basic-tasks/find-account-and-zone-ids/) by going to the [dashboard](https://dash.cloudflare.com/), navigating to **Workers**, or copying it from the browser URL:

```
https://dash.cloudflare.com/abcdef1234567890abcdef1234567890
```

Create a **New repository secret** like the previous step:

```
CLOUDFLARE_ACCOUNT_ID
```

### Pages

Go to **Pages** > **Create a project** > **Direct Upload** and name the project after your repository.

> You can also use **Connect to Git** but you'll need to disable automatic deployments on production and preview branches.

### Action

Create the workflow file:

```sh
touch .github/workflows/publish-to-cloudflare-pages.yml
```

Update the workflow:

```yaml
name: publish-to-cloudflare-pages
on: push

permissions:
  contents: read
  deployments: write

jobs:
  publish-to-cloudflare-pages:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Publish to Cloudflare Pages
        uses: cloudflare/pages-action@v1
        with:
          apiToken: ${{ secrets.CLOUDFLARE_PAGES_API_TOKEN }}
          accountId: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
          projectName: ${{ github.event.repository.name }}
          directory: public
          gitHubToken: ${{ github.token }}
```

Make sure to update the asset `directory` for your project.

Save the action and it should deploy your project to Cloudflare Pages! :rocket:

## License

[MIT](LICENSE)
