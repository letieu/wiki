# Use multiple github account

1. Create each ssh key for each account
2. Create `~/.ssh/config` file
```sshconfig
# default account
Host github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_account1

# account2
# use with github-account2 host
Host github-account2
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_account2
```
3. Set origin
    - for default account (`account1`), don't need change: `git@github.com:letieu/btw.nvim.git`
    - for `account2`, change host (`github.com` -> `github-account2`): `git@github.com:letieu/btw.nvim.git` -> `git@github-account2:letieu/btw.nvim.git`

4. Git config base on folder
edit `~/.gitconfig` file:
```gitconfig
# default config
[user]
	name = letieu
	email = letieu8@gmail.com

# specific config for ONE folder
[includeIf "gitdir:~/code/ONE/"]
  path = ~/code/ONE/.gitconfig

```
