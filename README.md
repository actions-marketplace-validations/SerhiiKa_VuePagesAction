# Build Vue and deploy it to Github Pages 🚀
This Action will Build your Vue Project and deploy it to Github Pages

## Getting Started 🎉
1. Create the `vue.config.js` file
2. Add this to your `vue.config.js` (and rename "YourRepoName" to your repo name)
```javascript
module.exports = {
    publicPath: process.env.NODE_ENV === 'production'
  ? '/YourRepoName/'
  : '/',
}
```
3. Create a Github Actions Workflow file and add this to it (and replace "YourGithubName" and "YourRepoName" with the names)
```yml
name: Build Vue
on: [push]
jobs:
  build_vue:
    runs-on: ubuntu-latest
    name: Build Vue
    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js '16.x'
      uses: actions/setup-node@v2
      with:
        node-version: "16.x"
        cache: "npm"
    - id: Build-Vue
      uses: SerhiiKa/VuePagesAction@1.0.4
      with:
        username: 'YourGithubName'
        reponame: 'YourRepoName'
        token: ${{ secrets.GITHUB_TOKEN }} # Leave this line unchanged
```
4. Go to Settings -> Scroll down to GitHub Pages -> Select `gh-pages` as branch and `/` as directory 

## Options 🔧
|   Name   |            Description           |     Default    | Required |
|:--------:|:--------------------------------:|:--------------:|:--------:|
| username |           Your username          |        -       |     ✅    |
| reponame |       Your repository name       |        -       |     ✅    |
|   token  | Please leave this line unchanged |        -       |     ✅    |
| gitemail |         Git commit email         | CI@example.com |     ❌    |
|  gitname |          Git commit name         |       CI       |     ❌    |
|  gitmsg  |        Git commit message        |     deploy     |     ❌    |
|   cname  |           Custom domain          |        -       |     ❌    |
|  useyarn |         Use yarn to build        |      false     |     ❌    |
