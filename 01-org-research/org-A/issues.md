# Issue: Docker Installation Failure on Ubuntu 24.04 (Noble)

## Summary

While following the OpenELIS Global development documentation for installing Docker, the installation failed on Ubuntu 24.04 (codename: noble). The `docker-ce` package was not available after adding the Docker repository.

---

## Environment Details

* OS: Ubuntu 24.04 (Noble)
* Machine: Latitude E7470
* User: gourav
* Installation Method: As per OpenELIS Dev Environment Setup documentation

---

## Commands Executed

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt-get update

apt-cache policy docker-ce

sudo apt-get install -y docker-ce

sudo systemctl status docker
```

---

## Observed Output

* Warning: `apt-key` is deprecated.
* Repository added for: `noble`
* `docker-ce` shows:

```
Installed: (none)
Candidate: (none)
Version table:
```

* Installation error:

```
Package docker-ce is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'docker-ce' has no installation candidate
```

* Docker service not found:

```
Unit docker.service could not be found.
```

---

## Analysis

Possible causes:

1. Docker repository may not yet provide stable builds for Ubuntu 24.04 (noble).
2. The documentation uses deprecated `apt-key` method.
3. Repository addition may have been aborted during confirmation.

---

## Impact

Docker cannot be installed using the documented steps, preventing further setup of the OpenELIS development environment.

---

## Suggested Follow-Up

* Update documentation to use the modern keyring method instead of `apt-key`.
* Verify Docker support for Ubuntu 24.04.
* Provide alternative installation instructions (e.g., using official Docker convenience script or Ubuntu's `docker.io` package).

---

## Status

Open – requires clarification or updated installation steps for Ubuntu 24.04.

