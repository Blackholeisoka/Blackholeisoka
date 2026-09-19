name: Generate trophy card

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate trophy.svg
        uses: Erik-Donath/github-profile-trophy@feature/generate-svg
        with:
          username: ${{ github.repository_owner }}
          file: dist/trophy.svg
          token: ${{ secrets.GITHUB_TOKEN }}
          theme: dracula
          max-rows: 1
          margin-width: 8
          margin-height: 8
          no-background: false
          no-frame: false

      - name: push trophy.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: trophy-output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
