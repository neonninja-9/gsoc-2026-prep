To address the issues raised on the Talk pages and the WMCS annual survey, here is a comprehensive draft for the updated documentation. This draft merges the necessary technical details while clarifying the distinction between Toolforge and Cloud VPS access.

### Proposed Page Update: Accessing Toolforge and Cloud VPS with PuTTY and WinSCP

#### 1. Introduction

To manage your files efficiently, upload multiple documents, or maintain complex folder structures for your Toolforge tools or Cloud VPS instances, you can use SSH-compatible file browsers (SFTP) and terminal emulators. While the command line is powerful, tools like PuTTY, WinSCP, and FileZilla provide a graphical interface that simplifies these tasks for Windows users.

#### 2. Prerequisites

Before starting, ensure you have:

* **Wikimedia Developer Account:** Your shell username (LDAP).
* **SSH Key Pair:** A private key on your local machine and the corresponding public key uploaded to [idm.wikimedia.org](https://idm.wikimedia.org).
* **Software:** Download and install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/) (which includes PuTTYgen and Pageant), [WinSCP](https://winscp.net/), or [FileZilla](https://filezilla-project.org/).

#### 3. Choosing Your Tool

* **PuTTY:** Best for command-line access (SSH terminal).
* **WinSCP:** Best for Windows-integrated file management (SFTP). It allows you to drag-and-drop files directly.
* **FileZilla:** A cross-platform alternative for those who prefer a dedicated FTP/SFTP client.

#### 4. Setting up SSH Key Compatibility

PuTTY and its suite require private keys in the **.ppk** format.

* **How to check:** Open your private key file in a text editor. If it starts with `-----BEGIN OPENSSH PRIVATE KEY-----`, it is **not** compatible with PuTTY yet.
* **How to convert:**
1. Open **PuTTYgen**.
2. Click **Load** and select your existing private key (change the file filter to "All Files").
3. Enter your passphrase if prompted.
4. Click **Save private key** to create a new `.ppk` file.



#### 5. Connecting to Toolforge

Toolforge uses **bastion hosts** (intermediary servers) to secure access. The primary entry point is `login.toolforge.org`.

**How to set up WinSCP for Toolforge:**

1. **New Site:** Select `SFTP` as the protocol.
2. **Host Name:** `login.toolforge.org`.
3. **User Name:** Your Wikimedia shell username.
4. **Advanced Settings:** * Navigate to **SSH** > **Authentication**.
* Under "Private key file," browse and select your `.ppk` file.


5. **Becoming your tool (Crucial for Permissions):**
* To edit files directly in your tool's directory, go to **Environment** > **SFTP**.
* In the "SFTP server" box, enter: `sudo -u tools.YOUR_TOOL_NAME /usr/lib/sftp-server`.
* *This ensures that any files you upload are owned by the tool, preventing "Permission Denied" errors later.*



#### 6. Connecting to Cloud VPS

Cloud VPS requires proxying through the general bastion host `bastion.wmcloud.org`.

**How to set up PuTTY for Cloud VPS:**

1. **Session:** Set "Host Name" to your specific instance (e.g., `your-instance.your-project.eqiad1.wikimedia.cloud`).
2. **Connection > SSH > Proxy:**
* **Proxy type:** `Local`.
* **Proxy hostname:** `bastion.wmcloud.org`.
* **Telnet command or local proxy command:** `plink.exe -agent -l %user %proxyhost -nc %host:%port`.


3. **Authentication:** Under **SSH > Auth > Credentials**, select your `.ppk` private key.

#### 7. Troubleshooting Permissions and Ownership

A common issue occurs when files are uploaded under your personal username instead of the tool's account. This leads to web services being unable to read or execute the scripts.

* **Identifying the issue:** If you see "500 Internal Server Error," log in via terminal and run `ls -l`. If files are owned by `your-username` instead of `tools.your-tool`, they must be reassigned.
* **The "Unified Ownership" Fix:**
If you accidentally uploaded files as yourself, you can fix them by logging into the bastion and running:
```bash
become your-tool-name
# This command reclaims ownership of all files in the tool directory
find /data/project/your-tool-name -user your-username -exec chown tools.your-tool-name:tools.your-tool-name {} +

```


* **Sticky Bit:** Toolforge directories usually have a "sticky bit" (shown as `rws` in permissions). This attempts to make new files inherit the tool's group ownership automatically. If this is missing, contact support.

#### 8. Communication and Support

If you encounter "Connection refused" or "Access denied," verify your keys at [toolsadmin.wikimedia.org](https://admin.toolforge.org/). For real-time help:

* **IRC:** `#wikimedia-cloud` on Libera.Chat.
* **Mailing List:** `cloud@lists.wikimedia.org`.

---

### Key Improvements Made:

* **Unified Intro:** Clearly explains the utility of these tools (uploading/managing structure).
* **Structured Sections:** Created distinct flows for Toolforge vs. Cloud VPS.
* **Standardized Terminology:** Consistently used "Bastion host" and linked to the Portal.
* **Key Format Guide:** Added a simple check for `.ppk` compatibility.
* **Permission Fixes:** Integrated the `sudo -u tools...` WinSCP trick and the manual `chown` fix for ownership issues.
* **Removed Ambiguity:** Specified `login.toolforge.org` as the standard host, removing the "likely set up each" phrasing.
