Sharing this note with others: https://github.com/lucbrinkman/lens-educational-content/blob/staging/Obsidian%20Setup.md
(this note is in `Lens Edu` to make sharing it easier. Most notes should be in `Lens` instead.)

- Related: [[Lens/How to organize things in Obsidian]]
## Setting up Obsidian with Lens Academy
We do our Lens Academy work in Obsidian, and synchronize them with a plugin called Relay. Obsidian uses the Markdown file format.

Steps to get started:
1. Install Obsidian https://obsidian.md/download
2. Create an Obsidian vault. This is a local folder on your pc.
	- **NEVER put your Obsidian vault in a onedrive/google drive/iCloud or other synchronization tool**. Doing so would cause many merge conflicts with our synchronization tool Relay. Additionally, our full Relay history is already backed up to Github by the server, so you don't need to worry about that either.
	- Put the folder at e.g. "C:\Users\lucbr\Documents\Obsidian Vault"
3. Go to the community plugin store inside of the Obsidian app and install Relay
4. In the Relay options, sign up and join the Lens Academy Relay server using this key: ` <ask Luc for the key> `, or see [[../Lens Academy/Relay Secret Key|Relay Secret Key]]
5. Our Relay server contains two folders: `Lens Academy` and `Lens Educational Content`. Install both

- **NEVER have your Lens Academy folder in a onedrive/google drive/iCloud or other synchronization tool.** This gives many merge conflicts in Relay. Additionally our full Relay history is already backed up to Github by the server.
### Where to put personal, non-Lens notes?
- The easiest is to set up a separate Vault to use for Personal Notes, which can be e.g. in a OneDrive/Google Drive folder for backups.
- Alternatively, see: [[#^shared-vault|Want to use one Obsidian Vault for both Lens Academy and Personal Notes?]]

### Already using Obsidian?
- The easiest is to set up a separate Vault to use for Lens Academy, and follow the steps.
- Alternatively, see: [[#^shared-vault|Want to use one Obsidian Vault for both Lens Academy and Personal Notes?]]


## 'Commentator' Plugin Quick Setup Guide
To get suggest and comments working, please add this plugin. If you're missing it, things might look cluttered as the syntax is just mixed in markdown.

### Install BRAT
1. Settings → Community plugins → Browse
2. Search "BRAT" → Install → Enable

### Install Commentator
1. Settings → BRAT → "Add Beta plugin"
2. Paste: `Fevol/obsidian-criticmarkup`
3. Click "Add Plugin"
4. Settings → Community plugins → Enable "Commentator"

### Key Commands (Cmd/Ctrl + P)
- **Toggle Suggestion Mode** — tracks all edits as suggestions
- **Add Comment** — annotate selected text
- **Accept/Reject Suggestion** — resolve individual changes
- **Open Annotation Panel** — see all comments/suggestions in sidebar

### Syntax Reference
| Type         | Markup               |
| ------------ | -------------------- |
| Addition     | `{++new text++}`     |
| Deletion     | `{--removed text--}` |
| Substitution | `{~~old~>new~~}`     |
| Comment      | `{>>your comment<<}` |
|              |                      |



# Using Templates
- Enable the *Templates* core plugin.
	- Under plugin settings, set the *Template folder location* to: `Lens/templates`
- Apply a template from the command mend (`Ctrl + P`) and select *Insert template*
## Editing Course Content
- Our Relay server automatically backs up any changes to Github every 10 seconds
- Lens Academy is synced to a private repo: https://github.com/lucbrinkman/lens-relay
	- It's a read-only repo but you can use it to check whether the stuff you do has been synced properly. Once it's on the Github, it's safe.
- **Lens Educational Content is synced to a public repo:** https://github.com/lucbrinkman/lens-educational-content
	- https://lensacademy.org loads the course content from this repo
	- Read [[README]] for more info on editing course content.


## Want to use one Obsidian Vault for both Lens Academy and Personal Notes? ^shared-vault
- Hint: this can be pretty nice. It just requires a little bit more setup.

- Alright, so the Lens Academy folders are synced by Relay.
- I recommend also creating a folder for your personal notes (whether about work, cooking, or anything else), and syncing that folder with GoogleDrive/OneDrive/iCloud.
- Here's how to do that:
- Create an Obsidian Vault in a folder that's not synchronized by e.g Google Drive, for example at: "C:\Users\lucbr\Documents\Obsidian Vault"
- Configure the Relay plugin with the Lens Academy Relay server to keep its files in a Lens Academy folder, such as "C:\Users\lucbr\Documents\Obsidian Vault\Lens Academy"
	- (you should already have this set up after [[#Setting up Obsidian]])
- Create a personal Obsidian folder that IS in a onedrive or google drive, e.g. at "C:\Users\lucbr\OneDrive\<personal folder name 1>"
- Ask Claude to help you to create a symlink (symbolic link) from "C:\Users\lucbr\Documents\Obsidian Vault\<personal folder name 2>" to "C:\Users\lucbr\OneDrive\<personal folder name 1>". (name 1 and 2 can be different, that's no problem)

- As name 2, I use _ because it's short.
- Thus, what I have is::
- `"C:\Users\lucbr\Documents\Obsidian Vault\Lens Academy"`
- `"C:\Users\lucbr\Documents\Obsidian Vault\Lens Educational Content"`
- `"C:\Users\lucbr\Documents\Obsidian Vault\_"`, which the pc routes through a symlink to `"C:\Users\lucbr\OneDrive\Personal Obsidian Vault`
- That way, my personal folder is synced with onedrive, and my Lens Academy folder is only synced with Relay
- In Obsidian, I open `"C:\Users\lucbr\Documents\Obsidian Vault"` as the vault, which shows two folders: ![[Recommended Obsidian Setup-1768916828002.webp]]
- Each just containing its files like normal folders do: ![[Recommended Obsidian Setup-1768572374976.webp]]
