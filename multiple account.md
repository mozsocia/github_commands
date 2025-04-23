https://www.youtube.com/watch?v=lAPcvItvdy0&ab_channel=AyyazTech

To use multiple GitHub accounts on a single Windows machine with Git, you need to configure Git to handle different accounts based on the repository or directory. Here's a step-by-step guide:

### 1. **Generate SSH Keys for Each GitHub Account**
   - Open a terminal (Git Bash, PowerShell, or Command Prompt).
   - Generate an SSH key for each GitHub account:
     ```bash
     ssh-keygen -t ed25519 -C "your-email@example.com" -f ~/.ssh/id_ed25519_account1
     ```
     Replace `your-email@example.com` with the email associated with the first GitHub account and `id_ed25519_account1` with a unique name for the key. Repeat for the second account:
     ```bash
     ssh-keygen -t ed25519 -C "your-email2@example.com" -f ~/.ssh/id_ed25519_account2
     ```
   - If your system doesn't support `ed25519`, use `rsa` instead:
     ```bash
     ssh-keygen -t rsa -b 4096 -C "your-email@example.com" -f ~/.ssh/id_rsa_account1
     ```

### 2. **Add SSH Keys to the SSH Agent**
   - Start the SSH agent:
     ```bash
     eval "$(ssh-agent -s)"
     ```
   - Add each private key to the agent:
     ```bash
     ssh-add ~/.ssh/id_ed25519_account1
     ssh-add ~/.ssh/id_ed25519_account2
     ```

### 3. **Add Public Keys to GitHub**
   - Copy the public key for each account to your clipboard:
     ```bash
     cat ~/.ssh/id_ed25519_account1.pub | clip
     ```
   - Log in to the respective GitHub account in a browser.
   - Go to **Settings > SSH and GPG keys > New SSH key** (or **Add SSH key**).
   - Paste the public key, give it a name, and save. Repeat for the other account.

### 4. **Configure SSH to Use Specific Keys for Each Account**
   - Edit or create the SSH config file at `~/.ssh/config`:
     ```bash
     notepad ~/.ssh/config
     ```
   - Add entries for each GitHub account:
     ```
     # Account 1
     Host github.com-account1
         HostName github.com
         User git
         IdentityFile ~/.ssh/id_ed25519_account1

     # Account 2
     Host github.com-account2
         HostName github.com
         User git
         IdentityFile ~/.ssh/id_ed25519_account2
     ```
   - Save and set correct permissions for the config file:
     ```bash
     chmod 600 ~/.ssh/config
     ```

### 5. **Configure Git for Each Repository**
   - For each repository, set the user details and remote URL to use the appropriate SSH alias.
   - In the repository directory for Account 1:
     ```bash
     git config user.name "Account1Username"
     git config user.email "account1-email@example.com"
     git remote set-url origin git@github.com-account1:Account1Username/repository.git
     ```
   - In the repository directory for Account 2:
     ```bash
     git config user.name "Account2Username"
     git config user.email "account2-email@example.com"
     git remote set-url origin git@github.com-account2:Account2Username/repository.git
     ```

### 6. **Optional: Use Conditional Includes for Global Git Config**
   - To automatically apply different Git configs based on the directory, edit `~/.gitconfig`:
     ```bash
     notepad ~/.gitconfig
     ```
   - Add conditional includes:
     ```
     [includeIf "gitdir:~/path/to/account1/repos/"]
         path = ~/path/to/account1/.gitconfig
     [includeIf "gitdir:~/path/to/account2/repos/"]
         path = ~/path/to/account2/.gitconfig
     ```
   - Create separate `.gitconfig` files for each account:
     - For Account 1 (`~/path/to/account1/.gitconfig`):
       ```
       [user]
           name = Account1Username
           email = account1-email@example.com
       ```
     - For Account 2 (`~/path/to/account2/.gitconfig`):
       ```
       [user]
           name = Account2Username
           email = account2-email@example.com
       ```

### 7. **Test Your Setup**
   - Test SSH connections for each account:
     ```bash
     ssh -T git@github.com-account1
     ssh -T git@github.com-account2
     ```
     You should see a success message like: `Hi Account1Username! You've successfully authenticated...`
   - Clone, push, or pull from a repository to confirm it works.

### 8. **Troubleshooting Tips**
   - **Wrong account used**: Ensure the correct `Host` alias (e.g., `github.com-account1`) is used in the repository's remote URL.
   - **Permission errors**: Verify SSH key permissions (`chmod 600 ~/.ssh/*`) and that keys are added to the SSH agent.
   - **Caching issues**: Clear the SSH agent (`ssh-agent -k`) and re-add keys if needed.

### Notes
- If you prefer HTTPS over SSH, you can use personal access tokens for each account and set different credentials per repository using `git config credential.helper store` and manually specifying tokens.
- For managing credentials, consider using a credential manager like Windows Credential Manager or `git-credential-manager` for easier handling.

This setup allows you to seamlessly work with multiple GitHub accounts on Windows. Let me know if you need clarification or further assistance!
