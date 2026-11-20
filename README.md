# Free GitHub VPS (SSH + Tailscale)

Temporary Linux VPS with SSH access, powered by GitHub Actions.

## Setup

1. **Add repository secrets** (Settings → Secrets and variables → Actions):

   | Secret Name         | Required | Description                                    |
   |---------------------|----------|------------------------------------------------|
   | `TAILSCALE_AUTHKEY` | Yes      | Get from https://login.tailscale.com/admin/settings/keys |
   | `VPS_USER`          | No       | Default: `vpsuser`                              |
   | `VPS_PASSWORD`      | No       | Default: `changeme123`                          |

2. **Install Tailscale** on your local machine (or your phone/tablet):
   - https://tailscale.com/download

3. **Run the workflow**:
   - Go to the **Actions** tab → select the VPS workflow → **Run workflow**

4. **Connect**:
   - Open the running workflow logs
   - Look for the **"Show connection information"** step
   - Use `ssh vpsuser@<tailscale-ip>` (or your custom user/password)

## How Long Does It Run?

- Max **~5 hours 50 minutes** (set to stay under GitHub's 6-hour limit)
- Everything is wiped when the job ends
- Re-run the workflow to get a fresh VPS

## Connect Options

**Option A — Tailscale SSH (recommended)**
```bash
ssh vpsuser@100.x.x.x
# or with password inline (install sshpass)
sshpass -p 'yourpassword' ssh vpsuser@100.x.x.x