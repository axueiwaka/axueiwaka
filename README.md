# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          #  - read:user
          #  - read:org
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: axueiwaka
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Europe/Kiev
          plugin_achievements: yes
          plugin_achievements_display: detailed
          plugin_achievements_secrets: yes
          plugin_achievements_threshold: S
          plugin_code: yes
          plugin_code_days: 3
          plugin_code_lines: 12
          plugin_code_load: 400
          plugin_code_visibility: public
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          plugin_sponsors: yes
          plugin_sponsors_past: yes
          plugin_sponsors_sections: goal, list, about
          plugin_sponsors_size: 24
          plugin_sponsors_title: Sponsor Me!
          plugin_sponsorships: yes
          plugin_sponsorships_sections: amount, sponsorships
          plugin_sponsorships_size: 24
          plugin_stargazers: yes
          plugin_stargazers_charts: yes
          plugin_stargazers_charts_type: classic
          plugin_stargazers_days: 14
