
**<a href="https://github.com/saeideh-moghaddam">
<img align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=saeideh-moghaddam" />
</a>**

---

**<a href="https://github.com/saeideh-moghaddam">
<img align="center" src="https://github-readme-stats.vercel.app/api?username=saeideh-moghaddam&show_icons=true&count_private=true&include_all_commits=true" /></a>**

---

name: GitHub-Profile-3D-Contrib

on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v2
      - uses: yoshi389111/github-profile-3d-contrib@0.7.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add -A .
          git commit -m "generated"
          git push
