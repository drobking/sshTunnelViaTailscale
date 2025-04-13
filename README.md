# SHH tunnel using tailscale

From zero to hero show you how to create SSH tunnel over the internet so you can connect to your PC or Server from wherever you want without any pain in ass
Im using Ubuntu but its okay if you using another OS just different commands but point is same

⸻

1. Install Tailscale on Both Devices

Install Tailscale on both:
	•	Your local device (laptop, phone, etc.)
	•	The remote server (the machine you want to SSH into)

# On Ubuntu/Debian
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up

Log in via browser when prompted.

⸻

2. Enable Tailscale SSH (on remote server)

Tailscale has its own built-in SSH, but you need to enable it.

On the server, run:

sudo tailscale up --ssh

Or edit Tailscale’s config on the admin panel:
https://login.tailscale.com/admin/machines

Enable Tailscale SSH and tag/authorize if required.

⸻

3. Get the Tailscale IP or device name

On your local device, run:

tailscale status

You’ll see something like:

100.101.102.103   server-name   linux   idle   online

Or just use the device hostname (e.g., server-name).

⸻

4. SSH into the remote device

If you’re using Tailscale SSH, no need to configure keys.

ssh user@server-name

or

ssh user@100.101.102.103

Replace user with the actual username on the remote machine.

⸻

5. Optional: Traditional SSH via Tailscale

If you’re not using Tailscale SSH, but just want to tunnel normal SSH:
	•	Make sure your SSH server is running on the remote machine.
	•	Use the Tailscale IP to connect like usual:

ssh user@100.x.x.x



⸻

Security Tip
	•	With Tailscale SSH, you can enforce ACLs to allow only certain users to access certain devices.

⸻
