🌐 ip2cname — DNS as Code for Developers

Create DNS records for yourname.ip2cname.com by simply cloning a repo and editing a config file. GitHub account = your namespace.

⸻

🚀 How It Works

ip2cname allows developers to define their own DNS zones using only a GitHub repository.

With your GitHub username, you automatically get:

*.yourgithubname.ip2cname.com

All you need to do:

✅ Steps
	1.	Clone this repo (or click “Use this template”):

git clone https://github.com/ip2cname/ip2cname.com.git
cd ip2cname.com


	2.	Edit dns_config.toml
Define your DNS records using TOML syntax:

[domain]
"${repo_owner}.ip2cname.com" = [
  { type = "A",     value = "192.0.2.1",       ttl = 300 },
  { type = "AAAA",  value = "2001:db8::1",     ttl = 300 },
  { type = "NS",    value = "nsgithub.ip2cname.com", ttl = 600 }
]

"cdn.${repo_owner}.ip2cname.com" = [
  { type = "A", value = "192.0.2.88", ttl = 300 }
]

The placeholder ${repo_owner} will automatically be replaced with your GitHub username.

	3.	Star this repo
To activate your configuration, just star this repo:
👉 https://github.com/ip2cname/ip2cname.com

⸻

📘 Example

If your GitHub username is alice, and you define:

[domain]
"abc.${repo_owner}.ip2cname.com" = [
  { type = "CNAME", value = "example.com.", ttl = 300 }
]

Then this record will be live:

abc.alice.ip2cname.com → example.com.


⸻

📎 Format Specification
	•	Supported record types: A, AAAA, CNAME
	•	TTL is optional (default: 300s)
	•	All domains must include ${repo_owner} or be subdomains of it

⸻

🛡️ Policy
	•	Only public GitHub users are supported
	•	Each user manages only their own namespace
	•	DNS records will be pulled periodically (and validated)
	•	Abuse (spam, malware, dynamic DNS) will be blocked

⸻

💬 FAQ

Q: Can I host multiple records?
Yes — just add more keys to the [domain] table.

Q: When will my records become live?
Usually within 1 minutes of starring this repo.

Q: Is this free?
Yes. Intended for developers, makers, and testers.

⸻

🧠 Why This Exists

We believe DNS should be programmable, hackable, and Git-native. No dashboards, no tokens — just clone, commit, and go.

⸻

📮 Contact

Questions or suggestions? Open an issue or email support@ip2cname.com.

⸻
