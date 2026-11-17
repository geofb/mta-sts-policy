https://www.cydaura.com/knowledge-hub/github-mta-sts-guide

Create a New GitHub Repository

    Go to github.com/new
    Name it anything (e.g., mta-sts-policy)
    Set visibility to Public (required for GitHub Pages on free accounts)
    Create the repo

Create a .nojekyll File (Recommended)

    In your repo, click Add file → Create new file
    Name it exactly: .nojekyll (no extension, in the root of the repository)
    Leave the file empty (or add a single space)
    Commit the file to the main branch

Why this matters: The .nojekyll file in the root tells GitHub Pages to skip Jekyll processing and serve all files as-is. This ensures your .well-known directory and policy file are served correctly without any interference. It's best to create this first before adding other files.
Create the Policy File

    In your repo, click Add file → Create new file
    Name it exactly: .well-known/mta-sts.txt
    Paste in your MTA-STS policy (use our MTA-STS Configuration Checker to generate a sample)
    Commit the file to the main branch

Sample Policy Content:

version: STSv1
mode: testing
mx: mx1.yourdomain.com
mx: mx2.yourdomain.com
max_age: 86401

Note: Replace mx1.yourdomain.com & mx2.yourdomain.com with your actual MX records.
Enable GitHub Pages

    Go to Settings → Pages
    Under "Source," choose Deploy from a branch
    Select main branch and root / folder

Create a Custom Domain for MTA-STS

    Go to your DNS provider and create a CNAME record:

mta-sts.yourdomain.com → <username>.github.io
Link the Custom Domain in GitHub

    Back in Settings → Pages, enter your custom domain: mta-sts.yourdomain.com

Enable HTTPS Enforcement

    Wait for GitHub to issue the HTTPS certificate (usually takes a few minutes, but can take up to 15 minutes)
    Once the certificate is issued, go back to Settings → Pages
    Check the Enforce HTTPS checkbox to ensure all traffic is redirected to HTTPS
