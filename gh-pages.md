Docusaurus + GitHub Pages Deployment Todo List
=============================================

Project Folder: project
GitHub Repo: https://github.com/samiceto/hackathon_book
Project Branch: 002-physical-ai-course
Deployment Branch: gh-pages

1. Project Setup
----------------
- Create Docusaurus project inside project folder:
  npx create-docusaurus@latest project classic
- Ensure package.json exists inside project/
- Install dependencies:
  cd project
  npm install

2. Configure Docusaurus
-----------------------
- Open project/docusaurus.config.js
- Update the following fields:
  url: 'https://samiceto.github.io',
  baseUrl: '/hackathon_book/',
  organizationName: 'samiceto',
  projectName: 'hackathon_book',
  trailingSlash: false
- Save changes

3. First-Time Deployment Fix (gh-pages branch)
----------------------------------------------
- Create gh-pages branch manually (one-time):
  cd D:\Quarter-4\spec_kit_plus\hackathon
  git checkout --orphan gh-pages
  git rm -rf .
  echo "Init gh-pages branch" > index.html
  git add index.html
  git commit -m "Initialize gh-pages branch"
  git push origin gh-pages
- Go back to working branch:
  git checkout 002-physical-ai-course

4. Build and Deploy
-------------------
- Set GitHub username environment variable (PowerShell):
  $env:GIT_USER="samiceto"
- Build Docusaurus project:
  npm run build
- Deploy to GitHub Pages:
  npm run deploy
  (Docusaurus will automatically update gh-pages branch)

5. Optional First-Time Deployment Alternative
---------------------------------------------
- Delete old gh-pages branch on GitHub:
  git push origin --delete gh-pages
- Deploy again (Docusaurus will recreate branch)

6. Testing Locally
------------------
- Stay on project branch (not gh-pages):
  git checkout 002-physical-ai-course
  npm run serve
- Verify local build at http://localhost:3000

7. GitHub Pages Settings
------------------------
- Go to GitHub → Repository → Settings → Pages
- Source: gh-pages branch
- Folder: / (root)
- Site URL: https://samiceto.github.io/hackathon_book/

8. Important Notes
------------------
- Do not run npm run serve on gh-pages branch (static files only)
- Do not merge project branch into gh-pages
- Future deploys:
  $env:GIT_USER="samiceto"
  npm run build
  npm run deploy
  (updates gh-pages automatically)
