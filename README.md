❓Why use SSH instead of HTTPS for GitHub?

Using SSH to connect to GitHub is:
✅ Easier – You don’t have to type your username and password or personal access token every time you push or pull.

✅ More secure – SSH uses a secure key pair instead of passwords.

✅ Better for automation – Works well with scripts, CI/CD, and other tools.
🔐 In short: SSH is safer and more convenient than HTTPS for everyday Git use.


1. 🔎 Check if you already have an SSH key

# Open a terminal and run:

```Shell 

ls -al ~/.ssh

```

# If you see files like:

id_ed25519
id_ed25519.pub
known_hosts

✅ You already have an SSH key if id_ed25519 and id_ed25519.pub (or similar) exist. Go to step 4 

2. 🛠️ Generate a new SSH key (if you don’t have one)

💻 macOS / Linux/Windows (Git Bash Or Powershell )

# Run the following command (replace your_email@example.com with your GitHub email):

``` shell 

ssh-keygen -t ed25519 -C "your_email@example.com"

```
Press Enter to accept the default location (~/.ssh/id_ed25519).

Choose a passphrase (optional, but recommended).
If you don´t want a passphrase press enter to continue 


3.✅  Make sure the SSH agent is running and your key is loaded

´´´Shell 

# Start the SSH agent
eval "$(ssh-agent -s)"

# Add your SSH key to the agent
ssh-add ~/.ssh/id_ed25519

'''


4. 📋 Add your SSH key to GitHub

# Copy the contents of your public key:

``` shell 

cat ~/.ssh/id_ed25519.pub

```

# Then go to:

GitHub > Settings > SSH and GPG keys > New SSH key
Paste your key
Give it a title
Click Add SSH key


5. ✅ Test the SSH connection

# Run folllowing command: 

```Shell

ssh -T git@github.com

```

# If it's your first time connecting, you may see:

The authenticity of host 'github.com (IP ADDRESS)' can't be established.
ED25519 key fingerprint is SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
Are you sure you want to continue connecting (yes/no/[fingerprint])?

Type yes and press Enter.If everything is working, you’ll see:

Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.

6. 🧼 Remove an SSH key

# Delete from your local machine:

```Shell 

rm ~/.ssh/id_ed25519 ~/.ssh/id_ed25519.pub

```

⚠️ This will permanently delete both your private and public keys.

# Remove from GitHub:

Go to GitHub > Settings > SSH and GPG keys
Click Delete next to the key you want to remove


