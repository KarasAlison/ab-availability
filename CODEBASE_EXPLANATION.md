This GitHub repository serves as an automated uptime monitor and status page for websites, powered by the open-source tool Upptime.

**Core Functionality:**

The primary purpose is to monitor the availability of specified websites and present this information on a live status page. In this specific configuration, it monitors a site named "AB - DEV".

**Configuration (`.upptimerc.yml`):**

The central configuration file, `.upptimerc.yml`, dictates the behavior of the monitoring system. It defines:
- The repository owner (`KarasAlison`) and name (`ab-availability`).
- The websites to be monitored. Currently, it lists "AB - DEV", with its URL stored securely as a GitHub secret (`$AB_DEV`).
- Settings for the status website, such as its base URL (`/ab-availability`), logo, name, introductory messages, and navigation links.

**Automated Monitoring (GitHub Actions):**

GitHub Actions, defined in workflow files within `.github/workflows/` (e.g., `uptime.yml`, `response-time.yml`, `graphs.yml`), drive the monitoring process. These workflows are automatically generated and updated by Upptime based on the `.upptimerc.yml` configuration. Key actions include:
- **Scheduled Checks**: The `uptime.yml` workflow, for instance, runs every 5 minutes to check the status of the configured websites.
- **Data Collection**: Workflows gather data on response times and uptime.
- **Graph Generation**: Workflows generate visual graphs of response times.
- **Status Page Updates**: Workflows update the static files for the GitHub Pages site.

**Data Storage and Display:**

Upptime organizes the collected data into several directories:
- **`history/`**: Contains YAML files (e.g., `ab-dev.yml`) logging uptime/downtime incidents and a `summary.json` for an overview. This data is crucial for historical uptime calculations.
- **`api/`**: Stores JSON files that act as data endpoints for metrics like response times and uptime percentages over various periods (daily, weekly, monthly, yearly) for each site.
- **`graphs/`**: Holds PNG images of response time graphs for different timeframes.

The status and collected data are displayed in two main ways:
- **`README.md`**: The repository's main README file is dynamically updated to show the current overall status and a summary table for each monitored site, including embedded response time graphs.
- **GitHub Pages Site**: A full status website is hosted via GitHub Pages (accessible at `https://KarasAlison.github.io/ab-availability`). This site offers a detailed view of uptime status, historical data, and incident reports, utilizing the data from the `api/` and `history/` directories. GitHub Issues are also integrated for incident reporting.

In essence, the repository provides a hands-off, automated solution for website uptime monitoring, leveraging GitHub's infrastructure (Actions, Issues, Pages) and the Upptime framework to deliver a continuously updated status page.
