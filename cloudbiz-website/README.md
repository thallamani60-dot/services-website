# CloudBiz – Static Website Deployment (Cloud Hosting & Edge CDN)

## 1. Project overview
CloudBiz is a responsive static business landing page built with HTML, CSS and JavaScript. It is designed to be deployed on Cloudflare Pages using a GitHub repository.

## 2. Objectives
- Deploy a static website to free cloud hosting.
- Configure Git-based continuous deployment.
- Serve the site over HTTPS.
- Use Cloudflare's global edge network.
- Document the deployment and verification process.

## 3. Technology stack
- HTML5, CSS3 and JavaScript
- Git and GitHub
- Cloudflare Pages
- Cloudflare edge CDN and managed SSL/TLS

## 4. Project structure
```text
cloudbiz-website/
├── index.html
├── style.css
├── script.js
├── _headers
├── README.md
├── .gitignore
└── assets/
    └── images/
```

## 5. Run locally
Open `index.html` in a browser, or use the VS Code Live Server extension. Check desktop and mobile layouts, navigation, contact-form demo and browser console.

## 6. Push the project to GitHub
Create a new GitHub repository named `cloudbiz-website`. In a terminal opened inside this folder, run:

```bash
git init
git add .
git commit -m "Initial CloudBiz website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/cloudbiz-website.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username. If the repository already contains a README or other files, create an empty repository or follow GitHub's instructions to reconcile histories.

## 7. Deploy with Cloudflare Pages
1. Sign in at https://dash.cloudflare.com/.
2. Open **Workers & Pages** and choose **Create application**.
3. Choose **Pages** and **Connect to Git**.
4. Authorize GitHub and select the `cloudbiz-website` repository.
5. Set the production branch to `main`.
6. Choose **None** as the framework preset.
7. Leave the build command blank.
8. Set the build output directory to `.` (the repository root).
9. Save and deploy.

After a successful deployment, Cloudflare displays a public URL similar to `https://PROJECT-NAME.pages.dev`. Record the actual URL here:

**Live website:** _Add your deployed URL_

## 8. Continuous deployment test
Make a small edit to `index.html`, then run:

```bash
git add .
git commit -m "Test automatic deployment"
git push origin main
```

Open the Cloudflare Pages **Deployments** tab and confirm a new production deployment starts and succeeds. Refresh the live website to verify the change.

## 9. HTTPS and SSL/TLS verification
Cloudflare Pages provides HTTPS for its `pages.dev` address. After deployment:
- Open the live URL using `https://`.
- Confirm the browser reports a secure connection and no certificate warning.
- Check the certificate details in the browser.
- Test the HTTP endpoint and inspect its redirect:

```bash
curl -I http://PROJECT-NAME.pages.dev
curl -I https://PROJECT-NAME.pages.dev
```

Replace `PROJECT-NAME` with the actual Pages project hostname. Confirm HTTP redirects to HTTPS and HTTPS returns a successful response. Do not claim a result until you have tested it.

For a custom domain, add it under the Pages project's **Custom domains** section and follow the DNS instructions shown by Cloudflare. Enable **Always Use HTTPS** for the custom-domain zone if available. A custom domain is optional for this project.

## 10. Security headers
The `_headers` file adds browser security headers to responses served by Pages. These are additional protections; they do not replace HTTPS or guarantee that the entire site is secure.

## 11. Screenshots to include
Add genuine screenshots from your own deployment:
1. GitHub repository showing project files.
2. Cloudflare Pages build configuration.
3. Successful production deployment and generated URL.
4. Live website open over HTTPS with certificate details.
5. Cloudflare deployment history showing a deployment after a Git push.
6. Responsive website view on a narrow/mobile screen.

Suggested location: create a `screenshots/` folder and save the images there. Do not use illustrative screenshots as proof of your own deployment.

## 12. Limitations
The contact form is a frontend demonstration. It validates required fields in the browser and displays a success message, but it does not send or store messages. A backend or form-handling service is needed for real submissions.

## 13. Conclusion
This project demonstrates static website hosting, GitHub-based continuous deployment, HTTPS delivery and edge CDN distribution using Cloudflare Pages.
