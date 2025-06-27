# 🚀 Local Drupal 10 Setup with Lando

This document provides a step-by-step guide to install and run a Drupal 10 environment using **Lando**, tailored for this project.

---

## ✅ Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop/)
- [Lando](https://docs.lando.dev/basics/installation.html)
- Git + Composer

---

## 📁 Project Bootstrap

1. Clone the Drupal Composer template:

```bash
git clone https://github.com/drupal-composer/drupal-project my-lando-drupal
cd my-lando-drupal
```

You should **not see** `web/` or `core/` yet — this is expected.

---

## 🧱 Step-by-Step Setup

### 1️⃣ Initialize Lando

```bash
lando init
```

When prompted:

- Where is your codebase? → `current working directory`
- What recipe? → `drupal10`
- Webroot? → `web`
- App name? → `lando-first`

This creates `.lando.yml` like:

```yaml
name: lando-first
recipe: drupal10
config:
  webroot: web
```

---

### 2️⃣ Start Lando

```bash
lando start
```

You’ll see some generated URLs like:

- https://lando-first.lndo.site
- http://localhost:32774

They won’t work yet — we haven’t installed Drupal.

---

### 3️⃣ Install Drupal Core

```bash
lando composer install
```

This will:
- Download `web/`, `core/`, and `vendor/` folders
- Set up Drupal core + dependencies

Now the URLs from `lando start` will work!

---

### 4️⃣ Open Installation in Browser

Visit:  
🔗 `https://lando-first.lndo.site`

Proceed with the Drupal installation wizard.

Use the following **DB connection** (from `lando info`):

| Setting         | Value       |
|------------------|-------------|
| Database name    | drupal10    |
| Username         | drupal10    |
| Password         | drupal10    |
| Host             | database    |
| Port             | 3306        |

---

## 🧩 Custom Module Installation

To add your custom module (`dataset_upload`):

```bash
mkdir -p web/modules/custom/
cp -R path/to/dataset_upload web/modules/custom/
```

Then enable it:

```bash
lando drush en dataset_upload -y
lando drush cr
```

---

## 🛠 Common Lando Commands

| Command               | Description                       |
|------------------------|-----------------------------------|
| `lando start`         | Start the environment             |
| `lando stop`          | Stop the environment              |
| `lando restart`       | Restart services                  |
| `lando rebuild -y`    | Rebuild Lando app                 |
| `lando composer <cmd>`| Run Composer inside container     |
| `lando drush <cmd>`   | Run Drush (Drupal CLI)            |
| `lando info`          | Show connection info              |
| `lando ssh`           | Shell into appserver              |

---

## ✅ Result

You now have:
- A fully running Drupal 10 site on Lando
- Composer and Drush support inside the container
- A ready-to-develop custom module (`dataset_upload`)

---

Let me know if you need DDEV setup instructions or want to add Solr, Mailhog, or Xdebug to Lando config.
