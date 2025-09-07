# **Ping Supabase to Prevent Pausing**

This repository contains a simple GitHub Action designed to keep a **Supabase** project alive by regularly pinging its database. This is particularly useful for projects on the free tier, which may be paused after a period of inactivity.

The workflow runs on a set schedule, performing a basic read query on a specified table to ensure the database remains active.

---

### **How It Works**

The workflow is configured to run automatically:

* **Schedule**: Runs at `9:00 AM UTC` every Monday and Thursday.
* **Manual Trigger**: Can also be triggered manually from the GitHub Actions tab.

The script uses the official `@supabase/supabase-js` library to connect to your project and execute a simple `SELECT` query.

---

### **Setup**

To use this GitHub Action for your own project, you'll need to set up two repository secrets:

1.  Navigate to your repository's **Settings > Secrets and variables > Actions**.
2.  Add a new repository secret named `NEXT_PUBLIC_SUPABASE_URL` and set its value to your Supabase project URL.
3.  Add a new repository secret named `NEXT_SERVICE_ROLE_KEY` and set its value to your Supabase **Service Role Key**.

> **Note**: This workflow uses the **Service Role Key** as it runs in a secure server environment and needs to bypass Row Level Security. **Never use the Service Role Key in your frontend code.**

---

### **Customization**

To customize the workflow, you can modify the `.github/workflows/blank.yml` file:

* **Change the Table Name**: Replace `'testtable'` in the `supabase.from('testtable')` line with the name of a table from your project.
* **Adjust the Schedule**: Change the `cron` expression to your preferred schedule. You can use a tool like [crontab.guru](https://crontab.guru/) to help you.

Feel free to fork this repository and adapt it to your needs!
