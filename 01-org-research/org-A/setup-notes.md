
````markdown
# Development Environment Setup Notes

This document outlines the steps required to set up a local development environment for **OpenELIS-Global-2**.

---

## 1. System Preparation

### Ubuntu Desktop
1. Install or boot into an Ubuntu Desktop environment (20.04 or newer).
2. Update system packages:
   ```bash
   sudo apt update
   sudo apt upgrade
   sudo apt full-upgrade
   sudo apt autoremove


---

## 2. Install Required Tools

### Java

Install Java (version 21 recommended):

```bash
sudo apt install default-jdk
java -version
javac -version
```

### Docker

Install Docker CE:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install -y docker-ce
sudo systemctl status docker
```

(Optional) Allow Docker commands without `sudo`:

```bash
sudo usermod -aG docker ${USER}
su - ${USER}
```

### Docker Compose

Install Docker Compose:

```bash
sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

### Chrome (Optional)

Install Google Chrome as your default browser for testing.

---

## 3. Clone OpenELIS-Global-2 Repository

1. Fork the repository:
   [https://github.com/I-TECH-UW/OpenELIS-Global-2](https://github.com/I-TECH-UW/OpenELIS-Global-2)
2. Clone into your workspace:

   ```bash
   cd /path/to/your/workspace
   git clone git@github.com:{YourUsername}/OpenELIS-Global-2.git --recurse-submodules
   ```

---

## 4. Quick Deployment Test

In the project root:

```bash
docker-compose up -d
```

Access the app in browser:

* [https://localhost:8443/OpenELIS-Global](https://localhost:8443/OpenELIS-Global)
  You may need to dismiss the browser’s security warning.

---

## 5. Docker Compose Development Setup

### Build and Run

1. Build project:

   ```bash
   mvn clean install -DskipTests
   ```
2. Start containers:

   ```bash
   docker-compose -f dev.docker-compose.yml up -d
   ```

### Reflect Local Changes

* Frontend React code automatically hot reloads.
* For backend Java:

  ```bash
  mvn clean install -DskipTests
  docker-compose -f dev.docker-compose.yml up -d --no-deps --force-recreate oe.openelis.org
  ```

### Default App URLs

| Instance     | URL                                                                              | Credentials        |
| ------------ | -------------------------------------------------------------------------------- | ------------------ |
| Legacy UI    | [https://localhost/api/OpenELIS-Global/](https://localhost/api/OpenELIS-Global/) | admin: adminADMIN! |
| New React UI | [https://localhost/](https://localhost/)                                         | admin: adminADMIN! |

---

## 6. Native Development with Tomcat & Eclipse

### Install Tools

```bash
sudo apt install maven
```

Install Eclipse IDE (Java EE edition) and optional plugins (eGit, Lombok).

### Eclipse Setup

1. Import OpenELIS-Global-2 as existing project.
2. Add required modules (`dataexport-core`, `dataexport-api`) to classpath.
3. Configure Tomcat server in Eclipse.

### Tomcat SSL Configuration

1. Download and extract Tomcat.
2. Configure server settings for SSL using project provided keystore files.

### Common Properties and Logs

```bash
sudo mkdir /run/secrets
sudo ln -s /path/to/project/dev/eclipse_common.properties /run/secrets/common.properties

sudo mkdir /var/lib/openelis-global/logs/
sudo chmod 777 /var/lib/openelis-global/logs/
```

---

## Summary

You now have:

* A working local instance of OpenELIS-Global-2
* Docker development workflows
* Native IDE support for deeper code navigation and debugging

---

```
````
---

If you want, I can also generate a **condensed checklist** style version or turn this into a **setup script** you can run locally.
::contentReference[oaicite:0]{index=0}
```

